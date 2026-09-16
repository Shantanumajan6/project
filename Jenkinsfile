pipeline {
    agent any

    stages {

        stage('MAVEN_BUILD') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy') {
            steps {
                sh 'cp target/*.war /mnt/servers/apache-tomcat-10.1.59/webapps/'
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
