pipeline {
      agent any
      stages {
        stage('Build') {
                    // Get some code from a GitHub repository
                    git credentialsId: '4a96169d-d4a3-4e84-87e8-4c2723d619f1', url: 'https://github.com/ZygmuntJakub/isdp_3'

                    // Run Maven on a Unix agent.
                    sh "mvn clean package"
              }
               stage('DBCheck') {
        				sh "mvn compile exec:java -Dexec.mainClass=\"DBCheck\" -f ~/DBCheckTest/pom.xml"
                    }

               stage('Deploy') {
                          // Run Maven deploy.
                          sh "mvn cargo:redeploy"
                          }
      }

}