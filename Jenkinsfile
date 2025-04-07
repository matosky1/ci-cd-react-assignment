pipeline {
    agent {
        docker {
            image 'node:22.1.0-alpine' 
        }
    }

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
            steps {
                sh '''
                    echo "Running tests..."
                    npm test -- --watchAll=false
                '''
            }
        }

        // stage('Deploy') {
        //     environment {
        //         NETLIFY_AUTH_TOKEN = credentials('netlify-token')
        //         NETLIFY_SITE_ID = 'your-netlify-site-id'
        //     }
        //     steps {
        //         sh '''
        //             echo "Installing Netlify CLI..."
        //             npm install -g netlify-cli
        //             echo "Deploying to Netlify..."
        //             netlify deploy --prod --dir=build --auth=$NETLIFY_AUTH_TOKEN --site=$NETLIFY_SITE_ID
        //         '''
        //     }
        // }
    }
}
