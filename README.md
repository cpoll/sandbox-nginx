# To run:
- Build dockerfile: `docker build -t nginx-test.latest .`

- Run the container: `docker run -it --mount type=bind,source="$(pwd)"/nginx/conf.d,target=/etc/nginx/conf.d -p 1234:80 nginx-test.latest bash`

- in the container, run `nginx -g 'daemon off;'`
    - You could use the default CMD entrypoint, but this way makes restarting nginx a bit easier.

Visit localhost:1234 to test.

A lot of things don't work with localhost, so add an /etc/hosts entry on your machine for 127.0.0.1 nginx-test.local web-test.local web-test.test

# Testing
- run `python3 -m http.server` to properly test iframe.html, etc.
- Use a different url like web-test.local:8000/iframe.html to access the html
- Access control: Any reqs originating from *.local should work
    - But web-test.test should only work if it's making a request to http://nginx-test.local:1234/bypass


