### Using CLI

Pydio Cells comes out-of-the-box with a powerful CLI (Command Line Interface) to control the services, integrate with the host system and perform admin tasks with no need for a graphical interface.

For instance, you can simply launch the server from a terminal by typing:  
`$ ./cells start`  
or for Enterprise edition  
`$ ./cells-enterprise start`  

_Note: it is not the correct way of launching the application when running in production mode, as it will exit when closing the terminal._

In the rest of this section, when showing terminal commands, we will assume that:

- You are in the folder as the binary file _or_ that the application has been installed in the `PATH` of your operating system.
- You are using Pydio Cells Home Edition. For this matters, both versions are pretty the same, just replace `cells` by `cells-enterprise`.

Pydio Cells comes also with an extended command line tools, `cells-ctl` that is a simple but full fledge client offering most of the important end-user features that can be found in the web interface. You will find more information about this tools in the corresponding section of the _Advanced_ chapter.

### Commands List

```
$ ./cells --help

Usage:
  ./cells [flags]
  ./cells [command]

Available Commands:
  config      Configuration Manager
  doc         Generate ReST documentation for this command
  help        Help about any command
  install     Pydio Cells Installer
  install-cli Pydio Cells Command-Line Installer
  list        List all available services and their statuses
  start       Start Cells services
  stop        Stop one or more services
  update      Check for available updates and apply them
  version     Display current version of this software

Flags:
      --fork               Used internally by application when forking processes
      --grpc_cert string   Certificates used for communication via grpc
      --grpc_key string    Certificates used for communication via grpc
  -h, --help               help for ./cells
      --log string         Sets the log level mode (default "info")
      --registry string    Registry used to manage services (default "nats")

Use "./cells [command] --help" for more information about a command.

```


**Launch the installation process** (and optionnaly completely go through it, with thus no need for a graphical interface to install Pydio)

`./cells install`

**Start and the server** or a given service:

```
# For instance, to enable debug mode
./cells start --log debug

# Start just a couple of services
./cells start nats pydio.grpc.config pydio.api.proxy

# Start all services except one, here the dav server
./cells start -x pydio.rest.gateway.dav
```

**Display Configuration** of the running instance.

`./cells config list`

That is among others handy to retrieve the default credential used by the front end to communicate with the backend.

**List Services**: Pydio Cells is built following principles of the Micro Service architecture, having each part of the application communicating with the rest via messages and auto discovery using a registry. To see the currently running services, use the 'list' command: 

```
$ ./cells list

 GENERIC SERVICES                           
 # discovery                                
 nats                            [X]        
 # frontend                                 
 pydio.api.front-plugins         [X]        
 # gateway                                  
 micro.api                       [X]        
 pydio.api.websocket             [X]        
 pydio.rest.gateway.dav          [X]        
 pydio.rest.gateway.wopi         [X]        
                                            
 GRPC SERVICES                              
 # broker                                   
 pydio.grpc.activity             [X]        
 pydio.grpc.chat                 [X]        
 pydio.grpc.log                  [X]        
 pydio.grpc.mailer               [X]        
 # data                                     
 pydio.grpc.data-key             [X]        
 pydio.grpc.docstore             [X]        
 pydio.grpc.meta                 [X]        
 pydio.grpc.search               [X]        

[...]

```

You can access a real time list of the services known by the application and there status.

For additional information, we strongly encourage you to refer to the manual page that can be found in-line: `./cells --help`