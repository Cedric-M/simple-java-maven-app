pipeline {
    agent {
        docker {
            image 'maven:3-alpine' 
            args '-v /root/.m2:/root/.m2' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test' //This sh step executes the Maven command to run the unit test on your simple Java application.
            }
            post {
                always {
                    //This junit step archives the JUnit XML report and exposes the results through the Jenkins interface
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
}