---
layout: "huaweicloud"
page_title: "HuaweiCloud: huaweicloud_ges_graph_v1"
sidebar_current: "docs-huaweicloud-resource-ges-graph-v1"
description: |-
  graph management
---

# huaweicloud\_ges\_graph\_v1

graph management

## Example Usage

### create an empty graph

```hcl
resource "huaweicloud_networking_secgroup_v2" "secgroup" {
  name = "terraform_test_security_group"
  description = "terraform security group acceptance test"
}

resource "huaweicloud_ges_graph_v1" "graph" {
  availability_zone = "{{ availability_zone }}"
  graph_size_type = 0
  name = "terraform_ges_graph_test"
  region = "{{ region_name }}"
  security_group_id = "${huaweicloud_networking_secgroup_v2.secgroup.id}"
  subnet_id = "{{ network_id }}"
  vpc_id = "{{ vpc_id }}"
}
```

## Argument Reference

The following arguments are supported:

* `availability_zone` -
  (Required)
  Indicates availability zone.  Changing this parameter will create a new resource.

* `graph_size_type` -
  (Required)
  Indicates the graph size type.   0: indicates 10 thousand edges.   1:
  indicates 1 million edges.   2: indicates 10 million edges.   3:
  indicates 100 million edges.   4: indicates 1 billion edges.   5:
  indicates 10 billion edges.   6: indicates 100 billion edges.  Changing this parameter will create a new resource.

* `name` -
  (Required)
  Indicates the graph name.  Changing this parameter will create a new resource.

* `region` -
  (Required)
  Indicates the region code.  Changing this parameter will create a new resource.

* `security_group_id` -
  (Required)
  Indicates the security group ID.  Changing this parameter will create a new resource.

* `subnet_id` -
  (Required)
  Indicates the subnet ID in the specified VPC.  Changing this parameter will create a new resource.

* `vpc_id` -
  (Required)
  Indicates the VPC ID.  Changing this parameter will create a new resource.

- - -

* `auto_assign` -
  (Optional)
  Indicates whether to assign a new eip to the graph automatically.  Changing this parameter will create a new resource.

* `eip_id` -
  (Optional)
  Indicates the ID of an EIP.  Changing this parameter will create a new resource.

## Attributes Reference

In addition to the arguments listed above, the following computed attributes are exported:

* `created` -
  Indicates the time when a graph is created.

* `edgeset_path` -
  Indicates the OBS path of the edge data set. Structure is documented below.

* `private_ip` -
  Indicates the private network access address of a graph instance.
  Users can access the instance using the IP address through the ECS
  deployed on the private network.

* `public_ip` -
  Indicates the public network access address of a graph instance.
  Users can access the instance using the IP address from the Internet.

* `schema_path` -
  Indicates the path for storing the metadata file. Structure is documented below.

* `version` -
  Indicates the graph version.

* `vertexset_path` -
  Indicates the OBS path of the vertex data set. Structure is documented below.

The `edgeset_path` block contains:

* `path` -
  Indicates the OBS storage path, excluding OBS endpoint.

* `status` -
  Indicates the OBS file import status:   success: Imported
  successfully.   partiallyFailed: Partially failed.   failed:
  Failed to import the file.

The `schema_path` block contains:

* `path` -
  Indicates the OBS storage path, excluding OBS endpoint.

* `status` -
  Indicates the OBS file import status:   success: Imported
  successfully.   partiallyFailed: Partially failed.   failed:
  Failed to import the file.

The `vertexset_path` block contains:

* `path` -
  Indicates the OBS storage path, excluding OBS endpoint.

* `status` -
  Indicates the OBS file import status:   success: Imported
  successfully.   partiallyFailed: Partially failed.   failed:
  Failed to import the file.

## Timeouts

This resource provides the following timeouts configuration options:
- `create` - Default is 30 minute.
- `delete` - Default is 30 minute.
