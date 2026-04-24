# 🚀 Java + Node.js Multi-Stage Jenkins Pipeline

This project demonstrates a **multi-stage, multi-agent Jenkins pipeline** using Docker-based agents to run different technology stacks within the same CI pipeline.

It showcases how Jenkins can dynamically switch environments to execute tasks for **Java (backend)** and **Node.js (frontend)** in isolated containers.

---

## 📌 Project Overview

* 🔹 Uses **Jenkins Declarative Pipeline**
* 🔹 Implements **multi-stage pipeline**
* 🔹 Uses **multi-agent (Docker containers)**
* 🔹 Runs **Java and Node.js in separate environments**
* 🔹 Demonstrates **CI pipeline flexibility across technologies**
---

## 🛠️ Technologies Used

* Jenkins (Pipeline as Code)
* Docker (Agent containers)
* Java (OpenJDK 11)
* Node.js (v16 Alpine)

---

## 📂 Project Structure

```
java-node-multi-stage-pipeline/
│
├── Jenkinsfile
└── README.md
```

---

## ⚙️ Pipeline Workflow

### 🔸 Stage 1: Java Execution

* Uses Docker image: `openjdk:11-jdk-slim`
* Creates a simple Java program
* Compiles using `javac`
* Executes using `java`

### 🔸 Stage 2: Node.js Execution

* Uses Docker image: `node:16-alpine`
* Runs a simple Node.js script
* Prints output to console

---

## 📜 Jenkinsfile

```groovy
pipeline {
  agent none

  stages {
    stage('Java Stage') {
      agent {
        docker { image 'openjdk:11-jdk-slim' }
      }
      steps {
        sh '''
          echo "Running Java Hello World"
          cat <<EOF > HelloWorld.java
          public class HelloWorld {
              public static void main(String[] args) {
                  System.out.println("Hello World from Java!");
              }
          }
          EOF
          javac HelloWorld.java
          java HelloWorld
        '''
      }
    }

    stage('NodeJS Stage') {
      agent {
        docker { image 'node:16-alpine' }
      }
      steps {
        sh '''
          echo "Running Node.js Hello World"
          node -e "console.log('Hello World from Node.js!')"
        '''
      }
    }
  }
}
```

---

## ▶️ How to Use

1. Create a Jenkins Pipeline Job
2. Connect your GitHub repository
3. Set **Script Path**:

   ```
   Jenkinsfile
   ```

   OR if inside folder:

   ```
   java-node-multi-stage-pipeline/Jenkinsfile
   ```
4. Run the pipeline

---

## 📸 Expected Output

* Java stage prints:

  ```
  Hello World from Java!
  ```
* Node.js stage prints:

  ```
  Hello World from Node.js!
  ```

---

## 💡 Key Learnings

* How to use **Docker agents in Jenkins**
* Running **multiple tech stacks in one pipeline**
* Structuring **multi-stage CI pipelines**
* Using **Pipeline as Code (Jenkinsfile)**

---

## 🚀 Future Improvements

* Add build & test stages
* Integrate with GitHub Webhooks
* Add Docker image build & push
* Deploy to AWS / Kubernetes
* Add real backend & frontend apps

---

## 👤 Musthaq Ahamed 

* Your Name

---

## ⭐ If you like this project

Give it a ⭐ on GitHub and use it as a reference for your DevOps learning journey!
