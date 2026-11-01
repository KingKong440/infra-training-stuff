# GOD-90: Day 14 | Task 2 | Snowflake account creation and load CSV content

- **Jira:** https://sudhaharrajeshkannan.atlassian.net/browse/GOD-90
- **Status:** In Review
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** —
- **Reporter:** Sujit Kannan
- **Created:** 2026-10-31T15:38:51.187Z
- **Updated:** 2026-11-01T17:04:18.062Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

1.) Create a new Enterprise snowflake account.

2.) Create the following in-order: Database, Schema, Warehouse, Table, File Format, Stage

3.) Upload CSV dataset file by clicking on: Catalog Tab → Explorer → Databases → <YOUR_DB_NAME> → <YOUR_SCHEMA_NAME> → Stages → <YOUR_STAGE_NAME> → Upload Files

4.) Transfer the contents of csv file from Snowflake’s stage to Snowflake’s table using COPY command. Declare ON_ERROR = 'ABORT_STATEMENT' to avoid partial-data ingestion.

5.) Verify data load operation by performing SQL commands such as SELECT count(*) to query about how many rows does the table holds currently, SELECT * to view all rows of the Snowflake’s table.

6.) DROP database and warehouse after performing all the operations.

## Attachments

- [Snowflake_Task.pdf](attachments/Snowflake_Task.pdf)
