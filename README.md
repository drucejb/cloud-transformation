# cloud-transformation

## GCP Pre-requisites
* Enable API [storagetransfer.googleapis.com] on project.
* Find  project-PROJECT_ID@storage-transfer-service.iam.gserviceaccount.com  Service Account for transfer agent. 
    * Grant 'Storage Admin'
    * Grant 'Storage Transfer Service Agent'

## Setup Linux VM for transfer service
* Install gcloud sdk
* Authenticate with gcloud as a personal acct (eg. first.last@gmail.com)
* Install Docker
* Create an agent pool
     ```gcloud transfer agent-pools create isn-i-drive-sync```
* Configure GCloud application default as first.last@gmail.com
  ``` gcloud auth application-default login ```
* Create a transfer agent
  ``` gcloud transfer agents install --pool=isn-i-drive-sync --count=1 --mount-directories=/mnt/c/sandbox ```
* Create a transfer  job
  ``` gcloud transfer jobs create posix:///mnt/I/Jobs gs://isn-engineering/Jobs/ --source-agent-pool=isn-i-drive-sync```



