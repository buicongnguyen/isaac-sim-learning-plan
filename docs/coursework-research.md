# Isaac Sim Coursework Research Notes

Last updated: 2026-06-22

## Cornell CS 4756/5756 Robot Learning

Finding: the public coursework does not appear to use Isaac Sim for official homework or practice.

Evidence:

- Course page: https://www.cs.cornell.edu/courses/cs4756/2026sp/
- Public assignment notebooks use Gymnasium-Robotics and MuJoCo FetchReach-v4.
- A1 notebook references the Fetch Reach task as part of Gymnasium Robotics' MuJoCo environments.
- A2, A3, A4, and A5 reference FetchReach-v4, Gymnasium-Robotics, MuJoCo setup, and Gymnasium environments.
- I did not find Isaac Sim, Isaac Lab, Isaac Gym, or Omniverse references in the checked public assignment materials.

Useful assignment links:

- A1: https://raw.githubusercontent.com/kuanfang/cornell-cs4756-2026sp/master/assignments/A1/programming/CS4756_A1_Programming_Release.ipynb
- A2: https://raw.githubusercontent.com/kuanfang/cornell-cs4756-2026sp/master/assignments/A2/programming/student.ipynb
- A4: https://raw.githubusercontent.com/kuanfang/cornell-cs4756-2026sp/master/assignments/A4/A4.ipynb

## University of Miami CSC398: Introduction to Autonomous Robots

Finding: this course explicitly uses Isaac Sim.

Notes:

- The course page says it uses Gazebo and Isaac-Sim for simulation.
- Assignment 2 uses an HSR Isaac Sim world for laser-scan processing practice.
- Assignment 5 starts an Isaac Sim world for particle-filter localization.
- Re-check on 2026-06-23: the instructor's teaching page lists CSC 398 for Fall 2024 and Fall 2026, but the linked CSC398 course page itself still shows a 2024 last update and 2024 assignment PDFs. Treat Fall 2026 as planned/listed, not yet a published refreshed course page.

Links:

- Course page: https://www.cs.miami.edu/~visser/csc398-autonomous-robots.html
- Course page, canonical `/home/visser` path: https://www.cs.miami.edu/home/visser/csc398-autonomous-robots.html
- Teaching page listing Fall 2026: https://www.cs.miami.edu/home/visser/teaching.html
- Assignment 2 PDF: https://www.cs.miami.edu/~visser/csc398-files/CSC398-Assignment-2.pdf
- Assignment 5 PDF: https://www.cs.miami.edu/home/visser/csc398-files/CSC398-Assignment-5.pdf
- Assignment 6 PDF: https://www.cs.miami.edu/~visser/csc398-files/CSC398-Assignment-6.pdf

## University of Miami CSC752: Autonomous Robotic Systems

Finding: this graduate course explicitly uses Isaac Sim.

Notes:

- The course page says much of the course is practical work with ROS and ISAAC Simulation.
- Activity 1 starts an `isaac-sim` Docker environment and a Python simulation suite.
- Assignment 5 uses Isaac Sim for particle-filter localization.
- Assignment 6 uses Isaac Sim for RRT path planning.

Links:

- Course page: https://www.cs.miami.edu/~visser/csc752-autonomous-robotic-systems.html
- Activity 1 PDF: https://www.cs.miami.edu/home/visser/csc752-files/CSC752-Activity-1.pdf
- Assignment 5 PDF: https://www.cs.miami.edu/home/visser/csc752-files/CSC752-Assignment-5.pdf
- Assignment 6 PDF: https://www.cs.miami.edu/home/visser/csc752-files/CSC752-Assignment-6.pdf

## NVIDIA Practice Materials

These are not traditional university homework sequences, but they are useful as structured Isaac Sim practice.

- Isaac Sim + Jetson HIL course docs: https://nvidia-ai-iot.github.io/isaac-sim-jetson-hil-course-doc/
- Isaac Sim exercises: https://nvidia-ai-iot.github.io/isaac-sim-jetson-hil-course-doc/isaac-sim/index.html
- Hardware-in-loop exercises: https://nvidia-ai-iot.github.io/isaac-sim-jetson-hil-course-doc/hardware-in-loop.html
- Industrial Metaverse Teaching Kit syllabus: https://developer.nvidia.com/industrial-metaverse-teaching-kit-syllabus

## Related But Not Isaac Sim

Washington and Lee Assignment 6 uses Isaac Gym and IsaacGymEnvs for deep reinforcement learning practice. It is relevant to robot learning, but it should not be counted as Isaac Sim coursework.

- Assignment page: https://simondlevy.academic.wlu.edu/2023/09/10/assignment-6/
