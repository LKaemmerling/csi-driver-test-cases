## CSI Driver Issue 149

1. `kubectl apply -f volume.yml`
2. wait until `kubectl get pods -o wide | grep my-csi-app-vol-resize` shows `running`
3. `kubectl get pvc | grep csi-pvc-vol-resize` should show a volume with size 10G
4. You should also see the volume within the pod. `kubectl exec -it my-csi-app-vol-resize -- /bin/sh`
5. Within this shell with `df` you should see the volume with 20G
6. `kubectl apply -f volume_resized.yml`
7. `kubectl get pvc | grep csi-pvc-vol-resize` should show a volume with size 20G after a small amount of time
8. `kubectl get pvc | grep csi-pvc-vol-resize` should output the volume name similar to ` pvc-ec2b557b-8bed-4cd5-a848-c71a9081c74d` 
9. You can check in the Cloud Console if the volume `pvc-ec2b557b-8bed-4cd5-a848-c71a9081c74d` now has the size of 20G alternative you can use the hcloud CLI: `hcloud volume list | grep  pvc-ec2b557b-8bed-4cd5-a848-c71a9081c74d`
10. You should also see the volume within the pod. `kubectl exec -it my-csi-app-vol-resize -- /bin/sh`
11. Within this shell with `df` you should see the volume with 20G
