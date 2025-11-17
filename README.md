This repository showcases the complete Salesforce configuration and customization work done to build a fully functional Travel Approval App. The app centralizes travel requests, enforces approval processes, improves visibility, and replaces outdated manual spreadsheet-based workflows.

📘 Project Introduction

The company required a custom Travel Approval App to solve challenges caused by their legacy email-and-spreadsheet approach to handling travel requests. The lack of a centralized system resulted in:

No visibility into travel requests across units

Missing or inconsistent approval steps

No structured reporting or trend analysis

Business Requirements

The new system needed to ensure:

Employees must submit future travel requests electronically

Each request includes estimated travel expenses (airfare, hotels, rental cars, etc.)

All requests require manager approval, and travel coordinator approval for out-of-state trips

Managers must access dashboards and reports for travel KPIs

Both managers and employees must use the app on desktop and mobile

Final Outcome

A complete Travel Approval App prototype was built that:

✔ Centralizes travel requests
✔ Automates multi-level approvals
✔ Enables reporting & dashboards
✔ Supports mobile access
✔ Improves transparency and accountability

✨ Key Features Implemented
1. Customized & Configured the Travel App

Created a custom Lightning App named Travel App

Added navigation items for Travel Approvals, Departments, Reports, Dashboards, etc.

Ensured the app is optimized for mobile & Lightning Experience

🗂️ Data Model Configuration
2. Custom Objects
Department

Stores department-level details:

Department Name

Cost Center Code

Travel Approval

Captures all travel request details:

Purpose of Trip

Travel Destination

Trip Start/End Dates

Out-of-State indicator

Status

Total Estimated Expenses

Expense Item (Third Object)

Created as a Master-Detail child of Travel Approval to store:

Airfare cost

Hotel cost

Rental car cost

Other expenses

Total Amount

Each Travel Approval record displays associated Expense Items in its related list.

🧱 Custom Fields
Travel Approval Fields

Created fields such as:

Purpose of Trip (Text Area)

Status (Picklist)

Out-of-State (Checkbox)

Destination State (Picklist)

Trip Start Date (Date)

Trip End Date (Date)

Total Estimated Cost (Roll-Up Summary from Expense Items)

Expense Item Fields

Expense Type (Picklist)

Amount (Currency)

Description

📥 Data Import

Imported 16 Department records using Data Import Wizard

Ensured sample data was available for testing reports and approvals

👤 User & Page Setup
Created a Testing User

Added a user to simulate the Salesforce Administrator role

Used for testing approvals and record access

Search Layout

Customized Search Layouts to show relevant fields in search results

Compact Layout

Created a compact layout for quick glance of key fields:

Purpose of Trip

Status

Trip Dates

List View

Created a list view: Out-of-State Trips

Filtered based on Out-of-State = TRUE

Visible to all users

Page Layout

Designed user-friendly page layouts for both Travel Approval and Expense Items

Grouped fields logically for easy record creation and updates

🔔 Feed Tracking

Enabled feed tracking on important fields such as:

Status

Destination

Trip End/Start Dates

Out-of-State

This ensures transparent audit activity through Chatter.

✔️ Validation Rules

Created a validation rule to ensure:

Trip End Date must be greater than Trip Start Date

Prevents invalid travel requests and improves data quality.

📈 Roll-Up Summary

Added a Roll-Up Summary field to Travel Approval to calculate:

Total Expenses = SUM(Expense Item Amounts)

⚙️ Flow Automation
Record-Triggered Flow

This flow runs on create/update of Travel Approval records:

Checks whether the trip is out-of-state

Uses a Decision element:

Outcome 1: Out-of-State

Outcome 2: In-State

Automatically updates fields depending on destination and checkbox selection

📝 Approval Process
Step 1 – Manager Approval

Criteria:

Total Expenses > 0

All travel approval requests must be approved by the employee's direct manager.

Step 2 – Travel Coordinator Approval

Criteria:

Out-of-State = TRUE

For out-of-state travel, the Travel Coordinator must approve.
(You assigned yourself as the Travel Coordinator during testing.)

🔄 Approval Actions
Final Approval Action

Field Update: Set Status = Approved

Final Rejection Action

Field Update: Set Status = Rejected

📧 Email Approval Response

Enabled email response for approvals:

Approvers receive an email with a link to the record

They can approve by replying with APPROVE, YES, REJECT, or NO

📊 Reports
Report 1: Travel Requests by Department

Steps included:

Selected Travel Approval report type

Added fields: Status, Out-of-State, Destination State, Start/End Dates

Grouped by Department

Saved in Public Report Folder

Report 2: Travel Requests by Month

Grouped Trip End Date by Calendar Month

Added Out-of-State field to grouping

Saved in Public Report Folder

📉 Dashboard

Created a dashboard named Travel Requests Dashboard with:

Component 1

Report: Travel Requests by Department

Visualization: Bar Chart

Y-Axis: Department

X-Axis: Record Count

Component 2

Report: Travel Requests by Month

Visualization: Stacked Vertical Bar Chart

Sorted by Trip End Date

The dashboard provides insightful trends for travel managers and coordinators.

🚀 Summary

This Salesforce Admin project demonstrates capabilities in:

App customization

Object modeling

Process automation

Approval workflows
Data management

Reporting & dashboard building

Security & layout optimization

The Travel Approval App is now a powerful prototype for handling organization-wide travel management with complete transparency and streamlined approvals.
