pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven 'M3'
    }

    stages {
        stage('Build') {
        	steps {
                // Get some code from a GitHub repository
                git 'https://github.com/raki2741/java-tomcat-maven-example.git'
            }
	}
	stage ('Build') {
		steps {
			sh 'mvn install'
		}
	}
	stage ('Deploy') {
		steps {
			script {
				nexusArtifactUploader artifacts: [[artifactId: 'java-tomcat-maven-example', classifier: '', file: '/home/ubuntu/workspace/maven-project/target/java-tomcat-maven-example.war', type: 'war']], credentialsId: 'dfd40e02-e39a-45fa-89f1-bd696fc92846', groupId: 'com.example', nexusUrl: '13.234.226.90:8081/', nexusVersion: 'nexus2', protocol: 'http', repository: 'maven-central', version: '1.0-SNAPSHOT'
			}
		}
	}
    }
}
