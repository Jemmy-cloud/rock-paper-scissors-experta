=========
|Experta|  
=========

|pypi| |version| |tests| |docs| |coverage|

Experta is a Python library for building expert systems strongly inspired
by CLIPS_.

.. code-block:: python

   from random import choice
   from experta import *


   class Light(Fact):
       """Info about the traffic light."""
       pass


   class RobotCrossStreet(KnowledgeEngine):
       @Rule(Light(color='green'))
       def green_light(self):
           print("Walk")

       @Rule(Light(color='red'))
       def red_light(self):
           print("Don't walk")

       @Rule(AS.light << Light(color=L('yellow') | L('blinking-yellow')))
       def cautious(self, light):
           print("Be cautious because light is", light["color"])


.. code-block:: python

   >>> engine = RobotCrossStreet()
   >>> engine.reset()
   >>> engine.declare(Light(color=choice(['green', 'yellow', 'blinking-yellow', 'red'])))
   >>> engine.run()
   Be cautious because light is blinking-yellow


Migrating from Pyknow
Experta is a Pyknow fork. Just replace any pyknow references in your code/examples to experta and everything should work the same.

Examples
You can find some more examples on GitHub.

