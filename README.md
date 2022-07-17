# OpenFoamAdjointAnalysis
 Optimising the Airflow Over the Rear Wing of a Formula SAE Vehicle Using Adjoint Shape Optimisation

Formula Series Racing is a collection of car racing competitions where the goal is to create a vehicle and
race the fastest possible time within the constraints for each category. Formula SAE is a category which is
designed for university students. Queen’s University has a design team called Queen’s Formula SAE Team
(QFSAE) which competes in this event.
To improve the performance of their vehicle, QFSAE allocates large amounts of resources and time into
designing their vehicle to have optimal aerodynamic performance. In the context of Formula Racing, optimal
performance is minimizing aerodynamic resistance (drag) while maintaining sufficient downward force on the
vehicle to safely turn around the track corners at high speeds. The vehicle’s rear wing significantly impacts
its overall aerodynamic characteristics. The goal of this project is to work with QFSAE to optimise the
shape of their rear wing, while adhering to the Formula SAE rules, and being seamless to introduce into
their existing design. A successfully optimised design is one that reduces the coefficient of drag of the wing
by 5%, while maintaining at least 95% of the downforce contributed by the wing.
The mathematical model that governs the aerodynamic characteristics being optimised can be reduced
to the study of fluid dynamics and the Navier-Stokes equations. The Navier-Stokes equations are a system
of differential equations which model the behaviours of fluids. They are used to determine the velocity and
pressure of a fluid for a given set of initial conditions. These equations do not generally have analytic solutions, so approximations such as Reynolds-Averaged Navier-Stokes (RANS) and tools such as Computational
Fluid Dynamics (CFD) are used to numerically compute approximations of the theoretical solutions.
Optimising the rear wing over all possible shapes is a complex problem, with the amount of parameters
scaling with the complexity of the model being analyzed. Solving the optimisation directly with an exhaustive
search is not feasible in terms of computation power required to calculate the solutions to fluid dynamic
models. An optimisation technique called adjoint optimisation was used to feasibly work toward a solution.
This technique defines a cost function and computes its gradient map at each point on the surface of the
object. This sensitivity map implies which direction, inward or outward, to change each point on the object
to move toward the optimal shape.
The open source CFD called OpenFOAM was used to perform the numerical analysis of the wing.
The validity of the OpenFOAM model was tested by analyzing the simple shapes of a sphere and a cube.
After obtaining base values within 5% accuracy of their theoretical values, the adjoint optimisation technique
implemented by OpenFOAM was applied to these shapes. The resulting modifications reduced the coefficient
of drag significantly over two iterations. Applying the same process to the rear wing, the values for coefficient
of drag and lift were calculated to be within 2.8% and 2.0%, respectively, of the validation data received
from the QFSAE team. Using the results of the adjoint optimisation on the rear wing, a modified model
was created which reduced the coefficient of drag by 3.5% while maintaining 98.2% of the downforce. No
further improvements to the model were able to be made through adjoint optimisation on the original wing
design. An adjoint optimisation was performed on the modified wing, and by confirming that there were
no features on the sensitivity map, local optimimality of this design was concluded. This local minimum is
a sufficient solution, to maintain within the problem constraints. To obtain a wing design better than this
minimum, larger changes would need to be made to the wing which would invalidate the model in terms of
implementation feasibility and not adhering to the Formula SAE rule set.
