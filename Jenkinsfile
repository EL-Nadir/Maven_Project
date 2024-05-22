pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Clean the workspace
                deleteDir()
                
                // Checkout the Git repository
                git branch: 'main', url: 'https://github.com/nadir-0000/Maven_Project.git'
            }
        }
        
        stage('Build') {
            steps {
                script {
                    // Run Maven commands (clean, test, package)
                    sh 'mvn clean test package'
                    
                    // Define the path to the JAR file
                    def jarPath = "target/executable-jar-1.0-jar-with-dependencies.jar"

                    // Check if JAR file exists and run it
                    if (fileExists(jarPath)) {
                        sh "java -jar ${jarPath}"
                    } else {
                        error "Error: The JAR file was not found."
                    }
                }
            }
        }
    }
}
