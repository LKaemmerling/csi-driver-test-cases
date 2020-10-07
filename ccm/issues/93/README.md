## CCM Issue 93

https://github.com/hetznercloud/hcloud-cloud-controller-manager/issues/93

CCM Version: https://github.com/hetznercloud/hcloud-cloud-controller-manager/commit/ab348452278822030a4cdfd17dacabb991fa29c5 (latest commit)
CCM Deployment File: https://raw.githubusercontent.com/hetznercloud/hcloud-cloud-controller-manager/ab348452278822030a4cdfd17dacabb991fa29c5/deploy/ccm-networks.yaml
k8s Version: v1.19


1. `kubectl apply -f deployment.yml`
2. `kubectl apply -f service.yml`
3. After a few seconds the service should have a public IP. You can access this IP and then see a response from nginx.
4. Run `kubectl scale --replicas=2 deployment nginx-hello-world`
5. Health Checks should still work
6. When running `kubectl get pods` you should see pods like `nginx-hello-world-54f8cdd6fc-z8rzk`
7. When accessing the LB IP you should be able to see the pod IP as `Server address` like:
```
Server address: 10.244.1.197:80
Server name: nginx-hello-world-54f8cdd6fc-z8rzk
Date: 07/Oct/2020:13:37:46 +0000
URI: /
Request ID: 4ae61d8cb7f1694d266c8f7d30e0f4ba
```