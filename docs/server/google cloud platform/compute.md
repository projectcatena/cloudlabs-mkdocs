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
| `name`                 | string       | Name for the compute instance.                            | Yes           |
| `selectedImage`        | Image        | Contains the name and project URL for a machine image.    | Yes           |
| `selectedInstanceType` | InstanceType | Contains the name of an instance type (e.g. e2-micro).    | Yes           |

>??? quote "Request"
    ```JSON
    {
        "name": "test",
        "selectedImage": {
            "name": "debian-11",
            "project": "projects/debian-cloud/global/images/family/"
        },
        "selectedInstanceType": {
            "name": "e2-micro"
        }
    }
    ```
>??? quote "Response"
    ```JSON
    {
        d69456c0-c7c7-4360-bebd-b122e26c3b7d
    }
    ```