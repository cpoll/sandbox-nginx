# To run:
- Build dockerfile
    docker build -t nginx-test.latest .

- Run the container
    docker run -it --mount type=bind,source="$(pwd)"/nginx/conf.d,target=/etc/nginx/conf.d -p 1234:80 nginx-test.latest bash

- in the container, run `nginx -g 'daemon off;'`
    - You could use the default CMD entrypoint, but this makes restarting nginx a bit easier.

A lot of things don't work with localhost, so add an /etc/hosts entry on your machine for 127.0.0.1 nginx-test.local web-test.local

# Testing
- run `python3 -m http.server` to properly test iframe.html, etc.
- Use a different url like web-test.local:8000/iframe.html to access the html
