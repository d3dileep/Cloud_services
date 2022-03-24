# Cloud_services

This repo is for python integration with cloud services, these notebook tested on GCP jupyter notebook. 
You need credential to access GCP services outside GCP environment, use the following code shown to upload local computer file to GCP bucket
````
from gcloud import storage
from oauth2client.service_account import ServiceAccountCredentials
import os


credentials_dict = {
    'type': 'service_account',
    'client_id': os.environ['BACKUP_CLIENT_ID'],
    'client_email': os.environ['BACKUP_CLIENT_EMAIL'],
    'private_key_id': os.environ['BACKUP_PRIVATE_KEY_ID'],
    'private_key': os.environ['BACKUP_PRIVATE_KEY'],
}
credentials = ServiceAccountCredentials.from_json_keyfile_dict(
    credentials_dict
)
client = storage.Client(credentials=credentials, project='myproject')
bucket = client.get_bucket('mybucket')
blob = bucket.blob('myfile')
blob.upload_from_filename('myfile')

````
1. Google's GCP firestore database from platform AI notebook https://github.com/d3dileep/Cloud_services/blob/main/gcp/firestore_insert_data.ipynb
2. Google's vision API for PDF OCR with Parallelization for parallel processing multiple documents. It also uses google cloud storage. text cleaning performed on pandas dataframe using map and lambda functions. https://github.com/d3dileep/Cloud_services/blob/main/gcp/gcp_vision_api_text_cleaning.ipynb
3. Unzip a zip file located in the same GCP storage bucket using python.  https://github.com/d3dileep/Cloud_services/blob/main/gcp_unzip_in_storage.ipynb
