# Self Service

Provides API interfaces for the Tools: Self Service functionality, which involves viewing and managing catalog item types. These are the types that become available for order by the [Service Catalog](#service-catalog) persona.

This is the adminstrative api for the Tools: Self Service functionality.

## Get All Catalog Item Types

```shell
curl "$MORPHEUS_API_URL/api/catalog-item-types" \
  -H "Authorization: BEARER $MORPHEUS_API_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "catalogItemTypes": [
    {
      "id": 1,
      "name": "Example Instance",
      "description": "Example catalog item type",
      "type": "instance",
      "blueprint": null,
      "refType": "InstanceType",
      "refId": null,
      "active": true,
      "enabled": true,
      "featured": true,
      "iconPath": "/assets/containers-png/nginx.png",
      "config": {
        "group": {
          "id": 20,
          "name": "Example Group"
        },
        "cloud": {
          "id": 8,
          "name": "Example Cloud"
        },
        "type": "nginx",
        "name": "${userInitials}-${cloudCode}-${type}-simple-${sequence}",
        "hostName": "${userInitials}-${cloudCode}-${type}-simple-${sequence}",
        "layout": {
          "id": 7342,
          "code": "nginx-1.14-single"
        },
        "plan": {
          "id": 68,
          "code": "container-128"
        },
        "version": "1.9",
        "config": {
          "createUser": true,
          "resourcePoolId": 94944,
        },
        "networkInterfaces": [
          {
            "network": {
              "id": "network-3",
            }
          }
        ],
        "volumes": [
          {
            "rootVolume": true,
            "name": "root",
            "size": 60,
          }
        ]
      },
      "optionTypes": [

      ],
      "createdBy": null,
      "owner": {
        "id": 1,
        "name": "root"
      },
      "dateCreated": "2020-09-09T23:35:47Z",
      "lastUpdated": "2020-09-16T03:58:32Z"
    },
        {
      "id": 2,
      "name": "Example App",
      "description": "Example catalog item type using a blueprint with scribe",
      "type": "blueprint",
      "blueprint": {
        "id": 15,
        "name": "Example Blueprint"
      },
      "refType": "AppTemplate",
      "refId": null,
      "active": true,
      "enabled": true,
      "featured": true,
      "iconPath": "/assets/containers-png/docker.png",
      "appSpec": "name: <%= customOptions.appName %>\r\ngroup:\r\n  name: Example\r\nenvironment: Test\r\ntiers:\r\n  Web:\r\n    instances:\r\n      - instance:\r\n          type: nginx\r\n          cloud: Example\r\n  App:\r\n    instances:\r\n      - instance:\r\n          type: activemq\r\n          cloud: Example",
      "optionTypes": [
        {
          "id": 2926,
          "name": "App Name",
          "description": "Enter a unique name for the app",
          "code": "appName",
          "fieldName": "appName",
          "fieldLabel": "App Name",
          "fieldCode": null,
          "fieldContext": "config.customOptions",
          "fieldGroup": null,
          "fieldClass": null,
          "fieldAddOn": null,
          "fieldComponent": null,
          "fieldInput": null,
          "placeHolder": null,
          "verifyPattern": null,
          "helpBlock": null,
          "defaultValue": null,
          "optionSource": null,
          "optionList": null,
          "type": "text",
          "advanced": false,
          "required": true,
          "exportMeta": false,
          "editable": false,
          "creatable": true,
          "config": {
          },
          "displayOrder": 0,
          "wrapperClass": null,
          "enabled": true,
          "noBlank": false,
          "dependsOnCode": null,
          "contextualDefault": false
        }
      ],
      "createdBy": null,
      "owner": {
        "id": 1,
        "name": "root"
      },
      "dateCreated": "2020-09-25T19:13:05Z",
      "lastUpdated": "2020-09-28T20:29:55Z"
    }
  ],
  "meta": {
    "size": 2,
    "total": 2,
    "max": 25,
    "offset": 25
  }
}
```

This endpoint retrieves all catalog item types.

### HTTP Request

`GET https://api.gomorpheus.com/api/catalog-item-types`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
max | 25 | Max number of results to return
offset | 0 | Offset of records you want to load
sort | name | Sort order
direction | asc | Sort direction, use 'desc' to reverse sort
phrase |  | Filter by wildcard search of name and description
name |  | Filter by name, wildcard may be specified as **%**, eg. `example-%`
description |  | Filter by description, wildcard may be specified as **%**. eg. `example-%`
enabled |  | Filter by enabled, eg. `true` or `false`
featured |  | Filter by featured, eg. `true` or `false`

## Get a Specific Catalog Item Type

```shell
curl "$MORPHEUS_API_URL/api/catalog-item-types/1" \
  -H "Authorization: BEARER $MORPHEUS_API_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "catalogItemType": {
    "id": 1,
    "name": "Example Nginx",
    "description": "Example catalog item for an nginx instance",
    "type": "instance",
    "blueprint": null,
    "refType": "InstanceType",
    "refId": null,
    "active": true,
    "enabled": true,
    "featured": true,
    "iconPath": "/assets/containers-png/resource.png",
    "config": {
      "group": {
        "id": 20,
        "name": "Example Group"
      },
      "cloud": {
        "id": 8,
        "name": "Example Cloud"
      },
      "type": "nginx",
      "name": "${userInitials}-${cloudCode}-${type}-simple-${sequence}",
      "hostName": "${userInitials}-${cloudCode}-${type}-simple-${sequence}",
      "layout": {
        "id": 7342,
        "code": "nginx-1.14-single"
      },
      "plan": {
        "id": 68,
        "code": "container-128"
      },
      "version": "1.9",
      "config": {
        "createUser": true,
        "resourcePoolId": 94944,
      },
      "volumes": [
        {
          "rootVolume": true,
          "name": "root",
          "size": 60,
        }
      ]
    },
    "optionTypes": [

    ],
    "createdBy": null,
    "owner": {
      "id": 1,
      "name": "root"
    },
    "dateCreated": "2020-09-09T23:35:47Z",
    "lastUpdated": "2020-09-16T03:58:32Z"
  }
}
```

This endpoint retrieves a specific category item type.

### HTTP Request

`GET https://api.gomorpheus.com/api/catalog-item-types/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | ID of the Catalog Item Type


## Create a Catalog Item Type

```shell
curl -XPOST "$MORPHEUS_API_URL/api/catalog-item-types" \
  -H "Authorization: Bearer $MORPHEUS_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
  "catalogItemType": {
    "name": "Example App",
    "description": "Example catalog item type",
    "type": "instance",
    "iconPath": "/assets/containers-png/apache.png",
    "config": {
      "group": {
        "id": "<%= customOptions.morphgroup %>"
      },
      "cloud": {
        "id": "<%= customOptions.morphcloud %>"
      },
      "type": "apache",
      "instance": {
      },
      "name": "${userInitials}-apache-${sequence}",
      "config": {
        "createUser": true,
        "resourcePoolId": "<%= customOptions.morphpool %>"
      },
      "environment": "<%= customOptions.morphenv %>",
      "volumes": [
        {
          "rootVolume": true,
          "name": "root",
          "size": 10,
          "storageType": 5
        }
      ],
      "hostName": "${userInitials}-apache-${sequence}",
      "layout": {
        "id": 31,
        "code": "apache-amazon-2.4-single"
      },
      "networkInterfaces": [
        {
          "primaryInterface": true,
          "network": {
            "id": "<%= customOptions.morphnetwork %>",
            "hasPool": false
          },
          "ipMode": "",
          "showNetworkPoolLabel": false,
          "showNetworkDhcpLabel": true
        }
      ],
      "plan": {
        "id": "<%= customOptions.morphplan %>"
      },
      "version": "2.4",
      "securityGroups": [
        {
          "id": "<%= customOptions.morphsecgroup %>"
        }
      ]
    },
    "optionTypes": [
      34,35,36,37,38,39,40
    ]
  }
}'
```

> The above command returns JSON Structured like this:

```json
{
  "success": true,
  "catalogItemType": {
    "id": 1
  }
}
```

Use this command to create a catalog item type.

### HTTP Request

`POST https://api.gomorpheus.com/api/catalog-item-types`

