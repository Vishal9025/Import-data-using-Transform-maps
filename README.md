# Import-data-using-Transform-maps
8 phases.

# Project Title

## **Import Data Using Transform Maps in ServiceNow**

### Project Overview

The objective of this project is to import data from an external source, such as an Excel or CSV file, into **ServiceNow** using **Import Sets and Transform Maps**.

A Transform Map is used to define how the imported data should be mapped from the Import Set table to the target ServiceNow table. It can also be used to transform, validate, or modify data during the import process.

---

# 1. Brainstorming & Ideation Phase

### Problem Identification

Organizations often receive large amounts of data from external sources such as Excel files, CSV files, or other systems. Manually entering this data into ServiceNow is time-consuming and can lead to errors.

### Proposed Idea

Develop a ServiceNow data-import process that allows users to:

* Upload data from a CSV/Excel file.
* Store the imported data in an Import Set table.
* Map source fields to the appropriate target-table fields.
* Transform and validate the data.
* Automatically insert or update records in the target table.
* Reduce manual data entry and improve data accuracy.

### Proposed Solution

Use the following ServiceNow components:

**Data File → Import Set → Transform Map → Target Table → Imported Records**

### Expected Benefits

* Reduces manual data entry.
* Saves time when importing large datasets.
* Improves data consistency.
* Provides a repeatable import process.
* Allows data validation and transformation.
* Supports inserting new records and updating existing records.

---

# 2. Requirement Analysis Phase

### Functional Requirements

The system should:

1. Allow users/admins to upload a CSV file.
2. Create or use an appropriate Import Set table.
3. Import source data into the Import Set table.
4. Create a Transform Map.
5. Map source fields to target-table fields.
6. Define a **Coalesce** field where required.
7. Transform the source data into the required target format.
8. Insert new records into the target table.
9. Update existing records when the matching/coalesce value already exists.
10. Provide import logs and error information.

### Non-Functional Requirements

* The import process should be reliable.
* Data should be validated before being inserted into the target table.
* The process should be easy for administrators to maintain.
* The system should handle multiple records efficiently.
* Appropriate user permissions should be maintained.

### Example Source Data

| Employee ID | Employee Name | Email                                         | Department |
| ----------- | ------------- | --------------------------------------------- | ---------- |
| E001        | Arun Kumar    | [arun@example.com](mailto:arun@example.com)   | IT         |
| E002        | Priya Sharma  | [priya@example.com](mailto:priya@example.com) | HR         |
| E003        | Rahul Kumar   | [rahul@example.com](mailto:rahul@example.com) | Finance    |

The above data can be provided as a CSV file and imported into ServiceNow.

---

# 3. Project Design Phase

### System Architecture

The proposed architecture is:

**CSV/Excel File**
↓
**Import Set**
↓
**Import Set Table**
↓
**Transform Map**
↓
**Field Mapping / Data Transformation**
↓
**Target Table**
↓
**Final Records**

### Main Components

#### 1. Import Set

The Import Set temporarily stores the data imported from the external file.

#### 2. Import Set Table

A staging table is created to hold the imported source data before transformation.

#### 3. Transform Map

The Transform Map defines how the fields from the Import Set table are mapped to the target table.

#### 4. Field Maps

Field Maps establish relationships between source fields and target fields.

Example:

| Source Field  | Target Field |
| ------------- | ------------ |
| Employee ID   | Employee ID  |
| Employee Name | Name         |
| Email         | Email        |
| Department    | Department   |

#### 5. Coalesce

A unique field, such as **Employee ID**, can be configured as a Coalesce field.

This allows ServiceNow to determine whether a record should be:

* **Inserted** as a new record, or
* **Updated** if a matching record already exists.

#### 6. Transform Scripts

Transform Scripts can be used when additional data processing is required before the data reaches the target table.

---

# 4. Project Planning Phase

### Project Activities

| Activity               | Description                                    |
| ---------------------- | ---------------------------------------------- |
| Requirement Collection | Identify the required source and target fields |
| Data Preparation       | Prepare the CSV/Excel source file              |
| Import Set Creation    | Create/configure the Import Set                |
| Transform Map Creation | Create the Transform Map                       |
| Field Mapping          | Map source fields to target fields             |
| Data Transformation    | Configure required transformations             |
| Testing                | Test valid and invalid records                 |
| Documentation          | Prepare project documentation                  |
| Demonstration          | Record the project demonstration               |

### Suggested Timeline

**Day 1:** Requirement analysis and project design

**Day 2:** Prepare source data and Import Set

**Day 3:** Create Transform Map and field mappings

**Day 4:** Configure transformation and Coalesce

**Day 5:** Test the import process

**Day 6:** Prepare documentation

**Day 7:** Record the demonstration video

---

# 5. Project Development Phase

### Step 1 – Prepare the Source File

Create a CSV file containing the required data.

Example:

