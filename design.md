# Covid Vaccination Availability Notification App

## Requirement
Develop a web application which can take in users vaccination location preferences and notify the user whenever vaccination slots becomes available in those location. Notification can be simple desktop notification.

## Design
### Source of information: Cowin public api
  - Reference: https://apisetu.gov.in/public/marketplace/api/cowin#/
  - Endpoint: https://cdn-api.co-vin.in/api
### User flow
  - User browses to home page.
  - User is asked for state name 
    - A drop down menu [State list can be fetched using this api - /v2/admin/location/states]
  - Once user selects a state, he is given a district list
    - Again a drop down menu [District list can be fetched using the api - /v2/admin/location/districts/{state_id}]
    - Since we are doing it for our friends and family usage, we can hard the state (as Kerala) and district list as well 
  - User is asked for his age/age group
  - User is asked whether he wants it for first dosage or second dosage
  - User is provided with the current availability status if any and message that he will be notified if vaccine becomes available for next 7 days
    - Center
    - Vaccine name
    - Cost
### Notification Logic
  - API: /v2/appointment/sessions/public/calendarByDistrict
  - Polling frequency: 5 seconds  
  - Logic: Get the vaccine availability by calling the above given API every 5 seconds and notify the user if it is available anywhere according to his preference.
### General Directions
  - We want this up and running asap, so minimum ui and styling.
