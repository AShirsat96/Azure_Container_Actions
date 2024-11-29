# Azure Blob Container Management

A Python utility for managing Azure Blob Storage containers, providing functionality to create, list, and delete containers within an Azure Storage Account.

## Prerequisites

- Python 3.11.7
- Azure Storage Account
- Azure Storage Account Connection String
- Azure Storage Blob SDK

## Installation

Install the required Azure libraries:

```bash
pip install azure-storage-blob
pip install azure-mgmt-storage
```

## Required Libraries
```python
import os
import uuid
from azure.storage.blob import BlobClient, BlobServiceClient
from azure.core.exceptions import ResourceExistsError
from azure.storage.blob.aio import BlobClient
```

## Configuration

Initialize the blob service client:
```python
connection_string = "your_connection_string"
blob_service_client = BlobServiceClient.from_connection_string(connection_string)
container_name = "your_container_name"
```

## Features

### 1. Create Container
Creates a new container in your Azure Storage Account:

```python
def create_blob_container(blob_service_client: BlobServiceClient, container_name):
    """
    Creates a new blob container.
    
    Args:
        blob_service_client: Azure blob service client
        container_name: Name for the new container
        
    Raises:
        ResourceExistsError: If container already exists
    """
```

Example usage:
```python
create_blob_container(blob_service_client, "my-container")
```

### 2. List Containers
Lists all containers in the storage account with their metadata:

```python
def list_containers(blob_service_client: BlobServiceClient):
    """
    Lists all containers and their metadata.
    
    Args:
        blob_service_client: Azure blob service client
        
    Returns:
        Prints container names and associated metadata
    """
```

Example usage:
```python
list_containers(blob_service_client)
```

### 3. Delete Container
Deletes a specified container:

```python
def delete_container(blob_service_client: BlobServiceClient, container_name):
    """
    Deletes a specified blob container.
    
    Args:
        blob_service_client: Azure blob service client
        container_name: Name of the container to delete
    """
```

Example usage:
```python
delete_container(blob_service_client, "container-to-delete")
```

## Error Handling

The implementation includes handling for:
- Container already exists (ResourceExistsError)
- Invalid container names
- Authorization errors
- Network connectivity issues

## Complete Example

```python
import os
from azure.storage.blob import BlobServiceClient
from azure.core.exceptions import ResourceExistsError

# Initialize client
connection_string = "your_connection_string"
blob_service_client = BlobServiceClient.from_connection_string(connection_string)
container_name = "my-container"

# Create container
create_blob_container(blob_service_client, container_name)

# List all containers
list_containers(blob_service_client)

# Delete container
delete_container(blob_service_client, container_name)
```

## Best Practices

1. Security:
   - Secure storage of connection strings
   - Use appropriate access levels
   - Implement proper authentication

2. Naming Conventions:
   - Use lowercase letters, numbers, and hyphens
   - Container names must be 3-63 characters
   - Start with a letter or number

3. Error Handling:
   - Check for existing containers
   - Handle authorization errors
   - Implement proper logging

## Container Limitations

- Names must be 3-63 characters long
- Can only contain lowercase letters, numbers, and hyphens
- Must start with a letter or number
- Cannot contain consecutive hyphens

## Future Enhancements

Consider adding:
- Container metadata management
- Access level configuration
- Batch operations
- Async operations support
- Retry policies
