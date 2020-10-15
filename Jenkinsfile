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
				sh 'npm audit --json || echo 0'
			}
		}

		stage ("NodeJSScan") {
			steps {
				sh 'nodejsscan -d `pwd` --output nodejsscan.report'
			}
		}

		stage ("Retire.js") {
			steps {
				sh 'retire --path `pwd` --outputpath retire.report --exitwith 0'
			}
		}

    }

}
