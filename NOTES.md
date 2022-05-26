# web-test.local:8000/iframe.html
- Chrome sends over Referer
- nginx gets http_host (nginx-test.local:1234)
- nginx gets http_referer (http://web-test.local:8000)
- nginx can use map to regex out web-test.local:8000 (or anyting else)
- nginx does not get http_origin

# nginx-test.local:1234
- nginx gets http_host (nginx-test.local:1234)
- nginx does not get referer or origin
