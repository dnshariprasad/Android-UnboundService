# Android Service #

Service is an application component that can perform time-consuming operations in the background and has no user interface.
Another component of the application can start a service, which will continue to work in the background, even when the user moves into another application.
In addition, the component can be attached to the service to interact with her ​​and even perform interprocess communication (IPC). For example, the service can process network transactions, to play music, perform input and output file, and all this in the background.

### In fact, the service can take two forms: ###

* Launched / Started / Unbound
* Tied / Bound

### Started Service ###

Service is "running" when a component of the application launches its challenge startService(). It runs in the background indefinitely. It is stopped by stopService() method. The service can stop itself by calling the stopSelf() method.

### Bound Service ###

Service is "bound" when an application component attached to her calling bindService().Tied service offers client-server interface that allows components to communicate with the service, send, receive results and even do it between different processes through inter-process communication (IPC). Tied service works only as long as it is tied to the other components of the application. Several components can be linked to the service at the same time, but when they all cancel the binding, the service is deleted.

### Who do I talk to? ###

* Repo owner or admin
* Other community or team contact