# AZ-104 Study Notes — Sections 2–5

*Scott Duffy's course (Udemy 70533) — covers Azure Concepts, PowerShell/CLI, and Entra ID fundamentals*

---

## Section 2: Azure Concepts

### Core service categories
- **Compute** — VMs, App Services, Container Instances, AKS, Functions
- **Storage** — Blob, File, Queue, Table, Disk storage, all under one storage account
- **Networking** — VNets, NSGs, load balancers, DNS, VPN Gateway, ExpressRoute
- **Microservices** — small independent services that communicate over APIs; Azure tooling here includes AKS (Kubernetes), Container Apps, Service Bus, Event Grid

### VM vs App Services — when to use which
| | VM | App Service |
|---|---|---|
| Control | Full OS access | Platform-managed (PaaS) |
| Use case | Custom/legacy software, full server control | Web apps, APIs, mobile backends |
| Scaling | Manual or scale sets | Built-in autoscale |
| Patching | Your responsibility | Microsoft-managed |

### Storage & data services quick map
- **Blob storage** — unstructured data (files, images, backups), access tiers: Hot/Cool/Archive
- **Azure Files** — SMB/NFS file shares, mountable like a network drive
- **Disk storage** — backs VM OS/data disks
- **Table/Queue** — legacy NoSQL key-value and messaging (mostly superseded by Cosmos DB / Service Bus in new builds, but still testable)

> 🎯 **Exam tip:** "Which storage type for X" questions are common. Rule of thumb — unstructured files → Blob, shared drive feel → Files, VM disk → managed disk.

---

## Section 3: PowerShell and CLI

### Will the exam ask you to write scripts?
No — AZ-104 doesn't require writing PowerShell/CLI from scratch. You need to **recognize correct syntax** and know **which command does what**. Multiple choice / drag-drop style, not a coding test.

### Commands worth memorizing (Az module vs CLI)

| Task | Azure PowerShell (Az) | Azure CLI |
|---|---|---|
| Login | `Connect-AzAccount` | `az login` |
| List subscriptions | `Get-AzSubscription` | `az account list` |
| Switch subscription | `Set-AzContext -Subscription "<id>"` | `az account set --subscription "<id>"` |
| List resource groups | `Get-AzResourceGroup` | `az group list` |
| Create resource group | `New-AzResourceGroup -Name x -Location y` | `az group create --name x --location y` |
| List VMs | `Get-AzVM` | `az vm list` |
| Stop VM | `Stop-AzVM` | `az vm stop` |

**Pattern to remember:**
- PowerShell (Az module): `Verb-AzNoun` (PascalCase, hyphen-separated, always starts with `Az`)
- CLI: `az <noun> <verb>` (lowercase, space-separated)

### Installing PowerShell Core + Az module
```powershell
# Install Az module
Install-Module -Name Az -Repository PSGallery -Force

# Connect
Connect-AzAccount
```
CLI equivalent install is via package manager (`apt`, `brew`, MSI installer) — not PowerShell-based.

### Switching subscriptions
- PowerShell: `Set-AzContext -Subscription "<sub-name-or-id>"`
- CLI: `az account set --subscription "<sub-name-or-id>"`

> 🎯 **Exam tip:** Cloud Shell in the portal comes with both PowerShell and Bash (CLI) pre-authenticated — no install needed. Questions sometimes test whether you know Cloud Shell exists as the "no setup" option.

---

## Section 4: Introduction to Microsoft Entra ID (formerly Azure AD)

### What is Entra ID
Microsoft's cloud-based identity and access management service. Every Azure subscription is backed by exactly **one** Entra ID tenant (but one tenant can have multiple subscriptions).

### Free vs Premium P1 vs Premium P2

| Tier | Key features |
|---|---|
| **Free** | Basic user/group management, on-prem sync (Connect), basic SSO |
| **P1** | Dynamic groups, advanced conditional access, hybrid identity features (e.g., self-service password reset write-back) |
| **P2** | Everything in P1 + Identity Protection + Privileged Identity Management (PIM) |

> 🎯 **Exam tip:** P2 = PIM. If a question mentions Privileged Identity Management or risk-based conditional access, the answer involves P2.

### Managing multiple directories / tenants
- A single Microsoft account (or Azure AD account) can have access to multiple tenants.
- Switch tenants via the **Directories + subscriptions** blade (the directory switcher icon in the top nav of the portal).

### Creating an Entra ID tenant
Portal → **Microsoft Entra ID** → **Manage tenants** → **Create**. You choose a tenant type (Microsoft Entra ID vs Entra External ID for customer-facing apps) and an initial domain (`yourtenant.onmicrosoft.com`).

### Custom domains
- Add via **Custom domain names** blade.
- Must verify ownership via a DNS TXT (or MX) record before it becomes usable for sign-in.
- You can have multiple custom domains, but only one is the default for new user UPNs.

> 🎯 **Exam tip:** Domain verification = DNS record check. If a question is about "why can't users sign in with the new domain," the answer is usually "domain not verified yet."

---

## Section 5: Manage Microsoft Entra Users and Groups

### Users
- Create individually via portal, **bulk create** via CSV template, or PowerShell/CLI for automation.
- Key user properties: UPN, display name, usage location (required before license assignment).

### Groups
- **Security groups** — used for access control (resources, apps, RBAC).
- **Microsoft 365 groups** — collaboration-focused (shared mailbox, calendar, Teams, etc.).
- **Membership types:**
  - *Assigned* — manually add/remove members
  - *Dynamic User* — rule-based membership (requires P1+)
  - *Dynamic Device* — rule-based, devices only (requires P1+)

### Licenses
- Assign at the **user** or **group** level (group-based licensing is the scalable approach for orgs).
- Requires a **usage location** set on the user first, or assignment fails.

### Administrative Units (AUs)
- Scope admin permissions to a subset of users/groups/devices (e.g., delegate a regional IT admin to manage only their region's users).
- Useful for large orgs that want to avoid granting full Global Admin.

### Manage devices
- Devices can be **Entra joined**, **Entra registered**, or **Hybrid Entra joined** (synced from on-prem AD).
- Device settings blade controls whether users can join devices, multi-factor requirements for join, etc.

### Bulk operations
- CSV-based bulk create, bulk update, bulk delete for users — portal provides downloadable templates.
- Useful exam scenario: "fastest way to onboard 500 new users" → bulk CSV import, not manual creation.

### External users (B2B)
- Invite guest users from outside the org (another Entra tenant, Microsoft account, or even email-based one-time-passcode guests).
- Guests show up with `#EXT#` in their UPN.
- Governed by **External collaboration settings** and **Access reviews** (to periodically confirm guests still need access).

### Self-Service Password Reset (SSPR)
- Lets users reset their own password without help desk involvement.
- Requires registering authentication methods (phone, email, security questions, Authenticator app).
- Admin configures: which users it applies to, number of methods required, and registration enforcement.

> 🎯 **Exam tip:** SSPR vs MFA are often confused. SSPR = self-recovery of a forgotten password. MFA = second factor required at every (or conditional) sign-in. They share authentication methods but solve different problems.

---

## Quick recall — things that trip people up
- "Azure AD" and "Microsoft Entra ID" are the **same product**, just renamed — expect both terms on the exam.
- Usage location must be set **before** a license can be assigned to a user.
- Dynamic groups (user or device) require **Entra ID P1 or higher**.
- PIM (Privileged Identity Management) requires **P2**.
- B2B guest accounts appear with `#EXT#` in the UPN.
- `az` CLI commands are lowercase/space-separated; Az PowerShell cmdlets are `Verb-AzNoun`.
