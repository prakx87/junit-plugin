pipeline {
    agent any
	tools {
	    maven 'Maven 3.3.9'
	    jdk 'jdk8'
    }
    stages {
	    stage('Initialize') {
            steps {
                sh '''
		    export JAVA_HOME=/var/jenkins_home/tools/hudson.model.JDK/jdk8/jre
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
		    echo "JAVA_HOME = ${JAVA_HOME}"
                '''
            }
        }
        stage('Build') {
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true install'
            }
            post {
                success {
                    junit 'target/surefire/reports/**/*.xml'
                }
            }
        }
    }
}
