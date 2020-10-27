pipeline {
	agent any

	stages {
		stage("Make package-lock") {
			steps {
				sh 'npm install'
			}
		}
		stage ("Snyk API Authentication") {
			sh 'snyk auth 1ecb298e-b334-4b22-8ed3-ff0ffd45e99c'
		}
                stage ("Snyk test report"){
                    steps {
                            sh 'snyk test --json > /var/lib/jenkins/reports/snyk_report.json'
			}

		}
                  stage("Snyk dashboard monitor") {
                       steps {
                               sh 'snyk monitor'
                       }
                }		

	}
}
