# Cloud Storage

The CloudLabs server utilizes GCP Cloud Storage to store the virtual disks uploaded by users. Furthermore, Cloud Build is also used to build and transform the virtual disks to images that can be used as part of a compute instance's boot disk.

For more information, refer to [this](https://cloud.google.com/compute/docs/import/importing-virtual-disks) documentation.

## Upload Flow

Due to the sheer size of typical virtual disks, a reliable method to upload files is required. This is achieved through allowing users to upload their virtual disks directly to a Cloud Storage bucket using a dynamically generated [Signed URL](https://cloud.google.com/storage/docs/access-control/signing-urls-with-helpers).

## API Reference

This section documents the API specifications for the CloudLabs server endpoints.

### Get Signed URL
```
POST: /api/storage/signed
```
> Parameters:

>| Name                  | Type         | Description                                               | Required      |
| -----------------------| -------------| --------------------------------------------------------- | ------------- |
| `objectName`           | string       | File name of the virtual disk of type vmdk or vhd.        | Yes           |

>??? quote "Request"
    ```JSON
    {
        "objectName": "Windows_Server_2019-disk1.vmdk",
    }
    ```
>??? quote "Response"
    ```JSON
    {
        "objectName": "Windows_Server_2019-disk1.vmdk",
        "signedURL": "https://storage.googleapis.com/bucket_name/Windows_Server_2019-disk1.vmdk_and_more",
    }
    ```

### Start a Build
```
POST: /api/storage/start
```
> Parameters:

>| Name                  | Type         | Description                                               | Required      |
| -----------------------| -------------| --------------------------------------------------------- | ------------- |
| `objectName`           | string       | File name of the virtual disk of type vmdk or vhd.        | Yes           |
| `imageName`            | string       | Image name that conforms to GCP's [specifictions](https://cloud.google.com/compute/docs/reference/rest/v1/images).      | Yes           |

>??? quote "Request"
    ```JSON
    {
        "objectName": "Windows_Server_2019-disk1.vmdk",
        "imageName": "windows-server-2019",
    }
    ```
>??? quote "Response"
    ```JSON
    {
        "objectName": "Windows_Server_2019-disk1.vmdk",
        "imageName": "windows-server-2019",
        "buildStatus": "QUEUED",
        "buildId": "5d86bae4-263d-4ba8-a643-f90ad0fffa65"
    }
    ```