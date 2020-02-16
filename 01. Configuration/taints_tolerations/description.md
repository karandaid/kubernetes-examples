Taints and tolerations work together to ensure that pods are not scheduled onto inappropriate nodes.

# TAINTS
One or more taints are applied to a node; this marks that the node should not accept any pods that do not tolerate the taints.

## Commands
### Syntax
#### Apply
* kubectl taint nodes node1 key1=value1:effect

#### Removing
* kubectl taint nodes node1 key1=value1:effect-

### Examples
#### Applying
* kubectl taint nodes foo dedicated=special-user:NoSchedule
* kubectl taint node -l myLabel=X  dedicated=foo:PreferNoSchedule
* kubectl taint nodes foo bar:NoSchedule

#### Removing
* kubectl taint nodes foo dedicated:NoSchedule-

### Update the taints on one or more nodes.
  *  A taint consists of a key, value, and effect. As an argument here, it is expressed as key=value:effect.
  *  The key must begin with a letter or number, and may contain letters, numbers, hyphens, dots, and underscores, up to
253 characters.
  *  Optionally, the key can begin with a DNS subdomain prefix and a single '/', like example.com/my-app
  *  The value is optional. If given, it must begin with a letter or number, and may contain letters, numbers, hyphens,
dots, and underscores, up to  63 characters.
  *  The effect must be NoSchedule, PreferNoSchedule or NoExecute.
  *  Currently taint can only apply to node.

# TOLERATIONS
Tolerations are applied to pods, and allow (but do not require) the pods to schedule onto nodes with matching taints.
Note:
## There are two special cases:

### An empty key with operator Exists matches all keys, values and effects which means this will tolerate everything.

```
tolerations:
- operator: "Exists"
```
An empty effect matches all effects with key key.
```
tolerations:
- key: "key"
  operator: "Exists"
```
