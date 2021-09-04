# AIFitness  
This is the project I finished at the individual enterprise.  
Because the property of this project belongs to the company, therefore, I can only put some demo videos and do some brief introduction.  
The source code of this project is saving is the GitLab of the individual enterprise I worked in  

In this project, we have 2 identification, students and teachers.  
  
The teacher can record their fitness actions, after the teacher finishes, our system will ask the teacher to name the fitness actions, then our system will save the fitness video and the JSON file of the keypoint.  
  
The student can select the action they would like to do, then the teacher from our record will teach the student step by step. The system will compare the action between the student and the teacher to determine if the student's action is correct.  


Technical skills and tools:  
1. Keypoint Detection (AlphaPose)  
2. Keypoint Detection (Mobile)
3. CodeBlock  
4. cvui  
5. Algorithm to compare the action between teachers and students  
6. hierarchical clustering  
7. TCP  
8. RTSP  
...  
  
  
## Teacher Part:  
We will give some rules to the teacher when they record their actions.  
When they press the start button, we will show a clock to countdown, the teacher needs to pose their first fitness posture in time.  
Then, at every intermediate point that the teacher thinks can stop and wait for the student, the teacher needs to keep this posture and wait for a few seconds for the system to mark this posture as an Interrupt point  
After the teacher finishes the record, our system will remove unnecessary keypoints and calculate the important keypoints' slope and the angle at each intermediate point.  
Let me show the current important keypoints' dot diagram, you will find out there are too many points crowding together which make the image messy and also make the system so difficult to calculate  
  
The left gif is the teacher's action, the right image is its dot diagram  
![image](https://github.com/ericleee0119/AIFitness/blob/main/image/curl_resize.gif)![image](https://github.com/ericleee0119/AIFitness/blob/main/image/curl_resize.png)  
  
![image](https://github.com/ericleee0119/AIFitness/blob/main/image/hangOn_resize.gif)![image](https://github.com/ericleee0119/AIFitness/blob/main/image/hangOn_resize.png)  

To solve the problem above, I use hierarchical clustering to reduce the amount of the point and make sure in each region, we will have one dot to indicate.  
The below images show the result of hierarchical clustering at only interrupt points  

![image](https://github.com/ericleee0119/AIFitness/blob/main/image/hangOn_resize.png) ![image](https://github.com/ericleee0119/AIFitness/blob/main/image/hangOn_hier.png)  
  
We will record the coordinate of the teacher's important keypoint moving and calculate the angle and slope of the interrupt point, and use the information to determine if the student does a correct fitness action  
The below image shows the angle  
![image](https://github.com/ericleee0119/AIFitness/blob/main/image/angle.PNG)  
  
  
## Student Part:
