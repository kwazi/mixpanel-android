Documentation:
    You can find getting started guides for using Mixpanel at

    https://mixpanel.com/docs/integration-libraries/android for tracking events
    https://mixpanel.com/docs/people-analytics/android for updating people analytics
    https://mixpanel.com/docs/people-analytics/android-push for sending push notifications

Demo:
    See https://github.com/mixpanel/mixpanel-android for a full featured sample application

Changelog:

v2.1
---------------------

* Support for Mixpanel push notifications

    The Mixpanel library now handles registering for and receiving
    Google Cloud Messaging notifications sent from the Mixpanel interface.
    See https://mixpanel.com/docs/people-analytics/android-push
    for instructions on getting started using Mixpanel to
    engage directly with users of your application.

* ant-based build system for core libraries

    To build the core library, type 'ANDROID_HOME=/path/to/android/sdk ant library'
    at your command line.

* API brought closer to Mixpanel Javascript and iPhone APIs

    Main class now named "MixpanelAPI", as in iPhone library

    Methods renamed to align with iPhone API method names

    People Analytics features are now accessed via the
    MixpanelAPI.People class, accessed via MixpanelAPI.getPeople()

    People.identify is now independent of MixpanelAPI.identify

    User identity and super properties now persist across
    application shutdown

* More explicit threading model

    Eliminated dependency on external Looper for timing
    of messages sent to Mixpanel

* Extensive documentation

    Public APIs are now more thoroughly documented

* Unit Tests provided as part of core code

   Unit tests are an Eclipse project under
   test/, are run against the demo application

v2.0
-------------------
* Added support for Mixpanel People
* Added MPConfig object for easier configurability
* MPMetrics.VERSION now available
* Improved debugging information available
* Event queuing submission model revamped

v1.3
-------------------
Due to an unexplained increase in Sqlite insertion times on ICS, we now use a background thread to queue up
events being sent.

v1.2
-------------------
* Add country geolocation by default. Now all events tracked will have the property 'Country.'

v1.1
-------------------
* Convert MPMetrics into a singleton, fixing a rare race caused by multiple instances.
* Reduce the number of flushes being called when events are backed up.
* Correctly check status of API call result
* Better support for using multiple tokens within a single Android application

v1.0 (original)
------------------
* Removed the funnel() methods. Funnels have been built from events for some time now, and this update to Android simply reflects that change we have made.
  The proper way to perform funnel analysis is to create a funnel based on events that you are sending. For more information, please see http://mixpanel.com/api/docs/guides/funnel-analysis

* Renamed the event method to track, to be more consistent with the existing APIs. 
  Furthermore, the propeties object passed to the new track method is no longer a HashMap, but a JSONObject.
  This will cause types to be correctly preseved in Segmentation.
