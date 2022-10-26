# Working with Azure Blobs

This demo explains how the Azure Blobs SDK can be used to perfrom blob operation on the Azure storage account.

## Step 1

- Update the connection string in appsettings.json - line 9
- Update the container name in BlobRepository.cs - line 18

## Step 2
- Open terminal in VS Code
- Run the web API
```
cd '.\Working with Azure Blobs SDK\BlobStorageAPI'
dotnet run
```
- Browse the application on https://localhost:7226/swagger

## Test the below blob operations
- Upload
- List
- Download
- Delete