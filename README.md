# Control Rubrics

1.- Implemented body rate control in C++
Substracting Comanded P,Q and R, from the actual P,Q,R states from the drone, gives the error which then is multiplied by kpPQR and also the intertia momentos of x,y and z
this result then is return in the function.

![image](https://user-images.githubusercontent.com/29236973/138579310-18ace3f9-ccdb-42ea-8aa5-aba0507622d3.png)

2.- Implement roll pithc control in C++
Passing the thrust to acceleration by divinding it by the mass, gives "c", which is used to normalize the vector acceleration to the specific body ref vector, which then is used to get the errors and multiply it by kpBank. By doing so, we get the body x and y commanded reference which then is used in the formula to get "Comanded p" and "Comanded q".

![image](https://user-images.githubusercontent.com/29236973/138580232-f41bf40a-4f81-4685-a3a1-94a0a56805b9.png)

3.- Implement altitude controller in C++.
In this part, i implemented a complete PID. I get the position and velocity errors and multiply them by their corresponding Gains.
Then in order to get U_bar, i added the P controller + PD Controller + PI controller and finally the commanded acceleration of Z.
In order to get the thrust, the u1_bar is normalized in the Z direction and substract from gravity.
The result is multiply it by the mass, and thus, this gives the Thrust.
But following NED coordinates, the thrust must be negative.

![image](https://user-images.githubusercontent.com/29236973/138580432-ee4c1a8f-ad1b-429f-8e42-0d52d19c26d9.png)

4.- Implement lateral position control in C++.
In this part a PD is implemented in the same way. First we get errors, then multiplying them by their correspondnig gains And finally adding the results to the X_acceleration and Y_acceleration.

![image](https://user-images.githubusercontent.com/29236973/138581624-adaee4d5-0a75-4e60-bdef-cb67ab7b614d.png)

5.- Implement yaw control in C++.
In this part it is needed to understand in which part the angle is, if the angle is bwteen 0 and 179, then we can proceed with positive angles, if the angle is from 180 to 359, then is better to use negative angles.
Once this is determined, i proceeded to get the error from the angles.
Once all of this is done, the error is multiplied by the kpYaw gain.

![image](https://user-images.githubusercontent.com/29236973/138583454-fc389b2f-5fc0-4def-84fb-55b8e0ddbae9.png)

6.- Implement calculating the motor commands given commanded thrust and moments in C++.
Finally used the required formulas so that i could get C_bar, P_bar, Q_bar and R_bar.
Knowing that F1 + F2 + F3 + F4 = C and so one so for with the other variables, it is easy to use linear algebra and get the inverse of the matrix in order to get the angular velocities W1,W2,W3,W4.

![image](https://user-images.githubusercontent.com/29236973/138583489-58d39c2a-6fbb-40d1-9c1f-2085c23ade00.png)

# Flight Evaluation
The control system fulfill all the specifications in each scenario with the same gains and quantities.
