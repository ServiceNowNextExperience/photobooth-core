# Photobooth Core

The Photobooth Core application containing the tables and flows to support the photobooth application.

To open you may use App Engine Studio > Photobooth Core

**PRO TIP** Be sure to "Pull from repository" each time you start dev and it will make your life easier and you won't be having to stash all your changes everytime I modify this readme before checking in.

## Used By

This application is not dependent on other apps but it is used by the [Photobooth App](https://github.com/ServiceNowNextExperience/photobooth).

If you install that application you can use it to exercise this code.

## Components

### Tables [STARTED]

1. Photobooth
   - Unique record for each Photobooth installation (e.g. if there are two booths at a single event).
2. Snapshot
   - Contains images from each snapshot made.
   - To be monitored by the flow to process the requests.
   - Images are an array containing a bitmap of SRGB colors (e.g. [172, 186, 299...]) and will be several kilobytes in size, so need to ensure the best field type to store this.
3. Request
   - New record is inserted each time a request is made to start a snapshot session. This may originate with a 3rd party API call, but it will notify the Photobooth App to initiate the taking of a new Snapshot and contain the appropriate email address to send the results to.
   - "State" flag is used with AMB Record Watcher to initiate a snapshot when state changes to "Ready" (this is for testing only and may be removed if we do not want to use this pattern)

### API [STARTED]

Receives the imageData (Uint8ClampedArray) from the camera and saves it in the Snapshot table for later processing by the Flow.

NOTE: Created new Scripted Rest API /photobooth/snapshot.  It currently just logs the request.

### Flow [STARTED]

Process a new Snapshot record and send an email with the image to the email specified in the associated request.

NOTE: Empty flow created.
