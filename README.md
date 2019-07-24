cups-epilog
===========
Original source: http://mtm.cba.mit.edu/cups/cups-epilog/src/cups-epilog.c

CUPS driver for the Epilog Laser engraver  

Tested on Epilog Legend 24EX, probably works also on the Legend32.
 * Epilog Legend32 Laser  
  
 Description:  
 Epilog laser engraver  
  
 The Epilog laser engraver comes with a windows printer driver. This works  
 well with Corel Draw, and that is about it. There are other windows  
 applications, like inkscape, but these rasterise the image before sending to  
 the windows printer driver, so there is no way to use them to vector cut!  
  
 The cups-epilog app is a cups backend, so build and link/copy to
 But in order to have a backend which can be use with the provided PPD and set the 
 engraving option in the GUI, you need to use thew "epilog" script as backend.
 This one will hac^W extract the option from the ps file and pass it to the real
 backend. So put "epilog" in /usr/lib/cups/backend/epilog, and put 
 cups-epilog in the $PATH. 
  
 With this linux driver, vector cutting is recognised by any line or curve in  
 100% red (1.0 0.0 0.0 setrgbcolor).  
  
 Create printers using epilog://host/Legend where host is the  
 hostname or IP of the epilog engraver. Use the provided PPD when you setup the printer
 
 Uses gs to rasterise the postscript input.  
 URI is epilog://host/Legend
 
Installation:  
 ``gcc -o cups-epilog `cups-config --cflags` cups-epilog.c `cups-config --libs` ``

 http://www.cups.org/documentation.php/api-overview.html  

 Manual testing can be accomplished through execution akin to:  
 $ export DEVICE_URI="epilog://epilog-mini/Legend/rp=100/rs=100/vp=100/vs=10/vf=5000/rm=mono/af=0"  
 # ./epilog job user title copies options  
 $ ./epilog 123 jdoe test 1 options < hello-world.ps  
  
