# AWS-S3-Operations-with-Python
This guide provides essential commands for basic file operations on AWS S3 using Python and Boto3

## 1. Install `boto3`

**Command:**
```bash
pip install boto3
```
**Role:**  
Installs the AWS SDK for Python to interact with AWS services.

## 2. Import Required Libraries

**Command:**
```python
import boto3
```
**Role:**  
Imports the necessary libraries for AWS S3 interaction and error handling.

## 3. Create an S3 Bucket

**Command:**
```python
s3 = boto3.client('s3', aws_access_key_id='YOUR_ACCESS_KEY',
                   aws_secret_access_key='YOUR_SECRET_KEY')

s3.create_bucket(Bucket='your_new_bucket_name')
```
**Role:**  
Creates a new S3 bucket with the specified name.

## 4. Delete an S3 Bucket

**Command:**
```python
s3.delete_bucket(Bucket='your_bucket_name')
```
**Role:**  
Deletes the specified S3 bucket. Note: The bucket must be empty before it can be deleted.

## 5. Establish S3 Client/Resource

**Command:**
```python
s3 = boto3.client('s3', aws_access_key_id='YOUR_ACCESS_KEY',
                  aws_secret_access_key='YOUR_SECRET_KEY')
```
**Role:**  
Creates an S3 client for performing operations on S3 buckets.

## 6. Upload a File to S3

**Command:**
```python
s3.upload_file('local_file.txt', 'your_bucket_name', 'uploaded_file.txt')
```
**Role:**  
Uploads a file from the local system to an S3 bucket.

## 7. Download a File from S3

**Command:**
```python
s3.download_file('your_bucket_name', 'uploaded_file.txt', 'downloaded_file.txt')
```
**Role:**  
Downloads a file from an S3 bucket to the local system.

## 8. Read File Content from S3

**Command:**
```python
obj = s3.get_object(Bucket='your_bucket_name', Key='uploaded_file.txt')
data = obj['Body'].read().decode('utf-8')
print(data)
```
**Role:**  
Reads and displays the content of a file stored in S3.

## 9. Write Content to a File in S3

**Command:**
```python
s3.put_object(Bucket='your_bucket_name', Key='new_file.txt', Body='File content here')
```
**Role:**  
Writes content to a new or existing file in S3.

## 10. List Files in an S3 Bucket

**Command:**
```python
response = s3.list_objects_v2(Bucket='your_bucket_name')
for obj in response.get('Contents', []):
    print(obj['Key'])
```
**Role:**  
Lists all the files available in an S3 bucket.

### For more advanced functionalities, refer to the [Boto3 documentation](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html).
