# GitHub README – Wyndo Cloud Optimization Project

## Project Title
**QASECR for Wyndo**  
*Quality Assurance, Security, and Reliability in Wyndo’s Cloud Infrastructure*

---

## Project Overview
We partnered with **Wyndo**, a startup focused on helping consumers discover real-time local inventory in brick-and-mortar stores, to enhance their cloud infrastructure by identifying security risks, reducing AWS costs, and improving system reliability through real-time monitoring and automation. Our project **secured the backend, slashed cloud waste, and implemented continuous monitoring**—making Wyndo’s backend safer, leaner, and future-ready.

---

## Problem Statement
Wyndo’s cloud infrastructure was growing fast—but so were its **security gaps and cloud costs**. Their Amazon RDS database was publicly accessible, ElastiCache was over-provisioned, and no automated alarms were in place to catch CPU/memory spikes or unauthorized configuration changes. Although AWS provides tools like Guardduty, these were not being used. As a result:

- **Undetected Misconfigurations:** Critical security issues (open database, permissive network rules) went unnoticed.
- **Unnecessary Cloud Spend:** Wyndo was overpaying for underutilized resources (over-provisioned ElastiCache costing ~$126/month).
- **Lack of Visibility:** No insight into performance issues—outages or inefficiencies could linger.
- **Data Exposure Risk:** Sensitive customer data (PII) was not scanned, posing compliance risks.

Our goal was to rebuild confidence from the backend by fortifying security and optimizing costs.

---

## ISBA Subfields

| Subfield    | How It Applied in This Project |
|-------------|--------------------------------|
| **Analytics** | Analyzed AWS usage and billing data, interpreting CloudWatch metrics and using Cost Explorer to visualize spending trends. |
| **Security**  | Conducted vulnerability assessments (IAM, KMS, network configs), reduced exposure, enabled GuardDuty, and improved PII detection. |
| **Systems**   | Attempted to optimize EC2/ElastiCache resources, improved reliability, introduced automated monitoring and scheduled audits. |

Our capstone integrates **Information Systems**, **Business Analytics**, and **Cybersecurity** to address Wyndo’s challenges.

---

## Solution Overview
We performed a full AWS infrastructure audit—identifying vulnerabilities, enhancing monitoring, and optimizing costs. Our approach followed an iterative **Assess-Analyze-Remediate-Monitor** process aligned with SDLC and CRISP-DM principles:

- Assessed current state.
- Analyzed key issues.
- Implemented remediation.
- Established monitoring for continuous feedback.

---

## Technical Stack
- **Programming Languages:** Python (boto3), SQL (Amazon RDS)
- **Frameworks/Methodologies:** Assess-Analyze-Remediate-Monitor (CRISP-DM, SDLC)
- **Data Storage:** Amazon RDS (PostgreSQL), Amazon ElastiCache (Redis)
- **Tools & Services:** AWS Macie, CloudWatch, CloudFront, Cost Explorer, AWS IAM, Canva
- **APIs:** AWS Cost Explorer API, CloudWatch Metrics API
- **Hosting & Infrastructure:** Amazon EC2, Elastic Beanstalk, S3, VPC, Lambda, Step Functions
- **Data:** AWS logs, billing reports, security policy documents

---

## Solution Details (Technical Implementation)

### Key Technical Deliverables

**Security Audit & IAM Hardening:**  
Reviewed IAM configurations, tightened KMS policies, and scheduled lockdowns for public endpoints and network ACLs.

**Database Protection:**  
Secured publicly accessible RDS instances with IP restrictions and recommended private subnet migration. Selected AWS Glue over Macie for effective PII data scanning and masking directly within RDS.

**Cost Optimization:**  
Recommended Reserved Instances for ElastiCache saving ~$219/year. Identified low RDS utilization for future downsizing.

**Monitoring & Alarms:**  
Implemented Amazon CloudWatch Alarms for:
- Database Health (RDS replication lag)
- Cache Performance (Redis CPU, memory, swap usage)
- Security Events (API calls, security group changes)

Set AWS Billing Alerts for proactive cost monitoring.

### Architecture & Process Diagrams
See the repository’s `/docs` folder for diagrams.

*(Diagrams illustrate AWS Cloud Monitoring & Remediation Flow, showcasing GuardDuty, Inspector, CloudWatch alerts, and rapid incident response.)*

---

## Next Steps / Future Improvements

- **Monthly Cost Audits:** Use AWS Lambda and Cost Explorer API for automated monthly cost anomaly detection.
- **Integrate Third-Party Intrusion Detection Systems:** Ensure it would be compatible with your architecture, and provides visibility into potential threats across AWS resources
- **Improve Operational Efficiency:** Explore lower memory use options for backend.
- **Implement MFA for IAM Roles:** Follow security best practices by ensuring all IAM users have MFA enabled.

These steps further enhance security, reduce overhead, and support future growth.

---

## Retrospective

### Challenges Encountered
- **Limited Documentation:** Reverse-engineered AWS setups, improved Confluence documentation.
- **Critical Exposure:** Quickly secured public-facing RDS without downtime and planned secure long-term architecture.
- **Tracing Performance Anomalies:** Addressed Redis performance with improved logging and interim CloudWatch analysis.
- **EC2 Downsizing:** Unable to downsize EC2 Instance due to memory usage, recommended reconfiguring backend code if Wyndo chooses to move forward with this.

### Lessons Learned
- **Bake-In Monitoring:** Implement monitoring early in the project lifecycle.
- **Right-Tool for the Job:** Implemented Amazon Macie with Step Functions automation to scan RDS snapshot exports for PII, enabling cost-efficient and targeted data classification without continuous monitoring overhead.
- **Cost Visibility = Better Decisions:** Enhanced financial awareness improved architecture decisions.
- **Documentation:** Essential to guide decisions through clear documentation.

---

## References
- [Final Presentation Slides](https://www.canva.com/design/DAGj-xzcEmo/PTC_YQylEIjWv-KlUjmX-Q/edit?utm_content=DAGj-xzcEmo&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)
- [Project Demo Recording](https://lmu0.sharepoint.com/:v:/s/ISBACapstoneProject368-WyndoQASecurityReliability/EYTL94iDIMdNsahFD8jdC0YB-Cup2heZb7CeKGq-xd1Ezg?e=HekwAS)
- [Project Documentation](https://drive.google.com/file/d/1atQGbPC9EK8pr5ToCJMOOFslqwod50QK/view?usp=sharing)
- [AWS Glue Documentation](https://docs.aws.amazon.com/macie/latest/user/what-is-macie.html)
- [AWS Cost Explorer API Reference](https://docs.aws.amazon.com/cost-management/latest/APIReference/API_Operations_AWS_Cost_Explorer.html)
- [Purchasing RI Instructions](https://docs.google.com/presentation/d/1bw2_c6OZsPLix4xVxU5trRnPav5q9ZVDQbspeKsrkSA/edit?usp=sharing)
