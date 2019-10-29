node {
    def app

    stage('pull images')
        {
        docker.withRegistry('', 'doc_hub') {
            sh 'docker pull dhfirststep/nodejs_firststep/nodejs_app-20'
        }
    }

    stage('run application')
        {
        sh 'docker run --rm -d -p 8082:8081 dhfirststep/nodejs_firststep/nodejs_app-20'
    }

}
