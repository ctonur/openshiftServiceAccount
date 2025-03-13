# OpenShift ServiceAccount README dosyasına root yetkisi ekleme

sa_readme_update = """\
---

## **📌 5. Pod’a Root Yetkisi Vermek (Privileged Mode)**  

Kubernetes ve OpenShift, güvenlik nedeniyle pod’ları varsayılan olarak **root yetkisi olmadan** çalıştırır. Ancak bazı özel durumlarda root yetkisi vermek gerekebilir.  

### **1️⃣ Security Context ile Root Yetkisi Vermek**  
Pod veya container için `securityContext` kullanarak **root yetkisiyle** çalışmasını sağlayabilirsin:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: privileged-pod
  namespace: my-namespace
spec:
  containers:
  - name: my-container
    image: ubuntu
    command: ["sleep", "3600"]
    securityContext:
      runAsUser: 0 # Root kullanıcısı olarak çalıştır
      privileged: true # Tam yetkili mod (dikkatli kullan)
