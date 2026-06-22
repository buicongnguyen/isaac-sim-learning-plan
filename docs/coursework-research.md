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

Finding: this graduate course explicitly uses Isaac Sim. This is currently one of the best 2025 sources for Isaac Sim coursework with public assignment PDFs.

Notes:

- The course page says much of the course is practical work with ROS and ISAAC Simulation.
- Activity 1 starts an `isaac-sim` Docker environment and a Python simulation suite.
- Assignment 5 uses Isaac Sim for particle-filter localization.
- Assignment 6 uses Isaac Sim for RRT path planning.
- Re-check on 2026-06-23: Fall 2025 CSC752 assignments are public. Assignment 4 uses Isaac Simulator with the RoboCanes Lab and HSR robot data for EKF localization. Assignment 5 starts an Isaac Sim RoboCanes lab world for particle-filter localization. Assignment 6 starts an Isaac Sim RoboCanes lab world for RRT path planning.

Links:

- Course page: https://www.cs.miami.edu/~visser/csc752-autonomous-robotic-systems.html
- Activity 1 PDF: https://www.cs.miami.edu/home/visser/csc752-files/CSC752-Activity-1.pdf
- Fall 2025 Assignment 4 PDF: https://www.cs.miami.edu/home/visser/csc752-files/CSC752-Assignment-4.pdf
- Assignment 5 PDF: https://www.cs.miami.edu/home/visser/csc752-files/CSC752-Assignment-5.pdf
- Assignment 6 PDF: https://www.cs.miami.edu/home/visser/csc752-files/CSC752-Assignment-6.pdf

## HKU DATA8010 / ELEC8111: Embodied AI, Spring 2026

Finding: official Spring 2026 course page with simulation-based assignments and an Isaac Sim tutorial.

Notes:

- Course title: Embodied AI: Perception, Representation, and Action.
- The course description says students learn through simulation-based assignments, survey projects, and seminar discussions.
- Schedule includes "Tutorials on Issac Sim and PyBullet" on Feb 10 with HW1.
- The linked Isaac Sim tutorial PDF covers Isaac Sim background, architecture, USD, GPU simulation, batched environments, and an Isaac Lab inverse-kinematics example.

Links:

- Course page: https://embodied-ai-hku.github.io/DATA8010/
- Isaac Sim tutorial PDF: https://embodied-ai-hku.github.io/DATA8010/slides/Issac%20Sim%20Tutorial.pdf

## UC Berkeley EECS C106B: Robotic Manipulation and Interaction, Spring 2026

Finding: promising Spring 2026 Isaac Lab / Isaac Sim course-project lead, but the Isaac handout source found is third-party rather than the official course site.

Notes:

- Berkeley's class schedule confirms EECS C106B was offered in Spring 2026 as Robotic Manipulation and Interaction.
- A third-party uploaded project handout titled "EECS C106B SP26: Project 4b - Reinforcement Learning in Isaac Sim" says students work in Isaac Lab and Isaac Sim on an Allegro in-hand reorientation task, PPO, reward design, and sim-to-real deployment.
- Treat this as a strong lead to investigate further, but not as fully verified official public course material unless an official Berkeley-hosted copy is found.

Links:

- Berkeley course catalog page: https://www2.eecs.berkeley.edu/Courses/EECSC106B/
- Berkeley Spring 2026 class schedule search result: https://classes.berkeley.edu/taxonomy/term/6346?page=13
- Third-party project preview: https://www.studocu.com/en-us/document/university-of-california-berkeley/introduction-to-robotics/eecs-c106b-sp26-project-4b-reinforcement-learning-in-isaac-sim/162444539

## Clemson Creative Inquiry: Introduction to Embodied AI and Vision-Language-Action Robotics

Finding: active project/course-style experiential learning page mentioning Isaac Sim as one supported simulator.

Notes:

- Clemson's active Creative Inquiry project list includes "Introduction to Embodied AI and Vision-Language-Action Robotics."
- The project describes a data-driven robotics course/project where students teach robots to perceive and manipulate using natural language commands.
- It says the course utilizes physics simulators such as MuJoCo, Isaac Sim, or PyBullet.

Links:

- Clemson CI projects page: https://www.clemson.edu/centers-institutes/watt/creative-inquiry/ci-projects.html

## Georgia Tech VIP: Laboratory for Intelligent Decision and Autonomous Robots

Finding: active project-based course/research program with IsaacLab/IsaacSim humanoid projects.

Notes:

- The VIP page includes humanoid loco-manipulation and RL projects.
- One project says simulation will be conducted in IsaacLab, followed by hardware testing.
- Another says students will use IsaacLab to train RL agents for G1 humanoid locomotion.
- Several projects list grading based on proposal, midterm, final report, presentation, participation, or weekly progress, making this course-like project work rather than a conventional lecture course.

Links:

- VIP page: https://lab-idar.gatech.edu/vip/

## NVIDIA Physical AI Learning, 2026

Finding: current official self-paced course hub, not university homework, but very up-to-date Isaac Sim / Isaac Lab practice material.

Notes:

- The 2026 NVIDIA Physical AI Learning page lists free self-paced paths for Isaac Sim, Isaac Lab, Isaac ROS, OpenUSD, healthcare robotics, and SO-101 sim-to-real.
- The SO-101 course covers a complete sim-to-real workflow with Isaac Lab, GR00T, LeRobot, Cosmos, and real hardware.
- This is likely the freshest structured learning path for modern Isaac Sim/Isaac Lab workflows.

Links:

- Physical AI Learning hub: https://docs.nvidia.com/learning/physical-ai/
- SO-101 workshop repository: https://github.com/isaac-sim/Sim-to-Real-SO-101-Workshop

## University of Pennsylvania Course-Project Lead, 2025

Finding: student project page only, but useful as evidence of recent course projects using Isaac Lab.

Notes:

- A UPenn GRASP student project page lists "Autonomous Drone Racing with Reinforcement Learning" as a 2025 course project for ESE 6510 Physical Intelligence: Science and Systems.
- It says the project trained a quadcopter through a race track in the NVIDIA Isaac Lab simulator using PPO, observation engineering, reward design, and domain randomization.

Links:

- Project page: https://beethoven-q.github.io/kaitianchao/

## NVIDIA Practice Materials

These are not traditional university homework sequences, but they are useful as structured Isaac Sim practice.

- Isaac Sim + Jetson HIL course docs: https://nvidia-ai-iot.github.io/isaac-sim-jetson-hil-course-doc/
- Isaac Sim exercises: https://nvidia-ai-iot.github.io/isaac-sim-jetson-hil-course-doc/isaac-sim/index.html
- Hardware-in-loop exercises: https://nvidia-ai-iot.github.io/isaac-sim-jetson-hil-course-doc/hardware-in-loop.html
- Industrial Metaverse Teaching Kit syllabus: https://developer.nvidia.com/industrial-metaverse-teaching-kit-syllabus

## Related But Not Isaac Sim

Washington and Lee Assignment 6 uses Isaac Gym and IsaacGymEnvs for deep reinforcement learning practice. It is relevant to robot learning, but it should not be counted as Isaac Sim coursework.

- Assignment page: https://simondlevy.academic.wlu.edu/2023/09/10/assignment-6/
