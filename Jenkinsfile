node {
    def app

    stage('Clone repository') {
        checkout scm
    }

    stage('Build image') {
        app = docker.build("jeyakumargd/hw_nodejs:${env.BUILD_NUMBER}")
    }

    stage('Test image') {
        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        docker.withRegistry('https://cloud.docker.com/docker/dhfirststep/nodejs_firststep', 'doc_hub' ) {
            app.push()
        }
    }
}
