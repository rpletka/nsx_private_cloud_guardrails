node () {

deleteDir()

      stage ('Checkout Build Code') {
         checkout scm
       }

        withCredentials([usernamePassword(credentialsId: 'nsxCredentials',
        usernameVariable: 'NSXUSERNAME', passwordVariable: 'NSXPASSWORD')]) {
        stage ('Execute Terraform Template') {
        sh '/usr/local/bin/terraform.13.4 init'
        sh '/usr/local/bin/terraform.13.4 providers'
        sh '/usr/local/bin/terraform.13.4 apply -state="/var/lib/jenkins/terraform/cloud_security/cloud_security.tfstate" -auto-approve -var nsxIP="10.1.1.30" -var nsxUser="$NSXUSERNAME" -var nsxPassword="$NSXPASSWORD"' 
        }
    }
}