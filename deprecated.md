####  Application Cache API (AppCache API) - DEPRECATED

**NOTE: AppCache API is deprecated!**

Two components make up the AppCache API: the manifest file and a JavaScript API to support it.

**Using AppCache manifest**

```html
<html manifest="myOfflineApp.appcache>
    ...
</html>
```

The application cache manifest file must list each and every file and resource required to
be stored for offline use.\
The manifest file contains three sections: CACHE, NETWORK, and FALLBACK.

```sh
CACHE MANIFEST
# My Web Application Cache Manifest
# v.1.0.0.25
#
#Cache Section. All Cached items.
CACHE
/pages/page1.html
/pages/page2.html
#Required Network resources
NETWORK:
login.html
#Fallback items. 
#NOTE: allback-login.html does not need to be placed inside CACHE section.
FALLBACK:
login.html fallback-login.html
```

**Using the AppCache API**

....