Download Link: https://assignmentchef.com/product/solved-robotics-homework2-inverse-kinematicsik
<br>
The goal of homework2 is to practice and implement what you have learned in the recent courses. In the following exercises, you will implement your own <strong>Inverse kinematics(IK)</strong> algorithm step by step and test the algorithm in simulation using a <strong>Franka Panda 7DoF</strong> arm.

<h1>Exercise</h1>

Just like homework1, let’s first take a look at what we have now. You should have already installed <strong>pybullet</strong> and <strong>numpy</strong>. You will get:

<ol>

 <li>py : this file is a template <strong>where you need to write your own code</strong>.</li>

</ol>

【IMPORTANT】<strong>You NEED to copy all of the implemented functions in</strong> core.py <strong>in last homework(homework1) to</strong> core.py <strong>of homework2.</strong>

<ol start="2">

 <li>py : build a simulation environment. <strong>This file does not need to be modified</strong>, but you can call some functions provided for you.</li>

 <li>py : this file provides some demonstrations to show whether your algorithms work well in the simulation by calling functions in robot_env.py and core.py .</li>

 <li>Folder /robot_model : contains the URDF files and its meshes. <strong>Do not change anything in this folder.</strong></li>

</ol>

<h1>Exercise 1: Velocity Kinematics</h1>

In this part, you need to implement two functions to calculate the Jacobian.

<strong>NOTE1</strong>: write your code in the template file core.py . <strong>DO NOT MODIFY THE FUNCTION NAME!!!</strong> Otherwise the autotest program will not work and you will lose your score &#x1f642;

<strong>NOTE2</strong>: <em>The input and output of the function are numpy arrays!</em>

Here is what you need to finish:

<ol>

 <li>Jb = jacobian_body(Blist,thetalist) : Computes the body Jacobian for an open chain robot.</li>

</ol>

input1: Blist: The joint screw axes in the end-effector frame when the manipulator is at the home position.

input2: thetalist: A list of joint coordinate values.

return: The corresponding body Jacobian.

<ol start="2">

 <li>Js = jacobian_space(Slist,thetalist) : Computes the space Jacobian for an open chain robot.</li>

</ol>

input1: Slist: The joint screw axes in the space frame when the manipulator is at the home position.

input2: thetalist: A list of joint coordinate values. return: The corresponding space Jacobian.

That’s the end of exercise1. Less functions need to implement compare to homework1, right? &#x1f642;

<h1>Exercise 2: Inverse Kinematics</h1>

Now it is time to use the code in exercise 1 and previous code in homework1 to perform your own <strong>inverse kinematics(IK)</strong> algorithm. Here are the functions you need to implement in the template:

NOTE1: use an iterative Newton-Raphson root-finding method starting from the initial guess thetalist0.

NOTE2: the maximum number of iterations has been set as a variable MAX_NUM_ITER .

<ol>

 <li>thetalist,success = IK_in_body(Blist,M,T,thetalist0,eomg,ev): Computes inverse kinematics in the body frame for an open chain robot.</li>

</ol>

input1: Blist: The joint screw axes in the end-effector frame when the manipulator is at the home position.

input2: M: The home configuration of the end-effector. input3: T: The desired end-effector configuration .

input4: thetalist0: An initial guess  that is “close” to satisfying                                 .

input5: eomg: A small positive tolerance on the end-effector orientation error. The returned joint variables must give an end-effector orientation error less than               .

input6: ev: A small positive tolerance on the end-effector linear position error. The returned joint variables must give an end-effector position error less than .         return1: thetalist: Joint variables that achieve  within the specified tolerances.

return2: A logical value(bool) where <em>TRUE</em> means that the function found a solution and <em>FALSE</em> means that it ran through the set number of maximum iterations without finding a solution within the tolerances                and        .

<ol start="2">

 <li>thetalist,success = IK_in_space(Slist,M,T,thetalist0,eomg,ev) : Computes inverse kinematics in the space frame for an open chain robot.</li>

</ol>

Equivalent to IK_in_body , except the joint screw axes are specified in the space frame.

<h1>Exercise 3: Play with the demo</h1>

Congratulations! You have completed your coding part. Just like homework1, it‘s time to play with a robot arm and see what your function can do! (in simulation)

<ol>

 <li>Set TESTING variable in py as: “IK” , then run the code in demo.py , especially running function: IK_test(robot, physicsClientId)</li>

</ol>

In this demo, you will set the target configuration and use the <strong>inverse kinematics</strong> algorithm to solve the corresponding joint angle, then control the joint angle of the robot and check whether the final position of the end effector coincides with the target position.

Again, you can press the CTRL and left mouse button and drag the mouse to change the view angle. You can also zoom in or out by sliding the mouse wheel.

If your IK algorithm is correct, you will find something like this:

<ol start="2">

 <li>Set TESTING variable as: “PICK_PLACE” , then run the code in py , especially running function: pick_and_place_demo(robot, physicsClientId)</li>

</ol>

In this pick and place demo, you will solve a pick and place problem and your goal is to move a yellow LEGO brick from the gray box to the blue box. The way points are already given, you will use your own IK algorithm to solve the corresponding joint angle for each way point and then control the robot to reach that joint angle.

If you implement the IK algorithm correctly, you will see that the robot arm successfully grabs Lego blocks from the gray box to the blue box.

Hope you can have some fun from this pick and place demo XD

This is the end of homework2~