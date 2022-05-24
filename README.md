# Azure Service Bus Scripts
Scripts to support Azure Service Bus administration

## Prerequisites
- [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli)
- [yq](https://github.com/mikefarah/yq) for creating full service entities
- user has already signed into target Azure tenant with `az login --tenant TENANT`
- user has sufficient permissions to manage Azure Service Bus entities

All scripts include a help section that can be viewed by passing the `-h` or `--help` argument to the script.

## Services
Create or delete all Azure Service Bus entities for a service.

A service must have created a `.yaml` configuration file in `services/config`.

Example `.yaml`:

```
topics:
  - name: ffc-demo-payment
    subscriptions:
      - ffc-demo-payment-payment
      - ffc-demo-payment-payment-core
  - name: ffc-demo-schedule
    subscriptions:
      - ffc-demo-schedule-payment
      - ffc-demo-schedule-payment-core
queues:
  - name: ffc-demo-claim
  - name: ffc-demo-calculation
```

For session enabled queues, the `sessions: true` property can be included.

Example:

```
queues:
  - name: ffc-demo-claim
    sessions: true
```

### [Create](services/create)

#### Arguments
- `-g`, `--resource-group` - Service Bus Resource Group
- `-n`, `--namespace-name` - Service Bus Namespace
- `-s`, `--service` - service name
- `-d`, `--developer` - suffix to be appended to each entity (optional)
- `-x`, `--no-developer-subscriptions` - do not apply suffix to subscriptions (optional)
- `-h`, `--help` 

Example:

`./services/create -s ffc-demo -n myNamespace -g myResourceGroup`

Example with developer suffix:

`./services/create -s ffc-demo -n myNamespace -g myResourceGroup -d jw`

### [Delete](services/delete)
#### Arguments
- `-g`, `--resource-group` - Service Bus Resource Group
- `-n`, `--namespace-name` - Service Bus Namespace
- `-s`, `--service` - service name
- `-d`, `--developer` - suffix to be appended to each entity (optional)
- `-h`, `--help` 

Example:

`./services/create -s ffc-demo -n myNamespace -g myResourceGroup`

Example with developer suffix:

`./services/create -s ffc-demo -n myNamespace -g myResourceGroup -d jw`

## Queues
### [List](queues/list)
List all queues.

#### Arguments
- `-g`, `--resource-group` - Service Bus Resource Group
- `-n`, `--namespace-name` - Service Bus Namespace
- `-h`, `--help` 

Example:

`./queues/list -n myNamespace -g myResourceGroup`

### [Create](queues/create)
Bulk create queues from file.

Example file content:

```
test-entity1
test-entity2
```

#### Arguments
- `-g`, `--resource-group` - Service Bus Resource Group
- `-n`, `--namespace-name` - Service Bus Namespace
- `-f`, `--file` - filename containing entity names
- `-h`, `--help` 

Example:

`./queues/create -n myNamespace -g myResourceGroup -f example.txt`

### [Delete](queues/delete)
Bulk delete queues from file.

Example file content:

```
test-entity1
test-entity2
```

#### Arguments
- `-g`, `--resource-group` - Service Bus Resource Group
- `-n`, `--namespace-name` - Service Bus Namespace
- `-f`, `--file` - filename containing entity names
- `-h`, `--help` 

Example:

`./queues/delete -n myNamespace -g myResourceGroup -f example.txt`

## Topics
### [List](topics/list)
List all topics.

#### Arguments
- `-g`, `--resource-group` - Service Bus Resource Group
- `-n`, `--namespace-name` - Service Bus Namespace
- `-h`, `--help` 

Example:

`./topics/list -n myNamespace -g myResourceGroup`

### [Create](topics/create)
Bulk create topics from file.

Example file content:

```
test-entity1
test-entity2
```

#### Arguments
- `-g`, `--resource-group` - Service Bus Resource Group
- `-n`, `--namespace-name` - Service Bus Namespace
- `-f`, `--file` - filename containing entity names
- `-h`, `--help` 

Example:

`./topics/create -n myNamespace -g myResourceGroup -f example.txt`

### [Delete](topics/delete)
Bulk delete from file.

Example file content:

```
test-entity1
test-entity2
```

#### Arguments
- `-g`, `--resource-group` - Service Bus Resource Group
- `-n`, `--namespace-name` - Service Bus Namespace
- `-f`, `--file` - filename containing entity names
- `-h`, `--help` 

Example:

`./topics/delete -n myNamespace -g myResourceGroup -f example.txt`

