node {
    def mvnHome
    stage('Preparation') { 
        git 'https://github.com/boopathikt/fleetman-position-tracker/'

    }
    stage('Build') {
        
        sh "mvn package"
    }

    stage('Results') {
        junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts 'target/*.jar'
    }
    
    stage ('Deploy'){
      ansiblePlaybook credentialsId: 'ssh-credentials', installation: 'ansible-installation', playbook: 'deploy.yaml', sudoUser: null
    }
}
