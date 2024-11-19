pipeline{
    agent any
    
    stages{
        
        stage('Checkout'){
            steps{
                checkout([
                    $class:'GitSCM',
                    branches:[[name: '*/main']],
                    userRemoteConfigs:[[
                            url:'https://github.com/architdhiman/selenium-amazon.git'
                        ]]
                    
                    ]
                )
            }
        }
        
         stage('Code clean'){
            steps{
                bat "mvn clean"
            }
        }
        
         stage('Code Compile'){
            steps{
                bat "mvn compile"
            }
        }
        
         stage('Test'){
            steps{
                bat "mvn test"
            }
        }
        
    }
    
}
