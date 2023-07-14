# Tunnel

[Apache Guacamole](https://guacamole.apache.org/) is a clientless remote desktop gateway, which has been integrated to the CloudLabs server to interface with a guacd instance.

## Overview

The main purpose of the server is to facilitate the creation of a tunnel between the client and a virtual machine instance on the cloud through the guacd service.

## API Reference

The API endpoints listed in this section should only be initiated using the `guacamole-common-js` npm package, which will automatically handle the communication between the front-end and back-end server in relation to the guacd service.

Example of initating a HTTP tunnel using the `guacamole-common-js` package:
```TypeScript
var guac = new Guacamole.Client(
    // True to enable CORS
    new Guacamole.HTTPTunnel('http://localhost:8080/tunnel', true, params)
);
```

### Create
```
POST: /tunnel?connect
```
> Parameters:

>| Name        | Type    | Description                                | Required      |
| ------------ | ------- | -------------------------------------------| ------------- |
| `hostname`   | string  | Hostname for the VM such as, "10.10.1.1".  | Yes           |
| `ignorecert` | boolean | For RDP certification.                     | Yes (for RDP) |
| `name`       | string  | User-specified name of the connection.     | Yes           |
| `password`   | string  | Password for the remote connection.        | Yes           |
| `port`       | integer | A custom port number for the protocol.     | No            |
| `protocol`   | string  | Remote access protocol such as "rdp".      | Yes           |

>??? quote "Response"
    ```JSON
    {
        d69456c0-c7c7-4360-bebd-b122e26c3b7d
    }
    ```

### Read
```
GET: /tunnel?read:{session-id}:{id}
```
> Parameters:

>| Name        | Type    | Description                                | Required      |
| ------------ | ------- | -------------------------------------------| ------------- |
| `session-id` | string  | Unique session id created by Guacamole.    | Yes           |
| `id`         | integer | Supposed id for each request to the VM.    | Yes           |

>
An important header, `Guacamole-Tunnel-Token` wil be set as well:
```JSON
{
    "Guacamole-Tunnel-Token": "IwCOVgo/6nevmcwbf/UePX9BFalcs0hL+a9euqY+LPN+"
}
```
>??? quote "Response"
    ```JSON
    {
        4.size,1.0,4.1024,3.768;4.size,2.-1,2.11,2.16;3.img,1.3,2.12,2.-1,9.image/png,1.0,1.0;4.blob,1.3,232.iVBORw0KGgoAAAANSUhEUgAAAAsAAAAQCAYAAADAvYV+AAAABmJLR0QA/wD/AP+gvaeTAAAAYklEQVQokY2RQQ4AIQgDW+L/v9y9qCEsIJ4QZggoJAnDYwAwFQwASI4EO8FEMH95CRYTnfCDOyGFK6GEM6GFo7AqKI4sSSsCJH1X+roFkKdjueABX/On77lz2uGtr6pj9okfTeJQAYVaxnMAAAAASUVORK5CYII=;3.end,1.3;6.cursor,1.0,1.0,2.-1,1.0,1.0,2.11,2.16;4.sync,8.15035699;0.;
    }
    ```

### Write
```
POST: /tunnel?write:{session-id}
```
> Parameters:

>| Name        | Type    | Description                                | Required      |
| ------------ | ------- | -------------------------------------------| ------------- |
| `hostname`   | string  | Hostname for the VM such as, "10.10.1.1".  | Yes           |
| `ignorecert` | boolean | For RDP certification.                     | Yes (for RDP) |
| `name`       | string  | User-specified name of the connection.     | Yes           |
| `password`   | string  | Password for the remote connection.        | Yes           |
| `port`       | integer | A custom port number for the protocol.     | No            |
| `protocol`   | string  | Remote access protocol such as "rdp".      | Yes           |

>??? quote "Response"
    ```
    Null
    ```