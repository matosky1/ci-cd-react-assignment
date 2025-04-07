pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                    echo "Installing dependencies..."
                    npm install
                    echo "Building app..."
                    npm run build
                '''
            }
        }

        stage('Test') {
            agent {
                docker {
                    image 'node:22.14.0-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo "Running tests..."
                    npm install
                    npm test -- --watchAll=false
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    echo "Installing Netlify CLI..."
                    npm install -g netlify-cli
                    echo "Deploying to Netlify..."
                    netlify deploy --prod --dir=build --auth=$NETLIFY_AUTH_TOKEN --site=$NETLIFY_SITE_ID
                '''
            }
        }
    }
}
