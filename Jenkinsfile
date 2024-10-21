pipeline{
  agent any
  stages{
     stage(' Create VPC') {
       steps{
          sh 'gcloud compute networks create test-custom-jenkins-vpc --project=hari-cloud-first-project  --subnet-mode=custom'
    }
  }
  stage(' Create subnets') {
       steps{
           sh 'sleep 40'
          sh 'gcloud compute networks subnets create test-cmd-subnets --project=hari-cloud-first-project --range=10.0.0.0/24 --network=test-custom-jenkins-vpc  --region=us-central1'
    }
  }
  stage(' Create instance with VPC') {
       steps{
           sh 'gcloud compute instances create instance-jenkins-vpc-subnet --project=hari-cloud-first-project --zone=us-central1-f --machine-type=e2-medium --network-interface=network-tier=PREMIUM,stack-type=IPV4_ONLY,subnet=test-cmd-subnets --service-account=jenkis-github@hari-cloud-first-project.iam.gserviceaccount.com'
    }
  }
 }
}