```text
Employee ID,Employee Name,Email,Department
E001,Arun Kumar,arun@example.com,IT
E002,Priya Sharma,priya@example.com,HR
E003,Rahul Kumar,rahul@example.com,Finance
```

### Step 2 – Create/Configure the Import Set

Upload the CSV file into ServiceNow through the appropriate Import Set functionality.

The imported records will initially be stored in the Import Set table.

### Step 3 – Create the Transform Map

Create a Transform Map between:

**Import Set Table → Target Table**

Configure:

* Source table
* Target table
* Transform Map name
* Active status

### Step 4 – Configure Field Maps

Map each source field to its corresponding target field.

Example:

```text
Employee ID       → Employee ID
Employee Name     → Name
Email             → Email
Department        → Department
```

### Step 5 – Configure Coalesce

Set **Employee ID** as the Coalesce field if it uniquely identifies an employee.

This helps ServiceNow identify existing records during the transformation.

### Step 6 – Add Transformation Logic

If necessary, use Transform Scripts to:

* Validate data.
* Modify field values.
* Convert data formats.
* Handle missing values.
* Apply business rules during transformation.

### Step 7 – Run the Transform

Execute the transformation and verify that the source data is correctly transferred to the target table.

---

# 6. Project Testing Phase

Testing should verify that the Transform Map correctly handles different types of data.

### Test Case 1 – Valid Data

**Input:** Complete and correctly formatted records.

**Expected Result:** Records should be successfully inserted into the target table.

### Test Case 2 – Existing Record

**Input:** A record with an Employee ID that already exists.

**Expected Result:** The existing record should be updated instead of creating a duplicate, when Coalesce is configured appropriately.

### Test Case 3 – New Record

**Input:** A new Employee ID.

**Expected Result:** A new record should be created.

### Test Case 4 – Missing Data

**Input:** A record with a required field missing.

**Expected Result:** The record should be handled according to the configured validation/transformation logic.

### Test Case 5 – Invalid Data

**Input:** Incorrect or invalid field values.

**Expected Result:** The system should identify or handle the invalid data appropriately.

### Testing Documentation

Maintain a table such as:

| Test Case | Input                | Expected Result     | Actual Result      | Status |
| --------- | -------------------- | ------------------- | ------------------ | ------ |
| TC01      | Valid record         | Record inserted     | Record inserted    | Pass   |
| TC02      | Existing Employee ID | Record updated      | Record updated     | Pass   |
| TC03      | New Employee ID      | New record created  | New record created | Pass   |
| TC04      | Missing field        | Validation/handling | As expected        | Pass   |
| TC05      | Invalid data         | Error/handling      | As expected        | Pass   |

---

# 7. Project Documentation Phase

Prepare the following documents for the project:

### 1. Project Introduction

Explain what the project is and why data import is required.

### 2. Problem Statement

Explain the problems associated with manually entering large amounts of external data into ServiceNow.

### 3. Objectives

* Automate data import.
* Reduce manual effort.
* Improve data accuracy.
* Avoid duplicate records.
* Provide a structured data transformation process.

### 4. Technologies Used

* **ServiceNow**
* **Import Sets**
* **Transform Maps**
* **Import Set Tables**
* **Field Maps**
* **Coalesce**
* **Transform Scripts**, if required
* **CSV/Excel** for source data

### 5. System Architecture

Include the workflow:

**Source File → Import Set → Transform Map → Target Table → Final Records**

### 6. Configuration Screenshots

Include screenshots of:

* Source CSV file
* Import Set
* Import Set Table
* Transform Map
* Field Maps
* Coalesce configuration
* Transform execution
* Imported records
* Import logs/results

### 7. Testing Results

Include all test cases and their results.

### 8. Conclusion

Explain how the project successfully imports and transforms external data into ServiceNow while reducing manual work and improving data consistency.

---

# 8. Project Demonstration Phase

The final demonstration video should clearly explain the complete project.

### Recommended Demo Flow

**1. Introduction**

Say the project name:

> “Our project is Import Data Using Transform Maps in ServiceNow.”

**2. Explain the Purpose**

Explain that the project is designed to import data from an external CSV/Excel file into ServiceNow and transform it into the required target-table format.

**3. Explain the Components**

Show:

* Source CSV file
* Import Set
* Import Set Table
* Transform Map
* Field Maps
* Coalesce
* Target Table

**4. Demonstrate the Working Process**

Show the complete process:

**Upload File → Import Data → Configure Transform Map → Map Fields → Transform Data → Verify Target Records**

**5. Demonstrate New Record Creation**

Show how a new source record is imported into the target table.

**6. Demonstrate Record Update**

Use an existing unique value, such as Employee ID, to demonstrate how Coalesce can identify an existing record and update it rather than creating a duplicate.

**7. Show Final Output**

Open the target table and show the successfully imported/transformed records.

**8. Conclusion**

Explain the benefits:

* Faster data import
* Reduced manual effort
* Better data consistency
* Reduced duplicate records
* Reusable and manageable import process
