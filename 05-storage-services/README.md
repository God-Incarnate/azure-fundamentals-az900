# 💾 Storage Services

Comprehensive guide to Azure storage services for different data types and access patterns.

## 📚 Services Covered

1. [Azure Blob Storage](#azure-blob-storage)
2. [Azure Disk Storage](#azure-disk-storage)
3. [Azure File Storage](#azure-file-storage)
4. [Azure Queue Storage](#azure-queue-storage)
5. [Azure Table Storage](#azure-table-storage)
6. [Azure Archive Storage](#azure-archive-storage)
7. [Storage Account Basics](#storage-account-basics)
8. [Comparison & Selection](#comparison--selection)

---

## Azure Blob Storage

### What is Blob Storage?

Object storage for unstructured data (any file type, any size).

### Key Features

```mermaid
graph TB
    A["Azure Blob Storage"] --> B["Container"]
    B --> B1["Blob 1: Image.jpg"]
    B --> B2["Blob 2: Video.mp4"]
    B --> B3["Blob 3: Document.pdf"]
    
    A --> C["Access Tiers"]
    C --> C1["Hot: Frequent"]
    C --> C2["Cool: Infrequent"]
    C --> C3["Archive: Rare"]
    
    style A fill:#FF9800,color:#fff
    style B fill:#FFB74D
    style C fill:#FFB74D
```

### Storage Tiers

| Tier | Access Cost | Storage Cost | Use Case | Min Duration |
|------|-----------|--------------|----------|--------------|
| **Hot** | Low | High | Frequent access | None |
| **Cool** | High | Low | Infrequent (30+ days) | 30 days |
| **Archive** | Very High | Very Low | Rare (90+ days) | 90 days |

### Use Cases

- Images & Videos
- Backup & Archive
- Log Files
- Media Distribution
- Data for Analysis

### Common Operations

```powershell
# Create Storage Account
az storage account create --name mystorageacct --resource-group myResourceGroup

# Create Container
az storage container create --account-name mystorageacct --name mycontainer

# Upload Blob
az storage blob upload --account-name mystorageacct --container-name mycontainer \
  --name myfile.txt --file local_file.txt

# Download Blob
az storage blob download --account-name mystorageacct --container-name mycontainer \
  --name myfile.txt --file local_file.txt
```

---

## Azure Disk Storage

### What is Disk Storage?

Persistent block storage for Virtual Machines.

### Disk Types

```mermaid
graph TB
    A["Azure Managed Disks"] --> B["Standard HDD"]
    A --> C["Standard SSD"]
    A --> D["Premium SSD"]
    A --> E["Ultra Disk"]
    
    B --> B1["Dev/Test"]
    B --> B2["Low Cost"]
    
    C --> C1["General Purpose"]
    C --> C2["Balanced"]
    
    D --> D1["Production"]
    D --> D2["High Performance"]
    
    E --> E1["Mission Critical"]
    E --> E2["Extreme Performance"]
    
    style A fill:#2196F3,color:#fff
    style B fill:#64B5F6
    style C fill:#64B5F6
    style D fill:#64B5F6
    style E fill:#64B5F6
```

| Type | IOPS | Throughput | Cost | Use Case |
|------|------|-----------|------|----------|
| **Standard HDD** | 500 | 60 MB/s | Low | Dev/Test |
| **Standard SSD** | 6,000 | 750 MB/s | Medium | General Purpose |
| **Premium SSD** | 20,000 | 900 MB/s | High | Production |
| **Ultra** | 160,000 | 2,000 MB/s | Very High | Mission Critical |

### Use Cases

- Operating System Disks
- Application Data
- Database Storage
- Virtual Machine Storage

### PowerShell Example

```powershell
# Create managed disk
New-AzDisk -ResourceGroupName myResourceGroup -DiskName myDisk `
  -Disk (New-AzDiskConfig -Location eastus -CreateOption Empty -DiskSizeGB 128 `
  -SkuName Premium_LRS)

# Attach to VM
$vm = Get-AzVM -ResourceGroupName myResourceGroup -Name myVM
$disk = Get-AzDisk -ResourceGroupName myResourceGroup -DiskName myDisk
$vm = Add-AzVMDataDisk -VM $vm -Name "myDisk" -ManagedDiskId $disk.Id -Lun 0
Update-AzVM -ResourceGroupName myResourceGroup -VM $vm
```

---

## Azure File Storage

### What is File Storage?

Managed cloud file shares accessible via SMB protocol.

### Key Features

- SMB 3.0 protocol
- POSIX file system compliance
- Azure File Sync for hybrid scenarios
- Identity-based authentication

### Use Cases

```mermaid
graph TB
    A["Azure File Storage"] --> B["Shared File Access"]
    A --> C["Backup & Archive"]
    A --> D["Hybrid Scenarios"]
    
    B --> B1["Multiple VMs"]
    B --> B2["On-Premises Servers"]
    
    C --> C1["Long-term Backups"]
    C --> C2["Archive"]
    
    D --> D1["On-Premises + Cloud"]
    D --> D2["Azure File Sync"]
    
    style A fill:#00BCD4,color:#fff
    style B fill:#4DD0E1
    style C fill:#4DD0E1
    style D fill:#4DD0E1
```

### PowerShell Example

```powershell
# Create file share
New-AzStorageShare -Name myshare -Context $storageContext

# Mount on Windows
$storageAccountKey = (Get-AzStorageAccountKey -ResourceGroupName myResourceGroup `
  -Name mystorageacct)[0].Value
$password = ConvertTo-SecureString -String $storageAccountKey -AsPlainText -Force
$credential = New-Object System.Management.Automation.PSCredential `
  -ArgumentList "Azure\mystorageacct", $password
New-PSDrive -Name Z -PSProvider FileSystem -Root "\\mystorageacct.file.core.windows.net\myshare" `
  -Credential $credential -Persist
```

---

## Azure Queue Storage

### What is Queue Storage?

Asynchronous messaging service for decoupling applications.

### Architecture

```mermaid
graph LR
    A["Producer<br/>Application"] -->|Add Message| B["Azure Queue"]
    B -->|Read Message| C["Consumer<br/>Application"]
    C -->|Delete Message| B
    
    D["Another<br/>Consumer"] -->|Read Message| B
    
    style B fill:#9C27B0,color:#fff
    style A fill:#CE93D8
    style C fill:#CE93D8
    style D fill:#CE93D8
```

### Use Cases

- Decouple application components
- Process large batches
- Scheduled job processing
- Buffering request spikes
- Event-driven architectures

### Python Example

```python
from azure.storage.queue import QueueClient

# Connect to queue
queue_client = QueueClient.from_connection_string(conn_str, "myqueue")

# Send message
queue_client.send_message("Hello World!")

# Receive message
messages = queue_client.receive_messages()
for msg in messages:
    print(msg.content)
    queue_client.delete_message(msg)
```

---

## Azure Table Storage

### What is Table Storage?

NoSQL key-value store for semi-structured data.

### Key Concepts

- **Partition Key** - Groups related data
- **Row Key** - Unique identifier within partition
- **Timestamp** - Automatic timestamp
- **Properties** - Custom attributes

### Architecture

```mermaid
graph TB
    A["Azure Table"] --> B["Partition 1"]
    A --> C["Partition 2"]
    
    B --> B1["Row 1: User1"]
    B --> B2["Row 2: User2"]
    B --> B3["Row N"]
    
    C --> C1["Row 1: User100"]
    C --> C2["Row 2: User101"]
    
    B1 --> P1["Name<br/>Email<br/>Phone"]
    B2 --> P2["Name<br/>Email<br/>Phone"]
    
    style A fill:#4CAF50,color:#fff
    style B fill:#81C784
    style C fill:#81C784
```

### Use Cases

- User profiles
- Device logs
- Session management
- Metadata storage
- IoT device data

### C# Example

```csharp
using Azure.Data.Tables;

// Create table client
var tableClient = new TableClient(new Uri("https://mystorageacct.table.core.windows.net/"),
    "myTable", new TableSharedKeyCredential("mystorageacct", storageKey));

// Create entity
var entity = new TableEntity("Users", "user1")
{
    { "FirstName", "John" },
    { "LastName", "Doe" },
    { "Email", "john@example.com" }
};

// Add entity
await tableClient.AddEntityAsync(entity);

// Query
var query = tableClient.QueryAsync<TableEntity>(e => e.PartitionKey == "Users");
```

---

## Azure Archive Storage

### What is Archive Storage?

Ultra-low-cost storage for rarely accessed data.

### Characteristics

- Lowest cost per GB
- High access latency (15 min - 1 hour)
- Long-term retention (7+ years)
- Data must remain at least 90 days

### Use Cases

```mermaid
graph TB
    A["Archive Storage"] --> B["Compliance"]
    A --> C["Long-term Backup"]
    A --> D["Historical Data"]
    
    B --> B1["Legal Holds"]
    B --> B2["Audit Trail"]
    
    C --> C1["Disaster Recovery"]
    C --> C2["Archival"]
    
    D --> D1["Past Records"]
    D --> D2["Old Logs"]
    
    style A fill:#F44336,color:#fff
    style B fill:#EF5350
    style C fill:#EF5350
    style D fill:#EF5350
```

---

## Storage Account Basics

### What is a Storage Account?

Unique namespace in Azure for storing and accessing data.

### Storage Account Setup

```mermaid
graph TB
    A["Create Storage Account"] --> B["Basic Info"]
    B --> C["Account Name"]
    B --> D["Region"]
    
    A --> E["Performance"]
    E --> E1["Standard"]
    E --> E2["Premium"]
    
    A --> F["Replication"]
    F --> F1["LRS - Local"]
    F --> F2["GRS - Geo"]
    F --> F3["RA-GRS - Read-Access Geo"]
    
    style A fill:#2196F3,color:#fff
    style B fill:#64B5F6
    style E fill:#64B5F6
    style F fill:#64B5F6
```

### Replication Options

| Option | Replicas | Availability | Cost |
|--------|----------|--------------|------|
| **LRS** | 3 (same DC) | 99.99% | Low |
| **ZRS** | 3 (multiple AZs) | 99.99% | Medium |
| **GRS** | 3 + 3 (paired region) | 99.99% | High |
| **RA-GRS** | 3 + 3 (read access) | 99.99% | Highest |

### PowerShell Setup

```powershell
# Create resource group
New-AzResourceGroup -Name myResourceGroup -Location eastus

# Create storage account
$storageAccount = New-AzStorageAccount -Name mystorageacct `
  -ResourceGroupName myResourceGroup -Location eastus `
  -SkuName Standard_GRS -Kind StorageV2

# Get storage context
$storageContext = $storageAccount.Context
```

---

## Comparison & Selection

### Service Comparison

| Feature | Blob | Disk | File | Queue | Table |
|---------|------|------|------|-------|-------|
| **Data Type** | Unstructured | Block | File Shares | Messages | Semi-structured |
| **Protocol** | HTTPS | Block | SMB | HTTPS | HTTPS |
| **Access** | HTTP | VM Direct | Network | API | API |
| **Scalability** | ✅ ✅ ✅ | ✅ ✅ | ✅ | ✅ ✅ | ✅ ✅ |
| **Cost** | Low | Medium | Medium | Low | Very Low |
| **Latency** | Low | Very Low | Low-Medium | Low | Low |

### Decision Tree

```mermaid
graph TD
    A["Choose Storage Service"] --> B{"Data Type?"}
    
    B -->|Files/Media| C{"How Access?"}
    B -->|Structured| D["Table Storage"]
    B -->|Messages| E["Queue Storage"]
    
    C -->|Direct Block| F["Disk Storage"]
    C -->|HTTP/Blob| G["Blob Storage"]
    C -->|File Share| H["File Storage"]
    
    style D fill:#4CAF50,color:#fff
    style E fill:#4CAF50,color:#fff
    style F fill:#4CAF50,color:#fff
    style G fill:#4CAF50,color:#fff
    style H fill:#4CAF50,color:#fff
```

---

## Key Takeaways

✅ Use Blob Storage for unstructured data (images, videos, logs)  
✅ Use Disk Storage for VM persistent storage  
✅ Use File Storage for shared file access (SMB)  
✅ Use Queue Storage for async messaging  
✅ Use Table Storage for key-value data  
✅ Use Archive for long-term retention  

---

## Next Steps

- Read: [06-database-services](../06-database-services/README.md)
- See: [practical-experiments](../08-practical-experiments/README.md)
