pipeline {
	agent any

	stages {
		stage("Make package-lock") {
			steps {
				sh 'npm install'
			}
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
