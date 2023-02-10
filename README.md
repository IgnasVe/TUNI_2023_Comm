
#### below will be removed 
Communication by means of modulated Johnson noise.  
**Significance**  
This paper presents experimental realization of an ultralow power wireless communication method that works by selectively connecting or disconnecting an impedance-matched resistor and an antenna. This modulates microwave frequency Johnson noise emitted by the antenna. The data transmission hardware is similar to that of an RFID tag, which communicates by reflecting RF signals; the crucial advantage of the present system is that it requires no preexisting RF signal. An interesting feature of the system is that all components of the system are at the same physical temperature, but it functions because they have different noise temperatures. It is also notable that the elimination of the RF carrier simplifies the system architecture and the reader hardware.  
**Abstract**  
We present the design of a passive wireless communication method that does not rely on ambient or generated RF sources. Instead, the method modulates the Johnson (thermal) noise of a resistor to transmit information bits wirelessly. By selectively connecting or disconnecting a matched resistor to an antenna, the system can achieve data rates of up to 26 bps and distances of up to 7.3 m. This communication method operates at very low power, similar to that of an RFID tag, with the advantage of not requiring a preexisting RF signal to reflect.

Jin-Ping Niu, Geoffrey Ye Li. (2019). An Overview on Backscatter Communications. Journal of Communications and Information Networks (Volume 4, Issue 2, June)
DOI: 10.23919/JCIN.2019.8917868   
Limited access at https://ieeexplore.ieee.org/document/8917868


## 3. Parameters and performance of the transmission system

Here start the actual laboratory tasks. We study the parameters of our transmission system and how those affect system performance.

◼ If you haven’t downloaded yet the COMM100_lab.zip file from Moodle, do it now, and extract the content of the zip-file to a new folder. This is important so that LabVIEW can access all the files.

◼ Open the file simulator.vi with LabVIEW. This is the main program used for setting all transmitter and receiver parameters. Note! Especially if you are using TUNI Virtual Desktop, please make sure that you use 32-bit version of LabVIEW. The 64-bit version might give an error regarding lvanlys.dll.


### 3.1. Transmit signal

Transmission systems have limited frequency range. The bandwidth of a transmit signal must be within the available frequency range.

➢ Task 3.1: Using the equation learned in this course, calculate the bandwidth of the transmit signal,
when the transmitter program uses default parameters. Remember that the signal bandwidth is affected by symbol rate and pulse shape. From the pulse shaping parameters section of simulator.vi,
you can see that it is using a raised-cosine pulse with a roll-off factor (filter parameter) of 𝛼 = 0,5.[Hint: Lecture 7, slides 24–27]

**Solution 3.1**  
  
```math equation
  B = (1 + \alpha) / 2T 
```
``` 
1/T (symbol rate) = 500kHz (symbol/sec)
𝛼 (filter parameter) = 0.5
oneside Bandwidth = (1+0.5) * 500/2 = 375 kHz
double  Bandwidth = 2 * 375         = 750 kHz
```


➢ Task 3.2: Check the spectrum figure of the transmit signal. Does the calculated bandwidth match with the actual bandwidth of the transmit signal shown in the spectrum? Note that you can zoom the figure by the tools on the bottom left corner. Include the spectrum figure to your report.

**Solution 3.2**  
<img src="https://user-images.githubusercontent.com/25344978/215765602-24a0ae1b-2595-4075-8f8a-e14f6c80140e.png" width="400">


The Packet length (bits) parameter of the transmitter defines the amount of information bits in one data packet.

➢ Task 3.3: Let us consider the case of 1000 transmitted information bits. When using QPSK modulation (modulation type), use the packet duration shown in the transmitter side to calculate the information data rate (bits/second) of this system. How about, what is the information data rate, if BPSK modulation is used? [Note that the packet duration field of the program does not update automatically after changing the modulation type parameter. You must run the program to update it.]

**Solution 3.3**  

|Modulation type|Packet duration(msec)|Information data rate(bits/second)|  
| ----- |--:|--:|
|QPSK | 1.136 msec| 1000/1.136 = 880.281690 bits/msec = 880282 bits/sec |
|BPSK | 2.136 msec| 1000/2.136 = 468.164794 bits/msec = 468165 bits/sec | 


