# superapi

## description

Superapi is a (super) wrapper around the excellent superagent library to help configuring any service call to an API or any  HTTP request.

The idea is to remove any setup while calling an API. Just provide a service id, some options and callbacks and your set up.

## configuration

Configuration is made by providing a JSON file in the format of:

```json
{
  baseUrl: "http://foo.domain.tld",
  headers: {
    // default headers
  },
  services: [
    { /* service description */ }
  ]
}
```

### general options

Below are the supported options in the configuration.

#### baseUrl: (string)

This is the base url that will be prefixed to any service path. For a base url like `http://foo.domain.tld/api` and a service path of `/my/service` the generated url will be, without any surprise `http://foo.domain.tld/api/my/service`.

#### default headers: (object)

The idea of this object is to provide some generic headers. As an example superagent does not set the header `X-Requested-With` which is often needed to be set with the value of `XMLHttpRequest`.

This the default headers can be:

```json
{
  "X-Requested-With": "XMLHttpRequest"
}
```

TODO


### service configuration

```json
myservice: {
  path: '/something' // mandatory
  method: 'GET|POST|PUT|DELETE|PATCH' default to 'GET'
  headers: {
    // key - value for any specific headers not handle by superagent
  },
  options: {
    // see superagent options
    type: String,
    accept: 'json'
  }
}
```