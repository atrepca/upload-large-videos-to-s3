---

# 🚀 S3 Video Uploader – AWS Lambda & Vue.js  
A simple **serverless** app to upload videos directly to **Amazon S3** using **presigned URLs**.  

## 🛠️ Features  
✅ **Presigned URLs** for secure uploads  
✅ **Vue.js frontend** for easy interaction  
✅ **S3 static site** hosted in the same bucket  
✅ **AWS SAM** deployment  

---

## 📂 Project Structure  
```
/s3-video-uploader
├── backend/app.js         # 🚀 Lambda function (Node.js 22.x) for generating presigned URLs
├── frontend/index.html     # 🎨 Frontend (Vue.js) for selecting & uploading videos
├── template.yaml  # ⚙️ AWS SAM template defining the infrastructure
```

---

## ⚙️ AWS SAM Template (template.yaml)  

This **SAM template** defines the required **AWS resources**:  

🔹 **S3 Bucket** (`S3UploadBucket`) – Stores uploaded videos, and the static site  
🔹 **Lambda Function** (`UploadRequestFunction`) – Generates presigned URLs  
🔹 **IAM Role** (`UploadLambdaExecutionRole`) – Grants Lambda permission to write to S3  
🔹 **CORS Configuration** – Allows cross-origin requests  
🔹 **Public S3 Policy** – Enables public access  

---

## 🚀 Deployment  

### 1️⃣ Prerequisites  
🔹 **AWS CLI** installed & configured  
🔹 **AWS SAM** installed (`brew install aws-sam-cli` for macOS, or follow AWS docs)  
🔹 **S3 Bucket** (automatically created by SAM)  

### 2️⃣ Deploy the Stack  
```sh
sam build
sam deploy --profile AWS_PROFILE --guided
```
👉 Replace `AWS_PROFILE` with your AWS profile name, and input params using `--guided`.

### 3️⃣ Set Required Environment Variables  
🔹 **AWS_REGION** (e.g., `eu-central-1`)  
🔹 **UploadBucket** (created automatically by SAM)  
🔹 Update **`API_URL`** in `frontend/index.html` with the Lambda function URL  

---

## 🌍 Running the App  

1️⃣ Open the static S3 site URL in a browser, e.g. `http://s3bucketname-website.aws-region-1.amazonaws.com/`  
2️⃣ Select a video & click **Upload Video**.  
3️⃣ The file is uploaded to S3 & a link is provided.  

---

## 📌 Important Notes  
⚠️ **CORS is enabled** (allowing all origins) – adjust if needed.  
⚠️ **The frontend uses a hardcoded API_URL** – update it with your Lambda function URL.  

---

🎉 **Happy Uploading!** 🚀