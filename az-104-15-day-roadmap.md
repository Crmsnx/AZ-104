# AZ-104 Accelerated Study Roadmap

**Compressed from Scott Duffy's 30-day / 45-min-a-day plan → 15 days at ~90 min/day**

| | |
|---|---|
| **Start date** | June 20, 2026 |
| **Course content complete by** | July 4, 2026 |
| **Internship starts** | June 29, 2026 (Days 10+ run parallel with CCNA/CPTS) |
| **Voucher deadline (schedule exam by)** | August 18, 2026 |
| **Buffer after course completion** | ~6 weeks for hands-on labs, practice exams & review |

> Pace logic: Scott Duffy's roadmap assumes 45 min/day over 30 days (~22.5 hrs of content). At ~90 min/day, the same ground is covered in 15 days. Days 1–9 are pre-internship and can run AZ-104 only. From Day 10 onward, each day's block splits 45/45 between AZ-104 and CCNA/CPTS.

---

## Week 1 — Identity, Governance & Storage

### Day 1 — Thu Jun 20 *(Sat)*
- [ ] Role of an Azure Administrator, Azure services overview, Azure portal tour
- [ ] Create and manage users/groups in Microsoft Entra ID, manage group properties

**Resources:** [AZ-104 Prerequisites](https://learn.microsoft.com/training/paths/az-104-administrator-prerequisites/) · [Manage identities & governance](https://learn.microsoft.com/training/paths/az-104-manage-identities-governance/)

### Day 2 — Sun Jun 21
- [ ] Implement RBAC, assign roles at different scopes
- [ ] Implement & manage Azure Policy, configure resource locks and tags

**Resources:** [Azure RBAC](https://learn.microsoft.com/azure/role-based-access-control/overview) · [Azure Policy overview](https://learn.microsoft.com/azure/governance/policy/overview)

### Day 3 — Mon Jun 22
- [ ] **Review:** identities, RBAC, governance — quick self-quiz on Days 1–2
- [ ] Create and configure storage accounts, configure replication (LRS/ZRS/GRS)

**Resources:** [Practice Assessments](https://learn.microsoft.com/credentials/certifications/practice-assessments-for-microsoft-certifications/) · [Manage storage](https://learn.microsoft.com/training/paths/az-104-manage-storage/)

### Day 4 — Tue Jun 23
- [ ] Configure containers in Blob Storage, access tiers, lifecycle management
- [ ] Configure Azure Files and Azure File Sync

**Resources:** [Configure Blob Storage](https://learn.microsoft.com/training/modules/configure-blob-storage/)

---

## Week 2 — Compute

### Day 5 — Wed Jun 24
- [ ] Create and configure virtual machines, manage VM sizes and disks
- [ ] Automate VM deployment with ARM templates, VHD templates, VM extensions

**Resources:** [Deploy & manage compute resources](https://learn.microsoft.com/training/paths/az-104-manage-compute-resources/)

### Day 6 — Thu Jun 25
- [ ] Provision Azure Container Instances and Azure Container Apps, AKS basics
- [ ] Create and configure Azure App Service, App Service plans, custom domains

**Resources:** [Configure Container Instances](https://learn.microsoft.com/training/modules/create-run-container-images-azure-container-instances/)

### Day 7 — Fri Jun 26
- [ ] **Review:** compute & storage — quick self-quiz on Days 3–6
- [ ] Create and configure virtual networks and subnets, public/private IPs

**Resources:** [Configure virtual networks](https://learn.microsoft.com/training/paths/az-104-manage-virtual-networks/)

### Day 8 — Sat Jun 27
- [ ] Create and configure NSGs, implement Azure Bastion and service endpoints
- [ ] Configure Azure DNS, load balancers, troubleshoot load balancing

**Resources:** [Configure network security groups](https://learn.microsoft.com/training/modules/design-implement-network-security-groups/)

---

## Week 3 — Networking & Internship Transition

### Day 9 — Sun Jun 28
- [ ] **Review:** networking fundamentals — quick self-quiz on Days 7–8
- [ ] Interpret Azure Monitor metrics, configure log settings and alerts

**Resources:** [Monitor & back up resources](https://learn.microsoft.com/training/paths/az-104-monitor-backup-resources/)

> 🎒 **Internship starts tomorrow.** From here on, each 1.5h block splits 45 min AZ-104 / 45 min CCNA/CPTS.

### Day 10 — Mon Jun 29 *(internship day 1)*
- [ ] Create Recovery Services vaults, configure backup policies, restore operations
- [ ] Configure Azure Site Recovery, perform failover to secondary region

**Resources:** [Implement backup & recovery](https://learn.microsoft.com/training/modules/design-implement-azure-backup/)

### Day 11 — Tue Jun 30
- [ ] **Review:** monitoring & backup — quick self-quiz on Days 9–10
- [ ] **Full-length practice exam** — assess current readiness, note weak domains

**Resources:** [Practice Assessments](https://learn.microsoft.com/credentials/certifications/practice-assessments-for-microsoft-certifications/)

---

## Week 4 — Reinforcement

### Day 12 — Wed Jul 1
- [ ] Analyze practice exam results, revisit weakest domain in depth
- [ ] Hands-on: navigate Azure portal, create/manage resources end-to-end

**Resources:** [Azure portal docs](https://learn.microsoft.com/azure/azure-portal/)

### Day 13 — Thu Jul 2
- [ ] Final review — summarize key concepts across all 5 domains
- [ ] Practice common tasks via Azure CLI and PowerShell

**Resources:** [Azure CLI docs](https://learn.microsoft.com/cli/azure/) · [Azure PowerShell docs](https://learn.microsoft.com/powershell/azure/)

### Day 14 — Fri Jul 3
- [ ] Revisit storage & compute modules — hands-on reinforcement
- [ ] Revisit networking modules — hands-on reinforcement (NSGs, VNets, peering)

### Day 15 — Sat Jul 4 *(course content complete)*
- [ ] Revisit monitoring & backup modules — hands-on reinforcement
- [ ] **Second full-length practice exam** — compare score vs. Day 11 baseline

**🎯 Core course content finished. ~6 weeks remain before the Aug 18 scheduling deadline.**

---

## Beyond Day 15 — Buffer Weeks (Jul 5 – Aug 16)

With this much runway, no need to cram. Suggested use of the buffer:

- **Weeks 1–2 (Jul 5–18):** Deep hands-on labs per domain in a free Azure sandbox account — focus on whichever domain scored lowest on practice exams
- **Weeks 3–4 (Jul 19–Aug 1):** Second pass through weak areas, additional practice question sets, start timing yourself under exam conditions
- **Weeks 5–6 (Aug 2–15):** Full timed practice exams (aim for consistent 80%+), light daily review only — avoid new material this close to the date
- **Aug 16–17:** Rest, no new study
- **Aug 18:** Schedule the exam (book a date 3–7 days out so you land it on momentum, not panic)

---

## Exam Day Reference

- Cost: ~$165 USD (varies by region)
- Format: ~65 questions, 3 hours
- Passing score: 700/1000
- Domain weighting: Identity & Governance (15–20%) · Storage (10–15%) · Compute (25–30%) · Networking (30–35%) · Monitor & Backup (10–15%)

---

*Roadmap compressed from Scott Duffy's official AZ-104 30-day study plan (Udemy course 70533) to fit a ~90 min/day pace.*
