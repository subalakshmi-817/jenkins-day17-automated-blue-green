# 🚀 Jenkins Day 17 – Automated Blue-Green Deployment

![Jenkins](https://img.shields.io/badge/Jenkins-CI%2FCD-red)
![Docker](https://img.shields.io/badge/Docker-Containerization-blue)
![GitHub](https://img.shields.io/badge/GitHub-Source%20Control-black)
![Nginx](https://img.shields.io/badge/Nginx-Web%20Server-green)
![Linux](https://img.shields.io/badge/Linux-Ubuntu-orange)
![DevOps](https://img.shields.io/badge/DevOps-Automation-purple)
![Blue-Green](https://img.shields.io/badge/Deployment-Blue--Green-brightgreen)
![Pipeline](https://img.shields.io/badge/Jenkins-Pipeline-yellow)

---

# 📌 Project Title

## Jenkins Day 17 – Automated Blue-Green Deployment

This project demonstrates an automated **Blue-Green Deployment strategy** using:

- Jenkins
- Docker
- GitHub
- Nginx
- Linux
- Shell scripting
- Jenkins Declarative Pipeline
- Docker containers
- Automated health checks
- Continuous Integration
- Continuous Deployment

The main purpose of this project is to understand how Jenkins can automatically build Docker images, deploy two different application environments, perform health checks, and verify the deployment.

---

# 📖 Table of Contents

1. Project Overview
2. Project Objective
3. What is Blue-Green Deployment?
4. Why Blue-Green Deployment?
5. Traditional Deployment Problem
6. Blue-Green Deployment Solution
7. Project Architecture
8. Architecture Flow
9. Technologies Used
10. Tools Required
11. Hardware Requirements
12. Software Requirements
13. Project Folder Structure
14. Blue Environment
15. Green Environment
16. Dockerfile Explanation
17. HTML Application
18. Jenkins Overview
19. Jenkins Pipeline Overview
20. GitHub Integration
21. Docker Integration
22. Jenkins Docker Permission
23. Pipeline Stages
24. Stage 1 – Checkout
25. Stage 2 – Build Blue Image
26. Stage 3 – Build Green Image
27. Stage 4 – Remove Old Containers
28. Stage 5 – Deploy Blue
29. Stage 6 – Health Check Blue
30. Stage 7 – Deploy Green
31. Stage 8 – Health Check Green
32. Stage 9 – Verify Deployment
33. Post Actions
34. Docker Images
35. Docker Containers
36. Port Mapping
37. Health Checks
38. Deployment Verification
39. Manual Deployment
40. Automated Deployment
41. Jenkins Job Configuration
42. Jenkinsfile
43. Git Configuration
44. GitHub Repository
45. Repository Description
46. README Documentation
47. Screenshots
48. Screenshot List
49. Installation
50. Configuration
51. Running the Project
52. Testing Blue
53. Testing Green
54. Testing Docker
55. Testing Jenkins
56. Troubleshooting
57. Docker Hub Network Issue
58. Git Push Error
59. Git Pull Rebase
60. Container Name Conflict
61. Jenkins Docker Permission Error
62. Docker Build Error
63. Workspace Error
64. Missing Blue Directory
65. Missing Green Directory
66. Jenkins Pipeline Failure
67. Health Check Failure
68. Port Conflict
69. Logs
70. Useful Commands
71. Git Commands
72. Docker Commands
73. Jenkins Commands
74. Linux Commands
75. Security Considerations
76. DevOps Concepts Learned
77. CI Concepts
78. CD Concepts
79. Infrastructure Automation
80. Containerization
81. Deployment Strategy
82. Advantages
83. Limitations
84. Real-World Applications
85. Production Improvements
86. Future Enhancements
87. Learning Outcomes
88. Project Workflow
89. Final Verification
90. Conclusion
91. Author
92. Project Status
93. Day 17 Learning Summary

---

# 1. 🚀 Project Overview

This project is part of my DevOps and Jenkins learning journey.

The project focuses on implementing an **Automated Blue-Green Deployment Pipeline** using Jenkins and Docker.

The application has two separate deployment environments:

- 🔵 Blue Environment
- 🟢 Green Environment

Each environment runs inside its own Docker container.

Jenkins is responsible for automating the deployment process.

The pipeline performs the following operations:

1. Checkout source code from GitHub.
2. Build the Blue Docker image.
3. Build the Green Docker image.
4. Remove old deployment containers.
5. Deploy the Blue environment.
6. Perform a Blue health check.
7. Deploy the Green environment.
8. Perform a Green health check.
9. Verify both deployments.
10. Display the final pipeline result.

---

# 2. 🎯 Project Objective

The main objective of this project is to understand automated deployment using Jenkins.

The project demonstrates how a DevOps engineer can automate application deployment using CI/CD tools.

The objectives are:

- Understand Jenkins pipelines.
- Understand Docker image creation.
- Understand Docker containers.
- Understand Blue-Green Deployment.
- Integrate GitHub with Jenkins.
- Automate Docker builds.
- Automate container deployment.
- Perform application health checks.
- Reduce manual deployment work.
- Improve deployment reliability.
- Understand CI/CD automation.
- Learn practical DevOps workflow.

---

# 3. 🔵🟢 What is Blue-Green Deployment?

Blue-Green Deployment is a deployment strategy where two separate application environments are maintained.

The environments are commonly called:

- Blue
- Green

The Blue environment represents one version of the application.

The Green environment represents another version of the application.

Instead of directly replacing the currently running application, the new version is deployed separately.

The new environment can then be tested before traffic is moved to it.

This reduces deployment risk.

---

# 4. 🤔 Why Blue-Green Deployment?

Traditional deployment can cause downtime.

For example:

```text
Old Application
      ↓
Stop Application
      ↓
Install New Version
      ↓
Start Application
      ↓
Application Available
