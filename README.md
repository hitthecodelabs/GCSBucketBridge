# Google Cloud Storage Bucket Migration

This project provides a script that helps to migrate data between Google Cloud Storage (GCS) buckets.

## Prerequisites

- Google Cloud SDK
- Python 3.x
- Google Cloud Storage Client for Python

## Setup and Installation

1. **Google Cloud SDK Installation:**
   
   Follow the instructions on the [official page](https://cloud.google.com/sdk/docs/install) to install and initialize the Google Cloud SDK.

2. **Python Installation:**
   
   Ensure that Python 3.x is installed on your system. If not, download it from the [official website](https://www.python.org/downloads/).

3. **Google Cloud Storage Client Installation:**
   
   Install Google Cloud Storage Client for Python using pip:

   ```shell
   pip install --upgrade google-cloud-storage
   ```

4. **Authentication:**

   Ensure that you have the JSON key file for the Google Cloud Service Account and set it in your environment variables:

   ```shell
   export GOOGLE_APPLICATION_CREDENTIALS="path_to_your_service_account_file.json"
   ```

## Usage

### Step 1: Authentication and Project Configuration

- Execute the following shell command to authenticate your gcloud CLI with Google Cloud:

  ```shell
  gcloud auth login
  ```

- Set your desired Google Cloud Project ID as the current project:

  ```shell
  gcloud config set project your_project_id
  ```

### Step 2: Service Account and Permissions

- Ensure that a Service Account with the necessary permissions to access and modify GCS buckets is available.

- Set permissions and create keys for the Service Account:

  ```shell
  gcloud iam service-accounts create your_service_account_name --description="your_description" --display-name="your_display_name"
  gcloud projects add-iam-policy-binding your_project_id --member=serviceAccount:your_service_account_name@your_project_id.iam.gserviceaccount.com --role=roles/storage.objectViewer
  gcloud iam service-accounts keys create ./your_key_name.json --iam-account your_service_account_name@your_project_id.iam.gserviceaccount.com
  ```

### Step 3: Run the Python Script

- Execute the Python script to perform the bucket data migration:

  ```shell
  python bucket_migration.py
  ```

### Step 4: Data Migration

- The script will perform the following operations:
    - List all the files in the source bucket.
    - Download the files from the source bucket to a temporary location.
    - Upload the files from the temporary location to the destination bucket.
   
## Note

Ensure to review and modify the `bucket_migration.py` script to set appropriate source and destination bucket names and other configurations as per your use-case.
