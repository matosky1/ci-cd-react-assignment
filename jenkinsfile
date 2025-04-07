pipeline {
    agent any

    stages {
        stage('Build'){

        } 
        stage('Test')
        {
            agent {
                docker {
                    image 'node:22.14.0-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    // ls -la
                    // node --version
                    // npm --version
                    // npm install
                    // npm run build
                    // ls -la
                    test -f build/index.html
                    npm test
                '''
            }
        }
        // stage('Test') {
        //     agent{
        //         docker{
        //             image 'node:22.14.0-alpine'
        //             reuseNode true
        //         }
        //     }
        //     steps {
        //         sh '''
        //           test -f build/index.html
        //           npm test
        //         '''
        //     }
        // }
    }
}a