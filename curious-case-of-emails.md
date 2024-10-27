## The Journey of an Email: From Code to Inbox

  

_Recently, one of my junior colleagues came to me, puzzled about why emails weren’t being triggered in the development environment. It worked perfectly on their local machine. They had a Node.js server hosted on a GKE pod, using Nodemailer to send emails from one Gmail ID to another. The code looked straightforward._

```javascript
const nodemailer = require("nodemailer");

class EmailService {
  constructor() {
    this.transporter = nodemailer.createTransport({
      host: "smtp.gmail.com",
      secure: false,
      auth: {
        user: "<email-id>",
        pass: "<app-password>",
      },
    });
  }
}
```
  
In this setup, Nodemailer’s default behavior would be to use port **587** for SMTP if secure is set to false.


After discussing what they had already tried, I learned they had:
- Validated the firewall rules, allowing SMTP ports - 587 and 465 to be accessed.

- Checked connectivity from within the pod to smtp.gmail.com on port 587.

- Confirmed that emails were being sent correctly when triggered locally.

- Reviewed logs but didn’t find any leads.


I suggested we take another look at the firewall rules. Once we started investigating, I noticed that on GCP’s page, there was a warning about **outbound connections to port 25 being disabled by default**. That made me suspect that the application might be trying to use port 25 instead of 587, and getting blocked in the process.

  
Not being too familiar with Nodemailer, I did a quick search (and asked GPT) to see what might be happening, and I came up with a few things to try:

- **Enable debug logs** in Nodemailer with this config:

```javascript
this.transporter = nodemailer.createTransport({
    host: "smtp.gmail.com",
    secure: false,
    ......
    debug:  true, // show debug output
    logger:  true // log information in console
});
```

  
- **Explicitly specify port 587** in the configuration to ensure Nodemailer doesn’t attempt to use port 25.

  
Above fix resolved the issue. The root cause as per GPT was due to some unintended fallback behavior with ports, especially when running on a cloud platform like GCP (Need to explore further to find details of the root cause). 

Okay cool, next I read a little bit about what is the SMTP protocol and then tried to figure out how does an email really travel all the way from my nodejs server into a gmail inbox?

**Here's the short version:** 
  My Node.js server is acting as the email client here, so first, it sets up a TCP connection with Gmail's SMTP server. The Gmail SMTP server then authenticates the sender's email and password and receives the email request, which includes the sender, recipient, subject, body, and any other details.  

<div align="center">
    <img src="https://github.com/user-attachments/assets/8bb9efde-1d8a-4b30-9cdd-b8b79c63607d" alt="WhatsApp Image 2024-10-26 at 10 44 19 PM" width="400" />
</div>

Once the Gmail server has the data, it closes the connection with my Node.js server and sends the email over to Gmail's internal systems for security checks and further processing. From there, the email heads into a queue and eventually gets picked up and delivered to the receiver's inbox.

And that, my friend, is the journey of an email—from code to inbox!

