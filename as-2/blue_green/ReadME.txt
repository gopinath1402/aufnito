commands:
kubectl.exe create -f .\python_blue_green_1-1.yaml
kubectl.exe create -f .\python_blue_green_1-2.yaml
kubectl.exe create -f .\ingress.yaml

---------
version 1.1 application is availble in /live (ex: http://<IP or domain >:port)
version 1.2 application is availble in /test (ex: http://< node port >:port) for testing. once version 1.2 is approved we need to cahnge the aufnito-blue-green service lable version into 1.2.
--------
sample commands to change the lable: 

for windows:
kubectl.exe patch service aufnito-blue-green -p '{\"spec\":{\"selector\":{\"version\":\"v1.2\"}}}' -n aufnito

for linux:
kubectl patch service aufnito-blue-green -p '{"spec":{"selector":[{"version":"v1.2"}]}}' -n aufnito


-------------------
Now we can delete version 1.1 deploymnet and aufnito-blue-green-test service

kubectl.exe get deploy aufnito-blue-green-1 -n aufnito  
