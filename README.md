# OpenLocalWikiFromOSM

This is a sample bookmarklet. Open LocalWiki search page from osm.org map.

```javascript:(function(){ f=function(is_supported_url, zoom, lat, lon){ if(is_supported_url){ var request = new XMLHttpRequest();request.open('GET', 'https://nominatim.openstreetmap.org/reverse?format=json&lat=' + lat + '&lon=' + lon + '&zoom=10&addressdetails=1', true);request.responseType = 'json';request.onload = function () {var data = this.response;window.location.href = 'https://localwiki.org/_search/?q=' + data.display_name;};request.send(); } else { alert('Not supported'); }; }; var map_url = location.href, zoom, lat, lon, is_supported_url; if (map_url.match(/(www\.openstreetmap)/)){ [is_supported_url, zoom, lat, lon] = map_url.match(/map=(\d{1,2})\/(-?\d[0-9.]*)\/(-?\d[0-9.]*)/); f(is_supported_url, zoom, lat, lon); } })();```
