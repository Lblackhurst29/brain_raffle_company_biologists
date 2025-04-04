Find here the code for the brain based raffle for [L2D](https://learntodiscover.ai/) used at the amazing conference put on by The Company of Bioligsts @ 100. 

The code runs in a jupyter notebook making use of a .obj file that contains the structure to make a mesh of a brain in plotly. The file is included in the repo but it can also be found through this [blog](https://neurosnippets.com/posts/interactive-network/).

A write up of the raffle can be found [here](https://learntodiscover.ai/blog/) or it has been copied out below for reading with this repo.

# Brains and Planes: Picking a winner at The Company of Biologists @ 100 Conference

![cuddly brains](/src/brain_raffle_company_biologists/conference_100/pictures/pic1.jpg)

At L2D, we’re all about brains; growing them, nurturing them, and giving them away to biologists! As mentioned in our previous blog post [here](https://learntodiscover.ai/l2d-at-the-the-company-of-biologists-100-conference/), our custom cuddly brains were a hit at the recent Company of Biologists @ 100 Conference, disappearing from our stall within the first few days! This prompted us to quickly come up with a raffle to prevent disappointment (and an empty stall).

However, at L2D, we didn’t want to rely on a standard online name picker. We’re all about taking on the challenge ourselves, using coding to meet our specific needs. So, Dr Adam Lee and I (Dr Laurence Blackhurst) put our heads together and thought up an idea that best represents our love of brains and machine learning. Thus was born the brain-space raffle!

After some failed attempts to create a brain from scratch using the Python package Plotly, I did what any coder would do, scour the internet for others' solutions to the problem. Borrowing from [Matteo Mancini’s work](https://neurosnippets.com/posts/interactive-network/), I was able to create a realistic 3D brain mesh using a `.obj` file coloured with out very own L2D pink. With the brain branding in place, we just needed a method to map our participants into this 3D space and then select a winner.

![brain mesh](/src/brain_raffle_company_biologists/conference_100/pictures/pic2.jpeg)

Much like datasets that power machine learning, our participants are integral to L2D’s future. So, I translated each participant into a three-feature data point with x, y, and z coordinates randomly assigned in the 3D space. Now I had my participants in a hypothetical space, they could now be selected.

![brain with points](/src/brain_raffle_company_biologists/conference_100/pictures/pic3.jpeg)

For inspiration, I turned to one of the workhorses of classical machine learning: linear regression. When fitting a line to a set of data, the model calculates the error of each point relative to the predicted hyperplane (typically using the [mean squared error](https://en.wikipedia.org/wiki/Mean_squared_error) as a measure of average error). With each randomly generated hyperplane, one training data point will always have the lowest error (bias). So, I decided that the participant closest to a hyperplane would be the winner!

![line of best fit](/src/brain_raffle_company_biologists/conference_100/pictures/pic4.jpeg)

With that idea, all that needed coding was a random produced hyperplane that would bisect the 3D space, followed by a calculation of each participant’s distance to the plane. Each participant’s data point information was stored in a dictionary alongside their contact details. Here’s what it looks like in its final form!

![all together](/src/brain_raffle_company_biologists/conference_100/pictures/pic5.jpeg)

With it all in place, all we had to do was run it 13 times to find our winners. If you’d like to look at the code behind the project, it can be found on my GitHub [here](). It comes with a dummy participant data generator, so you can play around with it straight away.