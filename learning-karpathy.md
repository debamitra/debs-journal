## Math is Hard (and so is AI)


I have been struggling with basics of Mathematics and learning Math for a while now. I have created endless plans using chatGPT and other llms, tried following them, got lost or bored after a while, stopped then restarted all over again and each time, it feels like I have made no progress at all.

2 months ago, I decided I wanted to learn about NNs from Karpathy’s Zero to Hero series. Before jumping in, I created a pre-requisite list of math concepts, linked them to Khan Academy tutorials and went through them one by one. Basics of calculus. Concepts like Limit, Slope, Derivative, Chain Rule  Partial Derivatives, Gradients etc were ticked off one by one. I felt like I understood them, and then came back and was like..."What is a Slope again?"

I eventually finished my "Math for Karpathy" list and started the first video , introduction to NN using micrograd. And wow, did it make sense now. 

The idea seems to be that neural nets are nothing but a mathematical expression or function that maps inputs to outputs. We train it with example inputs and expected outputs to fit a function to the data, then use that learned function to give us predicted outputs for new inputs. That's what I understood so far.

I struggled with backpropagation. What exactly was it? Karpathy manually built an expression using classes and objects where each operand was a data point. He then calculated the partial derivative of the final output with respect to each of the nodes. All of these partial derivatives together form the gradient of the expression. Then he created a loss function and generated a value. The objective became to reduce the loss by tweaking the weights and biases. Tweak in what way, and why? Use the gradient values to increase or decrease the weights and biases to get an output closer and closer to the target. Multiple iterations give you the desired parameterised function, which is then ready to predict outputs given new inputs.

So that was a tiny little neural network which I am trying to understand intuitively first. Then more rigourously with time.

Math is challenging and hard to stick with over time. But I understand that even consistency doesnt have to be perfect. Learning can be approached as a world of exploration and knowledge-building thats fun and satisfying in its own particular way. 

I am not "good" at math. But I feel happy when I am inside that world, discovering and learning slowly.

#### Linking the resources mentioned below:
- [Karpathy's Micrograd tutorial](https://www.youtube.com/watch?v=VMj-3S1tku0&list=PLAqhIrjkxbuWI23v9cThsA9GvCAUhRvKZ&index=1)
- [Math Pre-requisites to Karpathy's tutorial](https://docs.google.com/document/d/1Kz7A0SCdLGHCu-WA5K9U5xhKTCbEUB7-WCs1g-aC2kc/edit?tab=t.0)
