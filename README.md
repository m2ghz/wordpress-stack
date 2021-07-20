# wordpress-stack
Install Ingress Controller:

1: wget https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.47.0/deploy/stat
ic/provider/baremetal/deploy.yaml

2:  kubectl apply -f deploy.yaml
Watch ingress-controller progress:

3:  kubectl get pods -n ingress-nginx   -l app.kubernetes.io/name=ingress-nginx --watch
Verify ingress-controller version:

4:  POD_NAMESPACE=ingress-nginx

5:  POD_NAME=$(kubectl get pods -n $POD_NAMESPACE -l app.kubernetes.io/name=ingress-nginx --field-
selector=status.phase=Running -o jsonpath='{.items[0].metadata.name}')

6:  kubectl exec -it $POD_NAME -n $POD_NAMESPACE -- /nginx-ingress-controller --version

7: Configure NFS server on network and export 10G/5G/2G part

8: deploy all configMap and secret

9: deploy pv.yaml and pvc.yaml for claim volume

10: For deploy wordpress and mysql:

deploy wordpress-mysql.yaml

11: For deploy other tools like phpmyadmin, filebrowser and mailserver(post.io):
deploy tools.yaml


