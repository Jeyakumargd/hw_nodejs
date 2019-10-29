node {
    def app

    stage('Clone repository') {
        checkout scm
    }

    stage('Build image') {
        app = docker.build("jeyakumargd/hw_nodejs")
    }

    stage('Test image') {
        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        docker.withRegistry('docker.io', 'doc_hub' ) {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
