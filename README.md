🏥 Medical Diagnosis Center – ServiceNow
📌 Project Overview

The Medical Diagnosis Center is a ServiceNow-based digital diagnostic test management system developed using the ServiceNow Platform and Service Portal.

The application is designed to digitize and streamline medical diagnostic-center operations such as patient registration, diagnostic test selection, appointment booking, approval management, report generation, email notifications, role-based access control, and administrative reporting.

The system provides a centralized and user-friendly platform for patients, laboratory staff, receptionists, doctors, and administrators.

🎯 Project Objective

The main objective of this project is to provide a secure, automated, and user-friendly platform for managing diagnostic-center operations.

Key Objectives
📝 Digitize patient registration and appointment booking
🧪 Display available diagnostic tests
📅 Manage appointment dates and time slots
🔄 Automate appointment approval and status management
📧 Send automated email notifications
📄 Generate and manage diagnostic reports
💰 Support payment and refund processing as a phase-based feature
🔐 Implement role-based access using ACLs
📊 Provide dashboards and reports for management
⚡ Reduce manual paperwork and duplicate data entry
🏥 Improve coordination between patients, receptionists, laboratory technicians, doctors, and administrators
🌱 Support digital-first healthcare operations
🏗️ System Architecture

The application is built around the following ServiceNow components:

                    ┌─────────────────────────┐
                    │     Patients / Users    │
                    └────────────┬────────────┘
                                 │
                                 ▼
              ┌────────────────────────────────────┐
              │         ServiceNow Service Portal   │
              │                                    │
              │  📄 Pages                          │
              │  • Home Page                       │
              │  • Test Catalog Page               │
              │  • Book Appointment Page           │
              │  • My Appointments Page            │
              │  • Lab Reports Page                │
              │  • Payment Page                    │
              │  • Admin Dashboard Page            │
              │                                    │
              │  🧩 Widgets                        │
              │  • Medical Test Catalog Widget     │
              │  • Appointment Booking Widget      │
              │  • My Appointments Widget          │
              │  • Lab Reports Widget              │
              └──────────────────┬─────────────────┘
                                 │
                                 ▼
                ┌────────────────────────────────┐
                │     ServiceNow Application      │
                │                                │
                │  📋 Custom Tables              │
                │  • Patient Table                │
                │  • Diagnostic Test Table        │
                │  • Appointment Table            │
                │  • Report Table                 │
                │  • Payment Table                │
                └───────────────┬────────────────┘
                                │
             ┌──────────────────┼──────────────────┐
             ▼                  ▼                  ▼
       Business Rules      Notifications       ACL Security
             │                  │                  │
             ▼                  ▼                  ▼
        Automation          Email Alerts       Role-Based
                                                 Access
             │                  │
             └──────────┬───────┘
                        ▼
              ┌─────────────────────┐
              │ Reports & Dashboards │
              │                     │
              │ • Health Reports    │
              │   Dashboard         │
              │ • Appointments      │
              │   Reports           │
              └─────────────────────┘
📄 ServiceNow Pages

The Service Portal contains the following pages:

Page	Purpose
🏠 Home Page	Main landing page for the Diagnostic Center
🧪 Test Catalog Page	Displays available diagnostic tests
📝 Book Appointment Page	Allows patients to book diagnostic tests
📊 My Appointments Page	Displays patient appointment details and status
📄 Lab Reports Page	Allows patients to view/download diagnostic reports
💳 Payment Page	Handles payment-related functionality as a phase-based feature
📈 Admin Dashboard Page	Provides administrative reports and analytics
🧩 ServiceNow Widgets

Custom Service Portal widgets provide interactive functionality.

1. 🧪 Medical Test Catalog Widget

The Medical Test Catalog Widget displays available diagnostic tests.

Test Information
Diagnostic Test Name
Test Code
Test Category
Description
Price
Duration
Active Status

Examples of diagnostic tests include:

Blood Test
X-Ray
MRI
CT Scan
ECG
Thyroid Function Test
Liver Function Test
Kidney Function Test
2. 📝 Appointment Booking Widget

The Appointment Booking Widget allows patients to:

Select a diagnostic test
Select an appointment date
Select a time slot
Enter patient details
Submit an appointment request
Validate mandatory information
Check booking availability
Patient Details
Full Name
Age
Gender
Contact Number
Email Address
3. 📊 My Appointments Widget

The My Appointments Widget allows patients to:

