# Learning-Journal-2
Second Year (Retake) Learning Journal, for me to understand my problems better, report them, problem solve, and have logs.

## 24/11/26 ##

Working on the First component today, I have been trying to improve my familiarity with the new Unity Input System, so that is what this component is.

One of the big issues I had was always forgetting the "using UnityEngine.InputSystem;" Declaration at the top of the script.

Another issue I faced consistently, was whenever I learned in class or at home, I would be able to pull the inputs off, then would not be able to remember the syntax, so my way to fix this was doing the research on my laptop, and now I bring my laptop, which keeps me consistently refreshed on the syntax.

I learned the Input system through a per, Johnny Burkett, he assisted in making a small mock up that could help for this project, I am currently working on moving that mock up into unity

An area I would have struggled majorly is the syntax inside the brackets of the OnMove() function, the "InputAction.CallbackContext ctx" was not something I would've remembered, and I understand it is to reiterate to the computer to check the input action for this line of code when we se the ctx reference, it still isn't something I am confident saying needs to/not be there.

Also in incorporating the script to my computer, I ran into small issues like my projects InputActions and Action Maps where named differently, so copying the script exactly wouldn't work, and it's why when coding, you are much better off retyping line by line, as apposed to copy Pasting, because copy pasting will have you understanding much less! This way I just looked to see when issues arise and tried to figure out what the differences where and nail them down.
The specific issues where that the names being slightly different but all named similarly, I was often unsure of what certain names referred to, for example, in my example code I have and Action Map called "Player" but on this unity scene it was called "Movement" etc etc.

Once I had gotten the movement working I have now run into a bug, the object seems to be rotating whenever I move, I have a theory as to why, when working with Johnny, he recommended I use Linear Damping, and whilst I am, I turned it up quite high as the character was moving far too quickly, this may be having an affect on the rotation? 

- So I was wrong, I turned off the Linear Damping, and turned the speed down to 1, and not only did the rotating persist, it actually worsened, I must continue to debug Until I find out why this is happening.

I did not figure out WHY the character was continuously rotating, but I figured out a way to get around it, freezing the rotation through the rigidbody completely, now I did have a concern as to whether or not this would stop all rotation, or just the physics based rotation. 

Now unfortunately I did have a solid idea on how to work on this, but I had an issue with how to execute it, I tried making it so that when pressing a key, it set a rotation value, then in fixed update, running the following code:

Quaternion deltaRotation = Quaternion.Euler(eulerAngleVelocity * Time.deltaTime);
rb.MoveRotation(rb.rotation * deltaRotation);

The issue was when I pressed the key it was assigning a value, and then never unanssigning it, I tried moving code around to change this but it took me a while to realise, and I only did because Paul came over to help, that I am reading a float in the function that is called when you press the key, so I can move this to the line that assigns the number, and times that number by the float, as it is always 1 or 0, if its times by 0, it stays at 0, and if it is 1, it actually assigns it, genius I say.

Another thing I worked on was Swapping Action Maps, as the player pressing pause and disabling the player action map, enabling the UI one, and the real fun part was swapping back
see alot of games have certain actions be activatable through multiple different methods, such as closing a menu with an x on the screen, or pressing the standard return button (B/X/A) so I tried making the resume game button also trigger the input function, but this didn't work as those functions won't show up for the button, so instead if you press the key that would resume, the script just runs a separate function, and that function can be accessed either through the key OR the UI Button. This worked flawlessly and I was very happy.

Currently Running into an issue where I would like to be able to use the UI buttons with more than just the mouse, with the arrow keys too, pressing any would select one, but I cannot seem to find out a way to do this

closest I can manage is selecting a button by default, I could theoretically have it so you could press a key and then go to the designated button, but that crumbles when you have any more than two buttons on screen, I have seen an idea of assigning a value, and ID to each button, and each time you press a navigation button it either adds 1 or removes one from your id, meaning you'll go to either the button above you always, or below you always, not entirely sure how to assign these values though, I am going to give it an attempt 
