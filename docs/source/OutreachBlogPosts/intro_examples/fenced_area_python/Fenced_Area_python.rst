.. role:: boldblue
   :class: boldblue

.. role:: captiontext
   :class: captiontext

.. role:: analysisgreen
    :class: analysisgreen

.. role:: optblue
    :class: optblue

=========================
Fenced Area - Python Demo
=========================

Now that you have an idea of the approach to solve basic optimization problems, the next step is utilizing the most common way to create an optimization solution: code.  

Python provides a built-in basic optimization function that invokes a specific solver type to approach a solution. This function is called scipy.optimize minimize function. If you are not familiar with python, don’t worry! A framework is laid out, and each step is explained below.  

For understanding and applying the scipy.optimize, the area problem statement is changed slightly: 

Consider building a fence in your backyard, and you have 100 feet of fencing available to you. How long should the sides of the fence be to have the largest fenced in area possible? 

minimize(objective, x0, bounds=bnds, constraints=cons) 

This is the function we will be using to find the optimal solution to the area problem.  

:boldblue:`Objective`: The objective of the minimize function refers to the objective function of our optimization problem. It is the equation that we want to be minimized. However, we are looking for the maximum value for area, hence the objective function must be negated to get a maximum.  This works because the function looks for the smallest number possible to fulfill the constraints, hence by setting the area in the negative space, the magnitude of the smallest number will be the greatest possible area. Think back to the solution to the area problem and figure out what the objective function would be using x and y as the variables.  

.. dropdown:: Objective Function
   :icon: question

   :math:`-x \times y`

:boldblue:`x0``: This represents an initial guess for the problem; in other words, it gives the code a starting point to check values from. It is important to understand that minimize solves a problem using a gradient-based approach. By giving it an initial starting guess, the code will use that as the point to start with and calculate the gradient to determine the direction to move towards to find the overall minimum.  A good guess is critical and should be a value that is a reasonable approximation to what we expect our actual answer to be. Set x0 = [x0, y0] where x0 and y0 are the initial guess for each side of the fenced area.  

.. dropdown:: x0 *Note multiple answers possible
   :icon: question

   x0 = [20, 30]
   As long as these are positive values, the initial guess is a good one!

.. dropdown:: Finite Difference Gradient
   :icon: light-bulb
   
   Since we do not supply the function with the analytical derivative equation for the objective function, it takes an approximation instead, using the finite difference method. Essentially it takes a “guess” as to what the gradient is to figure out where to move by taking the input variable and perturbing it by a small amount. This approximates the derivative and by default the step “h” is :math:`1 \times 10^{-6}` in scipy minimize.
   
   :math:`f'(x) = \frac{f(x+h) - f(x)}{h}`


:boldblue:`bounds=bnds`: As the name suggests, bounds define the minimum and maximum allowable values for the variables in the objective function. Typically, this is determined by the physicality of the problem, such as if negative numbers are possible or if a maximum value for a variable. Considering that our variables are lengths of a physical material, state what the bounds of x and y must be. Note that to have a bound of infinity, python uses “none”. 

.. dropdown:: bounds=bnds
   :icon: question
   
   bnds = [(0, None), (0,None)]

:boldblue:`constraints=cons`: Constraint is an important and last step to optimizing the problem. Similar to the sampling approach that we took by hand, a constraint for the maximum amount of fence or the perimeter can be set. Referring to the area problem solution and using variables x, y and P, write out the constraint equation dependent on the perimeter and set equal to 0. 

.. dropdown:: constraints
   :icon: question
   
   :math:`2 \times(x+y) - P = 0`


These are the main inputs to the minimize function. There are some optional inputs possible, such as “method” that tell the code to choose a different approach to finding the minimum, the default being SLSQP.   

.. dropdown:: SLSQP
   :icon: light-bulb
   
   This stands for Sequential Least Squares Quadratic Programming. This is a method of optimization that approximates the non-linear function using a quadratic function. Using this approximation, it then iteratively solves a series of problems and with a gradient-based approach, slowly arrives at the final answer.  

Now that you have gained an understanding of the operation of minimize, try it out for yourself by changing the lines of code below the "EDIT LINE BELOW" markers.

.. notebooklite:: ./max_area_fd.ipynb
   :width: 100%
   :height: 500px


------------------------
Supplying the Derivative
------------------------

Now that you have a basic comprehension of how to apply scipy.minimize, we can add some additional inputs that may be useful for other types of optimization problems. If you know how to take partial derivatives, this is a good next step into understanding optimization. As mentioned before, currently our code approximates a gradient using the finite different method. However, we can provide an exact analytical gradient using the Jacobian matrix.  

:boldblue:`Jac`: The Jacobian matrix must be provided for both the objective function and the constraint function. It is the partial derivative of each equation written out as a matrix. Hence, you will need to take the partial derivative of :math:`-x \times y` and :math:`(x + y) = P` and write it out in the form [#, #].  

.. dropdown:: Jac
    :icon: question
    
    Jacobian of objective function: [-y, -x] 
    
    Jacobian of constraint function: [2, 2]   

:boldblue:`Finite Difference vs Analytical Gradient`
To demonstrate the difference in calculating the derivative using the finite difference method analytical gradient, the values are tabulated below using various step sized for finite difference. The function we will approximate is :math:`e^x`.

This will evaluated at x = 1 for both methods. The finite analytical gradient value is as follows:  
:math:`d/dx(e^x) = e^x = e^2 = 7.3805`

The finite difference values for various h values are as follows:

.. list-table:: 
   :widths: 50 50
   :header-rows: 1
   :class: center-table


   * - h "step"
     - Result
   * - 0.01
     - 7.4261
   * - 0.0001
     - 7.3894
   * - 0.000001
     - 7.3890
    
It is easy to see why SLSQP uses :math:`1*10^-6` as its step value when approximating the gradient values.

Here’s the code again but with the addition of using the Jac input, try it out to see if it gives you the same answer! 

INSERT CODE HERE











