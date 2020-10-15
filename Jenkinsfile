pipeline {

    agent any

    stages {

        stage ('Initialization') {
            steps {
                sh 'echo "Starting the build"'
            }
        }

        stage ('Build') {
            steps {
                sh '''
		    echo "Starting Build....."
                    npm install
                   '''
            }
        }

		stage ('Audit') {
			steps {
				sh 'npm audit --json > npm-audit-report.json'
			}
		}

    }

}
