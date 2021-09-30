pipeline {
    agent any

    stages {
        stage('CI') {
            steps {
                // Get some code from a GitHub repository
                // Run Maven on a Unix agent.
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                //docker login -u ${USERNAME}  -p ${PASSWORD}
                //docker push ahmedarafat10/jenkins_nodejs:latest
                sh """
                docker build . -f dockerfile -t ahmedarafat10/jenkins_nodejs:latest
              
                
                """

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        
        }     
                stage('CD') {
            steps {

                sh """

                docker run -d -p 3000:3000 ahmedarafat10/jenkins_nodejs:latest
                
                """

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }

        }
    }
}
