La Poste Tracking API - Node.js
================================
Use Node.js to track La Poste shipments with La Poste Tracking API.

Features
--------
- Real-time La Poste tracking.
- Batch La Poste tracking.
- Other features to manage your La Poste tracking.

Installation
------------

Installation is easy:

    $ npm install trackingmore-sdk-nodejs

Quick Start
----------
Get the API key:

To use this API, you need to generate your API key.

- <a href="https://admin.trackingmore.com/developer/apikey" target="_blank" rel="noreferrer">
  Click here</a> to access TrackingMore admin.

- Go to the "Developer" section.

- Click "Generate API Key".

- Give a name to your API key, and click "Save" .


Then, start to track your La Poste shipments.

Usage
----------

Create a tracking (Real-time tracking):

      const TrackingMore = require('trackingmore-sdk-nodejs')
      const key = 'your api key'
      const trackingmore = new TrackingMore(key)
      
      const params = {
        'tracking_number': '8J01608628504',
        'courier_code': 'laposte',
        'order_number': '',
        'customer_name': '',
        'title': '',
        'language': 'en',
        'note': 'test Order'
      }
      trackingmore.trackings.createTracking(params)
        .then(result => console.log(result))
        .catch(e => console.log(e))


Create trackings (Max. 40 tracking numbers create in one call):

    const TrackingMore = require('trackingmore-sdk-nodejs')
    const key = 'your api key'
    const trackingmore = new TrackingMore(key)
    
    const params = [{
        'tracking_number': 'CB141372389FR',
        'courier_code':'laposte'
    },{
      'tracking_number': 'XU007478444TS',
      'courier_code':'laposte'
    }]
    trackingmore.trackings.batchCreateTrackings(params)
      .then(result => console.log(result))
      .catch(e => console.log(e))



Get status of the shipment:

    const TrackingMore = require('trackingmore-sdk-nodejs')
    const key = 'your api key'
    const trackingmore = new TrackingMore(key)

    # Perform queries based on various conditions
    const params = [{
        'tracking_number': 'XU007478444TS',
        'courier_code':'laposte'
    },{
      'tracking_number': 'CB141372389FR',
      'courier_code':'laposte'
    }]
    trackingmore.trackings.batchCreateTrackings(params)
      .then(result => console.log(result))
      .catch(e => console.log(e))


Update a tracking by ID:

    const TrackingMore = require('trackingmore-sdk-nodejs')
    const key = 'your api key'
    const trackingmore = new TrackingMore(key)
    
    const params = {
        'customer_name': 'New name',
        'note':'New test order note'
    }
    const idString = "9e72fcfde285536bca6301bc006aa98e"
    trackingmore.trackings.updateTrackingByID(idString, params)
      .then(result => console.log(result))
      .catch(e => console.log(e))