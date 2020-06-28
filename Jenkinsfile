pipeline {
     agent any
     stages {
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-east-1',credentials:'MyCredentials') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'devops-c3-static-jenkins')
                  }
              }
         }
         stage('Lint HTML') {
              steps {
                  sh 'tidy -q -e *.html'
              }
         }
        //  stage('Build') {
        //      steps {
        //          sh 'echo "Hello World"'
        //          sh '''
        //              echo "Multiline shell steps works too"
        //              ls -lah
        //          '''
        //      }
        //  }
     }
}
