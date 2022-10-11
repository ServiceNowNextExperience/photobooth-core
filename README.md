# Photobooth Core

The Photobooth Core application containing the tables and flows to support the photobooth application.

## Used By

This application is not dependent on other apps but it is used by the [Photobooth App](https://github.com/ServiceNowNextExperience/photobooth).

If you install that application you can use it to exercise this code.

## Components

### Tables [NOT YET STARTED]

1. Photobooth: Unique record for each Photobooth installation (e.g. if there are two at a single event).
2. Snapshot: Contains each individual snapshot made, to be monitored by the flow to process the requests.
3. Request: New record is inserted each time a request is made to start a snapshot session. This may originate with a 3rd party API call, but it will notify the Photobooth App to initiate the taking of a new Snapshot and contain the appropriate email address to send the results to.

### API [NOT YET STARTED]

Receives the imageData (Uint8ClampedArray) from the camera and saves it in the Snapshot table for later processing by the Flow.

GraphQL?

REST?

### Flow [NOT YET STARTED]

??? Process a new Snapshot record and send an email with the image to the email specified in the associated request.
