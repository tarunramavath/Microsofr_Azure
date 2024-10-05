# Microsoft Azure Blob Storage with Python

This project demonstrates how to work with **Microsoft Azure Blob Storage** using **Python**. It covers the basic operations such as creating a container, uploading blobs, accessing blobs, and deleting both blobs and containers. The aim is to provide a practical guide for working with Azure Blob Storage through Python SDK.

## Prerequisites

Before running the code, ensure you have the following prerequisites:

1. **Python 3.x** installed on your system.
2. **Azure Storage Blob Python SDK** installed:
   ```bash
   pip install azure-storage-blob
   ```
3. **Azure Storage Account**: You need an active Azure account and a storage account created.
4. **Azure Storage Connection String**: You can get this from the Azure portal for your Storage Account.

## Azure Blob Storage Operations Covered

### 1. **Creating a Container**

A container is a logical grouping of blobs. In this section, you can create a new container in Azure Blob Storage.

```python
from azure.storage.blob import BlobServiceClient

# Azure Storage Connection String
connection_string = "your_connection_string_here"

# Create a BlobServiceClient
blob_service_client = BlobServiceClient.from_connection_string(connection_string)

# Create a container
container_name = "my-container"
container_client = blob_service_client.create_container(container_name)
print(f"Container '{container_name}' created successfully!")
```

### 2. **Accessing a Container**

To interact with a container, you can access and list all containers in your Azure Blob Storage.

```python
# List all containers
containers = blob_service_client.list_containers()
for container in containers:
    print(container['name'])
```

### 3. **Uploading a Blob**

A blob is an object (such as a file) stored in Azure Blob Storage. This section shows how to upload a file as a blob.

```python
from azure.storage.blob import BlobClient

# Upload a blob to the container
file_path = "path/to/your/file.txt"
blob_name = "my-blob.txt"
blob_client = container_client.get_blob_client(blob_name)

with open(file_path, "rb") as data:
    blob_client.upload_blob(data)
    print(f"Blob '{blob_name}' uploaded successfully!")
```

### 4. **Accessing a Blob**

You can access the blob and read its contents programmatically.

```python
# Download the blob
downloaded_blob = blob_client.download_blob()
content = downloaded_blob.readall()
print(f"Blob content: {content.decode('utf-8')}")
```

### 5. **Deleting a Blob**

Once you're done with a blob, you can delete it to free up storage space.

```python
# Delete the blob
blob_client.delete_blob()
print(f"Blob '{blob_name}' deleted successfully!")
```

### 6. **Deleting a Container**

After all operations are complete, you may want to delete the container along with its blobs.

```python
# Delete the container
container_client.delete_container()
print(f"Container '{container_name}' deleted successfully!")
```

## Running the Project

1. Make sure you've set your **Azure Storage Account connection string** in the code.
2. Follow the steps in the code snippets above to create a container, upload a blob, access it, and delete the blob/container.
3. Run the Python script and monitor the operations in your Azure portal for confirmation.

## Conclusion

This project provides an introduction to working with **Azure Blob Storage** using **Python**. By completing these operations, you’ll gain a strong understanding of how to interact with Azure Blob Storage in your own Python applications.


## Acknowledgments

- Thanks to the **Microsoft Azure team** for providing excellent cloud storage solutions.

