# Transport Logistics & Safety Management System

This project is a Python-based simulation system designed to manage scheduling, safety verification, and real-time status updates for aviation and maritime logistics. The project consists of two main modules: 
**Pilot Scheduling** and **Shipping Voyage Management**.

This repository demonstrates proficiency in Python programming logic, CSV file I/O, `datetime` manipulation, and the application of mathematical algorithms for geospatial calculations.

# Project Structure

- Pilot.py: Aviation management module. Handles pilot schedules, check-in validation, and flight conflict detection based on coordinates.
- Shipping.py: Maritime management module. Manages captain voyages, dynamic schedule adjustments, and safety verification based on weather conditions.
- Data Files (Required): `pilot_data.csv`, `captain_data.csv`, `weather_data.csv`, `late_checkin.csv`.

# 1. Aviation Management (`Pilot.py`)
* Data Parsing: Parses semicolon-delimited (`;`) CSV files to build a pilot schedule database.
* Check-in System: 
    * Validates time input formats (`HH:MM:SS`).
    * Compares check-in times against scheduled start times to automatically flag tardiness.
    * Logging: Automatically records late pilot IDs into `late_checkin.csv` for tracking.
* Conflict Detection: 
    * Implements the **Haversine Formula** to calculate precise distances (in km) between two pilots based on their coordinates.
    * Logic: A conflict warning is triggered if two pilots have the same start time and are located within 500km of each other.

# 2. Maritime Management (`Shipping.py`)
* Voyage Time Management: 
    * Utilizes `datetime` and `timedelta` for complex time calculations.
    * Allows users to dynamically "increase" or "decrease" voyage duration, automatically recalculating the Estimated Time of Arrival (ETA).
* Safety Verification:
    * Cross-references weather data against both "Departure" and "Arrival" ports.
    * Safety Logic: Validates conditions against thresholds (Min Temp: 5°C, Max Wind Speed: 30 km/h). If conditions are unmet, the system issues a "Voyage Cannot Proceed" warning.

# Tech Stack & Implementation

* Core Modules: 
    * `csv`: Handles reading/writing of data with varying delimiters (`|` and `;`).
    * `datetime`: Manages time arithmetic and string parsing (`strptime`, `strftime`).
    * `math`: Utilizes trigonometric functions (`sin`, `cos`, `sqrt`, `atan2`, `radians`) for the geospatial algorithm.
