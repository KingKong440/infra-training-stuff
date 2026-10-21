# CNC-13: Day 7 | Task 5 | Set Up a Jenkins Multibranch Pipeline Using Maven

- **Jira:** https://mail4mithunu.atlassian.net/browse/CNC-13
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-21T11:53:13.167Z
- **Updated:** 2026-10-21T12:25:39.492Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

Set up a Jenkins Multibranch Pipeline using either AWS EC2 or local Docker. Install Maven and the required Jenkins plugins, then build and test the existing GitHub Maven project using a Jenkinsfile.

Part 1: Set Up Jenkins

Choose one of the following options.

Option A: Host Jenkins on AWS EC2

1. Launch an EC2 instance using Amazon Linux 2023 or Ubuntu.
2. Install Java, Maven, and Git.
3. Install Jenkins using the official instructions: https://www.jenkins.io/doc/book/installing/
4. Start and enable Jenkins.
5. Access Jenkins at http://<EC2-PUBLIC-IP>:8080.
For Amazon Linux 2023, install the build tools:


```
sudo dnf install java-21-amazon-corretto-devel maven git -y
```

Verify the installations:


```
java -version
mvn -version
git --version
sudo systemctl status jenkins
```

Configure the EC2 security group to allow port 8080 from your IP address.

Option B: Host Jenkins Locally Using Docker

Create a persistent Jenkins volume and start the Jenkins container:


```
docker volume create jenkins_home

docker run -d \
  --name jenkins \
  --restart unless-stopped \
  -p 8080:8080 \
  -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  jenkins/jenkins:lts-jdk21
```

Check that Jenkins is running:


```
docker ps
docker logs jenkins
```

Open http://localhost:8080 and complete the initial setup.

Install Maven and Git inside the container:


```
docker exec -u root -it jenkins bash

apt-get update
apt-get install -y maven git

java -version
mvn -version
git --version

exit
```

Verify Maven from outside the container:


```
docker exec jenkins mvn -version
```

Note: Installing packages inside a running container is suitable for this lab. For a permanent setup, create a custom Jenkins image containing the required tools.

Part 2: Install Jenkins Plugins

From Manage Jenkins → Plugins, install:

- Pipeline
- Pipeline: Stage View
- Git
- GitHub Branch Source
Restart Jenkins if required.

Part 3: Use the Existing Maven Repository

Use the following GitHub repository:

Repository: https://github.com/Akshiv20/java-hello-world-with-maven 

Clone it locally to inspect its structure:


```
git clone https://github.com/Akshiv20/java-hello-world-with-maven.git
cd java-hello-world-with-maven
```

Verify that the project contains a pom.xml file and the Java source and test files required for a Maven build.

Part 4: Create the Jenkinsfile

Create a file named Jenkinsfile in the repository root with the following pipeline, following the provided example:


```
pipeline {
    agent any

    stages {
        stage("Clean Up") {
            steps {
                deleteDir()
            }
        }

        stage("Clone Repo") {
            steps {
                sh "git clone https://github.com/Akshiv20/java-hello-world-with-maven.git"
            }
        }

        stage("Build") {
            steps {
                dir("java-hello-world-with-maven") {
                    sh "mvn clean install"
                }
            }
        }

        stage("Test") {
            steps {
                dir("java-hello-world-with-maven") {
                    sh "mvn test"
                }
            }
        }
    }
}
```

Commit and push the Jenkinsfile to the GitHub repository. If you do not have write access to the repository, fork it into your own GitHub account and use your fork's URL in the Jenkinsfile and pipeline configuration.

Part 5: Configure the Multibranch Pipeline

1. Open Jenkins and select New Item.
2. Enter maven-multibranch-pipeline.
3. Select Multibranch Pipeline and click OK.
4. Under Branch Sources, add GitHub Branch Source or Git.
5. Configure the repository URL:  https://github.com/Akshiv20/java-hello-world-with-maven.git
6. Add credentials if required for a private repository.
7. Configure branch discovery and save.
8. Select Scan Multibranch Pipeline Now.
9. Verify that Jenkins discovers the branches containing a Jenkinsfile.
10. Run the pipeline for the discovered branches.
Part 6: Verify Stage View

Open the Multibranch Pipeline's branch job and inspect Stage View.

Verify that the following stages execute:

1. Clean Up
2. Clone Repo
3. Build
4. Test
Confirm that Maven commands complete successfully and the stage results are visible.

## Attachments

- [screenshot-2026-10-21_17-52-16.png](attachments/screenshot-2026-10-21_17-52-16.png)
- [screenshot-2026-10-21_17-52-38.png](attachments/screenshot-2026-10-21_17-52-38.png)
- [screenshot-2026-10-21_17-53-24.png](attachments/screenshot-2026-10-21_17-53-24.png)
- [screenshot-2026-10-21_17-54-46.png](attachments/screenshot-2026-10-21_17-54-46.png)
