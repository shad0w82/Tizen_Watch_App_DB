Samsung has recently alerted the public that the [Tizen service will be terminated as of September 30, 2025](https://seller.samsungapps.com/notice/getNoticeDetail.as?csNoticeID=0000009034). \
This means that after that date, we will no longer be able to download applications and watch faces for our Tizen products anymore. Moreover, in case you have to reset your watch or change the phone, you won't be able to restore you watch anymore, because even the stock apps, like reminders, stop watch, browser, weather and  many others you won't be able to download!

After Googling for a long time on forums trying to find a viable solution to the problem, I found [this great post](https://xdaforums.com/t/root-required-how-to-extract-gear-s3-watch-faces-and-apps-from-the-galaxy-store.4687851/#post-89676629) of VNNGYN on XDA, explaining a procedure to extract watchfaces and applications from the Samsung Gear S3 series.

His solution works great but, as stated by VNNGYN himself, the only way to perform the procedure is by a **rooted phone**. So after tinkering a bit, taking into account the idea of intercepting the download of the application file (WGT file) I came up with this other solutions, that doesn't need to root your phone.

### Intercept traffic data ###
Fortunately, the Galaxy Wearable app on Android still uses HTTP to fetch and download Tizen apps from the Galaxy Store, in a temporary directory before pushing them to the watch for the install process. So we can leverage the [PCAPdroid](https://github.com/emanuele-f/PCAPdroid) free tool to sniff traffic data and extract useful information from it. 


<p align="center">
<a href="https://f-droid.org/packages/com.emanuelef.remote_capture">
    <img src="https://fdroid.gitlab.io/artwork/badge/get-it-on.png"
    alt="Get it on F-Droid"
    height="80" />
</a> 
<a href='https://play.google.com/store/apps/details?id=com.emanuelef.remote_capture'>
    <img src="https://play.google.com/intl/en_us/badges/static/images/badges/en_badge_web_generic.png"
    alt="Get it on Google Play"
    height="80" />
</a>
</p>

Open the Galaxy Wearable app, go to the Galaxy Store and select the app you want to extract, click on "INSTALL" button  **but don't click on ACCEPT AND DOWNLOAD yet!**. 
<div class="imageGallery1">
<p align="center">
<a href="imgs/galaxy_store1.png"><img src="imgs/galaxy_store1.png" height="335"/></a>
<a href="imgs/galaxy_store2.png"><img src="imgs/galaxy_store2.png" height="335"/></a>
<a href="imgs/galaxy_store3.png"><img src="imgs/galaxy_store3.png" height="335"/></a>
<a href="imgs/galaxy_store4.png"><img src="imgs/galaxy_store4.png" height="335"/></a>
<a href="imgs/galaxy_store5.png"><img src="imgs/galaxy_store5.png" height="335"/></a>
</p>
</div>



Switch to PCAPdroid (don't kill the Galaxy Wearable app!) and select **PCAP file** as the Traffic Dump option. Then select **Target apps** switch to filter out all the data that doesn't come from the Galaxy Wearable app. Finally click on the start button (the little "play" button in the top right part of the app). Now go back to Wearable App and click "ACCEPT AND DOWNLOAD". Once the installation is finished, you can stop the data dump, and you'll have a PCAP file stored on your device.
<div class="imageGallery2">
<p align="center">
<a href="imgs/pcap_conf.png"><img src="imgs/pcap_conf.png" height="370"/></a>
<a href="imgs/pcap_start.png"><img src="imgs/pcap_start.png" height="370"/></a>
<a href="imgs/pcap_stop.png"><img src="imgs/pcap_stop.png" height="370"/></a>
</p>
</div>

{% include lightbox-elements.html %}

