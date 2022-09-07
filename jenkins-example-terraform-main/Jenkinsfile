pipeline{
    agent any
    stages{
        stage('Git checkout'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/itskkmgit/multi-branch-pipe.git/']]])
            }
        }
        stage("Init") {
            steps{
        sh script:'''
          #!/bin/bash
          echo "This is start $(pwd)"
          cd ./jenkins-example-terraform-main
          echo "This is $(pwd)"
          terraform init
        '''
            }
    }   

        stage('Plan'){
        steps{
		sh script:'''
          #!/bin/bash
          echo "This is start $(pwd)"
          cd ./jenkins-example-terraform-main
          echo "This is $(pwd)"
          terraform plan -out=testjenk.tfplan
        '''
            }
        }
        stage('Apply'){
		steps{
		sh script:'''
          #!/bin/bash
          echo "This is start $(pwd)"
          cd ./jenkins-example-terraform-main
          echo "This is $(pwd)"
          terraform apply -auto-approve "testjenk.tfplan" 
        '''
            }
        }
    }
}