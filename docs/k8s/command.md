
### **`port-forward`**

```bash
kubectl port-forward nginx-deployment-7c79c4bf97-kkjr9 8080:80
# output
Forwarding from 127.0.0.1:8080 -> 80
Forwarding from [::1]:8080 -> 80

# --address 0.0.0.0 可以使转发的端口对所有主机都可访问
kubectl port-forward prometheus-server-574dbc6996-4j9j9 9090:9090 --address 0.0.0.0
#output
Forwarding from 0.0.0.0:9090 -> 9090
Handling connection for 9090
Handling connection for 9090
Handling connection for 9090
Handling connection for 9090
```
