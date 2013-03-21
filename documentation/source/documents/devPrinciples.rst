===============================
Development Principles
===============================

CamFIN is a Cardiac Modelling tool, and as such it must incorporate physical models, numerical methods and support a variety
of data input and output. When developing these kinds of features the priority should always be on creating code that is **testable**,
and **maintainable**. The overall design should emphasize **seperation of concerns** in order to promote **flexibility**. It should
be possible to swap components (time stepping modules, physical model definitions etc.) in and out of the code with a minimum of pain.
It is to be expected that development of FEniCS and related tools will continue and that a better way to do things is always around
the corner.


CamFIN development principles
-------------------------------
Object Orientation:
       Where there is no significant performance penalty classes should be preferred over functions as they are easier to test.

The Law of Demeter:
	Objects should minimize the set of other objects that they talk to. This promotes flexibility in the 
        overall code see http://en.wikipedia.org/wiki/Law_of_Demeter.  

Test Driven Development:
        When possible follow the classical TDD developement approach. 
        	#. Write tests for a method of a class 
        	#. Implement the method and work on it until the tests are passed
       		#. Refactor the code to improve the overall design if necessary

Reversibility:
        No component of CamFIN should be irreplacable, and all decisions regarding design, solution algorithms and models etc...
        should be reversible.
               
Pragmatic Programming:
        The pragmatic approach to programming is always the right one. When in doubt consult the "bible" 
        http://pragprog.com/the-pragmatic-programmer.

-------------------------------
Architecture
-------------------------------  
Architecture is the set of all irreversible decisions in a software project, and as such it should be minimized. 
CamFIN's architecture is the dependency on the components of FEniCS http://fenicsproject.org/ and the library
DOLFIN-adjoint http://dolfin-adjoint.org/. These packages are needed in order to solve PDE constrained optimization problems,
and therefore essential. Nevertheless dependencies on these packages should be minimized as much as is feasible.

-------------------------------
Testing
-------------------------------
All production code should be covered by automatic test. CamFIN makes use of the following kinds of tests

Unit Test:
         A test that checks the functionality of a single method in isolation.

Integration Test:
         A test that checks the functionality of several classes (internal or external) together.

Regression Test:
         A test that compares a result (run time, memory footprint, convergence value etc...) to a previously calculated value
         that is hard coded into the source.


