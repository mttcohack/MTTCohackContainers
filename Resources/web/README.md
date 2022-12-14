# Web frontend for SQL API

## Usage

Simple PHP web page that can access the [SQL API](../api/README.md). It will show something like this:

![web](web.png)

The container requires these environment variables:

* `API_URL`: URL where the SQL API can be found, for example `http://1.2.3.4:8080` or `http://api:8080`

## Build

 You can build it locally with:

```bash
docker build -t cohack/web:1.0 .
```

## Deploy

This web portal requires an existing API to access. Please verify the [API docs](../api/README.md) for details about how to deploy the API before deploying this Web component.

### Run this image locally

Replace the image and the text `your_api_ip_or_hostname` with the relevant values. 

```bash
# Deploy on Docker
docker run -d -p 8081:80 -e "API_URL=http://your_api_ip_or_hostname:8080" --name web cohack/web:1.0
```
