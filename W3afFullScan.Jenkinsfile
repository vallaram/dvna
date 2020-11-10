pipeline {
	agent any

	stages {
               stage("Testing Phase of DVNA") {
                       steps {
			sh 'ssh root@178.62.36.148 docker run --name dvna -p 9090:9090 -d appsecco/dvna:sqlite'
                       }
		}

                stage("W3af Full Scan Analysis") {
			steps {
				sh 'docker run -it andresriancho/w3af `./w3af_console -s /var/lib/jenkins/reports/full.w3af`'
			}
		}

		stage("Close DVNA") {
                        steps {
			  sh 'ssh root@178.62.36.148 docker rm -f dvna'
                        }
                }
	    	
        }
   }
