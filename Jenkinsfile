node('built-in') {

    stage('Checkout') {
        checkout scm
    }

    stage('Scan Skill') {
        bat '''
            docker run --rm ^
              -v "%WORKSPACE%:/scan" ^
              skillspector:latest ^
              scan /scan/skill.md --no-llm -f markdown > report.md
        '''
    }

    stage('Archive Report') {
        archiveArtifacts artifacts: 'report.md', fingerprint: true
    }
}