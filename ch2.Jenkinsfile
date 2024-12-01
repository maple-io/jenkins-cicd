pipeline{
    agent any
    parameters{

        choice(name: 'ENVIRONMENT',
               choices:['DEVELOPMENT','STAGING','PRODUCTION'],
               description:'Choose the environment for this deployment'
            )
            
        password(name: 'APIKEY',
               defaultValue:'123ABC',
               description:'Input the API KEY for this deployment'
            )
        
        string(name: 'CHANGELOG',
               defaultValue:'this is default change log',
               description:'Input the content for change log'
            )
            
    }
    stages{
        stage('Test'){
            steps{
                echo '--- Test ----'
            }
        }    
        stage('Deploy'){
            when{
                expression{
                    params.ENVIRONMENT == 'PRODUCTION'
                }
            }
            steps{
                echo '--- Deploy to Prod Environemnt ----'
            }
        }
        stage('Report'){
            steps{
                echo '--- Report ----'
                echo "${params.CHANGELOG}"
                writeFile file: "${params.ENVIRONMENT}.txt", text: "${params.CHANGELOG}"
                
                //sh "echo "${params.CHANGELOG}" > report.txt"
                archiveArtifacts allowEmptyArchive: true, artifacts: '*.txt', fingerprint: true, onlyIfSuccessful: true
            }
        }
            
        
    }
}