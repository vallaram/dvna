pipeline {
	agent any

	stages {
		stage("Testing Phase of DVNA") {
                       steps {
			sh 'ssh root@178.62.36.148 docker run -v `pwd`/db.sqlite:/app/db.sqlite --name dvna -p 9090:9090 -d appsecco/dvna:sqlite'
                       }
		}
		stage("OWASP ZAP Analysis") {
			steps {
				sh 'python3 /var/lib/jenkins/reports/owasp-zap-auth-scan.py'
			}
		}
		stage("Close DVNA") {
                        steps {
			  sh 'ssh root@178.62.36.148 docker rm -f dvna'
                        }
		}
	}
}