➢ Task 3.4: If you transmit 1000 bits, how many symbols you transmit using BPSK modulation? How about in case of QPSK? [You will find answers easier from the course material than from LabVIEW.]

**Solution 3.4**  

|Modulation type|number of symbols (1000 bits)|  
| -----  | --:|
|QPSK |  500|
|BPSK | 1000|


➢ Task 3.5: With the symbol rate of 500 kSym/s, it takes 1 ms to transmit 500 QPSK data symbols.
However, the transmitter program indicates the packet duration to be 1,136 ms. It means that the net data share is then 1 ms⁄1,136 ms ≈ 88 %. What would be the net data share (%), if we transmit only 100 bits in one packet? [In other words, check with the transmitter program the packet duration for 100 bits when using QPSK and then calculate the net data share. Please note that also 1 ms will change to another number. You must calculate how many QPSK symbols corresponds to 100 bits, and then how long it takes to transmit those symbols with given symbol rate.]

**Solution 3.5**

500k (Symbol rate, Hz) ->   500 QPSK in 1ms (500symbols in 1000bits)   
500k (Symbol rate, Hz) ->    50 QPSK in 0.1ms (50symbols in 100bits)

|transmit bits| Packet duration (msec) |net data share (%)|  ratio |
| -----:| --:| --:| --:|
| 1000 | 1.136 msec | 88 % | 1.0/1.136|
| 100  | 0.236 msec | 42 % | 0.1/0.236|

<br>

### 3.2. Noise

In real life, there is always noise in the received signal, which makes receiving the signal more difficult. This is the reason why also our LabVIEW program simulates the channel by adding noise to the signal.

➢ Task 3.6: Where is this noise stemming from in real life?

**Answer**
  - Electrical noise  
      - Galvanic  
      - Electrostatic coupling  
      - electromagnetic induction  
      - radio frequency interferenece  
  - thermal noise
      - Thermal noise is caused by the thermal agitation of electrons in resistances
 
```
https://www.sciencedirect.com/topics/engineering/thermal-noise
An Overview of Digital Communication and Transmission
Vijay K. Garg, in Wireless Communications & Networking, 2007

4.17.4 Noise and SNR
Noise
Noise can be put into the following categories:
•Thermal noise
Thermal noise occurs in all transmission media and all communication equipment. It occurs due to random electron motion and is characterized by a uniform distribution of energy over the frequency spectrum with a Gaussian distribution of levels. 

•Inter modulation (IM) noise
Inter modulation (IM) noise is the result of the presence of IM products. If two signals with frequencies f1 and f2 are passed through a nonlinear device or medium, the result will be IM products that are spurious frequency components. These components may be present either inside or outside the band of interest for the device. IM noise may result from a number of causes:
  -Improper level setting. If the level of input to a device is too high, the device is driven into its nonlinear operating region
  -Improper alignment causing a device to function nonlinearly
  -Nonlinear envelope
  -Device malfunction

•Crosstalk
Crosstalk refers to unwanted coupling between signal paths. Crosstalk is caused by (1) electrical coupling between transmission media, (2) poor control of frequency response, and (3) the nonlinear performance in an analog multiplex system. There are two types of crosstalk:
  -Intelligible — where at least four words are intelligible to the listener from extraneous conversations in a seven-second period (for voice applications)
  - Unintelligible — crosstalk resulting from any other form of disturbing effects of one channel on another.

•Impulse noise
Impulse noise is noncontinuous and consists of irregular pulses or noise spikes of short duration and of relatively high amplitude. These spikes are often called “hits.” Impulse-noise degrades voice telephony only marginally, if at all; however, it may seriously degrade error rate on data or other digital circuits.
```

<br>


◼ Set default parameters for the transmitter and receiver. The easiest way is to close all LabVIEW windows without saving and then open simulator.vi again. Then run the program to transmit and receive a signal.

➢ Task 3.7: In LabVIEW, both the transmitted and received signal are visualized with several figures. Next, observe how the noise is visible in different figures. Include the screenshots of all necessary figures to your report, so that you can use them to support your explanations. There are going to be six figures in total, because parts a, b and c need two figures each (transmitted vs. received).

**Solution 3.7**

