pipeline {
    agent none

    stages {
        stage('Test') {
            environment {
                STAGE='prod'
            }
            agent {
                ecs {
                   cloud 'jenkins-slave-ecs'
                   image 'jenkins/jnlp-slave'
                   launchType 'FARGATE'
                   memory 1024
                   cpu 256
                   subnets('subnet-900709ae')
                   securityGroups('sg-02762415393b8d8cb')
                   taskrole 'arn:aws:iam::302228741901:role/ecsTaskExecutionRole'
                   executionRole 'arn:aws:iam::302228741901:role/ecsTaskExecutionRole'
                   assignPublicIp true
                   logDriver 'default'
                }
            }
            steps {
                sh '''
                    echo "Hello"
                   '''

            }
        }
    }
}
