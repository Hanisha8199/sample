pipeline{
    agent any
    stages{
        stage('Checkout'){
            steps{
                echo "Cloning the repo"
                git branch: 'main', url: 'https://github.com/HanishaS28/week-5.git'
            }
        }
        stage('Compile'){
            steps{
                echo "Compiling the latest code"
                bat 'javac Factorial.java TestFact.java'
            }
        }
        stage('Test'){
            steps{
                echo "Test execution"
                bat 'java TestFact'
            }
        }
        stage('Run'){
            steps{
                echo "executing the main application"
                bat 'java Factorial'
            }
        }
        stage('Build JAR files'){
            steps{
                echo "Build"
                bat 'jar cfm factorial.jar manifest.txt Factorial.class'
            }
        }
        stage('Archive JAR files'){
            steps{
                echo "Archive jar files"
                archiveArtifacts artifacts: 'factorial.jar'
            }
        }
    }
    post{
        success{
            echo 'Pipeline executed successfully!'
        }
        failure{
            echo 'Pipeline failed, check the logs.'
        }
    }
}
