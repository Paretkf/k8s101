Note

Kubernetes
- Cross server deployment

problem
- Docker compose ถ้าต้องการ deploy ไปหลายๆ server ต้อง shel ไปหลาย ๆ server
- Docker มี Docker swam ได้ความนิยมน้อยกว่า k8s โดย Google
- k8s จะทำให้ Deploy Docker ได้หลาย ๆ server
- k8s เป็นตัวจัดการ เรียกว่า kube cluster
- ในแต่ละ Cluster จะมี kube master 1 เครื่ิอง
- server แต่ละเครื่อง จะมี kubelet ทำงาน เป็นตัวจัดการ worker

Kube master
- kube api
- ใช้ cmd -> kubectl connect kube api (CRUD)

Pod
- unit ที่เล็กที่สุดใน k8s

Deployment
- กำหนดให้ k8s สร้าง pod
- กำหนดให้ pod ใช้ img อะไรกี่ pod
- เช่น สร้าง 3 replica set จะไปสร้าง pod 3 pod
- k8s จะจัดการ pod เมื่อมีไม่ครบตามที่ตั้งค่าไว้แล้วถ้าหากมี pod ไหนล่ม ตัว k8s จะไปจัดการให้

Namespace
- ห้องที่อยู่ของ Pod
- ตั้งตามชื่อ service
- แบ่งทรัพยากรบน cluster

Service
- มีหลายชนิด เช่น cluster IP ทำ load balance
- กำหนด
- จะให้ pod อื่นมา connect ได้
- headless server (cluster Ip = none) ใช้ ได้แค่ pod เดียว เช่น Database
- node port ทำให้ service connect ได้
- ingress ทำหน้าที่ forward 80 หรือ 443 ไปที่ service (domain:80, domain:443)
- ingress กำหนด rules ได้เช่น /api ให้ไป serviceA / ไปที่ serviceB

ขอดู cluster ที่ kubectl connect อยู่
```bash
$ kubectl get node
```

ขอดู cluster namespace
```bash
$ kubectl get ns
```

ขอดู pod ใน namespace
```base
$ kubectl get po -n ingress-nginx
```

ขอดู service
```bash
$ kubectl get svc -n ingress-nginx
```