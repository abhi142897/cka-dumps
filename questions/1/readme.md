Create a pod called web-pod using image nginx, expose it internally with a service called web-pod-svc.
Check that you are able to lookup the service as well as pod from within the cluster.
Use Image busybox:1.28 for  a new nslookup pod to cross verify and record results in web-svc.svc and web-pod.pod


solution -

k run web-pod --image=nginx --port 80                                  #creat a pod
k expose pod web-pod --name=web-svc --port 8082 --target-port 80       #expose svc on port 8082

curl <svc_ip>:8082   #lookup for svc from any node/pod in cluster.

k run busy-pod --image=busybox -- sleep 3600   #create new busybox pod

curl <svc_ip>:8082  #lookup for svc from new busybox pod
                                                  
