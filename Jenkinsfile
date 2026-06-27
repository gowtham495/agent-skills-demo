node('scan-server') {

    stage('Checkout') {
        checkout scm
    }

    stage('Scan All Skills') {
        sh '''
            docker run --rm \
                -v "$WORKSPACE:/scan" \
                skillspector:latest \
                scan /scan/skills -r --no-llm -f markdown > report.md
        '''
    }

    stage('Archive Report') {
        archiveArtifacts artifacts: 'report.md', fingerprint: true
    }
}