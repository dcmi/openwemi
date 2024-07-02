## OpenWEMI Namespace Resolver

The OpenWEMI namespace resolver service is configured as a wildcard service that resolves DCMI namespace URIs to their corresponding landing URLs based on the namespace configuration, which supports content negotiation and provides various actions for testing and debugging.

Base Namespace URI: `https://ns.dublincore.org/openwemi/`

> **Note**: the URI uses https:// scheme, but the service also supports `http://` scheme but it is not recommended. The service will redirect to the `https://` scheme if any client access URLs with `http://` scheme.  Also, enforcing strict [RFC3986]( https://www.rfc-editor.org/rfc/rfc3986#section-6.2.2.1), the namespace URIs are case-sensitive. and the service will not resolve the URI if the case is not matched.

The resolver, redirects the path after the base URI to the corresponding landing URL, as a fragment identifier. The landing URL is also depends on the media type requested in the `Accept` header. Please refer [RFC3986 Section 3]( https://www.rfc-editor.org/rfc/rfc3986#section-3) for the URI syntax.


### Example URIs

`http://ns.dublincore.org/openwemi/commonWork` will redirect to `https://dcmi.github.io/openwemi/ns/openWEMI.html#commonWork`

## Configuration

The DCMI namespace resolver is a configuration driven service that uses namespace specific configuration files to determine the landing URL, media types, and other settings for each namespace. The configuration files are maintained in [pkl format](https://pkl-lang.org) and used in various build and deployment processes.

The configuration file for the OpenWEMI namespace is available at [openwemi.pkl](openwemi.pkl). Any modifications to the configuration should be made in the configuration file and then deployed to the resolver service. This process is manually managed by the DCMI webmanager to ensure consistency and accuracy of the configuration settings.

You can validate the configuration file using the [pkl CLI ](https://pkl-lang.org/main/current/pkl-cli/index.html) tools.


```bash
# Validate and print the configuration file in YAML format
pkl eval openwemi.pkl -f yaml

# Validate and print the configuration file in JSON format
pkl eval openwemi.pkl -f json

```

## Content Negotiation

The DCMI namespace resolver supports content negotiation to provide responses in different formats based on the `Accept` header in the request. The accept header should be [RFC 9110 Section 12.5.1](https://www.rfc-editor.org/rfc/rfc9110.html#section-12.5.1) compliant and can include multiple media types separated by commas. The resolver will select the most appropriate media type based on the provided accept header. If no accept header is provided, the resolver will default to `text/html` or the default media type specified in the configuration of the namespace.

For example, if the accept header is `text/turtle, text/html`, the resolver will return the response in `text/turtle` format if available; otherwise, it will return the response in `text/html` format.

Test with curl:

```bash
curl --request GET \
  --url https://ns.dublincore.org/openwemi/commonWork \
  --header 'Accept: text/turtle'
```

##  Options for testing and debugging

DCMI namespace resolver provides several actions that can be triggered based on the provided `action` parameter. Depending on the action, the resolver returns different types of responses including JSON, plain text, and redirects. Below is the detailed documentation for each action.

### Actions

#### `resolve`
- **Description**: Redirects to the landing URL. This is the default action if no action is provided or if the action is invalid.
  - Type: Redirect
  - Status Code: Any valid HTTP status code
  - URL: Final landing URL
- **Response**:
  - Type: Redirect
  - Status Code: Any valid HTTP status code
  - URL: Final landing URL

#### `get_config`
- **Description**: Returns the configuration settings.
- **Response**:
  - Type: JSON
  - Body: Configuration settings

#### `expand`
- **Description**: Returns the landing URL as plain text.
- **Response**:
  - Type: Plain Text
  - Body: The fully expanded landing URL

#### `get_media_types`
- **Description**: Returns the media types from the configuration.
- **Response**:
  - Type: JSON
  - Body: All available media types
  ```json
  {
    "text/html": "https://dcmi.github.io/openwemi/ns/openWEMI.html",
    "text/turtle": "https://dcmi.github.io/openwemi/ns/openWEMI.ttl"
  }
  ```

#### `debug`
- **Description**: Returns debug information including media type, landing base, suffix, URL, status code, action, and headers.
- **Response**:
  - Type: JSON
  - Body:
    ```json
    {
      "media_type": "media_type",
      "landing_base": "landing_base",
      "landing_suffix": "landing_suffix",
      "landing_url": "landing_url",
      "status_code": "status_code",
      "action": "action",
      "headers": "headers"
    }
    ```


### Usage

To use the resolver, specify the desired action using the `action` parameter. The API will execute the corresponding handler and return the appropriate response. If the `action` parameter is not provided or does not match any of the predefined actions, the default action will be triggered, which redirects to the landing URL.

### Example Request

#### Request
```http
GET /openwemi/commonWork?action=resolve
```

#### Response
```http
HTTP/1.1 302 Found
Location: https://dcmi.github.io/openwemi/ns/openWEMI.html#commonWork
```
