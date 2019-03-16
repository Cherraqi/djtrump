#!groovy

node {


        stage 'Checkout'
            checkout scm

            sh 'git log HEAD^..HEAD --pretty="%h %an - %s" > GIT_CHANGES'
            def lastChanges = readFile('GIT_CHANGES')
           

        stage 'Test'
            sh 'pip install -r requirements.txt'
            sh 'python3 manage.py test --testrunner=djtrump.tests.test_runners.NoDbTestRunner'

        stage 'Deploy'
            sh './deployment/deploy_prod.sh'



    

}

