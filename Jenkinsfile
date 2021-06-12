pipeline {
  agent any
  stages {
    stage('Lint HTML') {
      sh 'tidy -q -e *.html'
    }
    stage('Upload to AWS') {
      steps {
        withAWS(region:'us-east-2', credentials:"aws-static") {
          s3Upload(file:'index.html', bucket:'arn-jenkins-bucket', path:'index.html')
        }
        sh 'echo "Hello World"'
        sh '''
            echo "Multiline shell steps works too"
            ls -lah
        '''
      }
    }
  }
}
