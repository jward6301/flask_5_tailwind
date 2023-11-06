# flask_5_tailwind
HHA 504 Week 5 Assignment

## Video Creation Or Procurement
* I used a video of me feeding a Chipmunk while on vacation in the Berkshires. The owner of the resturant has a family of Chipmunks that visit the restaurant's backyard. 

## Cloud CDN & Video Hosting:
1. Log into the Azure Portal using this link: https://azure.microsoft.com/en-us/get-started/azure-portal
2. Using the Search bar, look up Storage Accounts. Open it and click Create
3. You can either use an existing resource group or create a new one, as well as a storage account name.
4. Click Create and open the storage account
5. On the left side menu, select or search for overview. Under the Security section, make sure the following sections are enabled: allow blob anonymous, secure transfer required, allow storage account key access. Click save once these are enabled.
6. On the left side menu, select or search for containers. Add a container and create a name and change the anonymous access to container Anonymous read access for containers and blob. Click create.
7. Under this container click uplaod and upload a file of your choice. Once the file is uploaded, open it and save the URL attached to it. You will need it for your code.
8. On the left side menu, select or search for security and networking. In this section go to front door and CDN. CLick Azure CDN for the service type and create the profile and endpoint names. Chnage the query string to ignore query string. Click Create.
9. Once this is created, open it and click on the hostname and then the endpoint hostname. Copy the URL.
10. Combine the hostname and container URLs by copying the URL from the container after .net and adding it to the end of the hostname URL.
 
## Flask App with Tailwind CSS:
* I reused some code from previous assignments and made some changes based off of the Tailwind CSS link provided from Professor Williams. The link is https://tailwindcss.com/docs/installation.
* You should have an app.py file and a templates folder with .html files

## Cloud Deployment:
1. Once you have finsihed your folders and files necessary, you can open the Cloud Shell Terminal.
2. To install Azure CLI, type in the following command `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`
3. Type `az` to double check that it was installed correctly.
4. You now have to connect to your Azure account to run the app. Type in `az login --use-device-code`. A link and a code will show up, copy the code and then click on the link and follow the instructions.
5. Once you have connected to Azure, type in the following command to create the app: `az webapp up --name <> --runtime PYTHON:3.9 --sku B1` In the `<>` type in what you would like your app name to be.
6. If the command runs correctly, in Azure on the top search bar, type in App Services. Your new app should show up.  


## My App link
https://jess-flaskwebapp2.azurewebsites.net/

## Errors/Issues Faced
I encountered two errors when completing this assignment.
* First, when running `az webapp up --name <>--runtime PYTHON:3.9 --sku B1`, I receieved an error regarding the pricing tier not supporting basic. I cleared my terminal and checked my subscription using the following code `az account list --output table`. I am unsure why I receieved the error message, as the subscription was correct. I ran `az webapp up --name <>--runtime PYTHON:3.9 --sku B1` again and it worked correctly. 
* My second issue was when the Azure app was deployed, my html files were not being read correctly and all formatting wasn't showing besides the color of the text. I updated the following line  <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet"> and ran it locally to see if it fixed the issue. I then reran `az webapp up --name <>--runtime PYTHON:3.9 --sku B1` to create a new webapp and it was working correctly.