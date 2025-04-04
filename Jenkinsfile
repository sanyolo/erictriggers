pipeline {
	agent any
	tools {
	    maven "maven"
	    jdk "jdk"
	}

	stages {


	    stage('Fetch code') {
            steps {
               git branch: 'main', url: 'https://github.com/hkhcoder/vprofile-project.git'
            }

	    }


	    stage('Build'){
	        steps{
	           bat 'mvn install -DskipTests'
	        }

	        post {
	           success {
	              echo 'Now Archiving it...'
	              archiveArtifacts artifacts: '**/target/*.war'
	           }
	        }
	    }

	    stage('UNIT TEST') {
            steps{
                bat 'mvn test'
            }
        }

        stage('Checkstyle Analysis') {
            steps{
                bat 'mvn checkstyle:checkstyle'
            }
        }

	}
}
