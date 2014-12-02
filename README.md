Docs
====

## Best practices

### 12factor

All repositories must follow the [12factor](http://12factor.net) guidelines.

### Service Discovery

All service instances register themselves to a Domain Name which can be resolved to a FQDN.

**Example:**

| Service | Local Domain Name | Domain | FQDN | Call Example |
| ------- | ----------------- | ---- | ---- | ---- |
| myservice | myservice | mydomain.com | myservice.mydomain.com | `GET myservice.mydomain.com/apicall` |
| someservice | someservice | mydomain.com | someservice.mydomain.com | `POST someservice.mydomain.com/apicall` |
| mongod | mongodb | stateful.mydomain.com | mongodb.stateful.mydomain.com | `mgo.connect('someservice.mydomain.com/apicall')` |

### Stateful service guideline

Stateful (or persistent) services like MongoDB or Cassandra exist once per environment. Most stateful service have the ability to handle workspaces ("database" in mysql), so only one service is required.
