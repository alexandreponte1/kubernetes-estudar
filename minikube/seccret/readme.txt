#imperativo
kubectl create secret generic \
    app-secret --from-literal=DB_Host=mysql \
               --from-literal=DB_User=root  \
               --from-literal=DB_Password=passwrd


kubectl create secret generic \
    app-secret --from-file=app_secret.properties




#declarativo
kubectl apply -f secret-data.yml

Os dados dentro do arquivo secret devem estar em base64 pelo menos

❯ echo -n "mysql" | base64
bXlzcWw=
❯ echo -n "root" | base64
cm9vdA==
❯ echo -n "paswrd" | base64
cGFzd3Jk



❯ kubectl get secrets app-secret -o yaml
apiVersion: v1
data:
  DB_Host: bXlzcWw=
  DB_Password: cGFzd3Jk
  DB_User: cm9vdA==
kind: Secret
metadata:
  annotations:
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"v1","data":{"DB_Host":"bXlzcWw=","DB_Password":"cGFzd3Jk","DB_User":"cm9vdA=="},"kind":"Secret","metadata":{"annotations":{},"name":"app-secret","namespace":"default"}}
  creationTimestamp: "2024-08-30T15:28:05Z"
  name: app-secret
  namespace: default
  resourceVersion: "10763"
  uid: 8e5d32ba-8bec-4a75-8afa-3a9ad6e82998
type: Opaque