| signal |transmitted| received|
|:-- |--- | --- |
|a. constellation|![b-left](https://user-images.githubusercontent.com/25344978/215999497-34901e1c-452a-4539-a503-0562b5ac9162.PNG) |![b-right](https://user-images.githubusercontent.com/25344978/215999620-8c7f1a92-af26-480e-884d-91672c569ae5.PNG) |
|b. signal waveform |![a-left](https://user-images.githubusercontent.com/25344978/215999684-95c2f7ba-fcd0-49ba-8160-1f49cc552d63.PNG) | ![a-right](https://user-images.githubusercontent.com/25344978/215999746-37715fba-eff9-4573-93f8-7799a654eba1.PNG) |
|c. signal spectrum |![c-left](https://user-images.githubusercontent.com/25344978/215999824-90fadbca-7f30-4b0e-9ce8-7a90c9955392.PNG) |![c-right](https://user-images.githubusercontent.com/25344978/215999879-1bbcab38-7275-482b-8f70-f8251c7ce5b1.PNG) |

a) How the noise shows in the constellation figure? In other words, compare the transmitted and received signal constellations. Naturally, the transmitted signal constellation does not contain any noise, but the received signal constellation does.

b) How the noise shows in the time-domain (signal waveform) figure? Compare, once again, the transmitted and received signals. [Hint: You must zoom the figure to see the noise.]

c) How the noise shows in the signal spectrum? Compare, once again, the transmitted and received signals. [Hint: You do not need to zoom spectrum figures to see the noise.] 

<br>

The USRP is not a calibrated device, so we do not know exactly the actual transmit power level in watts or in dBm. However, we can increase or decrease the transmit power by tuning the power gain of the Transmit Amplifier shown in Figure 2. You can do this by tuning the TX Gain (dB) parameter in the user interface of simulator.vi. Similarly, you can tune receiver-side amplification (Drive Amplifier in Figure 2) with the RX gain (dB) parameter of the user interface.

➢ Task 3.8: Set the parameters of the simulator.vi program and save spectrum figures according to the instructions below. Compare then the two spectrum figures visually. The signal power should be approximately equal in both figures. How about the noise power? How do you explain this?

**Solution 3.8**

