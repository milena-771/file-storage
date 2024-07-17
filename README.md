# File Storage API 🗃️

## General description

This project is a file storage API developed as part of a school project. 
The API allows both **anonymous and authenticated users** to store files, with different privileges assigned to each. 
It is integrated into a **micro-services architecture** and includes its own database.
The application interacts with an other mail API to send access keys for authenticated users.

## Implemented Services

- create a customer (customer number from 10000, firstname, lastname, email, marketing consent)
- create a subscription (name, subscription code, description, isFree, duration, maximum stored files)
- create a contact role
- generate API Key (generate and store a unique API key for each customer)
- send API key by mail (send the API key by mail to the customer's contact email)
- store an anonymous file (single file per API call, max 100KB, gif/jpg/png)
- store an authenticated file (single file per API call, max 1000KB, any type)

## To be done

- track usage of the "store anonymous files" service. Store information here after each time a consumer hits the related service:
  - unique identifier of the uploaded file
  - file size
  - file type
  - All the headers of the related HTTP request
  - A flag indicating if the file was successfully stored on the disk
  - The main error message of the exception if applicable
- create a folder for an authenticated client with given information:
  - Parent folder identifier: optional, if not specified, folder is created at client's root folder
  - Folder name: required, max 255 chars [az-AZ-09], unique within a parent folder
  - The service must return a unique folder identifier, such as the filename when a file is uploaded.
- get some stats with given data related to the anonymous uploaded files:
  - Total number of uploaded files
  - Total number of uploaded files in success
  - Total number of uploaded files in error
  - Size of the largest uploaded file
  - Most frequently uploaded file type

