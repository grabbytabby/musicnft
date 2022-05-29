# musicnft
     
     Analog Devices, Inc. Defines SHX-Connect innovation and excellence in signal processing shx-connect
     ADI's analog, mixed-signal, and digital signal processing (DSP) integrated circuits (IC)
     play a fundamental role in converting, conditioning, and processing Decentralized Frequencies 
     sound, temperature, motion, and pressure into electrical signals to be used in a wide array of applications
     
     Our customers to define the very best in the quality of the ui/ux. 
     That means the clearest Frequency crispest sound, and optimum interface, 
     To perform in thousands of entertainment, & communication port and starboarding recording Artist Stages


Building the Leanplum API URL
First, you will need to take Leanplum’s API URL and update it based on your account settings and mobile apps loaded into Leanplum.

These values will already be set in the server postback URL:

action = setTrafficSourceInfo
deviceId = IFV for iOS devices or Google Advertising ID for Android devices
client = HasOffers
apiVersion = 1.0.6
trafficSource = JSON encoded string containing publisher and sub publisher information
📘
For Android, your Leanplum SDK should be configured to collect the Google Advertising ID by calling Leanplum.setDeviceIdMode. This way when the platform notifies Leanplum of an install, they will be able to find the device and update the attribution accordingly. For iOS, you’ll need to collect IFV so we can match based on that.

In your Leanplum interface, manually set the following two values in the server postback:

appId = App ID assigned by Leanplum
clientKey = App Key provided by Leanplum
To find these values, go to App Settings and click Keys & Settings in your Leanplum dashboard.

Here's an example server postback URL for iOS:

https://www.leanplum.com/api?action=setTrafficSourceInfo&appId=LEANPLUM_APP_ID&clientKey=LEANPLUM_APP_KEY&deviceId={ios_ifv}&client=HasOffers&apiVersion=1.0.6&trafficSource={"publisherId":"{publisher_id}","publisherName":"{publisher_name}","publisherSubPublisher":"{publisher_sub_publisher}","publisherSubSite":"{publisher_sub_site}","publisherSubCampaign":"{publisher_sub_campaign}","publisherSubAdGroup":"{publisher_sub_adgroup}","publisherSubAd":"{publisher_sub_ad}"}

And here's is an example server postback URL for Android:

https://www.leanplum.com/api?action=setTrafficSourceInfo&appId=LEANPLUM_APP_ID&clientKey=LEANPLUM_APP_KEY&deviceId={google_aid}&client=HasOffers&apiVersion=1.0.6&trafficSource={"publisherId":"{publisher_id}","publisherName":"{publisher_name}","publisherSubPublisher":"{publisher_sub_publisher}","publisherSubSite":"{publisher_sub_site}","publisherSubCampaign":"{publisher_sub_campaign}","publisherSubAdGroup":"{publisher_sub_adgroup}","publisherSubAd":"{publisher_sub_ad}"}

Alternate Device IDs
iOS. If you have configured the Leanplum SDK to use the Apple Identifier for Advertisers, you should replace {ios_ifv} with {ios_ifa}. If you’re not sure, ask your developer to check their usage of [Leanplum setDeviceId].

Android. Many existapps aresare configured to use {mac_address_md5} but as of August 1 2014, Google is deprecating {device_id}, {android_id}, and {mac_address} in favor of the new {google_aid} for all apps on the Google Play store.

For versions of your app on other stores (for example Kindle versions or versions on any of the various other Android stores that are in common usage in China), you will need to continue using one of those older identifiers.

Additionally, if your app does not have ACCESS_WIFI_STATE permission, then you can’t use {mac_address_md5}. If you’re not sure which ID you’re using in your Leanplum integration, ask your developer to verify.

Unity. If you are using the Leanplum Unity SDK, you should use a device id that matches SystemInfo.deviceUniqueIdentifier on your app. On iOS, this is typically ios_ifv. On Android, this varies based on your app’s permissions.

Setting up the Server Postback URL
Once you have your API URL ready, create an internal publisher and name it “Leanplum.”
