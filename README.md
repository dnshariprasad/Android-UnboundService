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

* These two types of services are discussed separately, the service can work both ways - it can be launched (and work indefinitely) and to allow binding. It depends on the implementation of couples callback methods: onStartCommand () allows components to run the service, and onBind () allows you to snap.

### Service Lifecycle Methods ###

* ** onStartCommand ()**
The system calls this method when another component, such as the operation requesting the launch of the service, causing **startService ()** . After executing this method, the service is started and can run in the background indefinitely. If you implement this method, you have to stop the service by calling **stopSelf ()** or** stopservice ()** . (If you only want to provide binding, to implement this method is not required).

* **onBind ()**
The system calls this method when the other component wants to bind to the service (for example, to perform a remote procedure call) by calling **bindService()**. In your implementation of this method, you must provide an interface that clients use to interact with the service, returning IBinder . It is always necessary to implement this method, but if you do not want to allow binding, you must return a value of null.

* **onCreate ()**
The system calls this method when you first create the service to perform the one-time setup procedure (before calling onStartCommand () or onBind () ). If the service is already running, this method is not called.

* **onDestroy ()**
The system calls this method, when the service is no longer used and is carried out to destroy it. Your service must implement this resource for cleaning, such as streams, registered receivers, receivers and so on. D. This is the last call, which gets service.

### Service & IntentService ###

**Service**

This is the base class for all services. When you inherit from this class, it is important to create a new thread, which will be carried out all the work of the service as the default service uses the main thread of your application that can slow down any operation that fulfills your application.

**IntentService**

This is a subclass of the Service , which uses a workflow for handling all queries run alternately. This is the best option if you do not need to have your office to handle multiple requests simultaneously. It is enough to implement a method onHandleIntent () , which receives the intention for each query is run, allowing you to perform the background operation.
The following sections describe how to implement the service using any of these classes.

Class IntentService does the following:

* It creates a work queue that conveys the intentions of one implementation of the method in your onHandleIntent () , so **you do not have to worry about threading**.
* It stops the service after all the running queries, so you **never need to call stopSelf ()** .
* Provides an implementation of the method **onBind () by default, which returns null**.
* It provides an implementation of the method onStartCommand () by default, which sends the intention of the work queue, and then in your implementation **onHandleIntent ()** .

All of this means that you only need to implement a method onHandleIntent () to do the job, provided by the customer. (Although, in addition, you must provide a constructor for a small service).