<h1> Raindrop Simulation </h1>
<p>
  This project analyzes the kinematics of a falling object with air resistance. 
  By creating a simulation of a falling raindrop, this project attempts to illustrate how different factors affect the path of an object under gravity.
</p>


<h2>Overview</h2> 
<h3>Classical Physics - Projectile Motion</h3>
<p>
  In classical Newtonian physics, projectile motion does not account for air resistance.  
  Because of this, the maximum height is determined only by the initial velocity, mass, and gravitational constant. Thus, we can use the basic kinematic equation
  <b> yf = yi + vi * t + 0.5 * a * t^2 </b> to plot the vertical position vs time. However, this is not the ideal scenario for the real world, as it neglects aerodynamic drag. 
  This kinematic model ignores the projectile's shape and assumes it is traveling through void space. 
</p>
<h3>Projectile Motion with Air Resistance</h3>
<p>
  To make this model more accurate, we must include air resistance, which is a force that acts in the opposite direction of motion. Air resistance can be expressed as 
  <b>b = 0.5 * c * p * A</b> where c is the drag coefficient, p is the density of the medium, and A is the cross-sectional area of the projectile perpendicular to the direction of motion.
</p>

<h2>Program Usage</h2>
<p>
  For this simulation, I made several assumptions about the data. First, the raindrop's shape was to be a sphere, so I could give it a radius of 1.5mm, or 0.00015m. 
  That way, I could calculate its cross-sectional area to be pi * r^2. 
  Also, the formula for the volume of a sphere is (4 * pi * radius^3)/3. 
  Using water's density of 1g/mL, I assigned the total mass to be volume * 1000 to convert that mass to kilograms and set it equal to a variable m.  
</p>
<p>
  Next, the density of the medium (air in this case) is found to be <b>1.2 kg/m^3</b>.
</p>
<p>
     The drag coefficient is dependent on the overall shape of the projectile.
  <ul>
    <li> Cubes have a coefficient of around <b>1.05</b> </li>
    <li> Cylinders have a coefficient of around <b>0.82</b> </li>
    <li> Perfect spheres have a coefficient around <b>0.50</b> </li>
  </ul>
  Since a raindrop is shaped like an elongated sphere but not yet a cylinder, I gave it a coefficient of 0.6. 
</p>
<p>
  Lastly, the raindrop is falling on planet Earth, where the gravitational acceleration constant is 9.8 m/s^2
  Although technically g varies slightly depending on altitude, the overall error would be minimal, so I assumed g would stay constant throughout the fall.
</p>

<h2>Implementation</h2>
<p>
  by setting the initial speed to 0 m/s and initial time to 0 sec, I took intervals of 0.12 sec. 
  By using these increments, I could write a program that would give information on the raindrop every 0.12 sec, based on its previous information 0.12 sec ago. 
  In other words, instead of using calculus by taking a limit dt that goes to 0, I took increments of <b>dt = 0.12 sec</b>.
</p>
<p>
  By deriving for the acceleration, we get <b>a = (g-(b*(vi**2))/m)</b>. We know that with acceleration, we can find:
  <ul>
    <li> vf = vi + a * t </li>
    <li> yf = yi * t + 0.5 * a * t^2</li> 
  </ul>
  Then, by setting vf as the new vi 0.12 sec later, we can repeat the process by finding the new acceleration value.
</p>

<h2>Results</h2>
<p>
  After plotting the data of the first 25 instances, a pattern emerges. 
  At first, the projectile acts like classical mechanics, where the speed increases linearly, and the position changes exponentially. 
  However, later on, the speed seems to stagnate at around 7.4 m/s, and the position increases only at a constant rate. 
  This means that our raindrop has reached terminal velocity, where the gravitational force has become equal to the air resistance force (based on its shape and mass).
</p>
