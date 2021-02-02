# Cloud-Test

# gsutil commands (Cloud Storage)
pwd
ls

# see config
gcloud config list

# list contents in given path
gsutil ls
gsutil ls gs://storage-lab-console/
gsutil ls gs://storage-lab-console/**

# Help for any command
gsutil mb --help

# example
gsutil mb -l northamerica-northeast1 gs://storage-lab-cli
gsutil ls

# Find and get label
gsutil label get gs://storage-lab-console/
gsutil label get gs://storage-lab-console/ >bucketlabels.json
cat bucketlabels.json

# Set label
gsutil label get gs://storage-lab-cli/
gsutil label set bucketlabels.json gs://storage-lab-cli/
gsutil label get gs://storage-lab-cli/

# Change label
gsutil label ch -l "extralabel:extravalue" gs://storage-lab-cli

# Version of bucket
gsutil versioning get gs://storage-lab-cli/
gsutil versioning set on gs://storage-lab-cli/
gsutil versioning get gs://storage-lab-cli/

# Copy Files in and out of cloud
gsutil ls gs://storage-lab-cli/
gsutil cp README-cloudshell.txt gs://storage-lab-cli/
gsutil ls gs://storage-lab-cli/

gsutil ls gs://storage-lab-cli/
gsutil ls -a gs://storage-lab-cli/
gsutil rm gs://storage-lab-cli/README-cloudshell.txt
gsutil ls gs://storage-lab-cli/
gsutil ls -a gs://storage-lab-cli/

gsutil cp gs://storage-lab-console/** gs://storage-lab-cli/
gsutil ls gs://storage-lab-cli/
gsutil ls -a gs://storage-lab-cli/

gsutil acl ch -u AllUsers:R gs://storage-lab-cli/Selfie.jpg

#Big Query Commands

gsutil mb gs://kani-gcp-bucket-1

# Big Query

# Show table
    bq show PROJECT_ID:DATASET_ID.TABLE_ID

# Query table
    bq query \
    "SQL_Statement"

# Show Existing datasets in selected project
    bq ls
# Show list of datasets in specific project
    bq ls project_id:

# Create new data set
    bq mk dataset_name

# Load table
    bq load datasetID.tableID source_path schema
    Eg: "bq load babynames.names2010 yob2010.txt name:string,gender:string,count:integer"
        "bq load --source_format=NEWLINE_DELIMITED_JSON --autodetect=True new_dataset2.test_table3 gs://kani-gcp-bucket-1/cake.json"
# Clean up
    bq rm -r datasetID


# Example:
bq ls
bq ls admin-project-301608:
bq mk employee_test
bq load employee_test.test_data gs://kani-gcp-bucket-1/employee.csv Name:string,Department:string,Manager:string,Sala
ry:integer
bq load --source_format=CSV --autodetect=True employee_test.test_data gs://kani-gcp-bucket-1/employee.csv
bq query "SELECT * FROM employee_test.test_data"

bq load --source_format=NEWLINE_DELIMITED_JSON --autodetect=True employee_test.json_table gs://kani-gcp-bucket-1/cake.json


# Demo

# List all buckets
gsutil ls

# Help with making a bucket
gsutil mb --help

# Making new bucket
gsutil mb gs://kani-gcp-bucket-3

# Cloning files to shell storage
git clone https://github.com/kanishk-21/Cloud-Test

# Copy files to bucket
gsutil cp -r Cloud-Test gs://kani-gcp-bucket-3

# List all files in bucket
gsutil ls gs://kani-gcp-bucket-3

# Make a new dataset in BigQuery
bq mkd demo_dataset

# Making and loading table in dataset
bq load demo_dataset.demo_table1 --autoformat=True --source_format=CSV  gs://kani-gcp-bucket-2/Cloud-Test/100 Records.csv
bq load demo_dataset.demo_table2 --autoformat=True --source_format=CSV  gs://kani-gcp-bucket-2/Cloud-Test/1000 Records.csv

# Query table
bq query 'SELECT * FROM demo_project:demo_dataset.demo_table1'



