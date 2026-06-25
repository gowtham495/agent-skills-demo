node('skillspector') {

    stage('Checkout') {
        checkout scm
    }

    stage('Scan Skills') {
        sh '''
            skillspector scan . --output report.json
        '''
    }

    stage('Show Report') {
        sh 'cat report.json'
    }
}