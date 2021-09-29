pipeline {
    agent any

    stages {
        stage('CI') {
            steps {
                // Get some code from a GitHub repository
                // Run Maven on a Unix agent.
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {

                sh """
                docker build . -f dockerfile -t ahmedaraft10/jenkins_nodejs:latest
                docker login -u ${USERNAME}  -p ${PASSWORD}
                docker push ahmedaraft10/jenkins_nodejs:latest
                
                """

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
}
        }
        
        
                stage('CD') {
            steps {

                sh """

                docker run -p 3000:3000 ahmedaraft10/jenkins_nodejs:latest
                
                """

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }

        }
    }
}
