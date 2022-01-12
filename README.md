# Service Bus Scripts
Scripts to support Azure Service Bus administration

## Scripts
### Prerequisites
- [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli)
- user has already signed into target Azure tenant with `az login --tenant TENANT`
- user has sufficient permission to manage Azure Service Bus entities
- [yq](https://github.com/mikefarah/yq) for creating full service entities

### Create
- [Queues](create/queues)
- [Topics](create/topics)

### Delete
- [Queues](delete/queues)
- [Topics](delete/topics)

## Service
Create or delete all Azure Service Bus entities for a service.

A service must have created a `.yaml` configuration file in `services/config`.

- [Create](services/create)