| condition | transmitter | receiver |
|:-- | -- | -- |
| TX Gain = 20dB  &nbsp; &nbsp; &nbsp;&nbsp;&nbsp;&nbsp;  <br> RX Gain = 0dB &nbsp; &nbsp; &nbsp;&nbsp;| ![38aleft](https://user-images.githubusercontent.com/25344978/216007963-6784333e-532f-4c95-9e4e-2f5562024773.PNG) |![38aright](https://user-images.githubusercontent.com/25344978/216008000-e0383156-e04a-4b03-815d-c2c267df7648.PNG)|
| TX Gain = 0dB &nbsp; &nbsp; &nbsp;&nbsp;&nbsp;&nbsp;  <br> RX Gain = 20dB  &nbsp; &nbsp; &nbsp;&nbsp;| ![38bleft](https://user-images.githubusercontent.com/25344978/216008068-3c4f6471-d044-4389-81c7-5f7dc4f48ce3.PNG) |![38bright](https://user-images.githubusercontent.com/25344978/216008110-066cbe37-5fd1-42a3-b32a-cb4044e079a0.PNG) |



◼ Set the transmitter gain to 20 dB and the receiver gain to 0 dB. Run the program. Save the figure of the received signal spectrum.

◼ Set the transmitter gain to 0 dB and the receiver gain to 20 dB. Run the program. Save, once again, the figure of the received signal spectrum.



### 3.3. How signal-to-noise ratio affects bit-error rate?

Let us study still a bit further, how noise affects a signal. We take an example in which there is so much noise that the receiver is not able to interpret all the bits correctly. Bit-error rate (BER) is a value, which is used in communications engineering to express how often bit errors occur in data transmission. For example, a bit-error rate of 10−3 = 0,001 means that, on average, every one-thousandth bit is erroneous. Bit errors are caused by noise, interference etc. The amount of noise in a signal is measured with signal-to-noise ratio 
SNR = 𝑆/𝑁 = 10*log10(𝑆/𝑁)dB, 
where S is signal power and N is noise power. We study next how SNR affects the bit-error rate in case of BPSK and QPSK modulation, when noise is the only thing that deteriorates signal quality.

◼ First, set parameters of simulator.vi program according to the table below. All other parameters not mentioned on the table should be kept in their default values.
 
```
TRANSMITTER            
Packet length (bits) 1000 
# of iterations 100
TX gain (dB) 30

RECEIVER
RX gain (dB) 0
```

➢ Task 3.9: Use the simulator.vi and fill in the average bit-error rates to the table below. Save also figure of the received signal constellation for all SNR values and for both modulation methods (12 figures in total). Arrange the constellation figures side by side to your report so that they are easy
to compare. Please also note:

   - SNR value is set to the simulator by using the noise power (dB) channel model parameter. For example, if you want to have SNR of 2 dB, you should use –2 dB as noise power. In other words, negative noise power means positive SNR in this simulator.

   - Because the # of iterations parameter is set to 100, the program transmits 100 packets, and each packet has 1000 bits (packet length). The program then calculates the average biterror rate among the 100 received packets and shows the result in the Average bit-error rate field of the simulator. This is the BER value you want to write down to your table.

   - Remember to also change the modulation type parameter so that you can simulate BER values for both QPSK and BPSK one after another.

   - Do not change the scale or size of the constellation figure in LabVIEW during simulations. This guarantees that constellation figures are easier to compare with each other.

**Solution 3.9** 

Table. Bit-error rate
|SNR | BER (QPSK) |BER (BPSK)|
|--:| --:| --:|
|0 dB| 0.167680 | 0.088050|
|2 dB| 0.110230 | 0.039510|
|4 dB| 0.060880 | 0.014790|
|6 dB| 0.025510 | 0.003250|
|8 dB| 0.007830 | 0.000260|
|10 dB| 0.001100 | 0.000010|

Figure. Constellation of BPSK and QPSK  
|SNR (dB) | BPSK constellation| QPSK constellation |
|--:| -- | -- |
|0 dB| ![B0](https://user-images.githubusercontent.com/25344978/216029411-c3ae95cc-42c1-43af-8705-7cdfc6fece4c.PNG) | ![Q0](https://user-images.githubusercontent.com/25344978/216029453-85f49f64-c0fb-41ca-a26b-bc133518bcda.PNG)|
|2 dB| ![B2](https://user-images.githubusercontent.com/25344978/216029490-bf87b029-b782-41ca-96bb-c94aa2d1c79f.PNG)|![Q2](https://user-images.githubusercontent.com/25344978/216029533-20038702-4357-42d8-bd07-32b763bb6050.PNG)|
|4 dB| ![B4](https://user-images.githubusercontent.com/25344978/216029569-759e9438-1ed0-4abb-beb4-c05434e8c87f.PNG)|![Q4](https://user-images.githubusercontent.com/25344978/216029605-622c7462-e1e0-4849-85af-419fbe19088f.PNG)|
|6 dB| ![B6](https://user-images.githubusercontent.com/25344978/216029649-fed81d0c-a231-40fa-8c64-bb298ac0441a.PNG) |![Q6](https://user-images.githubusercontent.com/25344978/216029680-3714ac49-aad6-43d9-a8ed-7c2ffb38a818.PNG)|
|8 dB| ![B8](https://user-images.githubusercontent.com/25344978/216029739-c86eabea-3bbd-45cf-b641-205e9fd94b44.PNG)|![Q8](https://user-images.githubusercontent.com/25344978/216029792-fdefc132-2dbf-44c0-b77f-a44adfac50f1.PNG)|
|10 dB| ![B10](https://user-images.githubusercontent.com/25344978/216029843-354188cf-f18f-4b6b-85fa-0fcb89d0b915.PNG) |![Q10](https://user-images.githubusercontent.com/25344978/216029866-adeba95f-4dd3-4cc6-a287-14f37ec97b97.PNG)|


<br>

➢ Task 3.10: Analyze the results of the previous task by answering to the following questions.  

a) How the amount of noise affects bit-error rate?

b) What can you conclude by comparing the BER results of BPSK to the BER results of QPSK?

c) Why do you get less bit errors with the other modulation type although the signal power and noise power (i.e. SNR) are the same for both modulation types?

d) So, if one modulation type gives you less bit errors than the other modulation type (SNR being the same), why would you ever want to use the modulation type that causes more bit errors?


➢ Task 3.11: Draw a graph of the values in the table of Task 3.9. The graph should have SNR on the horizontal axis and BER on the vertical axis. In the graph, you should have two curves (QPSK and BPSK). If possible, use logarithmic scale on vertical axis, which makes the small BER values easier to read. You can draw the graph using Excel or any other computer program you like. 

   - In Matlab, logarithmic scale on vertical axis can be plotted with semilogy command.  
   - In Excel desktop versions, you must click the graph and then Format → Vertical (Value) Axis → Format Selection → Axis options → Logarithmic Scale, Base 10.   
   - In web version of Excel, you must click the graph and then Chart → Axes → Primary Vertical Axis → Log scale. This way you do not have to calculate logarithmic values yourself, but the software does it for you!]

**Solution 3.11**

Figure. Bit-error rate   
<img src="https://user-images.githubusercontent.com/25344978/216043263-494c303a-b662-409d-84e4-71b91f617e74.png" width="400">



## 4. Link budget of the transmission system

In this final section, we practice calculating a link budget for our USRP-based transmission system. More information about link budgets can be found, e.g., from lecture slides [Lecture 4, slides 27–28] and from the corresponding lecture video recording.

➢ Task 4.1: In the following table, some values are given related to our transmission system. Look also at Figures 2 and 4 to understand the overall arrangement better. First, find out the attenuations of the coaxial cable and the attenuator by following the instructions given after the table. After that, calculate the received signal power in the output of the Drive Amplifier. Give your answer in dBm unit.


| Transmission system | dB |
|------|------:|
|Signal power before the Transmit Amplifier | –50 dBm|
|Transmit Amplifier gain | 20 dB|
|Attenuation of the coaxial cable | 0.624 dB|
|Attenuation of the 30-dB attenuator | 28.9 dB|
|Low Noise Amplifier gain | 14 dB|
|Drive Amplifier gain | 20 dB|
|Other attenuations (RF switches, connectors, etc.) | 2 dB|
| | |
|Received signal power | -27.524 dBm |

```
-50 + 20 + 14 + 20 - 0.624 - 28.9  - 2 = -27.524 dBm
-27.524 dBm => 1.7684793782817999e-3 mW = 1.76847 microWatt
```

◼ The length of our coaxial cable in this system is 1 m. Find out, how many decibels of attenuation this cable causes. From the datasheet of the cable [5], you can read how much attenuation is caused by 100 m of cable, when the signal frequency is 2,5 GHz. Using that attenuation value, it is then straightforward to calculate, how much attenuation our one-meter cable causes. 
```
62.4 dB / 100 meter --> 0.624 dB / 1 meter
```
<img src="https://user-images.githubusercontent.com/25344978/215868506-7bb5b310-b05f-42da-ad02-880c2d059b09.jpg" width="500">


<br>

◼ We also have a 30-dB attenuator in our system. However, this 30 dB is only a nominal value. In practice, the attenuation is frequency-dependent. Check from the manufacturer’s datasheet [6], how many decibels of attenuation there is at the frequency of 2,5 GHz.  
```
2.5GH --> about 28.9 dB
```
<img src="https://user-images.githubusercontent.com/25344978/215868146-a72bf28a-ffbd-4a73-8688-e945882b0723.jpg" width="400">


<br>

Values provided by datasheets are so-called typical values and that accuracy is enough for us in this laboratory work. However, each individual component has slightly different values. Therefore, if we would like to determine the attenuation very accurately, we should measure the attenuation of that particular cable and attenuator with calibrated laboratory equipment.


## References

[1] Ettus Research, B200/B210/B200mini/B205mini.
Available: https://kb.ettus.com/B200/B210/B200mini/B205mini

[2] NI USRP-2900 Block Diagram.
Available: https://www.ni.com/docs/en-US/bundle/usrp-2900-feature/page/block-diagram.html

[3] NI USRP-2900/2901 Getting Started Guide. Available:
https://www.ni.com/docs/en-US/bundle/usrp-290x-getting-started/page/2900-connectors.html

[4] NI USRP-2900 Device Specifications.
Available: https://www.ni.com/docs/en-US/bundle/usrp-2900-specs/page/specs.html

[5] Times Microwave Systems, LMR-195 Flexible Low Loss Communications Coax Datasheet. Available: https://timesmicrowave.com/documentation/lmr-19