View appointments
Check appointment status
Check approval status
View appointment details
Cancel appointments where permitted
Reschedule appointments where configured
4. 📄 Lab Reports Widget

The Lab Reports Widget allows patients to:

View available reports
View report details
Access generated diagnostic reports
Download reports where configured
📋 Custom Tables

The application uses custom ServiceNow tables to store and manage application data.

Table	Purpose
Patient	Stores patient information
Diagnostic Test	Stores diagnostic test details
Appointment	Stores booking and appointment information
Report	Stores diagnostic report information
Payment	Stores payment information
Data Relationships
Patient
   │
   └────── Appointment
              │
              ├────── Diagnostic Test
              │
              ├────── Payment
              │
              └────── Report
📅 Appointment Booking and Validation

The system is designed to provide accurate scheduling and avoid appointment conflicts.

Booking Validation Features
Real-time validation of available test slots
Prevention of duplicate bookings
Prevention of overlapping appointments
Equipment conflict prevention
Technician conflict prevention
Capacity control per time slot
Maximum number of tests per patient per day
Advance booking limits
Cut-off time restrictions
Mandatory-field validation
Example

A time slot can be configured with a maximum number of patients per hour. Once the capacity is reached, additional bookings for that slot can be prevented.

This improves appointment management and laboratory resource utilization.

🔄 Approval and Status Workflow

The appointment lifecycle is managed through different stages.

Requested
    ↓
Pending Approval
    ↓
Confirmed
    ↓
Sample Collected
    ↓
Processing
    ↓
Completed
    ↓
Report Available

Appointments can also be moved to:

Cancelled
Workflow Features
Optional Lab Manager approval
Approval for high-value or specialized tests
Automatic status updates
Patient notifications
Laboratory technician notifications
Administrator notifications
Escalation alerts for delayed reports
Audit trail tracking
💳 Payment Handling

Payment functionality is designed as a phase-based feature.

When enabled, the system can support:

Automatic fee calculation
Test-type based pricing
Normal / Express urgency
Home collection charges
Online payment
Payment status tracking
Digital invoice generation
Payment receipts
Transaction history
Cancellation and refund processing
Payment Status
Paid
Pending
Failed
💰 Cancellation and Refund

The cancellation Business Rule applies a 10% deduction from the total amount.

Example
Total Amount = ₹500

10% Deduction = ₹50

Refund Amount = ₹500 - ₹50

Refund Amount = ₹450

The refund amount is automatically populated when the configured cancellation condition is satisfied.

📧 Email Notifications

Email notifications are configured to notify customers about important appointment and diagnostic-report events.

Activity 1: Approval Notification
Configuration
Name:
Approval Notifications

Table:
x_1883080_medica_0_appointment

When to Send:
Record Inserted or Updated

Condition:
Approval Status changes to Approved

Active:
True

This notification is used to inform customers when their appointment is approved.

Activity 2: Report Notification
Configuration
Name:
reportsNotifications

Table:
x_1883080_medica_0_report_table

When to Send:
Record Inserted

Condition:
Report number is Not Empty

Active:
True

This notification informs customers when their diagnostic report becomes available.

Additional Notification Scenarios
📧 Appointment booking confirmation
📧 Payment confirmation
📧 Approval notification
📧 Rejection notification
📧 Appointment reminder
📧 Report availability notification
📧 Cancellation confirmation
📧 Refund notification
⚙️ Business Rules and Automation

Business Rules are used to automate important diagnostic-center processes.

1. Auto Populate Refund Amount on Cancellation

Business Rule:

Auto Populate Refund Amount on Cancellation

Table:

x_1883080_medica_0_appointment

Execution:

Before Insert & Update
Functionality

When an appointment is cancelled:

Read the total amount.
Calculate the 10% deduction.
Calculate the remaining refund.
Store the refund amount in the appointment record.
2. Auto Create Report on Appointment Complete

When the appointment status changes to Completed, the system can automatically create a report if a report does not already exist.

Functionality
Check appointment status
Check whether a report already exists
Generate report number
Retrieve diagnostic test information
Generate findings
Create report record
Link report with appointment
Link report with patient
Record report date
Record verifier
Set report status
Report Lifecycle
Sample Collected
       ↓
Processing
       ↓
Completed
       ↓
Report Generated
       ↓
Report Available
3. Rejection Details Updation

When an appointment is rejected:

Rejection reason is populated
Approved By is cleared

When an appointment is approved:

Approval note is recorded
Approved By is populated
Rejection reason is cleared

