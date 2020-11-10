pipeline {
	agent any

	stages {
               stage("Testing Phase of DVNA") {
                       steps {
			sh 'ssh root@178.62.36.148 docker rm -f dvna'
			sh 'ssh root@178.62.36.148 docker run --name dvna -p 9090:9090 -d appsecco/dvna:sqlite'
                       }
		}

                stage("W3af Full Scan Analysis") {
			steps {
				sh 'docker run -v /var/lib/jenkins/reports/:/home/w3af/w3af/scripts angadsharma1016/w3af:cd22e5252-edge ./w3af_console -y -s /home/w3af/w3af/scripts/full.w3af'
			}
		}

		stage("Close DVNA") {
                        steps {
			  sh 'ssh root@178.62.36.148 docker rm -f dvna'
                        }
                }
	    	
        }
   }
