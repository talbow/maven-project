pipeline {
   agent any
   stages{
       stage ('Build / Package'){
           steps {
               build job: '02-java-demo-package'
           }
           post {
               success {
                   echo 'Project clean and build successful...'
               }
           }
       }
       stage ('Static Analysis'){
           steps {
               build job: '02-java-demo-static-analysis'
           }
       }      
       stage ('Deploy to QA'){
           steps {
               build job: '02-java-demo-deploy-to-qa'
           }
       }
       stage ('Deploy to Prod'){
           steps{
               timeout(time:5, unit:'DAYS'){
                   input message:'Approve PRODUCTION Deployment?'
               }
               build job: '02-java-demo-deploy-to-prod'
           }
           post {
               success {
                   echo 'Java demo successfully deployed to Production.'
               }
               failure {
                   echo '!!! Deployment failed !!! - See Console Output for details'
               }
           }
       }
   }
}
