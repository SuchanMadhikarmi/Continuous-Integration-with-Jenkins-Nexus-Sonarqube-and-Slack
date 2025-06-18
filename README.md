# CI Project using Jenkins, Nexus, SonarQube, and Slack 

## Project Description

This project showcases a **fully automated Continuous Integration (CI) pipeline** implemented using **Jenkins**, **Nexus**, **SonarQube**, and **Slack integration**, hosted on **AWS EC2** instances. The pipeline ensures seamless **code quality checks, artifact management, security enforcement**, and **real-time collaboration notifications**. 

### **Key Features & Best Practices:**
- **CI/CD Automation:** Streamlined application build, test, and validation processes.
- **Infrastructure Security:** Secure credential management via **IAM roles** and **Jenkins secrets**.
- **Artifact Management:** Version-controlled storage using **Nexus Repository** to ensure stable deployments.
- **Code Quality Analysis:** Integrated **SonarQube** scans to enforce coding standards and identify vulnerabilities.
- **Collaboration Feedback:** **Slack Notifications** provide real-time updates on build status, ensuring team visibility.

This deployment guarantees **efficient, reliable, and scalable application builds**, while enforcing **quality gates** before production readiness.

---
## Next Phase: Continuous Delivery (CD)

Following the successful implementation of CI, the next phase of the project will focus on **Continuous Delivery (CD)**, enabling seamless **deployment automation** with **AWS ECS** and **Amazon ECR**. This ensures that validated code moves from **staging to production** through a robust, automated **delivery pipeline**, maintaining high availability and minimizing downtime.

For the next part of this project, check out the repository here:  
🔗 [Continuous Delivery of Java Web Application](https://github.com/SuchanMadhikarmi/Continuous-Delivery-of-java-web-application)



> **Note**: All configuration scripts including EC2 userdata and Jenkinsfile are available in the repository. Screenshots of the deployment steps are provided in the `screenshots/` folder.

---

## Tools & Technologies Used

- **CI Server**: Jenkins (hosted on EC2)  
- **Artifact Repository**: Nexus Repository Manager  
- **Static Code Analysis**: SonarQube  
- **Notification & Collaboration**: Slack  
- **Cloud Platform**: AWS EC2  
- **Build Tools**: Maven, JDK  
- **Source Control**: GitHub  
- **Scripting**: Bash, Jenkins Pipeline (Jenkinsfile)  

---

## Project Architecture
<p align="center">
  <img src="https://i.imgur.com/M4WicD6.png" height="80%" width="80%" alt="Geolocation Lookup"/>
</p>

</br>

## Security & Server Setup

### Step 1: Security Groups Configuration
Applied **least privilege principle** to each EC2 instance:

- **Jenkins**: Allowed only necessary ports (e.g., `8080`) from trusted IPs.
- **Nexus**: Made accessible only from Jenkins.
- **SonarQube**: Restricted access to Jenkins only for scanning.

### Step 2: EC2 Instance Setup
Launched three EC2 instances:

- `jenkins-server`
- `nexus-server`
- `sonarqube-server`

Installed and configured all required tools using **custom EC2 UserData scripts** (included in the repo).

---

## Jenkins Configuration

### Step 1: Initial Setup
Completed Jenkins **post-install setup**.

Installed essential plugins:

- GitHub Integration  
- SonarQube Scanner  
- Slack Notification  
- Timestamper (for artifact versioning)

### Step 2: Tool Configuration
- Configured **JDK** and **Maven** in Jenkins Global Tool Configuration.
- Stored **Nexus credentials** in Jenkins credentials manager.

### Step 3: SSH Integration with GitHub
- Forked a sample Maven project from an Udemy course.
- Generated **SSH key pair**.
- Added the **public key** to GitHub.
- Configured `.ssh/config` to map **private key** for GitHub access.

### Step 4: Manual Job Test
- Created and executed a **freestyle build job**.
- Test build **completed successfully**.

---

## Code Quality with SonarQube

### Step 1: SonarQube Integration
- Connected **SonarQube server** with Jenkins.
- Generated **scanner token** and configured it in Jenkins.
- Added **SonarQube analysis stage** in the Jenkinsfile.

### Step 2: Post-scan Notification
- Created a **webhook** in SonarQube to notify Jenkins after the scan completes.

---

## Artifact Management with Nexus

### Step 1: Nexus Repository Setup
Configured 4 Maven repositories:

- **releases** – for stable builds  
- **snapshots** – for development artifacts  
- **central** – mirror of Maven Central  
- **group** – proxy combining all above

### Step 2: Artifact Deployment
- Defined **artifact upload stage** in the Jenkinsfile.
- Enabled **artifact versioning** using the **Timestamper** plugin.

---

## Real-time Slack Notifications

### Step 1: Slack Integration
- Created a dedicated **Slack channel** for build alerts.
- Installed **Jenkins app** in Slack.
- Generated **Slack token** and added it to Jenkins credentials store.
- Configured **Slack plugin** in Jenkins.

### Step 2: Notification Triggers
Configured notifications for:

-  **Build Success**
-  **Build Failure**

Each notification includes:

- **Project Name**
- **Build Status**
- **Direct Jenkins Build Link**

---

##  Screenshots

Find all visual steps inside the `screenshots/` folder, including:

- EC2 instance setup  
- Jenkins pipeline execution  
- SonarQube code scan  
- Nexus repository setup  
- Slack build notifications  

---

---

##  Learning Outcomes

- Gained hands-on experience building a **Continuous Integration (CI) pipeline** using Jenkins, SonarQube, and Nexus.
- Automated code quality checks and artifact management to ensure reliable build processes.
- Integrated real-time notifications with Slack for immediate team feedback.
- Practiced writing and maintaining Jenkins pipelines using the **Pipeline-as-Code** approach.
- Improved understanding of CI best practices and automation on AWS infrastructure.

---

