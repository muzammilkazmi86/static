pipeline {
    agent any
    stages {
        stage('Upload to AWS') {
            steps {
                withAWS(region: 'us-east-2', credentials: 'jenkins') {
                s3Upload(bucket: 'jenkin-udacity-project', pathStyleAccessEnabled: true, payloadSigningEnabled: true, file: 'index.html')
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
            }
        }
    }
}
