pipeline {
    agent any 
    
    tools {
        maven 'maven 3'
    }
    parameters {
        string defaultValue: 'Raviteja', name: 'employeeIDName'
    }
    stages{
        stage('CheckOut'){
            steps{
                checkout poll: false, scm: scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/RAVITEJADARLA/jenkins_pipeline_springboot_demo.git']])
            }
        }
        stage('Build'){
            steps{  
                echo "Build Stage"
                sh 'mvn compile'
            }
        }
        stage('Unit Test'){
            steps{
                echo "Testing Stage"
                sh 'mvn test'
            }
        }
        stage('Installation'){
            steps{
                echo "Installation Stage"
                sh 'mvn install'
            }
        }
        stage ('Jar File'){
            steps{
                echo "Jar File Generate"
                archiveArtifacts artifacts: 'target/calculator-0.0.1-SNAPSHOT.jar', followSymlinks: false
            }
        }
        stage('Employee Name'){
            steps{
                echo "${params.employeeIDName}"
            }
        }
    }
}
