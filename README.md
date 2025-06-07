# Curl-Adapter for PHP
This is a wrapper library for PHP's cURL functions. It allows you to easily send GET and POST requests

## Installation
To install this library, include it in your project using composer:
```json
{
    "require": {
        "struktal/curl-adapter": "~1.1.0"
    }
}
```

## Usage
<details>
<summary><b>Simple GET or POST requests</b></summary>

The following example shows how to send a GET request to a HTML page:
```php
$curl = new Curl();
$curl->setUrl("URL");
$curl->setMethod(Curl::$METHOD_GET);
$curl->setHeaders([
    "Accept: text/html, application/xhtml+xml"
]);
$response = $curl->execute();
$responseCode = $curl->getHttpCode();
$curl->close();
```
`URL` is the URL of the server that you want to send the request to.

To send a POST request, simply replace `Curl::$METHOD_GET` with `Curl::$METHOD_POST`. However note, that the above example does not send any POST data to the server.
</details>

<details>
<summary><b>POST requests with data</b></summary>

To send POST data to the server, use the `setPostFields()` method:
```php
$curl = new Curl();
$curl->setUrl("URL");
$curl->setMethod(Curl::$METHOD_POST);
$curl->setHeaders([
    "Accept: application/json"
]);
$curl->setPostFields([
    "key" => "value"
]);
$response = $curl->execute();
$responseCode = $curl->getHttpCode();
$curl->close();
```
The above example requests a JSON response from the server with the URL `URL` and sends the POST data `key=value` along with the request.

You can also send JSON-encoded POST data by setting the `asJson` flag of the `setPostFields` method to `true`.
</details>
