# Apptio Usage Service
This simple app wraps the [app-usage-service](https://docs.pivotal.io/pivotalcf/1-11/opsguide/accounting-report.html) and calls
the usage service for each organization and concatenates the results. It also handles the OAuth authentication since Apptio datalink
does not support that mode of authentication.
## Running on Cloudfoundry
1. create `usage-user` with `cloud_controller.admin_read_only` rights
2. Modify the manifest.yml with the relevant environment variables for your environment
3.  `cf push`

## Example usage
`curl http://basic:basic@localhost:8080/app-usage/2017/08`
## Example output
```json
{
  "orgs": [
    {
      "organization_guid": "c7aa8a09-1194-4dd1-97b2-ad01098b8bdc",
      "organization_name": "Org1",
      "period_start": "2017-08-01T00:00:00Z",
      "period_end": "2017-08-31T23:59:59Z",
      "app_usages": [
        {
          "space_guid": "61e7a4d0-c0b7-43e5-9f24-4d732983dd16",
          "space_name": "dev",
          "app_name": "app1",
          "app_guid": "84f102e0-ea1f-4bee-92f9-ab05b028742f",
          "instance_count": 1,
          "memory_in_mb_per_instance": 512,
          "duration_in_seconds": 1781433
        },
        {
          "space_guid": "61e7a4d0-c0b7-43e5-9f24-4d732983dd16",
          "space_name": "dev",
          "app_name": "app2",
          "app_guid": "aae20390-21f9-4640-b666-de7b97d89d24",
          "instance_count": 1,
          "memory_in_mb_per_instance": 2048,
          "duration_in_seconds": 1781825
        }
      ]
    },
    {
      "organization_guid": "d1c51651-23b3-491e-a348-1a6538b5291f",
      "organization_name": "org2",
      "period_start": "2017-08-01T00:00:00Z",
      "period_end": "2017-08-31T23:59:59Z",
      "app_usages": [
        {
          "space_guid": "ee8556c0-daac-493e-8c88-16263923b995",
          "space_name": "dev",
          "app_name": "app3",
          "app_guid": "0f97ce20-e24f-4821-81df-a7425503eedd",
          "instance_count": 1,
          "memory_in_mb_per_instance": 1024,
          "duration_in_seconds": 719181
        },
        {
          "space_guid": "ee8556c0-daac-493e-8c88-16263923b995",
          "space_name": "dev",
          "app_name": "app4",
          "app_guid": "d4869bb4-41e8-4ae4-b949-78b1ae1e1503",
          "instance_count": 1,
          "memory_in_mb_per_instance": 1024,
          "duration_in_seconds": 717116
        }
      ]
    },
    {
      "organization_guid": "b9612720-884f-4e7d-a80f-ec878c3e14c5",
      "organization_name": "test",
      "period_start": "2017-08-01T00:00:00Z",
      "period_end": "2017-08-31T23:59:59Z",
      "app_usages": [
        {
          "space_guid": "57d0c6c0-6270-4ced-85ba-52e0a6db76b5",
          "space_name": "dev",
          "app_name": "app5",
          "app_guid": "ebfedf50-95b9-49ec-a844-0abfa743a089",
          "instance_count": 1,
          "memory_in_mb_per_instance": 1024,
          "duration_in_seconds": 190541
        }
      ]
    },
    {
      "organization_guid": "9b648d40-50df-44ee-8a00-ec39a43b2261",
      "organization_name": "org3",
      "period_start": "2017-08-01T00:00:00Z",
      "period_end": "2017-08-31T23:59:59Z",
      "app_usages": []
    }
  ]
}
```
