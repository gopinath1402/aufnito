commads:

kubectl.exe create -f .\python_canary_1-1.yaml
kubectl.exe create -f .\python_canary_1-2.yaml
kubectl.exe apply -f .\svc.yaml
kubectl.exe apply -f .\ingress.yaml

explaination:

Both deploymnet file has different version application. Canary deploymnet, once update version is stable. we can increase replica of lastest version application and reduce the old version application.