# SCD2_DimensionUpdate_FF_To_ORCLDB
Purpose:
This mapping is designed to update existing dimensions and insert new dimension records from a flat file source into an Oracle database. It utilizes SCD Type 2 to track changes in dimension attributes over time.

Components:

Source: Flat file containing dimension data.
Transformations:
Expression: Calculates the SCD Type 2 indicator (e.g., 'Insert', 'Update', 'Delete').
Lookup: Looks up existing dimension records based on a unique identifier.
Router: Routes data to different update strategies based on the SCD indicator.
Update Strategy: Transforms data for different SCD types.
Sequence Generator: Generates unique identifiers for new records.
Target: Oracle database table for the dimension.

Workflow:

1. Source: The flat file is read, and data is extracted.
2. Expression: The SCD indicator is calculated based on the source data and existing dimension records.
3. Lookup: The source data is compared to existing dimension records to identify updates or inserts.
4. Router: Data is routed to the appropriate update strategy based on the SCD indicator.
5. Update Strategy: The data is transformed and loaded into the target table according to the SCD Type 2 rules.

Requirements:

Source File: Ensured the source file has the necessary columns for the dimension (e.g., dimension key, attributes, effective start date, effective end date).
Target Table: The target table have columns for the dimension key, attributes and versioning to differentiate new and old records.
Sequence Generator: Configured the Sequence Generator to generate unique identifiers for new records.
