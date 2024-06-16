pipeline{
agent any
tools
{
maven 'maven_3.6.1'
}
environment {
        // Define environment variables if needed
        DOCKER_REGISTRY = 'lokeshnagam121'
        dockerImage = 'lokeshnagam121/springboot'
        IMAGE_TAG = 'latest'
        registryCredential ='dockerhub'
}
stages
{
stage('Checkout Code from GitHub')
  {
        steps{git credentialsId: 'git', url: 'https://github.com/Loki-1/SpringBootApp.git'}
  }
stage('Build WAR File with Maven')
  {
  steps
  {
  sh  "mvn clean package"
  }
  }
stage('Executing SonarQube Report')
  {
  steps
  {
  sh  "mvn sonar:sonar"
  }
  }
  stage('Uploading Artifacts Into Nexus Repo')
  {
  steps
   {
  sh  "mvn deploy"
   }
  }
stage('Build Docker Image') {
            steps {
                // Build your Docker image
                script {
                     // Build your Docker image
                    sh 'docker build -t lokeshnagam121/springboot .'
                }
            }
        }
stage('Push Docker Image to Docker Hub') {
            steps {
                script {
                    // Push the Docker image to the registry
                    docker.withRegistry('', registryCredential) {
                        docker.image("${dockerImage}:${IMAGE_TAG}").push()
                    }
                }
            }
        }
stage('Deploy Application on kubernetes cluster') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: '', contextName: '', credentialsId: 'k8-token', namespace: 'test-ns', restrictKubeConfigAccess: false, serverUrl: 'https://172.31.23.196:6443') {
                sh "kubectl apply -f springboot-with-mongo.yaml -n test-ns"
                sh "kubectl get svc -n test-ns"
                }
            }
        }
}
post {
            always {
                emailext (
                    subject: "Pipeline Status: ${BUILD_NUMBER}",
                    body: '''<html>
                                <body>
                                    <p>Build Status: ${BUILD_STATUS}</p>
                                    <p>Build Number: ${BUILD_NUMBER}</p>
                                    <p>Check the <a href="${BUILD_URL}">console output</a>.</p>
                                </body>
                            </html>''',
                    to: 'lokesh.naagam@gmail.com,naagam.lokesh@gmail.com',
                    from: 'jenkins@example.com',
                    replyTo: 'jenkins@example.com',
                    mimeType: 'text/html'
                )
            }
        }
}
