Quiz
=================


.. admonition:: Q1: Which of the following best describes the purpose of an objective function?
    :class: dropdown



        .. raw:: html

            <form class="quiz-form" data-answer="It specifies what you want to minimize or maximize  ">
                <label><input type="radio" name="q1" value="It defines the limits on possible solutions "> It defines the limits on possible solutions </label><br>
                <label><input type="radio" name="q1" value="It specifies what you want to minimize or maximize  "> It specifies what you want to minimize or maximize  </label><br>
                <br>
                <button type="button" onclick="submitAnswer(this)">Submit Answer</button>
                <p class="feedback"></p>
            </form>

    

---


.. admonition:: Q2: According to the diagram, why is it important to identify constraints in an optimization problem?
    :class: dropdown


    

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

---


.. admonition:: Q3: What quantities in an optimization problem formulation are you directly changing to impact your design?
    :class: dropdown
   

        .. raw:: html

            <form class="quiz-form" data-answer="Design variables">
                <label><input type="radio" name="q3" value="Objective function"> Objective function </label><br>
                <label><input type="radio" name="q3" value="Constraints"> Constraints  </label><br>
                <label><input type="radio" name="q3" value="Design variables"> Design variables  </label><br>
                <label><input type="radio" name="q3" value="Critical points"> Critical points </label><br>
                <br>
                <button type="button" onclick="submitAnswer(this)">Submit Answer</button>
                <p class="feedback"></p>
            </form>

.. admonition:: Q4: In which step would you define mathematical expressions that limit the values your design variables can take?
    :class: dropdown

    

        .. raw:: html

            <form class="quiz-form" data-answer="Identifying constraints">
                <label><input type="radio" name="q4" value="Choosing the objective"> Choosing the objective</label><br>
                <label><input type="radio" name="q4" value="Choosing design variables"> Choosing design variables  </label><br>
                <label><input type="radio" name="q4" value="Identifying constraints"> Identifying constraints  </label><br>
                <label><input type="radio" name="q4" value="Formulating the analysis procedure"> Formulating the analysis procedure </label><br>
                <br>
                <button type="button" onclick="submitAnswer(this)">Submit Answer</button>
                <p class="feedback"></p>
            </form>

    
---

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
