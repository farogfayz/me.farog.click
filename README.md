# 🌐 Hugo Portfolio with AWS Deployment 🚀

Welcome to my personal portfolio website! This project showcases how I developed and deployed my **Hugo static site** using **AWS services** and **GitHub Actions**. 🎉

---

## 🛠️ Tech Stack

- **[Hugo](http://gohugo.io/)**: Static site generator.
- **[AWS S3](http://aws.amazon.com/s3/)**: For hosting the static site.
- **[AWS CloudFront](http://aws.amazon.com/cloudfront/)**: Content delivery network for improved speed and security.
- **[AWS Certificate Manager (ACM)](http://aws.amazon.com/certificate-manager/)**: To provide SSL/TLS for the site.
- **[AWS Route 53](http://aws.amazon.com/route53/)**: To manage my domain.
- **[GitHub Actions](http://github.com/features/actions)**: CI/CD pipeline for automatic deployment.

---

## 🌟 Features

- **Fast and Secure**: Thanks to Hugo, S3, and CloudFront.
- **SSL Certificate**: Encrypted and secure connection using AWS Certificate Manager.
- **Custom Domain**: Domain managed with Route 53.
- **Continuous Deployment**: Automatically updates the site via GitHub Actions.

---

## 📦 Setup and Workflow

### 1️⃣ **Local Development**

1. Install Hugo:
   ```bash
   brew install hugo
   ```
   or check [Hugo installation guide](http://gohugo.io/getting-started/installing/).

2. Create a Hugo site:
   ```bash
   hugo new site my-portfolio
   ```

3. Add a theme and start developing!
   ```bash
   git clone <theme-repo-url> themes/my-theme
   hugo server
   ```

4. Build the site:
   ```bash
   hugo
   ```

---

### 2️⃣ **Deploy to AWS**

#### **Setup S3 Bucket**
- Create an S3 bucket.
- Enable static website hosting in the bucket settings.
- edit the bucket policy so you can confirm public access to the bucket content

#### **Set Up CloudFront**
- Create a CloudFront distribution.
- Link it to the S3 bucket as the origin.
- Add an alternate domain name (CNAME) for your custom domain.

#### **Add SSL with AWS Certificate Manager**
- Request an SSL certificate for your domain via ACM.
- Attach the certificate to your CloudFront distribution.

#### **Configure Route 53**
- Create a hosted zone for your domain.
- Add an **A record** pointing to your CloudFront distribution.

---

### 3️⃣ **Automate with GitHub Actions**

1. Add the following GitHub Action workflow file to `.github/workflows/deploy.yml`:
   ```yaml
   name: Deploy Hugo Site to AWS

   on:
     push:
       branches:
         - main

   jobs:
     deploy:
       runs-on: ubuntu-latest

       steps:
       - name: Checkout Code
         uses: actions/checkout@v3

       - name: Setup Hugo
         uses: peaceiris/actions-hugo@v2
         with:
           hugo-version: 'latest'

       - name: Build Site
         run: hugo

       - name: Sync to S3
         uses: jakejarvis/s3-sync-action@v0.5.1
         with:
           args: --delete
         env:
           AWS_S3_BUCKET: ${{ secrets.AWS_S3_BUCKET }}
           AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
           AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
   ```
2. Add the required AWS credentials to your GitHub repository secrets.
3. the above GitHub Action workflow file will sync all the files in my case i only sync the /Public folder for easy use.

---

## 🌍 Domain Linking

- Manage your custom domain in **Route 53**.
- Point the domain to your **CloudFront distribution** using **A records**.

---

## 🔐 Security

- All site traffic is encrypted using an SSL certificate from AWS Certificate Manager.
- CloudFront ensures a secure and fast content delivery.

---

## 🤝 Contributing

Feel free to fork this repository and make your own modifications. PRs are welcome! 🙌

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).

---

Thank you for visiting!
feel free to contact me for any issues. 
