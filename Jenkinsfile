pipeline {
    environment { 
        AWS_ACCESS_KEY_ID = credentials('AWS_ACCESS_KEY_ID')
        AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
        AWS_DEFAULT_REGION = "us-east-1"
        // TERRAFORM_ACTION = 'DEPLOY'
        TERRAFORM_ACTION = 'DESTROY'
      }
    agent any
    stages {  
        stage("To create a EKS Cluster") {
            when {
            //  branch 'development'
            expression {
                env.TERRAFORM_ACTION == 'DEPLOY'
                 }
            }
            steps {
                script {
                    dir('Task3-Sprint1') {
                        sh "terraform init"
                        sh "terraform fmt"
                        sh "terraform validate"
                        sh "terraform plan"
                        sh "terraform apply --auto-approve"
                    }
                }
            }
        }
        stage("To destroy a EKS Cluster") {
            when {
            //  branch 'development'
            expression {
                env.TERRAFORM_ACTION == 'DESTROY'
                 }
            }
            steps {
                script {
                    dir('Task3-Sprint1') {
                        sh "terraform init"
                        sh "terraform destroy --auto-approve"
                    }
                }
            }
        }    
    }
}
