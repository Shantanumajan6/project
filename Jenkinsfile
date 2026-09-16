pipeline {
    agent any

    stages {

        stage('MAVEN_BUILD') {
            steps {
                sh '/mnt/build-tools/apache-maven-3.9.16/bin/mvn -f /mnt/project/pom.xml clean package'
            }
        }

        stage('Deploy') {
            steps {
               sh 'cp /mnt/project/target/LoginWebApp.war /mnt/servers/apache-tomcat-10.1.59/webapps/LoginWebApp.war'
            }
        }

        stage('Restart Tomcat') {
            steps {
                sh '/mnt/servers/apache-tomcat-10.1.59/bin/shutdown.sh || true'
                sh 'sleep 5'
                sh '/mnt/servers/apache-tomcat-10.1.59/bin/startup.sh'
            }
        }

    }
}
