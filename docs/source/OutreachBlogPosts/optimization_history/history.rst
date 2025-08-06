.. role:: boldblue
   :class: boldblue

.. role:: captiontext
   :class: captiontext

=======================
Motivating Optimization
=======================
What comes to mind when you think of the word “optimize?” Officially, Merriam-Webster dictionary defines :boldblue:`optimize` as "to make as perfect, effective, or functional as possible" [1]. This is a very formal definition for the word, but the concept of optimization is much more intuitive than the definition suggests and is something that everyone does throughout their daily lives. 

As an initial example, suppose that you have gone to the store, and you want to buy as many snacks as possible for 20 dollars. There are numerous snacks in the store at various prices, so you must determine which snacks you want the most and how to lower the total cost. This is the idea of optimization, and it is related to an everyday task like going to the grocery store.  

From a historical perspective, humans have been optimizing for millennia, as it can apply to almost any situation that eases day-to-day life. Optimization can be traced to ancient societies, where efficient survival was critical. This could take the form of a farmer maximizing the harvest using limited land or a hunter minimizing exerted energy. Optimization even extends beyond human beings into nature, as it has been discovered that plants and animals also try to find the best approaches to accomplish tasks. Take a look at the video below to explore optimization at work in nature.  

.. youtube:: HyzT5b0tNtk
   :align: center

From these examples and definitions, :boldblue:`the concept of optimization can be narrowed down to determining the minimum (or maximum) of some set of requirements to fulfill another set of requirements`.  

.. dropdown:: Definition: Minimum
   :icon: light-bulb
   
   The minimum is usually thought of as the least of something. However, the least amount of anything in the real world must be zero, since it is impossible to have a negative amount of a physical quantity. For example, the least amount of candy you can get on Halloween is zero pieces. Therefore, we must place limits, or :boldblue:`constraints`, on our parameters to help determine what a realistic minimum or maximum can be. We will review these concepts in more detail in later sections.

.. dropdown:: Pause and Reflect: Think of some ways that you have potentially used optimization in your life. Note that they do not necessarily have to be complex situations!
   :icon: question

   Consider some additional examples of optimization in these simple situations.

   - Taking a shortcut through your neighborhood to get to your friend's house

   - Picking a breakfast that you can finish quickly in the morning to get to school on time

   - Making a pillow fort as large as possible with a limited number of pillows

Now, consider a more practical example of optimization. During World War II, engineers were deciding where to add armor to planes so that they would have a greater chance of surviving in dogfights. Planes that returned from battles often had bullet holes in the fuselage and wing, so one would naturally assume that is where they are most often hit. As a result, the initial logic was that engineers should add more armor to the wings and fuselage. However, a statistician, Abraham Wald, disagreed. He posed that the armor should be placed on the engine and nose, where there were fewer instances of damage. Before reading the answer, pause and think about why Wald was correct with this idea. 

Wald observed that the planes that sustained damage in the engine and nose were not returning from combat. The initial set of Aircraft that the engineers were investigating did not consider these planes, so the original solution of adding more armor to the fuselage and wings would not drastically increase their survivability. To correct this, they had to reconsider the problem and account for the planes that were lost in battle, not just those that returned. Then, with Wald's help, the engineers were able to place this additional armor in the engine and nose regions. In terms of optimization, they maximized the survivability of the planes with constraints on the total cost and the amount of additional armor that could be added to the aircraft.

.. figure:: images/plane.png
      :figwidth: 100 %
      :alt: Surivorship bias plane example
      :scale: 20 %
      :align: center
      :target: https://en.wikipedia.org/wiki/Survivorship_bias

      :captiontext:`Distribution of Damaged Aircraft during World War II (Credit Wikipedia [3])`

      ..

Although the fundamental idea of optimization is simple and has a natural origin, it is difficult to precisely say when the concept was fully realized as a mathematical application. From a mathematical perspective, it is believed to originate as early as the ancient Greek civilization with Archimedes finding the maximum value of a parabola. Others give credit to Sir Isaac Newton for his study of minimal resistance, where he sought a shape that minimized drag with potential applications for ship designs.  

.. figure:: images/Combined_People.png
      :width: 800px
      :alt: Images of Archimedes (left) and Sir Isaac Newton (right)
      :align: center
      
      :captiontext:`Key Figures in Optimization - Archimedes (left, Credit Getty Images [4]) and Sir Isaac Newton (right, Credit Wikipedia [5])`

      ..

The origins of optimization were put into text by Leonis Vitalyevich in 1939 with his monograph “Mathematical Methods for Organization and Planning of Production.” However, the actual application of optimization was used on a wide scale throughout World War II, as indicated with the previous example.
   
Presently, optimization is an ever-growing field with numerous practical applications, ranging from mathematics and engineering to economics and marketing. A current and widely known example of a system using optimization to function is ChatGPT. The generative artificial intelligence uses various techniques to comb through mass amounts of data and outputs answers quickly. Essentially, ChatGPT operates using optimization by reducing the time taken to provide an answer to the user. For a more detailed review of notable events in optimization history, you can look at the timeline in the image below.

The idea of a fully-fledged :boldblue:`optimization problem` may seem unfamiliar at first, but we will delve deeper into specifics in later sections. If you would like to learn more about current techniques and applications of optimization, feel free to explore the other sections of this website!


   .. figure:: images/TimelineNew.png
      :width: 500px
      :alt: timeline for the history of optimization
      :align: center

      :captiontext:`Chronological Timeline of Notable Events in Optimization History`

      ..

References
``````````

[1] `Meriam-Webster Dictionary <https://www.merriam-webster.com/dictionary/optimize>`_

[2] `YouTube BBC News <https://www.youtube.com/watch?v=HyzT5b0tNtk&t=1s>`_

[3] `Surivorship Bias Plane <https://en.wikipedia.org/wiki/Survivorship_bias>`_

[4] `Archimedes <https://www.biography.com/scholars-educators/a43249494/who-discovered-pi-archimedes-of-syracuse>`_

[5] `Isaac Newton <https://en.wikipedia.org/wiki/Isaac_Newton>`_



