pipeline {
    agent any

    stages {

        stage('Pull Code') {
            steps {
                git branch: 'master',
                url: 'https://github.com/gayusakthi/terraform-project-vpc-ec2-nginx-http-ssh-security-group-outputs-HCL-code'
            }
        }

        stage('Terraform Init Validate Plan Apply') {
            steps {
                sh '''
                    set -e

                    terraform init
                    terraform validate
                    terraform plan
                    terraform apply -auto-approve
                '''
            }
        }

        stage('Show Outputs') {
            steps {
                sh '''
                    terraform output
                '''
            }
        }
    }

    post {
        success {
            echo 'Infrastructure deployment successful'
        }

        failure {
            echo 'Infrastructure deployment failed'
        }
    }
}
