# Amazon Simple Storage Service (S3) 
*  is an object storage service that offers industry-leading scalability, data availability, security, and performance.
* used to store and protect any amount of data for a range of use cases

## Features of Amazon S3
* Storage classes: offers a range of storage classes designed for different use cases
* Storage management: can use to manage costs, meet regulatory requirements, reduce latency, and save multiple distinct copies of your data for compliance requirements. has storage management features : 
    * S3 Lifecycle 
    * S3 Object Lock 
    * S3 Replication
    * S3 Batch Operations
* Access management: auditing and managing access to your buckets and objects, can use the following features:
    * S3 Block Public Access
    * AWS Identity and Access Management (IAM)
    * Bucket policies 
    * Amazon S3 access points
    * Access control lists (ACLs)
    * S3 Object Ownership
    * Access Analyzer for S3 
* Data processing: To transform data and trigger workflows to automate a variety of other processing activities at scale, features: 
    * S3 Object Lambda
    * Event notifications 
* Storage logging and monitoring: can use to monitor and control how your Amazon S3 resources are being used
    * Automated monitoring tools
        * Amazon CloudWatch metrics for Amazon S3
        * AWS CloudTrail 
    * Manual monitoring tools
        * Server access logging
        * AWS Trusted Advisor 
* Analytics and insights: help you gain visibility into your storage usage, which empowers you to better understand, analyze, and optimize your storage at scale.
    * Amazon S3 Storage Lens
    * Storage Class Analysis
    * S3 Inventory with Inventory reports
* Strong consistency: read-after-write consistency for PUT and DELETE requests of objects in your Amazon S3 bucket in all AWS Regions.

## How Amazon S3 works
* an object storage service that stores data as objects within buckets.
* To store your data in Amazon S3:
    * create a bucket and specify a bucket name and AWS Region
    * upload your data to that bucket as objects in Amazon S3

## Amazon S3 data consistency model
* This section provides examples of behavior to be expected from Amazon S3 when multiple clients are writing to the same items.
    * This section provides examples of behavior to be expected from Amazon S3 when multiple clients are writing to the same items.
        * both W1 (write 1) and W2 (write 2) finish before the start of R1 (read 1) and R2 (read 2).

        ![Ex1](/images/ex1.jpg)
        
        * W2 does not finish before the start of R1

        ![Ex1](/images/ex2.jpg)

        * W2 begins before W1 has received an acknowledgement

        ![Ex1](/images/ex3.jpg)

## Related services
* you can use data into Amazon S3 after load it with other AWS services:
    * Amazon Elastic Compute Cloud (Amazon EC2),Amazon EMR, AWS Snow Family, AWS Transfer Family

## Accessing Amazon S3
* You can work with Amazon S3 in any of the following ways:
    * AWS Management Console: console is a web-based user interface for managing Amazon S3 and AWS resources
    * AWS Command Line Interface:used to issue commands or build scripts at your system's command line to perform AWS (including S3) tasks.
    * AWS SDKs: AWS provides SDKs (software development kits) that consist of libraries and sample code for various programming languages and platforms
    * Amazon S3 REST API:  Amazon S3 is designed to be programming language-neutral, using AWS-supported interfaces to store and retrieve objects.

## Paying for Amazon S3
* you don't have to plan for the storage requirements of your application.
* charges you only for what you actually use, with no hidden fees and no overage charges
* When you sign up for AWS, your AWS account is automatically signed up for all services in AWS, including Amazon S3

# Getting started
* execute the commands:
>amplify add storage

>amplify push

* Add these libraries into the dependencies in `build.gradle`
>dependencies {
>
>    implementation 'com.amplifyframework:aws-storage-s3:1.35.4'
>
>    implementation 'com.amplifyframework:aws-auth-cognito:1.35.4'
>
>}

* Initialize Amplify Storage 
>Amplify.addPlugin(new AWSCognitoAuthPlugin());
>
>Amplify.addPlugin(new AWSS3StoragePlugin());

## Uploading data to your bucket

![Ex1](/images/upload.jpg)



