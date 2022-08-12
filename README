# Install gcloud tool - https://cloud.google.com/sdk/docs/install#deb 
sudo apt update 
sudo apt install wget -y 
wget https://raw.githubusercontent.com/Jaibw/bigquery/master/install-gcloud.sh 
sh install-gcloud.sh 
which gcloud 

## gcloud auth 
gcloud auth login --no-launch-browser 
gcloud config set project techlanders-aug22
gcloud compute instances list --format='table(name,status,tags.list())'

## Open BigQuery and run below query 
SELECT name, SUM(number) as total_people
    FROM `bigquery-public-data.usa_names.usa_1910_2013`
    WHERE state = 'TX'
    GROUP BY name, state
    ORDER BY total_people DESC
    LIMIT 20

## Service account creation 
gcloud auth list
gcloud services list
# gcloud services enable bigquery.googleapis.com
export PROJECT_ID=techlanders-aug22
gcloud iam service-accounts create USER-bigquery-sa --display-name "USER bigquery service account"
gcloud iam service-accounts keys create ~/key.json --iam-account USER-bigquery-sa@${PROJECT_ID}.iam.gserviceaccount.com
gcloud projects add-iam-policy-binding ${PROJECT_ID} --member "serviceAccount:USER-bigquery-sa@${PROJECT_ID}.iam.gserviceaccount.com"  --role "roles/bigquery.user"
export GOOGLE_APPLICATION_CREDENTIALS=~/key.json
