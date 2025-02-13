pipeline {
    agent {
        label {
            label "built-in-project"
            customWorkspace "/data/project-myapp"
        }
    }

    stages {
        stage ('CLEAN OLD MAVEN REPO') {
            steps {
                sh "rm -rf /home/saccount/.m2/repository"
            }
        }

        stage ('BUILD WITH MAVEN') {
            steps {
                sh "mvn clean package"
            }
        }

        stage ('DEPLOY WAR TO SERVER') {
            steps {
          
