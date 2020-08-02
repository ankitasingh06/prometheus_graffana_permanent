# prometheus_grafana_permanent

Hello reader!!

•Aim:-This task is based on making the content of prometheus and grafana permanent

•Theory:-
‣ Prometheus:- Prometheus is an open-source systems monitoring and alerting toolkit originally built at SoundCloud.  It is now a standalone open source project and maintained independently of any company. To emphasize this, and to clarify the project's governance structure.Prometheus works well for recording any purely numeric time series. It fits both machine-centric monitoring as well as monitoring of highly dynamic service-oriented architectures. In a world of microservices, its support for multi-dimensional data collection and querying is a particular strength.

‣ Grafana :- Grafana is open source visualization and analytics software. It allows you to query, visualize, alert on, and explore your metrics no matter where they are stored. In plain English, it provides you with tools to turn your time-series database (TSDB) data into beautiful graphs and visualizations.

• Solution :-
In the repository , there is all required and used program files(.yml files) which we will use to create PV(Persistent Volume), PVC(Persistent Volume Claim) and deployment for the both Prometheus and Grafana server.

-> step1:- Create PV for prometheus:-
   kubectl create -f pv_prom.yml
   
-> step2 :- Create PVC for prometheus:-
   kubectl create -f pvc_prom.yml

-> step3 :- Create Deployment for launching prometheus:-
   kubectl create -f prom_deploy.yml
   
-> step4 :- Create PV for grafana:-
   kubectl create -f pv_grafana.yml
   
-> step5 :- Create PVC for grafana:-
   kubectl craete -f pvc_garfana.yml

-> step6 :- Create Deployment for launching grafana :-
   kubectl create -f grafana_deploy.yml
   
-> step7 :- 
  For exposing both the servers, so that outer world can access them :-
    for prometheus:-
   kubectl expose deployment prom_deploy --port=9090 --type=NodePort
   
   for grafana:-
   kubectl expose deployment grafana_deploy --port=3030 --type=NodePort
   
-> Step8:-
  For getting the port no. of both the servers:-
   kubectl get all
   
 -> Step9 :- Now we have to add URL of grafana server running on that port no. so that prometheus will get integrated with grafana,
      for thsi we have to access "prometheus.yml" file by going inside the pod and enter location of grafana
      
 Below is the Screenshot of running Prometheus server
 
 
 Below is the Screenshot of running Grafana server
 
   
