# Dashboard Field Notes

This document explains the main fields and measures used in the Upper Midwest Fleet Safety & DOT Compliance Risk Dashboard.

## Main Tables

### dim_carrier_midwest

Carrier-level dimension table filtered to carriers physically based in ND, MN, SD, IA, and WI.

| Field | Description |
|---|---|
| DOT_NUMBER | FMCSA carrier identifier. |
| LEGAL_NAME | Legal name of the motor carrier. |
| DBA_NAME | Doing-business-as name, if available. |
| CARRIER_OPERATION | Carrier operation type listed in the FMCSA census file. |
| HM_FLAG | Indicates whether the carrier has hazardous materials activity. |
| PC_FLAG | Indicates whether the carrier has passenger carrier activity. |
| PHY_CITY | Physical city listed for the carrier. |
| PHY_STATE | Physical state listed for the carrier. Used as carrier home state in the dashboard. |
| PHY_ZIP | Physical ZIP code listed for the carrier. |
| NBR_POWER_UNIT | Number of power units listed in the FMCSA carrier census file. |
| DRIVER_TOTAL | Total drivers listed in the FMCSA carrier census file. |
| RECENT_MILEAGE | Recent mileage value listed in the carrier census file. |
| RECENT_MILEAGE_YEAR | Year associated with the recent mileage value. |

### fact_inspections_midwest

Inspection-level fact table filtered to inspections tied to Midwest-based carriers.

| Field | Description |
|---|---|
| Unique_ID | Unique inspection identifier. |
| Report_Number | Inspection report number. |
| Report_State | State where the inspection was reported. |
| DOT_Number | FMCSA carrier identifier linked to the carrier table. |
| Insp_Date | Inspection date. |
| OOS_Total | Total out-of-service indicator/count from the inspection file. |
| Driver_OOS_Total | Driver out-of-service total from the inspection file. |
| Vehicle_OOS_Total | Vehicle out-of-service total from the inspection file. |
| Unit_Type_Desc | Description of the inspected unit type. |
| BASIC_Viol | BASIC violation indicator/count from the inspection file. |
| Inspection_Year | Year extracted from inspection date. |
| Inspection_Month | Month number extracted from inspection date. |
| Inspection_Month_Name | Month name extracted from inspection date. |
| Inspection_Quarter | Quarter extracted from inspection date. |

### fact_violations_midwest

Violation-level fact table filtered to violations tied to Midwest-based inspections.

| Field | Description |
|---|---|
| Unique_ID | Inspection identifier linking violations back to inspections. |
| Insp_Date | Inspection date. |
| DOT_Number | FMCSA carrier identifier. |
| Viol_Code | Violation code. |
| BASIC_Desc | FMCSA BASIC category description. |
| OOS_Indicator | Indicates whether the violation was out-of-service. |
| Severity_Weight | FMCSA severity weight associated with the violation. |
| Time_Weight | Time weight associated with the violation. |
| Total_Severity_Wght | Total severity weight value. |
| Section_Desc | Description of the violation section/type. |
| Group_Desc | Violation group description. |
| Viol_Unit | Unit associated with the violation. |

### fact_crashes_midwest

Crash-level fact table used for crash analysis.

| Field | Description |
|---|---|
| Report_number | Crash report number. |
| DOT_Number | FMCSA carrier identifier. |
| Report_Date | Crash report date. |
| Report_State | State where the crash was reported. |
| Fatalities | Fatality count listed on the crash record. |
| Injuries | Injury count listed on the crash record. |
| Tow_Away | Indicates whether the crash involved a tow-away. |
| Crash_Year | Year extracted from crash report date. |
| Crash_Month | Month number extracted from crash report date. |
| Crash_Month_Name | Month name extracted from crash report date. |
| Crash_Quarter | Quarter extracted from crash report date. |

## Dashboard Measures

| Measure | Description |
|---|---|
| Total Carriers | Distinct count of carrier DOT numbers. |
| Total Inspections | Count of inspection records. |
| Total Violations | Count of violation records. |
| Total Crashes | Count of crash records. |
| OOS Violations | Count of violations where the OOS indicator is true. |
| OOS Violation Rate | OOS Violations divided by Total Violations. |
| Violations per Inspection | Total Violations divided by Total Inspections. |
| Inspections per Carrier | Total Inspections divided by Total Carriers. |
| Violations per Carrier | Total Violations divided by Total Carriers. |
| Crashes per 1,000 Carriers | Total Crashes divided by Total Carriers, multiplied by 1,000. |

## Notes

- Carrier home state is based on the physical state listed in the FMCSA motor carrier census file.
- Inspection and violation totals are linked to Midwest-based carriers by DOT number.
- Violation records are linked to inspection records by Unique_ID.
- Trend visuals exclude partial months where appropriate to avoid misleading month-to-month comparisons.
- This dashboard does not display official CSA/SMS percentile scores or final FMCSA safety ratings.
