pipeline {
  agent any
  stages {
    stage('Upload to AWS') {
      parallel {
        stage('Upload to AWS') {
          steps {
            sh 'echo "Hello World"'
            sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
            withAWS(credentials: 'jenkins', region: 'us-east-2') {
              s3Upload(bucket: 'jenkin-udacity-project', pathStyleAccessEnabled: true, payloadSigningEnabled: true, file: 'index.html')
            }

          }
        }

        stage('Lint HTML') {
          steps {
            sh 'tidy -q -e *.html'
          }
        }

      }
    }

  }
}