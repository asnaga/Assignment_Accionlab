# Assignment_Accionlab
#Kubernetes StatefulSet

(Best practice is to keep State yaml and PV yaml seperate namespace for better mangmnt.)

yaml
----
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: my-stateful-app
spec:
  servceName: my-service
  replicas: 4
  selector:
    matchLabels:
      app: my-stateful-app
    template:
      metadat:
        labels:
          app: my-stateful-app
      spec:
        containers:
        - name: my-contaner
          image: my-app:latest
          port:
          - containerPort: 8080
          resources:
            requests:
              memory: "512Mi"
              cpu: "250m"
            limits:
              memory: "1G"
              cpu: "500m"
            volumeMounts:
            - name: data-volume
              mountPath: /data
  volumeClamTemplates:
  -  metadata:
       name: data-volume
     spec:
       accessModes: ["ReadWriteOnce"]
       resources:
         requests:
           storage: 10Gi
       storageClaimName: standard
     updateStrategy:
       type: RollingUpdate


            

            
