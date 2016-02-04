By using this library you can focus on implementing protocol and logic, instead of spending countless hours of writing and debugging asynchronous, non blocking, high performance socket routines.

This project came into existence while i was writing a new, ground breaking IRC chat web application.

To deal with 1000's of concurrent, always on (comet aka hanging iframe) http (server) connections, and an equal amount of IRC client connections, plus being able to interpret and parse and delegate all the messages and events, i needed a very fast, stable, flexible and easy to use 'daemon' library for PHP.

However no such thing existed yet, hence this library was created.

The tarbal includes a demo HTTP server implimentation, which will give you a good impression of what its capable off, and how to use this library.

To create a server is as simple as 3 lines of code, for example for our http server:
$daemon = new socketDaemon();
$server = $daemon->create\_server('httpdServer', 'httpdServerClient', 0, 2001);
$daemon->process();

And then a class implementation which deals with the on\_read and on\_disconnect events.

The socket library takes care of the rest of the IO management (using a socket select loop), read and write buffering (for full asynchronous, non blocking communication) and resource management.

Creating a client with this framework is just as simple:

$client = $daemon->create\_client('myClientClass', 'remote.com', 80);

And then implimenting a socketClient class, ie:
class myClientClass extends socketClient {
.. deal with on\_read, on\_write, on\_connect and on\_disconnect..
}

Enjoy!