### JSON Parameters

Parameter | Required | Description
--------- | -------- | -----------
name | Y | Catalog Item Type name
description | N | Catalog Item Type description
type | N | Type, `instance`, `blueprint` or `workflow`. This determines whether an [Instance](#instances) or [App](#apps) will be provisioned. Instance types require a `config` and blueprint requires a `blueprint` and `appSpec`, while workflow types requires a `workflow` and `context`.
iconPath | N | Icon Path, relative location of an icon image, eg. `/assets/containers-png/nginx.png`.
enabled | N | Can be used to enable / disable the catalog item type. Default is true
featured | N | Can be used to feature the catalog item type. Default is false
optionTypes | N | Array of option type IDs, see [Option Types](#option-types). Only applies to type `instance` and `blueprint`. The `workflow` type always uses the option types from the workflow and its tasks instead.
config | Y | Config Object, see [Catalog Config For Instance](#catalog-config-for-instance)
blueprint | Y | [Blueprint](#blueprints) object, identified by id or name. Only applies to type `blueprint`
appSpec | Y | App Spec YAML, see [App Spec For Blueprint](#app-spec-for-blueprint). Only applies to type `blueprint`
workflow | Y | Operational [Workflow](#workflows) object, identified by id or name. Only applies to type `workflow`
context | N | Context for running the workflow, determines if a resource must be selected. `instance`,`server`, or `appliance`.

#### Catalog Config For Instance

The `config` for **instance** type catalog items is an object with fields:

Parameter | Required | Description
--------- | -------- | -----------
name | Y | Name of instance
group | Y | Group, id or name of the group to associate the instance with
cloud | Y | Cloud, id or name of the cloud being provisioned into
type | Y |  Instance Type, id or code for the type of instance eg. `nginx`
layout |  Y | Layout, id or code for the instance type that you want to provision. i.e. single process or cluster
plan | Y | Plan, id or code for the memory and storage option

For the full list of instance provisioning options, see [Create an Instance](#create-an-instance)

#### App Spec For Blueprint

The `appSpec` for **blueprint** type catalog items is a *string* in the Scribe YAML format with fields:

Parameter | Required | Description
--------- | -------- | -----------
name | N | Name of the app
group | N | Name of group
environment | N | Name of environment
tiers | N | Object with each key is a tier name and its value is the tier configuration, including an array of `instances`, each with their own type and settings.

## Create a Catalog Item Type For Blueprint

```shell
curl -XPOST "$MORPHEUS_API_URL/api/catalog-item-types" \
  -H "Authorization: Bearer $MORPHEUS_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
  "catalogItemType": {
    "name": "Example App",
    "description": "Example catalog item type",
    "type": "blueprint",
    "iconPath": "/assets/containers-png/resource.png",
    "blueprint": {
      "id": 13278
    },
    "appSpec": "name: <%= customOptions.appName %>\r\ngroup:\r\n  name: Example\r\nenvironment: Test\r\ntiers:\r\n  Web:\r\n    instances:\r\n      - instance:\r\n          type: nginx\r\n          cloud: Example\r\n  App:\r\n    instances:\r\n      - instance:\r\n          type: apache\r\n          cloud: Example",
    "optionTypes": [
      2926
    ]
  }
}'
```

> The above command returns JSON Structured like this:

```json
{
  "success": true,
  "catalogItemType": {
    "id": 1
  }
}
```

Use this command to create a catalog item type for a **blueprint**. This type uses the specified `blueprint` and `appSpec` to provision an [App](#apps).

### HTTP Request

`POST https://api.gomorpheus.com/api/catalog-item-types`

### JSON Parameters

See [Create](#create-a-catalog-item-type).


## Create a Catalog Item Type For Workflow

```shell
curl -XPOST "$MORPHEUS_API_URL/api/catalog-item-types" \
  -H "Authorization: Bearer $MORPHEUS_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
  "catalogItemType": {
    "name": "Example Operation",
    "description": "Example catalog item type",
    "type": "workflow",
    "workflow": {
      "id": 13
    },
    "context": "instance"
  }
}'
```

> The above command returns JSON Structured like this:

```json
{
  "success": true,
  "catalogItemType": {
    "id": 1
  }
}
```

Use this command to create a catalog item type for a **workflow**. This type uses the specified `workflow` and `context` to execute an Operation Workflow(#workflows).  This type cannot be configured with its own option types, they come from the workflow and its tasks instead.

### HTTP Request

`POST https://api.gomorpheus.com/api/catalog-item-types`

### JSON Parameters

See [Create](#create-a-catalog-item-type).

## Update a Catalog Item Type

```shell
curl -XPUT "$MORPHEUS_API_URL/api/catalog-item-types/:id" \
  -H "Authorization: Bearer $MORPHEUS_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
  "catalogItemType": {
    "featured": true
  }
}'
```

> The above command returns JSON structured like this:

```json
{
  "success": true
}
```

Use this command to update an existing catalog item type.

### HTTP Request

`PUT https://api.gomorpheus.com/api/catalog-item-types/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the catalog item type

### JSON Parameters

Parameter | Required | Description
--------- | -------- | -----------
name | Y | Catalog Item Type name
description | N | Catalog Item Type description
iconPath | N | Icon Path, relative location of an icon image, eg. `/assets/containers-png/nginx.png`.
enabled | N | Can be used to enable / disable the catalog item type. Default is true
featured | N | Can be used to feature the catalog item type. Default is false
optionTypes | N | Array of layout option type IDs, see [Option Types](#option-types)
config | Y | Config Object, see [Catalog Config For Instance](#catalog-config-for-instance)
blueprint | Y | [Blueprint](#blueprints) object, identified by id or name. Only applies to type: `blueprint`
appSpec | Y | App Spec YAML, see [App Spec For Blueprint](#app-spec-for-blueprint). Only applies to type: `blueprint`
workflow | Y | Operational [Workflow](#workflows) object, identified by id or name. Only applies to type: `workflow`
context | N | Context for running the workflow, determines if a target resource must be selected. `instance`,`server`, or `appliance`.


## Delete a Catalog Item Type

```shell
curl -XDELETE "$MORPHEUS_API_URL/api/catalog-item-types/:id" \
  -H "Authorization: BEARER $MORPHEUS_API_TOKEN"
```

> The above command returns JSON structure like this:

```json
{
  "success": true
}
```

Will delete a catalog item type. 

### HTTP Request

`DELETE https://api.gomorpheus.com/api/catalog-item-types/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the catalog item type
