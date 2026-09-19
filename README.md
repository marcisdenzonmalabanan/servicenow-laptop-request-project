ServiceNow Portfolio Project: End-to-End IT Service Catalog & Fulfillment Workflow
🎯 Objective

Design and build a complete "New Employee Laptop Request" workflow in ServiceNow — from catalog intake through manager approval, IT fulfillment, and reporting — to replace an ad-hoc, email-based onboarding process with a structured, auditable admin-owned system.

🛠️ Tools & Modules Used
ServiceNow Developer Instance (Personal Developer Instance)
Service Catalog (catalog items, variables, variable sets)
Flow Designer (approval workflow automation)
Business Rules & ACLs (Incident customization and field security)
Reporting & Dashboards (Data Visualization, List reports)
Update Sets (configuration migration and change tracking)
📋 Step-by-Step Implementation
Step 1: Security & User Model
Action: Created two security groups (IT Support, Approvers) and three test users with least-privilege role assignments.
Purpose: Establish a realistic access model before building any workflow logic on top of it.
Step 2: Service Catalog Item
Action: Built a "New Employee Laptop Request" catalog item with a laptop model dropdown (MacBook Pro, Dell Latitude, Lenovo ThinkPad), an accessories checkbox field, and a required justification field.
Enhancement: Set catalog item pricing to avoid conflicting with out-of-the-box auto-approval logic.
Step 3: Approval Workflow (Flow Designer)
Action: Built a flow triggered on request creation that dot-walks to the requester's Manager for dynamic approval, creates an IT fulfillment task on approval, sends email notifications at each stage, and auto-closes the request on completion.
Troubleshooting: Diagnosed and resolved a permissions failure by changing the flow's Run As property from "User who initiates session" to "System user," since the original setting caused fulfillment tasks to inherit the approver's own restricted permissions.
Step 4: Incident Management Customization
Action: Added a custom field to the Incident table, tied to a Business Rule that auto-assigns priority based on category, and layered an ACL restricting write access on that field to the IT support role.
Verification: Confirmed the field was editable for IT Support and hidden on the Self-Service view for end users — tested against two distinct user roles.
Step 5: Reporting & Dashboard
Action: Built a two-widget dashboard combining a status breakdown (Approved vs. Closed Complete) with a fulfillment-time list view showing Opened/Closed timestamps per request.
Troubleshooting: A calculated Duration field approach failed at the platform level; pivoted to a side-by-side timestamp list as a reliable working alternative.
Step 6: Update Set Discipline
Action: Activated a named Update Set before any configuration work began, capturing every change made throughout the build, then exported it as XML for migration/audit purposes.
💡 Business Value & Key Takeaways
Process improvement: Replaced an untracked, ad-hoc request process with a fully auditable workflow that has a clear approval trail and measurable turnaround time.
Security discipline: Applied least-privilege access control and validated it against multiple user roles rather than assuming it worked.
Change management: Demonstrated Update Set hygiene — the same configuration-migration discipline expected of a production ServiceNow admin.
Problem-solving under real constraints: Diagnosed a non-obvious permissions bug (Run As) and worked around a platform-level reporting limitation rather than stalling on it.
