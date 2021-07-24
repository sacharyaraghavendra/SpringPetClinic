// Whatever we are doing we have to put under
// pipeline block
pipeline{
    // specify the agen we will be running a job
    agent{
        // currently we only have master agent
        label 'master'
    }
    // specify the tool we are going to use
    tools{
        maven 'M3'
    }
    //provide stages of your pipeline
    stages{
        stage('Checkout'){
            steps{
                git branch: 'main',
                url: 'https://github.com/sacharyaraghavendra/SpringPetClinic'
            }
        }
        stage('Build'){
            steps{
                sh 'mvn compile'
            }
        }
        stage('Test'){
            steps{
                sh 'mvn test'
            }
        }
        // After testing we have to package
        stage('Package'){
            steps{
                sh 'mvn package'
            }
        }
        // After package we have to deploy to production
        // Currently we are deploying in same server
        // So deploy stage
        stage('Deploy'){
            steps{
                sh 'java -jar /var/lib/jenkins/workspace/PetClinicDeclarativePipeline/target/*.jar'
            }
        }
        
    }
}
