## CSI Driver Issue 150

https://github.com/hetznercloud/csi-driver/issues/150

CSI Driver Version: https://github.com/hetznercloud/csi-driver/commit/5f0c36c7113fa2815cda9d343d2d15662ff5af56 (latest commit)
CSI Driver Deployment File: https://raw.githubusercontent.com/hetznercloud/csi-driver/master/deploy/kubernetes/hcloud-csi-master.yml
k8s Version: v1.18

1. `kubectl apply -f storageclass.yml` - Create the custom storage class
2. `kubectl apply -f app.yml` - Create an app with the custom storage class
3. wait until `kubectl get pods -o wide | grep my-csi-app` shows `running`
4. `kubectl get pvc | grep csi-pvc` should show a volume with size 10G
5. You should also see the volume within the pod. `kubectl exec -it my-csi-app -- /bin/sh`
6. Within this shell with `df` you should see the volume
