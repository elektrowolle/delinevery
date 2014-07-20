#delinevery


A line following delivery bot

##Basic concept

The robot is following a line till it detects a qrcode. QR-Codes can be 
seen as nodes. These nodes can represent:

* junction
* waiting position
* delivery/pick up target 
* elevator point. 
* A charging point

If the robot meets a qrcode it will read it out, scan the orientation 
of the code and decide what to do. Actions could be either(Sorted by priority):

* Announce to god that the robot arrived at the qr code and where he started (this will be used for measuring timespans between different locations and better pathfinding)
* Wait for requested interaction if requested
 * pick up delivery
 * place delivery
* ask god (robot server) for an outstanding user request
* rotate
 * if delivery is waiting or package is contained rotate into direction of shortest path to target
 * else explore for new directions
* follow the line to next qr-code

A server called god can be accessed by an web app to call the robot for a new 
parcel to be delivered. After a delivery is inquired an email will be sent 
to the receipent with a request of avaibility for picking up the delivery in an 
estimated time. The receiver may reply that he won't be avaible at that time 
and make a new later offer which will be send to the origin if the person is 
not available for the certain time. If both partys agree the request will be 
queued and the robot will be send to pick up and deliver the package at the 
specific time.

##Dependencies
* [ZXING](https://github.com/zxing/zxing) qr decoding and encoding library (Calculate the [orientation](http://stackoverflow.com/questions/7842705/android-zxing-orientation-resultmetadata-is-null-get-rotation-orientation) of an qr code)
* Lego Mindstorms NXT and [Lejos](http://www.lejos.org/nxj.php)(java for mindstorms) for a quick robot test model
* raspberry pi with arch linux as the brain
 * [Creative](http://elinux.org/RPi_USB_Webcams) [Live](http://www.saturn.de/mcs/product/CREATIVE-Live-Cam-Sync-HD,48352,241195,583541.html?langId=-3) for qrcode detection (and possibly later line detection)
* appengine for hosting god
 
##TODO

* [ ] Modeling
 * [ ] Building a Lego Model, capable of carrying small loads, a battery and a raspberry pi
 * [ ] A real robot capable of transporting heavier loads
* [ ] Programming a hardware interface
 * [ ] working with lego
 * [ ] working with better hardware
* [ ] implement line following
* [ ] implement stop at qr codes
* [ ] implement qr code orientation reading
* [ ] implement explore mode
* [ ] implement basic god api
 * [ ] announcing qr codes
 * [ ] request for orientation for the path