This keeps approval and rejection information consistent.

🔐 Security and ACLs

The application uses Access Control Lists (ACLs) to control access to application data.

Security Features
Table-level access control
Field-level access control
Role-based access
Patient-specific record access
Appointment creation permissions
Laboratory report access restrictions
Administrative access restrictions
Impersonation testing
Debug Security Rules validation

Users can access the Service Portal functionality without being given unrestricted access to the underlying database tables.

📊 Reports and Dashboard

A management dashboard is configured to provide operational visibility.

Health Reports Dashboard
Dashboard Name:
Health Reports Dashboard

The dashboard can provide information related to:

Appointment activity
Appointment status
Approval status
Test activity
Operational performance
📈 Appointments Reports
Report Configuration
Report Name:
Appointments Reports

Data Source:
Table

Table:
x_1883080_medica_0_appointment

Type:
Bar Chart

Group By:
Status

Additional Group By:
Approval Status

Stack By:
Created, Approval Date

Aggregation:
Count

The generated report can be added to the Health Reports Dashboard.

🧪 Diagnostic Test Catalog

The application can contain diagnostic tests such as:

Test Name	Code	Category	Price	Duration
Complete Blood Count (CBC)	CBC-001	Blood Test	₹45	30 minutes
Lipid Profile	LIP-002	Blood Test	₹60	30 minutes
HbA1c (Diabetes)	HBA-003	Blood Test	₹70	30 minutes
Thyroid Function Test (TFT)	THY-004	Blood Test	₹95	30 minutes
Liver Function Test (LFT)	LFT-005	Blood Test	₹75	30 minutes
Kidney Function Test (KFT)	KFT-006	Blood Test	₹65	30 minutes
Urine Routine & Microscopy	UR-007	Blood Test*	₹25	20 minutes
Chest X-Ray	XRY-008	Blood Test*	₹80	15 minutes
ECG (Electrocardiogram)	ECG-009	Blood Test*	₹55	20 minutes
COVID-19 PCR Test	COV-010	Blood Test*	₹120	45 minutes
Vitamin D Test	VIT-011	Blood Test	₹55	30 minutes
Iron Studies	IRN-012	Blood Test	₹50	30 minutes

The category values marked with * preserve the configured source data.

👥 Stakeholder Mapping
1. Primary Stakeholders — Patients

Patients can:

Register and manage their profile
Browse diagnostic tests
Book diagnostic tests
Upload prescriptions where configured
Make online payments where enabled
View appointments
Download/view reports
Receive notifications
Cancel or reschedule appointments
2. Secondary Stakeholders — Management

Management and Lab Managers can:

Approve special or high-value tests
Monitor operational performance
View dashboards and analytics
Manage staff access and permissions
Handle escalations
Handle cancellations
3. Technical Stakeholders — System Administrator

The System Administrator is responsible for:

Configuring tables
Configuring forms and fields
Developing Service Portal pages
Developing Service Portal widgets
Creating Business Rules
Creating ACLs
Configuring notifications
Developing Flow Designer workflows
Creating reports and dashboards
Managing Update Sets
Managing application deployment
🛠️ Technologies Used
Technology	Usage
ServiceNow	Application platform
Service Portal	Patient-facing interface
JavaScript	ServiceNow scripting
GlideRecord	Server-side record operations
HTML	Portal UI
CSS	Portal styling
AngularJS	Service Portal client-side development
Business Rules	Automation
Flow Designer	Workflow automation
ACLs	Security
Reports & Dashboards	Analytics
Update Sets	Deployment
Git / GitHub	Version control
📋 Prerequisites

Before implementing the project, the following are required:

ServiceNow instance
Service Portal enabled
Access to Studio / Scoped Application Development
Appropriate ServiceNow roles
Access to Email Notifications
Access to Business Rules
Access to ACL configuration
Access to Reports & Dashboards
🚀 Implementation Roadmap
1. Requirement Gathering & Analysis
Conduct stakeholder meetings
Identify functional requirements
Identify non-functional requirements
Define appointment lifecycle
Define report-management process
Define booking rules
Define cancellation rules
Define payment rules

Deliverable: Requirement Specification Document

2. Service Portal UI Design
Design Service Portal interface
Create Home Page
Create Test Catalog Page
Create Book Appointment Page
Create My Appointments Page
Create Lab Reports Page
Create Payment Page
Create Admin Dashboard Page
Develop required widgets
Implement validations

Deliverable: Configured Service Portal

