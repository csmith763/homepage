.. role:: boldblue
   :class: boldblue

.. role:: captiontext
   :class: captiontext


==========================
Principles of Optimization
==========================

Now that you have been introduced to the foundational concepts of optimization, this post will describe optimization from a more mathematical perspective. From the previous section, you may recall that the primary goal of optimization is to minimize or maximize an objective function. But what does it mean for something to be a :boldblue:`minimizer`? 

----------------------
Concept of a Minimizer
----------------------

To explain the concept of a :boldblue:`minimizer`, let’s consider a simple example of a ball that can roll along a curved track, as shown below. The ball is constrained to always be on the surface of the track, and it must remain within the two walls on either side of the track. The ball starts at the top of the hill, as shown with the blue, solid circle. Then, it might roll and settle at either one of the positions shown with the red, hatched circles. If you consider both, the :boldblue:`global minimizer` is the position on the left, as this is when the ball reaches its lowest point across all options. However, the position on the right is an example of a :boldblue:`local minimizer`, as this position is the lowest point within a small region around the point. For optimization problems, we want to find the :boldblue:`global minimizer`, as this corresponds to the smallest value of the objective function. However, it is possible that we conclude at a :boldblue:`local minimizer`, such as when the ball moves to the position on the right. 

.. figure:: images/1_MovingBallExample.svg
   :figwidth: 100 %
   :alt: example of a ball on a curved track, demonstrating the idea of global and local minimizers
   :align: center

   :captiontext:`Global and Local Minimizers for a Ball on a Curved Track`

.. dropdown:: Mathematical Notation: global and local minimizers
   :icon: number

   To define the concept of global and local minimizers mathematically, consider a function :math:`f(x)`, which might be the height of the ball on the track as a function of its location on the track. A global minimizer is defined such that :math:`f(x^* )≤f(x)` for all :math:`x`, where the “star” denotes the location of the minimizer. In the example above, this is the ball’s position on the left, since the height at that point is less than the height at any other point on the surface. A local minimizer is defined as :math:`f(x^* )≤f(x)` for all :math:`x` in some neighborhood :math:`\mathcal{N}`, which is a small region around the point. Again, in the previous example, this is the ball’s position on the right, since there is a region around that point where the ball’s height is locally less than neighboring positions, but it is not lower than all possible points on the track.

---------------------
Concept of a Gradient
---------------------

While the position of the ball allows us to determine its height, another important piece of information is the slope of the surface at a given position. At each point along the surface, the :boldblue:`gradient` is equivalent to the slope of the surface that the ball can move along. The :boldblue:`gradient` is mathematically represented by :math:`\nabla f(x)`, and it always points uphill, which is opposite to the red arrows shown in the previous image. 

To gain an intuition for the :boldblue:`gradient`, experiment with the two GeoGebra applets embedded below. For this first applet, the scenario of the ball moving on the curved track is mimicked. The orange point can be dragged along the curved surface between the two boundaries, and, as the point moves, the red arrow representing the :boldblue:`gradient` of the function changes size and direction. You can also toggle to view the :boldblue:`descent direction`, which will be introduced later in this section.

.. ggb:: skys5x3g
    :width: 800
    :height: 600
    :zoom_drag: true
    :full_screen_button: true

This second applet increases the dimension of the problem by one, as now the point can be moved both horizontally and vertically. The applet is divided into two separate view panes. On the right, you can see the surface of the objective function, which in this case does not have a well-defined meaning. However, for the purposes of this example, you can again consider the objective function as the altitude, which is the value in the :math:`Z` direction. The view on the left shows the contour plot of the function on the right. Here, the curves drawn indicate the locations where the function has a constant value, and the values are shown next to the curves. The benefit of a contour plot is that it allows for viewing a three-dimensional surface in a two-dimensional space. Again, the orange point can be dragged throughout the two-dimensional space, and the :boldblue:`gradient` will update as the point moves. The position of the orange point will also update in the right pane to help with understanding the two visuals.

.. ggb:: ww2g6esc
   :width: 800
   :height: 600
   :zoom_drag: true
   :full_screen_button: true

In both of these applets, it is important to observe that the :boldblue:`gradient` of the function always points up a hill or in the direction of increasing function value. Now, how does information about the gradient get utilized for optimization? 

-----------------------------------
The Gradient's Role in Optimization
-----------------------------------

In the context of optimization, the :boldblue:`gradient` plays an important role in determining what direction the optimizer will move our current design point. 

Consider again the example where we want to minimize the ball’s height. Recalling that the :boldblue:`gradient` tells us the direction of maximum increase and points uphill, this tells us a direction that we do not want to go! Therefore, during optimization, we want to move in :boldblue:`descent directions`, which are directions that will point us towards :boldblue:`minimizers`. 

Now, in all three of the examples that have been explored so far, particularly in the two applets, you may have noticed something interesting that happens to the :boldblue:`gradient` at :boldblue:`minimizers` (or maximizers). If you have not noticed this yet, feel free to scroll back and up and experiment before continuing! 

.. figure:: images/2_MovingBallExample_Gradient.svg
   :figwidth: 100%
   :alt: example of a ball on a curved track with a prompt to consider the relationship between minimizers and the gradient value
   :align: center

   :captiontext:`What Happens to the Gradient when the Ball is at a Minimizer?`

For all the examples above, and for all functions in general, the value of the :boldblue:`gradient` at a :boldblue:`minimizer` will be zero. Thinking about this intuitively, if the ball is already at the bottom of the hill, then there is nowhere else that it can move such that the function value decreases further!

