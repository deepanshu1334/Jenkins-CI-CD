// pipeline {
//     agent any

//     environment {
//         FRONTEND_DIR = 'frontend'
//         BACKEND_DIR = 'backend'
//         MONGO_URI = 'mongodb://mongodb:27017/mydb'
//         COMPOSE_FILE = 'docker-compose.yml'
//     }

//     stages {
//         stage('Clone Repository') {
//             steps {
//                 git 'https://github.com/deepanshu1334/Jenkins-CI-CD.git'  // Replace with your repo
//             }
//         }

//         stage('Install Backend Dependencies') {
//             steps {
//                 dir(BACKEND_DIR) {
//                     sh 'npm install'
//                 }
//             }
//         }

//         stage('Run Backend Tests') {
//             steps {
//                 dir(BACKEND_DIR) {
//                     sh 'npm test'  // Make sure you have test scripts in package.json
//                 }
//             }
//         }

//         stage('Install Frontend Dependencies') {
//             steps {
//                 dir(FRONTEND_DIR) {
//                     sh 'npm install'
//                 }
//             }
//         }

//         stage('Build Frontend') {
//             steps {
//                 dir(FRONTEND_DIR) {
//                     sh 'npm run build'
//                 }
//             }
//         }

//         stage('Build Docker Images') {
//             steps {
//                 sh 'docker-compose build'
//             }
//         }

//         stage('Deploy with Docker Compose') {
//             steps {
//                 sh 'docker-compose up -d'
//             }
//         }
//     }

//     post {
//         success {
//             echo '✅ Deployment Successful!'
//         }
//         failure {
//             echo '❌ Deployment Failed. Check logs.'
//         }
//     }
// }






// pipeline {
//     agent any

//     environment {
//         FRONTEND_DIR = 'frontend'
//         BACKEND_DIR = 'backend'
//         MONGO_URI = 'mongodb://mongodb:27017/mydb'
//         COMPOSE_FILE = 'docker-compose.yml'
//     }

//     stages {
//          stage('Clone Repository') {
//     steps {
//         script {
//             checkout([
//                 $class: 'GitSCM',
//                 branches: [[name: 'main']], // Ensure 'main' is used
//                 userRemoteConfigs: [[url: 'https://github.com/deepanshu1334/Jenkins-CI-CD.git']]
//             ])
//         }
//     }
// }


//         stage('Install Backend Dependencies') {
//             steps {
//                 dir(BACKEND_DIR) {
//                     sh 'npm install'
//                 }
//             }
//         }

//         stage('Run Backend Tests') {
//             steps {
//                 dir(BACKEND_DIR) {
//                     sh 'npm test'  // Make sure you have test scripts in package.json
//                 }
//             }
//         }

//         stage('Install Frontend Dependencies') {
//             steps {
//                 dir(FRONTEND_DIR) {
//                     sh 'npm install'
//                 }
//             }
//         }

//         stage('Build Frontend') {
//             steps {
//                 dir(FRONTEND_DIR) {
//                     sh 'npm run build'
//                 }
//             }
//         }

//         stage('Build Docker Images') {
//             steps {
//                 sh 'docker-compose build'
//             }
//         }

//         stage('Deploy with Docker Compose') {
//             steps {
//                 sh 'docker-compose up -d'
//             }
//         }
//     }

//     post {
//         success {
//             echo '✅ Deployment Successful!'
//         }
//         failure {
//             echo '❌ Deployment Failed. Check logs.'
//         }
//     }
// }





pipeline {
    agent any

    environment {
        FRONTEND_DIR = 'frontend'
        BACKEND_DIR = 'backend'
        MONGO_URI = 'mongodb://mongodb:27017/mydb'
        COMPOSE_FILE = 'docker-compose.yml'
    }

    stages {
        stage('Clone Repository') {
            steps {
                script {
                    checkout([
                        $class: 'GitSCM',
                        branches: [[name: 'main']], // Ensure 'main' is used
                        userRemoteConfigs: [[url: 'https://github.com/deepanshu1334/Jenkins-CI-CD.git']]
                    ])
                }
            }
        }

        // Add the Install Docker Compose stage here
        stage('Install Docker Compose') {
            steps {
                script {
                    sh 'curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose'
                    sh 'chmod +x /usr/local/bin/docker-compose'
                    sh 'docker-compose --version' // Check Docker Compose version
                }
            }
        }

        stage('Install Backend Dependencies') {
            steps {
                dir(BACKEND_DIR) {
                    sh 'npm install'
                }
            }
        }

        stage('Run Backend Tests') {
            steps {
                dir(BACKEND_DIR) {
                    sh 'npm test'  // Make sure you have test scripts in package.json
                }
            }
        }

        stage('Install Frontend Dependencies') {
            steps {
                dir(FRONTEND_DIR) {
                    sh 'npm install'
                }
            }
        }

        stage('Build Frontend') {
            steps {
                dir(FRONTEND_DIR) {
                    sh 'npm run build'
                }
            }
        }

        stage('Build Docker Images') {
            steps {
                sh 'docker-compose build'
            }
        }

        stage('Deploy with Docker Compose') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }

    post {
        success {
            echo '✅ Deployment Successful!'
        }
        failure {
            echo '❌ Deployment Failed. Check logs.'
        }
    }
}






