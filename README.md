# Asset Management Portal

Enterprise asset management solution built using:

- PHP
- Zendesk API
- Azure App Service
- MySQL

## Features

- Asset tracking
- Device assignment
- Employee lookup
- Reporting
- Lifecycle management

## The product
<img width="1653" height="903" alt="image" src="https://github.com/user-attachments/assets/9feeef0a-d283-4d29-ab71-fdd3d50502b9" />

<img width="1596" height="820" alt="image" src="https://github.com/user-attachments/assets/ff456844-40ec-41fd-8764-0cc904e92908" />

<img width="1446" height="852" alt="image" src="https://github.com/user-attachments/assets/fea80753-82b9-4d31-9378-5b3b5e9c2689" />

<img width="1315" height="521" alt="image" src="https://github.com/user-attachments/assets/daea5203-0e18-45ff-a644-d20b3cc9f7cd" />

<img width="1634" height="280" alt="image" src="https://github.com/user-attachments/assets/545bfe5f-1822-46f0-9dc1-45e868f9aeaf" />

<img width="1264" height="892" alt="image" src="https://github.com/user-attachments/assets/80c37763-31c7-4059-a8a4-acfdee824a77" />

<img width="1302" height="613" alt="image" src="https://github.com/user-attachments/assets/3614c982-0442-465b-ae99-45dd78c0ceb1" />

<img width="1402" height="809" alt="image" src="https://github.com/user-attachments/assets/f11a2f62-c0f9-479f-b633-482f508c84be" />

<img width="1254" height="945" alt="image" src="https://github.com/user-attachments/assets/d0ec2335-769f-4e8e-800f-b5061f2dfe0b" />



## Application and System Requirements

## Create asset field and tables in Zendesk to store and capture assets:
 - Add the required field needed to capture your assets. This will be stored in the Zendesk database
<img width="1618" height="857" alt="image" src="https://github.com/user-attachments/assets/71a368c2-00e4-4219-9de9-6ba90b5a1ae5" />

- Create an API token to authenticate to Zendesk to access its REST api's 
  <img width="1525" height="338" alt="image" src="https://github.com/user-attachments/assets/67ea3046-6b3f-4a60-9d06-30fb50ae7660" />


## PHP Scripts:
- Frontend: Index and htaccess File

<img width="741" height="533" alt="image" src="https://github.com/user-attachments/assets/46ad630e-b345-4fe9-9265-38c07a9aa5bc" />

- Backend: Authentication (EntraAuth for MS Entra Authentication and Group access), Controllers for Routing(Asset, Auth, and Dashboard Controllers), Helpers (Authz (used to execute authentication task), Cache (used to cache reports in memory web ui to improve performance), session )used to manage the authenication tasks per user), view (execute the web u.i and reports within the asset dashboard), env (used to execute the environment variables for service) 

<img width="942" height="558" alt="image" src="https://github.com/user-attachments/assets/1398622a-dfe7-4504-b861-f233b7f82119" />
<img width="964" height="619" alt="image" src="https://github.com/user-attachments/assets/ad7054d5-3359-448c-b5c1-011ebc421a42" />
<img width="772" height="655" alt="image" src="https://github.com/user-attachments/assets/64c225ef-3bdf-414e-a094-17da7863a787" />
<img width="894" height="366" alt="image" src="https://github.com/user-attachments/assets/3698add2-aee8-419e-8d6a-265fac4fbd25" />

- Services: XLsWriter (used to export reports into csv file), ZendeskClient (processes Zendesk api data against its database to the web app)
<img width="831" height="435" alt="image" src="https://github.com/user-attachments/assets/16299d9e-7ece-4978-bd5b-f77f73e73a3e" />
<img width="849" height="577" alt="image" src="https://github.com/user-attachments/assets/93d4d228-e6ea-44b7-b0d0-392759e6d032" />

- Views: Dashboard (frontend portal), error (error banner), login (Entra login page with MFA), layout (render the web portal layouts via css)
<img width="818" height="414" alt="image" src="https://github.com/user-attachments/assets/efbe981d-78e9-41eb-b111-7b13216b7bee" />
<img width="703" height="322" alt="image" src="https://github.com/user-attachments/assets/21525ee2-52be-458d-a188-144c419fe7f1" />
<img width="875" height="480" alt="image" src="https://github.com/user-attachments/assets/4e38fb25-5af4-4310-b7e1-36a4d4f931a4" />

## Entra and App Registration configuration for authentication
- Create the groups that will have access to view or edit app
<img width="612" height="274" alt="image" src="https://github.com/user-attachments/assets/50197cfb-d55b-4c8c-906a-8a4ba3978cbc" />
<img width="609" height="266" alt="image" src="https://github.com/user-attachments/assets/9d1aa56f-4022-451c-b43c-d9b6329a496d" />

- Create the app registration for the new app to allow users to authenticate
<img width="637" height="421" alt="image" src="https://github.com/user-attachments/assets/9bdedee2-bcef-4f55-8098-3a3fcca991d3" />

- Enable graph api to read azure group that has access to the new asset management portal to either view or edit assets:
  <img width="425" height="314" alt="image" src="https://github.com/user-attachments/assets/49ff1cba-01ea-4c64-8924-6fb68c291459" />

- Expose the api for the app to connect to the new app registration
<img width="244" height="327" alt="image" src="https://github.com/user-attachments/assets/30ac85f9-8663-415d-ab67-5002b7b6f2b0" />

- Setup the redirect to send users when logging into the app using MS Entra
- <img width="725" height="368" alt="image" src="https://github.com/user-attachments/assets/23e20246-3566-482f-9a9d-3f3d7a189a90" />

- Don't forget to capture the secret and key value to securely connect the new asset management app to your MS tenant
  <img width="1104" height="387" alt="image" src="https://github.com/user-attachments/assets/f118e971-9e1b-49b8-ac0a-b3a4dfe012cf" />

## Configuring the Azure Web to host the new app
- Create a new resource group to host services needed to run the new PHP app
<img width="1107" height="539" alt="image" src="https://github.com/user-attachments/assets/870595f9-6fcf-4d46-b101-af0d5b1479c4" />

- Create a new Azure Linux web app (this should already come with PHP services installed)
<img width="1266" height="874" alt="image" src="https://github.com/user-attachments/assets/1f5a2914-3ee3-4910-a5da-f8255254424f" />

- Add the environment variables needed to authenticate to the Zendesk asset database with zendesk api token
<img width="767" height="596" alt="image" src="https://github.com/user-attachments/assets/9ee02d50-f63c-4bb7-9e0c-11ff15eb4d58" />

- Configure networking for inbound access
<img width="1516" height="605" alt="image" src="https://github.com/user-attachments/assets/a203445a-c71e-465d-b12c-6cb4f400cc2b" />

- Enable SSH access local access with a new key pair
<img width="1077" height="364" alt="image" src="https://github.com/user-attachments/assets/3e92a532-9c2a-4570-8a4a-d08dfe8ec194" />
<img width="405" height="327" alt="image" src="https://github.com/user-attachments/assets/b36df063-f97a-4dbf-8512-31287a6d85b9" />

- Now deploy code to the httpd directory where Apache is pointing to
<img width="1165" height="338" alt="image" src="https://github.com/user-attachments/assets/97e7fa66-edf8-4fee-9ae1-af3ffe9322da" />




