3. Availability and Booking Logic
Create custom tables
Configure relationships
Implement slot validation
Prevent overlapping bookings
Configure capacity limits
Configure advance booking limits
Configure cancellation restrictions

Deliverable: Functional Booking System

4. Approval Workflow

Configure the appointment lifecycle:

Requested
→ Pending Approval
→ Confirmed
→ Sample Collected
→ Processing
→ Completed
→ Report Available

Deliverable: Automated Workflow

5. Notification Configuration

Configure:

Booking confirmation
Approval notification
Rejection notification
Payment notification
Report notification
Cancellation notification
Appointment reminders

Deliverable: Automated Notification System

6. User Acceptance Testing

Test:

Booking logic
Slot validation
Approval workflow
Report generation
Notifications
Payment calculations
Refund calculations
ACL security
Dashboard functionality

Deliverable: UAT Sign-off

7. Production Deployment
Create Update Set
Capture application configurations
Commit Update Set
Transfer configuration
Validate production instance
Perform smoke testing
Monitor system logs
Monitor application performance

Deliverable: Live Medical Diagnosis Center Application

🧪 Testing and Validation

The following end-to-end test scenarios should be validated:

Test Case	Expected Result
Patient Registration	Patient record is created
Test Catalog	Diagnostic test information is displayed
Appointment Booking	Valid appointment is created
Duplicate Booking	Conflicting booking is prevented
Approval	Appointment approval is processed
Approval Email	Customer receives approval notification
Report Generation	Report is generated after completion
Report Email	Customer receives report notification
Cancellation	Appointment is cancelled
Refund	Refund amount reflects configured deduction
ACL Testing	Unauthorized access is restricted
Dashboard	Appointment report is displayed
📦 Deployment Using Update Sets

The application configurations can be migrated using ServiceNow Update Sets.

Deployment Process
Development
     ↓
Configuration
     ↓
Testing
     ↓
Update Set
     ↓
Commit
     ↓
Transfer
     ↓
Production
     ↓
Smoke Testing
     ↓
Go-Live

After deployment, validate:

Service Portal
Pages
Widgets
Tables
Business Rules
Notifications
ACLs
Reports
Dashboards
📁 Recommended GitHub Repository Structure
Medical-Diagnosis-Center/
│
├── README.md
│
├── ServiceNow/
│   ├── Tables/
│   ├── Service-Portal/
│   ├── Widgets/
│   ├── Business-Rules/
│   ├── ACLs/
│   ├── Notifications/
│   ├── Reports/
│   ├── Dashboards/
│   └── Update-Sets/
│
└── Documentation/
    └── Project-Documentation.docx
🔮 Future Enhancements

The following features can be implemented in future phases:

💳 Online payment gateway integration
🧾 Digital invoice generation
🏠 Home sample collection
📱 SMS notifications
🔔 Automated appointment reminders
📊 Advanced Performance Analytics
🧑‍🔬 Equipment and technician allocation
🔄 Automated appointment rescheduling
📱 Mobile application integration
🤖 AI-assisted diagnostic insights
🌱 Resource Optimization and Sustainability

The system promotes efficient and sustainable diagnostic-center operations by:

Reducing paper-based records
Reducing manual registers
Optimizing laboratory equipment usage
Improving staff coordination
Centralizing medical records
Reducing unnecessary physical visits
Supporting digital report delivery
Improving resource planning through dashboards
🎯 Final Project Outcome

The Medical Diagnosis Center – ServiceNow project provides a centralized, secure, automated, and user-friendly solution for diagnostic-center management.

The application combines:

Service Portal
      +
Custom Tables
      +
Widgets
      +
Business Rules
      +
Email Notifications
      +
ACL Security
      +
Reports & Dashboards
      +
Automation
      +
Update Sets

This provides an effective digital platform for managing patients, diagnostic tests, appointments, reports, notifications, security, and administrative operations.

⭐ Project Highlights
🏥 ServiceNow-based Healthcare Application
🌐 Custom Service Portal
🧩 Custom Service Portal Widgets
📝 Online Appointment Booking
🧪 Diagnostic Test Catalog
📊 My Appointments
📄 Digital Lab Reports
📧 Automated Email Notifications
🔄 Appointment Approval Workflow
⚙️ Business Rule Automation
💰 Cancellation & Refund Automation
🔐 Role-Based ACL Security
📈 Reports & Dashboards
💳 Phase-Based Payment Support
🚀 Update Set-Based Deployment
