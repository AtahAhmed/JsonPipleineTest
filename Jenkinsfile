@Library('stratus-jenkins-shared-library@master') _
import java.text.SimpleDateFormat
import java.util.Date

pipeline {
    agent any

// We can provide the few options like timeout, timestamps etc..
    options {
        disableConcurrentBuilds()
        timeout(time: 60, unit: 'MINUTES')
        timestamps()
    }
    // TO define the evn variable as key value pari
     environment {}

     stages {
		stage('Initialization') {
            steps {
				def featureFlagJsonFiles = findFiles(glob: 'ff-*.json') 
				for featureFlagJsonFile in featureFlagJsonFiles
					def content = readJSON file: featureFlagJsonFile.path + '/' + featureFlagJsonFile.name + '.json'
					
					sh (curl -X POST -H "Content-Type: application/json"  --data content https://localhost:8082/postJson/ )
			}

       
        }
		
	}


}