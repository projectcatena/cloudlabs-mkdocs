# Compute Engine

The CloudLabs server utilizes the [Java Compute Engine API v1](https://cloud.google.com/java/docs/reference/google-cloud-compute/latest/com.google.cloud.compute.v1) to programmatically create and manage compute instances.

## Documentation

However, the aforementioned link is merely an API reference, a more detailed guide in managing compute instances can be found at the [GCP Compute Engine Guide](https://cloud.google.com/compute/docs/instances). 

Though, it is important to note that, the guide may exclude code examples for certain operations, such as reserving and assigning external IP addresses to compute instances. In this case, one may refer to both the aforementioned [Java Compute Engine API v1](https://cloud.google.com/java/docs/reference/google-cloud-compute/latest/com.google.cloud.compute.v1) or the [General Compute Engine API v1](https://cloud.google.com/compute/docs/reference/rest/v1) for reference.

## API Reference

This section documents the API specifications for the CloudLabs server endpoints.

### Create
```
POST: /api/compute/create
```
> Parameters:

>| Name                  | Type         | Description                                               | Required      |
| -----------------------| -------------| --------------------------------------------------------- | ------------- |
| `instanceName`         | string       | Name for the compute instance.                            | Yes           |
| `sourceImage`          | Image        | Contains the name and project URL for a machine image.    | Yes           |
| `machineType`          | InstanceType | Contains the name of an instance type (e.g. e2-micro).    | Yes           |
| `startupScript`        | string       | Content of shell script to be executed on startup.        | No            |
| `address`              | Subnet       | Subnet for the compute instance (only name is needed).    | Yes           |
| `maxRunDuration`       | Long         | Max runtime duration for instance in seconds (120 or more)| No            |

>??? quote "Request"
    ```JSON
    {
        "instanceName": "test18",
        "sourceImage": {
            "name": "debian-11",
            "project": "debian-cloud"
        },
        "machineType": {
            "name": "e2-micro"
        },
        "startupScript": "",
        "address": {
            "subnetName": "test-subnet-a"
        },
        "maxRunDuration": 120
    }
    ```
>??? quote "Response"
    ```JSON
    {
        "instanceName": "test18",
        "address": {
            "name": "test18-public-ip",
            "ipv4Address": "35.240.158.214"
        },
        "maxRunDuration": 120
    }
    ```

### Delete
```
POST: /api/compute/delete
```
> Parameters:

>| Name                  | Type         | Description                                               | Required      |
| -----------------------| -------------| --------------------------------------------------------- | ------------- |
| `instanceName`         | string       | Name for the compute instance.                            | Yes           |

>??? quote "Request"
    ```JSON
    {
        "instanceName": "test18",
    }
    ```
>??? quote "Response"
    ```JSON
    {
        "instanceName": "test18",
        "status": "DONE"
    }
    ```
    
### List Machine Types
```
GET: /api/compute/list-machine-types
```
> Parameters:

>| Name                  | Type         | Description                                               | Required      |
| -----------------------| -------------| --------------------------------------------------------- | ------------- |
| `query`                | string       | Query based on machine type name (e.g. e2-micro).         | No            |

>??? quote "Request"
    ```
    https://localhost/api/compute/list-machine-types?query=a2
    ```
>??? quote "Response"
    ```JSON
    [
        {
            "name": "a2-highgpu-1g"
        },
        {
            "name": "a2-highgpu-2g"
        },
        {
            "name": "a2-highgpu-4g"
        },
        {
            "name": "a2-highgpu-8g"
        }
    ]
    ```
