.. role:: boldblue
   :class: boldblue

.. role:: captiontext
   :class: captiontext

===========
Fenced Area
===========

Optimization is applicable in a variety of different disciplines from physics to construction. It can also extend to 2-D, 3-D or even higher orders of dimension. For this example, however, we will keep things simple and formulate an optimization problem in the 2-D space with something you might even have in your own backyard: a fence!  

Perhaps you want to start a garden or contain an area for your dog to play in, the question lies in how large you can make the space contained by the fence. It would be most beneficial to have the largest amount of space, but it is unreasonable to build a fence around your entire street. Think about what would be limiting for this project, some of the most important factors would be space, amount of material, and cost. With this, you have an optimization problem, but let’s phrase it in more formal terms that you have learned so far.

.. dropdown:: What is the objective?
   :icon: question
   
   Maximizing the area 
.. dropdown:: What are the design variables?
   :icon: question
   
   Dimensions of fence and the shape of the fence
.. dropdown:: What are the constraints?
   :icon: question
   
   Available fencing material (i.e. the perimeter), cost, and space
    
Set-up
``````
We’ll now look at how to set up an optimization problem and potential methods of solving it. To keep things simple, we will only be looking at one of the three possible constraints – available fencing material.  

Here is the explicit problem: Design a rectangular fence with the largest area possible given 30 feet of fencing.  
*Objective: Maximizing area 
*Design variables: length, width 
*Identify constraints: A limited amount of fence available 

With each component of the optimization problem laid out, think about ways you could solve the problem. Bear in mind that there is more than one way to arrive at the solution!

.. figure:: images/FencedArea/FencedAreaFormulation.svg
      :width: 300px
      :alt: 
      :align: center

      :captiontext:

      ..

Solution 
`````````
Before beginning to solve the problem, the question should be translated to a mathematical form. We define the variables that are changing and set up equations that relate them together. Here, the length of fence provided can be thought of as the perimeter which is a known equation for a rectangle. The inequality represents that we have at most 30 feet of fence but less can be used.  

.. math::

   \begin{gathered}
   \text{Variables}\\
   l = \text{length of fence}\\
   w = \text{width of fence}\\
   A = \text{Area of fence}\\[1em]
   \text{Total Perimeter}\\
   2l + 2w = P\\[1em]
   \text{Area}\\
   Area = l \cdot b\\[1em]
   \text{Inequality}\\
   P \leq 30
   \end{gathered}


Here are a few ways to approach the problem, the most straightforward being using sampling.  

Sampling
````````
Using the equations above, the solution can be found by plugging in numbers for a and b until the largest area is found that satisfies the perimeter constraint. Therefore, we will pick a value for the length and a value for the width and using the equations from above, calculate the perimeter and then the area. If the perimeter condition cannot be met, then the area value is not calculated.  

.. list-table:: 
   :widths: 50 50 50 50
   :header-rows: 1

   * - l
     - w
     - Perimeter
     - Area
   * - 2
     - 4
     - 12
     - 8
   * - 7
     - 11
     - 36
     - 

However, this method takes a long time, and is tedious. To simplify the problem, we can use intuition to know that the largest area will use all the available fence, so the perimeter is kept constant. This is an active constraint, and the design space will shrink as a result, leaving fewer numbers to have to go through to determine the answer. From there, a and b can vary so the perimeter adds up to 30 and figure out what the resulting area will be.

.. list-table:: 
   :widths: 50 50 50 50
   :header-rows: 1


   * - Perimeter
     - l
     - w
     - Area
   * - 30
     - 1
     - 14
     - 14
   * - 30
     - 2
     - 13
     - 26
   * - 30
     - 3
     - 12
     - 36
   * - 30
     - 4
     - 11
     - 44
   * - 30
     - 5
     - 10
     - 50
   * - 30
     - 6
     - 9
     - 54
   * - 30
     - 7
     - 8
     - 56
   * - 30
     - 8
     - 7
     - 56
   * - 30
     - 9
     - 6
     - 54

From this iteration, we find that a length of 7 and a width of 8 will give us the largest area. However, this is with the constraint that our sides are integers or whole numbers. If we can have the sides be fractions and add another row it is found that a length and width of 7.5 has the largest area of 56.25. This may not seem obvious, but by looking at where the area reaches the largest value before decreasing again, it means that the correct values are at that point. This visualizes the concept of derivatives!  

Another way of thinking about it is to intuit that the largest area of a rectangle will always be a square. We can change our equations to reflect this constraint. 

.. math::

   \begin{gathered}
   l = w\\
   2l + 2w = 30\\
   4l = 30\\
   l = 7.5
   \end{gathered}


Without keeping the perimeter constant and noticing that a square would have the largest area, using a trial-and-error method seems tedious, especially if we were to tackle a problem with more constraints than this. That's why some problems are being solved using an algorithm. An algorithm can be coded so that a computer solves each combination of values and outputs the correct answer. Click on the dropdown to learn more about algorithms

.. dropdown:: Algorithm
   :icon: light-bulb
   
   Merriam Webster defines an alogorith #ADD HYPERLINK as a procedure for solving a mathematical problem in a finite number of steps that frequently involves repetition of an operation. Commonly in computer programming an algorithm automatically does a series of steps repeatedly until it determines an answer. It can also typically be easily modified to fit a different set of constraints or design space.  

Graphically
```````````
Another approach to solving this problem is graphically and with a little bit of algebra. Looking at the equations formulated previously, a new equation can be formed by solving one variable for the other. If you have learned how to solve a system of equations try this out for yourself first before seeing the answer.  