.. dropdown:: Key Idea: First-order Necessary Conditions
   :icon: light-bulb

   This idea that establishes a relationship between a point being a :boldblue:`minimizer` and the value of the :boldblue:`gradient` is known as the :boldblue:`first-order necessary conditions`. Mathematically, this is written as follows 

                     :math:`x^*` is a local minimizer :math:`\Rightarrow \nabla f(x^*)=0`

So, from a high-level perspective, when optimizing, we want to move the design point in :boldblue:`descent directions` until we reach a :boldblue:`minimizer`, where the value of the :boldblue:`gradient` at that point is zero.

.. dropdown:: Key Idea: the benefit of convex functions
   :icon: light-bulb

   Consider once more the example of the ball on the track. In this image, there are two minimizers: one on the left side of the hill and one on the right. What happens if the ball ends up at the point on the right? This point is still a minimizer, so the gradient will be zero. However, as we can see graphically, this is not the global minimizer for the problem, which means that we have not found the best solution. For many problems, the design space cannot be visualized like this, so it can be hard to determine if a minimizer is the global minimizer. However, for :boldblue:`convex functions`, there is a guarantee that a local minimizer is the global minimizer, as there is only one for the problem! As a result, :boldblue:`convex optimization` is a special subset of optimization where the goal is to create these :boldblue:`convex functions` so that global minimizers can be found. 

Now that you are familiar with the concepts of gradients, minimizers, and descent directions, the next sections will dive into a few specific examples of optimization to help introduce these ideas in action for real problems. When thinking through the examples, try to connect the ideas that you learned in this section with the practical task of solving the problems to solidify the underlying theory! 

-------------------
Test your Knowledge
-------------------

.. admonition:: Q1: What does it mean when a point is called a "minimizer" of a function?

      .. raw:: html

         <form class="quiz-form" data-answer="It is where the function reaches its minimum possible value">
           <label><input type="radio" name="q1" value="It is where the function reaches its minimum possible value"> It is where the function reaches its minimum possible value</label><br>
           <label><input type="radio" name="q1" value="Where there is zero value of the function"> Where there is zero value of the function</label><br>
           <label><input type="radio" name="q1" value="This is where the function is changing from decreasing to increasing"> This is where the function is changing from decreasing to increasing</label><br>
           <label><input type="radio" name="q1" value="It's where the function intersects with the x-axis"> It's where the function intersects with the x-axis</label><br>
           <br>
           <button type="button" onclick="submitAnswer(this)">Submit Answer</button>
          <p class="feedback"></p>
        </form>

.. admonition:: Q2: In gradient descent optimization, how is the gradient used?
    
      .. raw:: html

         <form class="quiz-form" data-answer="To achieve a minimum, we move in the opposite direction of the gradient">
            <label><input type="radio" name="q2" value="To find a maximum, we move in the direction of the gradient"> To find a maximum, we move in the direction of the gradient</label><br>
            <label><input type="radio" name="q2" value="To achieve a minimum, we move in the opposite direction of the gradient"> To achieve a minimum, we move in the opposite direction of the gradient</label><br>
            <label><input type="radio" name="q2" value="Random number generator"> To determine critocal points, we set the gradient to zero</label><br>
            <label><input type="radio" name="q2" value="To determine the second derivative of the gradient"> To determine the second derivative of the gradient</label><br>
            <br>
            <button type="button" onclick="submitAnswer(this)">Submit Answer</button>
            <p class="feedback"></p>
         </form>


.. admonition:: Q3: In optimization, if we reach a point where the gradient equals zero, this point is:

      .. raw:: html

         <form class="quiz-form" data-answer="all the above">
            <label><input type="radio" name="q3" value="a minimum"> a minimum</label><br>
            <label><input type="radio" name="q3" value="a maximum"> a maximum</label><br>
            <label><input type="radio" name="q3" value=" saddle point"> a saddle point</label><br>
            <label><input type="radio" name="q3" value="all the above"> all the above</label><br>
            <br>
            <button type="button" onclick="submitAnswer(this)">Submit Answer</button>
            <p class="feedback"></p>
         </form>


.. admonition:: Q4: In optimization problems, when can you say that a local minimum is also a global minimum ?

      .. raw:: html

         <form class="quiz-form" data-answer="When the function is concave">
            <label><input type="radio" name="q4" value="When the function is concave"> When the function is concave</label><br>
            <label><input type="radio" name="q4" value="When the function is convex">When the function is convex</label><br>
            <label><input type="radio" name="q4" value="The optimal solution is where the objective function intersects the origin"> The optimal solution is where the objective function intersects the origin</label><br>
            <label><input type="radio" name="q4" value="When the function is continuous"> When the function is continuous</label><br>
            <br>
            <button type="button" onclick="submitAnswer(this)">Submit Answer</button>
            <p class="feedback"></p>
         </form>

.. raw:: html

   <script>
   function submitAnswer(button) {
      const form = button.closest('form');
      const selected = form.querySelector('input[type="radio"]:checked');
      const correct = form.dataset.answer;
      const feedback = form.querySelector('.feedback');

      if (!selected) {
         feedback.textContent = "Please select an option.";
         feedback.style.color = "gray";
         return;
      }

      if (selected.value === correct) {
         feedback.textContent = "✅ Correct!";
         feedback.style.color = "green";
      } else {
         feedback.textContent = "❌ Incorrect. Try again.";
         feedback.style.color = "red";
      }
   }
   </script>

