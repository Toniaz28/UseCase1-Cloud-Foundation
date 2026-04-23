# Thought Process – Use Case 1: Cloud Foundation

## Task 1: Create Resource Group with Tags

*What I did:*  
I created a resource group in the East US region and added four tags: Department, Environment, CostCenter, and Owner to organize the resources.

*Why I chose this configuration:*  
I used tags because they help with cost tracking, resource organization, and ownership management. This is important in a company environment where multiple teams share cloud resources.

*What I learned:*  
I learned that tags are not just labels—they are essential for governance and cost control, especially in large environments.

---

## Task 2: Create Virtual Network with Subnets

*What I did:*  
I created a virtual network with address space 10.0.0.0/16 and divided it into three subnets: WebSubnet, AppSubnet, and DataSubnet.

*Why I chose this configuration:*  
I separated the subnets to isolate different application tiers. This improves security and allows controlled communication between layers instead of exposing everything.

*What I learned:*  
I learned that subnetting is critical for structuring cloud environments and enforcing security boundaries between application components.

---

## Task 3: Configure Network Security Groups (NSGs)

*What I did:*  
I created three NSGs and applied specific inbound rules: allowing HTTP/HTTPS for the web tier, restricting app traffic to only the web subnet, and limiting data access to only the app subnet.

*Why I chose this configuration:*  
I followed the principle of least privilege by allowing only required traffic. This reduces the attack surface and prevents unnecessary exposure.

*What I learned:*  
I learned that NSG rules must be carefully planned, and priority matters because rules are evaluated from lowest number to highest.

---

## Task 4: Deploy a Linux Virtual Machine

*What I did:*  
I deployed an Ubuntu VM in the WebSubnet, connected via SSH, installed Nginx, and verified it by accessing the public IP in a browser.

*Why I chose this configuration:*  
I used the Standard_B1s size because it is cost-effective and suitable for testing. I allowed SSH temporarily for setup and HTTP for web access.

*What I learned:*  
I learned that even if the VM is running, services won’t be accessible unless both the NSG and the application (Nginx) are properly configured.

---

## Task 5: Create Storage Account with Blob and File Share

*What I did:*  
I created a storage account with LRS redundancy, added a private blob container, created a file share, and uploaded a test file.

*Why I chose this configuration:*  
I used private access to prevent unauthorized access to data. I chose LRS because it is cheaper and sufficient for a basic setup.

*What I learned:*  
I learned that making storage public can expose sensitive data, and redundancy options like LRS and GRS directly affect availability and cost.

---

## Task 6: Configure Azure Backup

*What I did:*  
I created a Recovery Services vault, defined a backup policy with daily backups, and enabled backup for the VM.

*Why I chose this configuration:*  
I chose daily backups with 7-day retention to balance cost and recovery needs. This ensures recent data can be restored if needed.

*What I learned:*  
I learned the importance of RPO (Recovery Point Objective) and RTO (Recovery Time Objective) and that backups are only useful if they can actually be restored successfully.

---

## Task 7: Security Review

*What I did:*  
I reviewed recommendations in Azure Advisor and analyzed the security, cost, and performance suggestions for my deployed resources.

*Why I chose this approach:*  
I used Azure Advisor because it provides built-in best practice recommendations that help improve the overall system.

*What I learned:*  
I learned that security is not just about configuration but also continuous monitoring and improvement based on recommendations.