.. math::

   \begin{gathered}
   2l + 2w = 30\\
   2l = 30 - 2w \\
   w = \frac{(30-2l)}{2}\\
   w = 15-l
   \end{gathered}

Now we have a in terms of b. This can then be substituted in the area equation as follows: 

.. math::

   \begin{gathered}
   lw = Area\\
   (15-b)b = Area\\
   15b - b^2 = Area\\
   \end{gathered}

It’s quadratic! You may have seen it written as ax2  + bx + c = 0, the same as our equation if variables are rearranged.   

This equation can then be plotted, and the max will be at the peak of the parabola.  

.. figure:: images/FencedArea/Parabola.png
      :width: 1000px
      :alt: 
      :align: center

      :captiontext:

      ..

This is what we call a global maximum as discussed in previous sections.  

To visualize this relationship, try to achieve the same values using the applet below.

*INSERT GEOGEBRA HERE*

There are other ways to solve this problem, if you are familiar with calculus explore more in the dropdown.

.. dropdown:: Calculus Based Solution
   :icon: light-bulb
   
   A derivative is the slope of the tangent line at a specific point of a function. Hence, the greater the derivative at a point the greater the slope. At a critical point, the derivative is zero and taking a second derivative tells us if it is a min or max. This is useful in optimization since a derivative of 0 means that there is a change in slope in the function. As seen in the table method, the derivative at the point where the max is would be 0 since it changes from increasing to decreasing areas. Therefore, if we know how to take the derivative of our mathematical for area and set it equal to 0 we can find the point at which the area is the max.  

   .. math::

      \begin{gathered}
      Area = 15b - b^2\\
      \frac{dArea}{db} = 15 - 2b\\
      0 = 15 - 2b\\
      b = 7.5
      \end{gathered}
   
We have arrived at the same solution as the other methods! As we can see, taking the derivative is often a very quick and easy way to get to a maximum and even a minimum value. It will also tell us if there is more than one point at which there is a maximum and minimum. 

Conclusion
``````````
Optimization is not just a tool that mathematicians and engineers can use. It can be applied to the simplest of problems that you may need to solve in your everyday life. It also allows different answers to be ascertained by changing the constraints and design parameters. In this example, we built a continuous rectangular fence, but in real life we might want to build a fence with the house as one of the sides so a new constraint would be having one side be a constant value. We could also remove the constraint of the fence being rectangular, perhaps a circle or a hexagon would allow for a greater area. Optimization allows us to solve for a variety of possibilities and by following the same methodology, one solution’s approach can easily be modified to come to a different answer.  

In the next sections we’ll take a look to see how optimization can have physics-based applications.  
