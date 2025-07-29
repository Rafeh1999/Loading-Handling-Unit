📦 Description – Handling Unit & Loading Unit Tracking in Sorting Operations (ZLXH Site)
This Splunk SPL query tracks and correlates handling units (HUs) and loading units (LUs) processed at the ZLXH site. The main goal is to provide full visibility of package movement, including scanning, sorting, and LU creation events, to support operational analytics and exception tracking.

The query performs the following:

Extracts and normalizes structured fields from JSON message logs across two indexes: uds_equipment and uds_application.

Filters logs where the function starts with validate or is newconscreated, and events are either SendMessage or ReceiveMessage.

Focuses on Direct Handling (DH) areas by matching with an external sort_area_type.csv lookup table.

Retrieves key package identifiers and metadata including:

loading_unit, handling_unit, tracking_number

scan_date_time, sort_plan, sort_rule, origin, destination

Joins historical LU creation data to enrich each HU scan with the related LU’s sorting configuration.

Cleans and deduplicates the data for a tidy output, showing HU-LU relationships and the times they were scanned.

Filters out noise (invalid HUs or empty values) to improve reliability of reporting.

The final dataset gives a clear view of how packages are associated with containers and sorting logic, making it highly useful for:

Dashboards monitoring sorting performance

Validating correct package handling

Investigating missing or misrouted units

Data feeds to support machine learning or automation efforts
