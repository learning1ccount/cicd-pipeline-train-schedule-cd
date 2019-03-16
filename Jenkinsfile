pipeline {
    agent any
    stages {
        stage('Build') {
		when {
			branch 'master'
		}
            steps {
                echo 'Running build automation'
                sh './gradlew build --no-daemon'
		archiveArtifacts artifacts: 'dist/trainSchedule.zip'
		}
        }
	stage('staging') {
		when {
			branch 'master'
		}
		steps {
		echo "deployment to staging environment is in progress"
		withCredentials([usernameColonPassword(credentialsId: 'webserver_login', usernameVariable: 'USERNAME', passwordVariable: 'USERPASS')]){
			sh '''
				cp ./dist/trainSchedule.zip /tmp

			'''




			}		
		


		}		


		}

    }
}
