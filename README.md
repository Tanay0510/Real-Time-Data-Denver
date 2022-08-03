# Real-Time-Data-Denver

#### Data Source - https://www.rtd-denver.com/business-center/open-data/gtfs-developer-guide

#### The GTFS-realtime feeds have the following format:

**Header**

- gtfs_realtime_version: “1.0” (TripUpdate, VehiclePositions) or “2.0” (Alerts)
- incrementality: FULL_DATASET
- timestamp

**Entity**

- id
- alert. Included if alert entity is provided. See alert below.
- trip_update. Included if trip_update entity is provided. See trip_update below.
- vehicle. Included if vehicle entity is provided. See vehicle below.

**Alert**

- active_period
  - start
  - end (optional)
- informed_entity
  - agency_id
  - route_id
  - route_type
  - stop_id
- stop_time_update
  - stop_sequence
  - stop_id
  - arrival
    - time. see additional information
  - departure
    - time. see additional information
- schedule_relationship. SCHEDULED if stop is a scheduled stop, SKIPPED if stop is skipped.
- cause
- effect
- header_text
  - translation
  - text
  - language
- description_text
  - translation
    - text
    - language
    
    
**trip_update**

- trip
  - trip_id
  - route_id
  - direction_id
  - schedule_relationship. SCHEDULED if trip is running as scheduled, ADDED if trip is an added trip, or CANCELED if trip has been canceled.
- vehicle
  - id
  - label
- stop_time_update
  - stop_sequence
  - stop_id
  - arrival
    - time. see additional information
  - departure
    - time. see additional information
  - schedule_relationship. SCHEDULED if stop is a scheduled stop, SKIPPED if stop is skipped.
- timestamp. the latest time this vehicle’s position was recorded.


**vehicle**

- trip
  - trip_id
  - route_id
  - direction_id
  - schedule_relationship. SCHEDULED if trip is running as scheduled, ADDED if trip is an added trip, or CANCELED if trip has been canceled.
- vehicle
  - id
  - label
- position
  - latitude
  - longitude
  - bearing
- stop_id
- current_status. Will have either a 0, 1, or 2.
  - 0 = INCOMING_AT
  - 1 = STOPPED_AT - if vehicle is stopped at the stop_id
  - 2 = IN_TRANSIT_TO - if vehicle is on its way to the stop_id
- timestamp

