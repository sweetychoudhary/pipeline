pipeline {
    agent any

	tools {
		maven 'maven3.6'
	}
//
//	environment {
//		M2_INSTALL = "/home/gamut/Distros/apache-maven-3.6.0/bin/mvn"
//	}

    stages {
		stage('Clone-Repo') {
			steps {
				checkout scm
			}
		}
		stage('Build') {
	    	steps {
				sh 'mvn install -DskipTests'
			}
	    }
		stage('Unit Tests') {
			steps {
				sh 'mvn surefire:test'
			}
		}
		stage('Deployment') {
	    	steps {
				sh 'sshpass -p "sonu" scp target/gamutkart.war sonu@13.232.104.180:/root/'
				//sh 'sshpass -p "gamut" ssh -i cdepem.pem gamut@172.17.0.3 "JAVA_HOME=/home/gamut/Distros/jdk1.8.0_211" "/home/gamut/Distros/apache-tomcat-8.5.41/bin/startup.sh"'
	    	}
		}
    }
}
