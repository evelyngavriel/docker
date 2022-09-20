pipeline{
    agent {
        label 'UKJenkinsExecutor1'
    }
    stages{
        stage('Build docker image')
        {
            script{
                sh 'docker build -t 366evelyng/test-docker:${branch} .'
            }
        }
        stage('Push image')
        {
          withCredentials([usernameColonPassword(credentialsId: '6e20c5c4-caca-40aa-a02a-aab81b2143a3', variable: 'passwd')])
          sh 'docker login -u 366evelyng ip ${passwd}'
          sh 'docker push 366evelyng/test-docker:${branch}'
        }
    }
}
