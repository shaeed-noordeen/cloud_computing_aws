# cloud_computing_aws

## What is cloud computing?
> Cloud computing means that instead of all the computer hardware and software you're using sitting on your desktop, or somewhere inside your company's network, it's provided for you as a service by another company and accessed over the Internet, usually in a completely seamless way. Exactly where the hardware and software is located and how it all works doesn't matter to you, the user—it's just somewhere up in the nebulous "cloud" that the Internet represents.

## Key benefits
> - On demand resource allocation - Allows the upgrading your hardware virtually rather than having hardware brought in to the premises and you only have to pay for what you use.
> - Scalabilty - Allows an orgnaisation to scale up or down depending on the customer traffic.
>  - Pay as you go - You only pay for what you use , rather paying thousands of pounds and not using all equipment thoroughly. 

## Types of cloud computing
> - Let’s take a look at what kind of cloud services are being provided by different providers:
- Infrastructure as a Service (IaaS): It is the building block of cloud IT. Allows you to choose the kind of networking, servers, databases, and storage space you want. It’s the most flexible option for building a cloud-based service and can be easily parallel with an on-premise IT. The underlying infrastructure would still have to be managed by you(virtually though).
- Platform as a Service (PaaS): Allows users to build, manage and deploy the applications without having to manage the underlying infrastructure such as networking, servers, databases, etc. e.g. AWS Elastic Beanstalk, Windows Azure, Heroku.
- Software as a Service (SaaS): It’s a complete service provided and managed completely by the service provided. Users just have to create accounts, configure and use the service. examples include Google Apps (Gmail), Dropbox, Zoom.

## AWS
> - When we talk about cloud computing, Amazon Web Services(AWS) is the first name that comes to mind. AWS is the pioneer of cloud computing in the cloud industry. Having launched in 2004 with just one service(SQS) they have come a long way. AWS, without a doubt, is the most mature cloud service provider and the current market leader in the cloud industry.
With more than 212 services including computing, storage, networking, database, analytics, application services, deployment, management, mobile, developer tools, and tools for the Internet of Things. AWS operates globally with 216 Points of Presence (205 Edge Locations & 11 Regional Caches) in 84 cities across 42 countries.

## Steps to 2 tier Architecture
> - Create App instance
>  - EC2 configurations - Linux Ubuntu 180.04LTS, t2-micro, default storage, tags eng99_shahid_app, SG public ip available to public and ssh my ip, add correct ssh (eng99.pem).
>  - ssh into app instance and add app file by either scp or git clone.
>  - run provision file to add all dependencies - update, upgrade, nginx, nodejs, pm2
>  - run app check if its working on browser
>  - Create db instance
>  - EC2 configurations - Linux Ubuntu 180.04LTS, t2-micro, default storage, tags eng99_shahid_db, SG private ip for app so it can connect and ssh my ip, add correct ssh (eng99.pem).
>  - ssh into db ec2 instance
>   - download all dependencies through provision file or manually - update, upgrade, nginx, nodejs, pm2, mongod.
>   - check mongod status then cd to etc and find mongod.conf file.
>   - change mongod.conf file ip to 0.0.0.0 and then cat mongod.conf to check if change has taken place.
>   - restart, enable and check status for mongodb.
>   - go back to app instance.
>   - create env var DB_HOST="mongodb://db-ip:27017/posts"
>   - source it with source ~/.bashrc
>   - cd app.
>   - node seeds/seed.js
>   - npm start app.
![download](https://user-images.githubusercontent.com/94617056/144422175-2cb78a21-0ac0-469b-a15d-5480db271a45.jpg)
