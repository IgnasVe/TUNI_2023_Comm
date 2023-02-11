## Device transmits radio waves with almost no power—without violating the laws of physics


**Group 10**

Ignas Vezikauskas, Yukyeong Kim, Ritwik Guha  


Device transmits radio waves with almost no power—without violating the laws of physics  
JANUARY 24, 2023  
by Joshua R. Smith and Zerina Kapetanovic. University of Texas, Austin 

Link to article: https://techxplore.com/news/2023-01-device-transmits-radio-powerwithout-violating.html


**Abstract**

This news article introduced a new ultra-low-power method of communication, which makes it possible to transmit information wirelessly, simply by opening and closing a switch that connects a resistor to an antenna. 

This system, combined with techniques for harvesting energy from the environment[1], could be the foundation to all kinds of devices that transmit data without a battery or other power sources. Apart from the energy needed to flip the switch, no other energy is needed. This system uses the switch as a transistor, an electrically controlled switch with no moving parts consuming a small amount of power.A Powered signal source (like an oscillator) is not needed, instead random thermal noise(Johnson noise) can take the place of the signal driving the antenna[2].

Figure.  
<img src="https://user-images.githubusercontent.com/25344978/218174612-9f9477be-c5ee-4bb4-9c55-549b4749442e.png" width="300">


**Analysis**

Article mentions arguments between peer reviewers and the research team that their method violated the second law of thermodynamics, but our interest is communication not thermodynamics, so we skipped this part, so for ease of understanding let's accept that it did not break the law. To put it briefly, in this new ultra-low-power method, like other low-power communication systems, a transmitter consumes a miniscule amount of energy, and on the other hand, the receiver consumes a hefty load of power, which is not considered a problem, since it (the base station) is often built with a much more powerful power supply. 

One of the main challenges is the design of the powering system, such as the one in an implantable medical device (IMD)[3]. These implantable medical devices(IMDs) should meet basic requirements such as safety, size constraints and reliability. 

Today the established methods of IMD powering can be divided into three categories. One is the use of implantable chemical sources, second is inductive powering and the third method is mechanical circulatory systems using external, rechargeable batteries, connected to the implant via percutaneous cables. The most prevalent challenges in this area are reducing the risks of the burns and general tissue heating during the charging, for example, spinal cord stimulators and obtaining  a reliable solution for the wireless powering of the mechanical circulatory support systems. 

The main advantage of this new method is that there is no need for a strong external radio signal, which could cause harm to the patient. The authors of the article believe that related ideas enable new forms of communication, which could be modulated using thermal noise from biological tissue or other electronic components. Application areas are tiny sensors, implated medical devices and contactless credit cards, and a potential foundation for a new era of satellite communication.

Ambient backscatter (known as RF backscatter) is a communication principle, where devices communicate by reflecting ambient radio frequency signals created by devices such as radio, television and mobile phones, therefore removing the neccessity for a battery or a power grid connection[4]. Backscattering technologies are similar to this new approach, but the outlining difference is that a backscatter communication system has an RF signal-generating source in addition to the data transmitter and receiver. 

A limitation of this new approach is that it has lower data rate and lower range than either backscatter technologies or conventional radios. So more research and further development of those features should be achieved, so that this technique could be used in real applications such as implanted devices. The researchers highlight that their work may lead to new connection between thermodynamics and communication technology.


**References**

1) Bruno Clerckx, Rui Zhang, Robert Schober, Derrick Wing Kwan Ng, Dong In Kim, H. Vincent Poor. (2019). Fundamentals of Wireless Information and Power Transfer: From RF Energy Harvester Models to Signal and System Designs. IEEE Journal on Selected Areas in Communications   (Volume: 37, Issue: 1, pp4-33, January).  
Limited access at https://ieeexplore.ieee.org/document/8476597

2) Zerina Kapetanovic, Miguel Morales, Joshua R. Smith. (2022). Communication by means of modulated Johnson noise. Proceedings of the National Academy of Sciences.(Volume 119, No. 49).   
Limited access at https://doi.org/10.1073/pnas.2201337119

3) A. A. Danilov. (2019). Powering of implantable medical devices: History, current status and prospects. XIV RUSSIAN-GERMANY CONFERENCE ON BIOMEDICAL ENGINEERING (RGC-2019). DOI:10.1063/1.5121941  
Available at https://www.researchgate.net/publication/335145265_Powering_of_implantable_medical_devices_History_current_status_and_prospects

4) Vincent Liu, Aaron Parks, Vamsi Talla, Shyamnath Gollakota, David Wetherall, Joshua R. Smith. (2013). Ambient backscatter: wireless communication out of thin air. ACM SIGCOMM Computer Communication Review. (Volume 43, Issue 4, pp39–50, October)   
Available at https://dl.acm.org/doi/pdf/10.1145/2486001.2486015
