pipeline {
  agent { 
  label 'nodes'
  }
  
  environment {
   AWS_EC2_PRIVATE_KEY=credentials('ec2-private-key') //
  }
  
  stages {
    
    //Get the Code from GitHub Repo
    stage('CheckOutCode'){
      steps{
        git branch: 'master', url: 'https://github.com/one-devops-training/jenkins-with-ansible-static-inv.git'
      }
    }
     
    //Run the playbook
    stage('RunPlaybook') {
      steps {
        sh "ansible-playbook -i inventory/walmart.hosts --private-key=$AWS_EC2_PRIVATE_KEY playbooks/installTomcat.yml --ssh-common-args='-o StrictHostKeyChecking=no'"
      }
    }
  
  }//stages closing
}//pipeline closing
