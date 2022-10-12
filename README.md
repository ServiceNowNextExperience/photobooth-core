# Photobooth Core

The Photobooth Core application containing the tables and flows to support the photobooth application.

## Used By

This application is not dependent on other apps but it is used by the [Photobooth App](https://github.com/ServiceNowNextExperience/photobooth).

If you install that application you can use it to exercise this code.

## Components

### Tables [NOT YET STARTED]

1. Photobooth
   - Unique record for each Photobooth installation (e.g. if there are two booths at a single event).
2. Snapshot
   - Contains images from each snapshot made.
   - To be monitored by the flow to process the requests.
   - Images are an array containing a bitmap of SRGB colors (e.g. [172, 186, 299...]) and will be several kilobytes in size, so need to ensure the best field type to store this.
3. Request
   - New record is inserted each time a request is made to start a snapshot session. This may originate with a 3rd party API call, but it will notify the Photobooth App to initiate the taking of a new Snapshot and contain the appropriate email address to send the results to.

### API [STARTED]

Receives the imageData (Uint8ClampedArray) from the camera and saves it in the Snapshot table for later processing by the Flow.

NOTE: Created new Scripted Rest API /photobooth/snapshot.  It currently just logs the request.

### Flow [NOT YET STARTED]

??? Process a new Snapshot record and send an email with the image to the email specified in the associated request.
