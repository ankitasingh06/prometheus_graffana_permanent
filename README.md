# prometheus_grafana_permanent

Hello reader!!

•Aim:-This task is based on making the content of prometheus and grafana permanent

•Theory:-
‣ Prometheus:- Prometheus is an open-source systems monitoring and alerting toolkit originally built at SoundCloud.  It is now a standalone open source project and maintained independently of any company. To emphasize this, and to clarify the project's governance structure.Prometheus works well for recording any purely numeric time series. It fits both machine-centric monitoring as well as monitoring of highly dynamic service-oriented architectures. In a world of microservices, its support for multi-dimensional data collection and querying is a particular strength.

‣ Grafana :- Grafana is open source visualization and analytics software. It allows you to query, visualize, alert on, and explore your metrics no matter where they are stored. In plain English, it provides you with tools to turn your time-series database (TSDB) data into beautiful graphs and visualizations.

• Solution :-
In the repository , there is all required and used program files(.yml files) which we will use to create PV(Persistent Volume), PVC(Persistent Volume Claim) and deployment for the both Prometheus and Grafana server.

   Created Job1 for Prometheus:-

-> step1:- Create PV for prometheus:-
   kubectl create -f pv_prom.yml
   
-> step2 :- Create PVC for prometheus:-
   kubectl create -f pvc_prom.yml

-> step3 :- Create Deployment for launching prometheus:-
   kubectl create -f prom-deploy.yml
   
 -> step4 :-  For exposing both the servers, so that outer world can access them :-
    for prometheus:-
   kubectl expose deployment prom_deploy --port=9090 --type=NodePort
   
   ![Screenshot (760)](https://user-images.githubusercontent.com/60088271/89267375-c6418100-d654-11ea-8763-72d191b34fe0.png)
   
   
   ---------------------------------------------------------------------------------------
   
   Created Job2 for Grafana:-
   
-> step1 :- Create PV for grafana:-
   kubectl create -f pv_grafana.yml
   
-> step2 :- Create PVC for grafana:-
   kubectl craete -f pvc_garfana.yml

-> step3 :- Create Deployment for launching grafana :-
   kubectl create -f grafana-deploy.yml
   
-> step4 :- 
  For exposing both the servers, so that outer world can access them :-
   
   for grafana:-
   kubectl expose deployment grafana_deploy --port=3030 --type=NodePort
   
   
   ![Screenshot (759)](https://user-images.githubusercontent.com/60088271/89267455-e2ddb900-d654-11ea-9d07-ceb2c64c3ce6.png)
   
   -----------------------------------------------------------------------------------------
   
-> Step5:-
  For getting the port no. of both the servers:-
   kubectl get all
   
   ![Screenshot (755)](https://user-images.githubusercontent.com/60088271/89267234-94301f00-d654-11ea-87a8-af461ed66223.png)

   
 -> Step6 :- Now we have to add URL of grafana server running on that port no. so that prometheus will get integrated with grafana,
      for thsi we have to access "prometheus.yml" file by going inside the pod and enter location of grafana
      
 Below is the Screenshot of running Prometheus server
 
 ![Screenshot (761)](https://user-images.githubusercontent.com/60088271/89268059-a3fc3300-d655-11ea-8b15-ee173d6e8039.png)
 
 Below is the Screenshot of running Grafana server
 
 ![Screenshot (762)](https://user-images.githubusercontent.com/60088271/89268136-bd9d7a80-d655-11ea-9a34-ffd78a04fc2a.png)
 
 * Bydefault username and password of grafana is => "admin/admin".
 After enter login details and updating your password, below is the front dashboard Screen shot of Grafana
 
 ![Screenshot (763)](https://user-images.githubusercontent.com/60088271/89268358-11a85f00-d656-11ea-87a3-b224b5515ab3.png)

 
 Below is screen shot of Build pipeline view :-
 
 ![Screenshot (758)](https://user-images.githubusercontent.com/60088271/89267330-b4f87480-d654-11ea-9ed8-0c0faae9237f.png)

 
 
 
   
