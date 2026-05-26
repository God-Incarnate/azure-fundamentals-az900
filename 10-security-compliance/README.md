# 🔐 Security, Compliance & Identity Management

Comprehensive guide to Azure security services and best practices.

## 📚 Topics Covered

1. [Azure Active Directory](#azure-active-directory)
2. [Multi-Factor Authentication](#multi-factor-authentication)
3. [Azure Key Vault](#azure-key-vault)
4. [Azure Security Services](#azure-security-services)
5. [Compliance & Governance](#compliance--governance)
6. [Security Best Practices](#security-best-practices)

---

## Azure Active Directory

### What is Azure AD?

Cloud identity and access management service for managing users, groups, and application access.

### Core Concepts

```mermaid
graph TB
    A["Azure AD"] --> B["Users & Groups"]
    A --> C["Applications"]
    A --> D["Roles & Permissions"]
    
    B --> B1["Single Users"]
    B --> B2["Groups"]
    B --> B3["Guest Users"]
    
    C --> C1["SaaS Apps"]
    C --> C2["Enterprise Apps"]
    C --> C3["Custom Apps"]
    
    D --> D1["RBAC"]
    D --> D2["Conditional Access"]
    D --> D3["MFA"]
    
    style A fill:#2196F3,color:#fff
    style B fill:#64B5F6
    style C fill:#64B5F6
    style D fill:#64B5F6
```

### Key Features

✅ **Single Sign-On (SSO)** - One login for multiple apps  
✅ **User Authentication** - Secure identity verification  
✅ **Identity Protection** - Detect & remediate risks  
✅ **Conditional Access** - Policy-based access control  
✅ **Guest Access** - External user collaboration  
✅ **Hybrid Support** - On-premises + cloud integration  

### User Management Workflow

```mermaid
graph LR
    A["Create User"] --> B["Assign License"]
    B --> C["Add to Group"]
    C --> D["Configure Roles"]
    D --> E["Set Permissions"]
    E --> F["Enable MFA"]
    F --> G["User Ready"]
    
    style A fill:#4CAF50,color:#fff
    style G fill:#4CAF50,color:#fff
```

### Azure AD Editions

| Edition | Users | Features | Cost |
|---------|-------|----------|------|
| **Free** | Unlimited | Basic | Free |
| **Office 365** | Unlimited | Self-Service | Included |
| **Premium P1** | Unlimited | Advanced | $6/user/month |
| **Premium P2** | Unlimited | All Features | $9/user/month |

### PowerShell: Create User

```powershell
# Connect to Azure AD
Connect-AzureAD

# Create new user
$PasswordProfile = New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password = "TempPassword123!"
$PasswordProfile.ForceChangePasswordNextLogin = $true

New-AzureADUser -AccountEnabled $true `
  -DisplayName "John Doe" `
  -UserPrincipalName "john.doe@contoso.onmicrosoft.com" `
  -PasswordProfile $PasswordProfile `
  -MailNickname "john.doe"

# Get all users
Get-AzureADUser -All $true | Select ObjectId, DisplayName, UserPrincipalName
```

---

## Multi-Factor Authentication

### What is MFA?

Authentication requiring multiple verification methods (something you know, have, are).

### MFA Methods

```mermaid
graph TB
    A["MFA Methods"] --> B["Knowledge"]
    A --> C["Possession"]
    A --> D["Inherence"]
    
    B --> B1["Password"]
    B --> B2["Security Questions"]
    
    C --> C1["TOTP (Authenticator App)"]
    C --> C2["SMS"]
    C --> C3["Email"]
    C --> C4["Hardware Token"]
    
    D --> D1["Fingerprint"]
    D --> D2["Face Recognition"]
    D --> D3["Iris Scan"]
    
    style A fill:#FF9800,color:#fff
    style B fill:#FFB74D
    style C fill:#FFB74D
    style D fill:#FFB74D
```

### MFA Authentication Flow

```mermaid
graph TD
    A["User Login"] --> B["Enter Username<br/>& Password"]
    B --> C["Password Verified?"]
    
    C -->|No| D["Access Denied"]
    C -->|Yes| E["MFA Challenge"]
    
    E --> F["Select Method"]
    F --> G{"Method Type?"}
    
    G -->|App| H["Enter TOTP Code"]
    G -->|SMS| I["Enter SMS Code"]
    G -->|Call| J["Approve Call"]
    
    H --> K["Code Valid?"]
    I --> K
    J --> K
    
    K -->|No| L["Denied"]
    K -->|Yes| M["Access Granted"]
    
    style M fill:#4CAF50,color:#fff
    style D fill:#F44336,color:#fff
    style L fill:#F44336,color:#fff
```

### Enabling MFA

```powershell
# Require MFA for specific user
$mfaRequirement = New-Object -TypeName Microsoft.Open.AzureAD.Model.StrongAuthenticationRequirement
$mfaRequirement.RelyingParty = "*"
$mfaRequirement.State = "Enabled"

$requirements = @($mfaRequirement)
Set-AzureADUser -ObjectId "user@contoso.com" `
  -StrongAuthenticationRequirements $requirements
```

### Benefits

✅ **Enhanced Security** - Prevents unauthorized access  
✅ **Compliance** - Meets regulatory requirements  
✅ **Risk Reduction** - Mitigates password attacks  
✅ **User Control** - Multiple authentication options  

---

## Azure Key Vault

### What is Key Vault?

Centralized cloud service for managing secrets, keys, and certificates.

### Key Vault Components

```mermaid
graph TB
    A["Azure Key Vault"] --> B["Secrets"]
    A --> C["Keys"]
    A --> D["Certificates"]
    
    B --> B1["Passwords"]
    B --> B2["Connection Strings"]
    B --> B3["API Keys"]
    B --> B4["Database Credentials"]
    
    C --> C1["Encryption Keys"]
    C --> C2["Signing Keys"]
    C --> C3["Stored in HSM"]
    
    D --> D1["SSL/TLS Certs"]
    D --> D2["Code Signing"]
    D --> D3["Auto Renewal"]
    
    style A fill:#9C27B0,color:#fff
    style B fill:#CE93D8
    style C fill:#CE93D8
    style D fill:#CE93D8
```

### Access Control

- **Role-Based Access Control (RBAC)**
- **Access Policies** - Per-object permissions
- **Network Rules** - Firewall restrictions
- **Audit Logging** - All access tracked

### PowerShell: Create & Manage Secrets

```powershell
# Create Key Vault
New-AzKeyVault -Name myKeyVault -ResourceGroupName myResourceGroup `
  -Location eastus -EnabledForSecretStorage

# Create secret
$SecretValue = ConvertTo-SecureString 'MySecret123!' -AsPlainText -Force
Set-AzKeyVaultSecret -VaultName myKeyVault -Name dbPassword `
  -SecretValue $SecretValue

# Retrieve secret
$secret = Get-AzKeyVaultSecret -VaultName myKeyVault -Name dbPassword
$secretValue = $secret.SecretValue | ConvertFrom-SecureString -AsPlainText

# List all secrets
Get-AzKeyVaultSecret -VaultName myKeyVault

# Delete secret
Remove-AzKeyVaultSecret -VaultName myKeyVault -Name dbPassword -Force
```

### Benefits

✅ **Centralized Management** - Single source of truth  
✅ **Security** - HSM-backed storage  
✅ **Audit Trail** - All access logged  
✅ **Integration** - Works with Azure services  
✅ **Automatic Rotation** - Optional secret rotation  

---

## Azure Security Services

### Security Center

Unified security management and threat intelligence.

```mermaid
graph TB
    A["Security Center"] --> B["Asset Inventory"]
    A --> C["Threat Detection"]
    A --> D["Security Recommendations"]
    A --> E["Compliance Monitoring"]
    
    B --> B1["All Azure Resources"]
    B --> B2["VMs"]
    B --> B3["Databases"]
    
    C --> C1["Malware Detection"]
    C --> C2["Anomaly Detection"]
    C --> C3["Vulnerability Scanning"]
    
    D --> D1["Patch Updates"]
    D --> D2["Firewall Rules"]
    D --> D3["MFA Enablement"]
    
    E --> E1["Regulatory"]
    E --> E2["Industry Standards"]
    
    style A fill:#F44336,color:#fff
    style B fill:#EF5350
    style C fill:#EF5350
    style D fill:#EF5350
    style E fill:#EF5350
```

### Azure Defender

Advanced threat protection for resources.

**Protections:**
- VMs & servers
- SQL databases
- App Service
- Storage accounts
- Kubernetes clusters
- Key Vault

### DDoS Protection

Protection against distributed denial-of-service attacks.

**Standard DDoS Protection:**
- Automatic attack mitigation
- Real-time attack metrics
- Attack analytics & insights

---

## Compliance & Governance

### Azure Policy

Enforce organizational standards and compliance.

```mermaid
graph TB
    A["Azure Policy"] --> B["Policy Definitions"]
    B --> B1["Allowed Locations"]
    B --> B2["Required Tags"]
    B --> B3["Allowed VM SKUs"]
    
    A --> C["Initiatives"]
    C --> C1["Policy Groups"]
    C --> C2["Predefined Sets"]
    
    A --> D["Enforcement"]
    D --> D1["Deny"]
    D --> D2["Audit"]
    D --> D3["DeployIfNotExists"]
    
    style A fill:#00BCD4,color:#fff
    style B fill:#4DD0E1
    style C fill:#4DD0E1
    style D fill:#4DD0E1
```

### Compliance Standards

| Standard | Focus | Use Case |
|----------|-------|----------|
| **SOC 2** | Security | Cloud services |
| **HIPAA** | Healthcare | Medical data |
| **GDPR** | Data Privacy | EU users |
| **PCI DSS** | Payment Security | Card payments |
| **ISO 27001** | Information Security | All organizations |
| **FedRAMP** | Government | Gov agencies |

### Governance Best Practices

1. **Resource Groups** - Logical organization
2. **Tagging Strategy** - Cost tracking & organization
3. **RBAC** - Least privilege access
4. **Azure Policy** - Enforce standards
5. **Audit Logs** - Monitor all changes
6. **Cost Management** - Track spending

---

## Security Best Practices

### Defense in Depth

```mermaid
graph TB
    A["Security Layers"] --> B["Perimeter"]
    A --> C["Network"]
    A --> D["Compute"]
    A --> E["Application"]
    A --> F["Data"]
    
    B --> B1["DDoS Protection"]
    B --> B2["WAF"]
    
    C --> C1["NSG Rules"]
    C --> C2["Firewalls"]
    
    D --> D1["Antimalware"]
    D --> D2["Updates"]
    
    E --> E1["Input Validation"]
    E --> E2["Authentication"]
    
    F --> F1["Encryption"]
    F --> F2["Access Control"]
    
    style A fill:#F44336,color:#fff
    style B fill:#EF5350
    style C fill:#EF5350
    style D fill:#EF5350
    style E fill:#EF5350
    style F fill:#EF5350
```

### Top 10 Security Practices

✅ **Enable MFA** - Always require MFA for admin accounts  
✅ **Use Key Vault** - Never hardcode secrets  
✅ **Encrypt Data** - Enable encryption at rest & in transit  
✅ **Network Isolation** - Use NSGs and firewalls  
✅ **Least Privilege** - Grant minimum required access  
✅ **Regular Audits** - Review logs and permissions  
✅ **Keep Updated** - Patch all systems regularly  
✅ **Monitor Threats** - Use Security Center  
✅ **Plan Backup** - Implement disaster recovery  
✅ **Security Training** - Educate team members  

### Security Configuration Checklist

- [ ] MFA enabled for admin users
- [ ] Key Vault configured for secrets
- [ ] Encryption enabled (at rest & in transit)
- [ ] NSG rules configured (least privilege)
- [ ] Azure Policy enforced
- [ ] Auditing enabled
- [ ] RBAC properly configured
- [ ] Backups scheduled
- [ ] DDoS protection enabled
- [ ] Security alerts configured

---

## Key Takeaways

✅ Azure AD provides centralized identity management  
✅ MFA significantly enhances security  
✅ Key Vault secures sensitive data  
✅ Security Center monitors threats  
✅ Compliance frameworks ensure standards  
✅ Defense in depth protects all layers  

---

## Next Steps

- Read: [practical-experiments](../08-practical-experiments/README.md)
- Explore: [IoT Services](../11-iot-services/README.md)
