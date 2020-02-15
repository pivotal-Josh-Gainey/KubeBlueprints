# KubeBlueprints

Kubernetes objects and attributes map

Simply performed with the following little script.

```java
mkdir kube-blueprints && cd kube-blueprints
for resource in `kubectl api-resources -o name`
do
    name=$(echo "$resource" | cut -d '.' -f 1)
    echo "Starting $name"
    kubectl explain $name --recursive > "$name"_blueprint.yaml
    echo "Finished $name"
done
```
