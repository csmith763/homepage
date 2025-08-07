.. role:: boldblue
   :class: boldblue

.. role:: captiontext
   :class: captiontext

===========
Constraints
===========

When forming an optimization problem, it is often necessary to consider what would make your problem impossible or undesirable. For instance, suppose you are designing an airplane. One of the quantities you must account for is the mass of the plane. Obviously, the airplane’s mass cannot be negative because that is not physically possible. Likewise, we know that we want to have a plane, so it must have *some* mass. This forms what is commonly called an “:boldblue:`inequality constraint`,” which looks like:

.. math::

   c_1(x) \equiv m > 0

Here, we are stating that our constraint, :math:`c_1`, is a function of the design variables, :math:`x`. The constraint is defined as the mass of the airplane, :math:`m`, being strictly greater than zero. 

Consider another aspect of an airplane: we want it to fly! During most of its flight, we can assume that it will be in *steady level flight*; meaning that it is not accelerating, and its weight, :math:`W`, is supported by its lift, :math:`L`. This is an “:boldblue:`equality constraint`” and is written as:

.. math::

   c_2(x) \equiv L = W

Now, we are defining another constraint, :math:`c_2`, which is likewise a function of the design variables :math:`x`, and is defined as the lift being equal to the weight—hence the name: equality constraint.

Consider a different optimization problem: you are walking through a valley with the goal to minimize your altitude. Without any constraints, this problem is fairly straightforward: if you can see the whole valley, then simply walk to its lowest point! This problem is depicted below, where the valley is represented by the orange-shaded surface and the minimum altitude is shown with the red dot. 

.. dropdown:: Key Idea: What are those extra curves in the image?
   :icon: light-bulb

   The blue, gray, and red curves in the image that are not on the surface are known as :boldblue:`contour lines`. These lines are used to help show curves where a function has a constant value. In this case, the contour lines are used to show where the valley has the same position when looking at the surface from a particular direction. The easiest set of contour lines to understand is those directly below the surface. This set of curves creates a topographic map of the surface, which is used to show points in the valley that have the same elevation. As the minimum is approached, the curves change from red to blue, indicating that the elevation is decreasing!

.. figure:: images/global_minimum.svg
   :width: 700px
   :alt: Global minimum of the valley problem
   :align: center

   :captiontext:`Global Minimum of the Unconstrained Valley Minimization Problem`

Now, suppose there is a lake at the bottom of the valley, and you need to stay dry. In this case, you would walk to the edge of the lake and stop: the lake acts as an *inequality constraint* on where you are allowed to move. The green curve shows all the minima for the problem, as each point has the same elevation if the lake is flat. You may notice that the global minimum, shown with the red dot, has not changed for the unconstrained problem. However, due to the presence of the lake, this position can no longer be reached. Therefore, we say that this constraint is :boldblue:`active`, since it is currently affecting you once you reach the water line. 

Now, instead of a lake at the bottom of the valley, what if there is a pond midway up the valley in the top left of the image? This would also act as an inequality constraint: you would not be able to walk into the pond without getting wet. However, you could walk around the pond and still reach the lowest point; making this constraint :boldblue:`inactive`. 

.. figure:: images/inequality_constraint.svg
   :width: 700px
   :alt: Inequality constraint applied to the valley problem
   :align: center

   :captiontext:`Curve of Minima for the Inequality Constrained Valley Problem`


Finally, suppose there is a road running through the valley that you must stay on because you would get lost otherwise. The objective remains the same: minimize your altitude; but your position is always constrained by the road. You could formulate this so that your position :math:`x` must lie on the path defined by the road :math:`p(s): x=p(s)`. Alternatively, you could formulate this constraint by saying the distance between you and the road must be equal to zero: :math:`x-p\left(s\right)=0`. Both of these are equivalent and are *equality constraints*, and they result in a constraint that is always active. Here, there is a single point on the path that minimizes your elevation, and this is the constrained minimum for the problem.

.. figure:: images/equality_constraint.svg
   :width: 700px
   :alt: Equality constraint applied to the valley problem
   :align: center

   :captiontext:`Single Minimum for the Equlity Constrained Valley Problem`

   ..

One final piece of terminology that often appears in optimization is the concept of :boldblue:`feasible` and :boldblue:`infeasible` points. Think back to the previous example, where you are trying to minimize your altitude in the valley while remaining on the road. As long as you stay on the road, regardless of your altitude, you know where you are, and the constraint is satisfied. This would be a :boldblue:`feasible` point because you have satisfied all the constraints. However, if you move off the road, the constraint is no longer met, making this an :boldblue:`infeasible`` point. For any optimization problem, feasible points are the points that satisfy all constraints in your problem.

In many optimization problems, you might often have several constraints, and it is possible to have constraints of both types for the problem you want to solve. The form for these constraints and how they are represented mathematically is dependent on the problem you want to solve, but the key idea about how the two types of constraints influence your problem is ultimately the same. 

Key Takeaways:
``````````````
- Constraints are posed mathematically as either inequality or equality statements

- The constraints which are directly affecting the choice of design variables to avoid constraint violations are called active constraints

- Inactive constraints are inequality constraints that are satisfied and are not at their specified constraint bounds

Definitions:
````````````

- Inequality constraint: a mathematical constraint where a value is greater than or less than some specified value

- Equality constraint: a mathematical constraint where a value is exactly equal to another specified value

Test your Knowledge
````````````````````

.. admonition:: Q: According to the diagram, why is it important to identify constraints in an optimization problem?
    

       .. raw:: html

            <form class="quiz-form" data-answer="To ensure optimized results make physical sense">
               <label><input type="radio" name="q2" value="To make mathematical calculations more easier  "> To make mathematical calculations more easier  </label><br>
               <label><input type="radio" name="q2" value="To ensure optimized results make physical sense"> To ensure optimized results make physical sense</label><br>
               <label><input type="radio" name="q2" value="To simplify the objective function  "> To simplify the objective function  </label><br>
               <label><input type="radio" name="q2" value="To reduce the number of design variables "> To reduce the number of design variables </label><br>
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
