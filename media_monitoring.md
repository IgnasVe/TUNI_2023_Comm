## Device transmits radio waves with almost no power—without violating the laws of physics


**Group 10**

Ignas Vezikauskas, Yukyeong Kim, Ritwik Guha  


Device transmits radio waves with almost no power—without violating the laws of physics  
JANUARY 24, 2023  
by Joshua R. Smith and Zerina Kapetanovic. University of Texas, Austin 

Link to article: https://techxplore.com/news/2023-01-device-transmits-radio-powerwithout-violating.html


**Abstract**

This news article introduced a new ultra-low-power method of communication, it is possible to transmit information wirelessly, simply by opening and closing a switch that connects a resistor to an antenna. 

This system, combined with techniques for harvesting energy from the environment[1], could lead to all kinds of devices that transmit data without battery or other power sources. Apart from the energy needed to flip the switch, no other energy is needed and in this system the switch is a transistor, an electrically controlled switch with no moving parts consuming small amount of power. Powered signal source (like oscillator) is not needed, instead random thermal noise(Johnson noise) can take the palce of the signal driving the antenna[2].

Figure.  
<img src="https://user-images.githubusercontent.com/25344978/218174612-9f9477be-c5ee-4bb4-9c55-549b4749442e.png" width="300">


**Analysis**

Article mentions about arguments between peer reviewer and research team that their method did violate the second law of thermodynamics or not, but our interest is communication not thermodynamics, so we skip this part, let's accpet that it did not break the law. Briefly in this new ultra-low-power method, like other low-power communication systems, transmitter consumes barely amount of energy, on the other hand receiver consumes good amount of power, which (base station) has usually no problem with power supply. 

Main advantage of this new method is that there is no need strong external radio signal to be exposed to the patient, which may cause physical damage. And they believe that related ideas enalbe new forms of communication can be modulated using thermal noise from biological tissue or other electronic components. Application areas are tiny sensors and implated medical devices and contactless credit cards and so on.

Design of a powering system is one of the main challenges in implantable medical device (IMD) development[3].These implatable medical devices(IMD) should meet some basic requirements such as safety, size constraints and reliability. 


IMD POWERING: STATE OF THE ART
Today, the established methods of IMD powering can be divided into the three classes. First one associated with the use of the implantable chemical sources. It is the optimal solution, but it can be implemented only for the IMDs with low power consumption (100 uW) and in the cases when there is enough room for implants. It is the common solution for pacemakers and implantable defibrillators. A second technique implies inductive powering. In this case continuous powering of the passive implant should be distinguished from the recharging of the implantable batteries.
First method is used for cochlear implants, second one is the common powering techniques for spinal cord stimulators. Finally, for the mechanical circulatory systems the external rechargeable batteries are used which are connected to the implant via percutaneous cables.
Existing problems in this field can be summarized as follows:
– it is desirable to have microimplants in the case of the IMD with low power consumption;
– it is necessary to reduce the risks of the burns and general tissue overheating in the course of charging of the spinal cord stimulators;
– it is necessary to obtain reliable solution for the wireless powering of the mechanical circulatory support systems since the driveline infections represent one of the main menaces for the patients.


**need to study**
Article notes that Backscatter[3] ...


Limitation of this system is that it has lower data rate and lower range than either backscatter radios or conventional radios. So improvement of those features should be achieved to be used in real applications such as implanted devices. They highlight that their work may lead to new connection between thermodynamics and communication technology suggesting literal connections.


**References**

1) Bruno Clerckx, Rui Zhang, Robert Schober, Derrick Wing Kwan Ng, Dong In Kim, H. Vincent Poor. (2019). Fundamentals of Wireless Information and Power Transfer: From RF Energy Harvester Models to Signal and System Designs. IEEE Journal on Selected Areas in Communications   (Volume: 37, Issue: 1, pp4-33, January).  
Limited access at https://ieeexplore.ieee.org/document/8476597

2) Zerina Kapetanovic, Miguel Morales, Joshua R. Smith. (2022). Communication by means of modulated Johnson noise. Proceedings of the National Academy of Sciences.(Volume 119, No. 49).   
Limited access at https://doi.org/10.1073/pnas.2201337119

3) A. A. Danilov. (2019). Powering of implantable medical devices: History, current status and prospects. XIV RUSSIAN-GERMANY CONFERENCE ON BIOMEDICAL ENGINEERING (RGC-2019). DOI:10.1063/1.5121941  
Available at https://www.researchgate.net/publication/335145265_Powering_of_implantable_medical_devices_History_current_status_and_prospects

4) Vincent Liu, Aaron Parks, Vamsi Talla, Shyamnath Gollakota, David Wetherall, Joshua R. Smith. (2013). Ambient backscatter: wireless communication out of thin air. ACM SIGCOMM Computer Communication Review. (Volume 43, Issue 4, pp39–50, October)   
Available at https://dl.acm.org/doi/pdf/10.1145/2486001.2486015

Adopted method and its implementation influenced size, reliability and safety of the IMD. Implantable autonomous chemical energy source represent the optimal solution, but its implementation is severely restricted by size constraints and it can be implemented only for devices which consume about 0.1 mW. Thus, wireless powering and energy harvesting attract attention of the community. 
