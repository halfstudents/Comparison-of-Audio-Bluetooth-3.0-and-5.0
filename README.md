# Comparison-of-Audio-Bluetooth-3.0-and-5.0
A study on the practical characteristics of bluetooth technology, I tested SNR, SIGNAL Output and Range, based on audio.

Get the full details from here: https://www.hackster.io/sainisagar7294/comparison-of-audio-bluetooth-3-0-and-5-0-9b82f3


Coming to bluetooth in audio applications, we have versions from 3.0 to 5.4. In the practical audio application we have to keep 2-3 things in mind. Like we need what is the max power it is consuming, what is the SNR of the received signal and what is the ideal power conditions. Some other parameters like wireless range, noise in signal, DAC resolution and number of bits also play an important role here. Today in the article we will plot them all and see the difference in performance of a 3.0 and 5.0 bluetooth in real time. 



I have available a lot of them in stock, ranging from 3.0 to 5.0 but here specifically using these two. I have covered an article in detail about these cheap bluetooth modules. There is one manufacturer from China named JIELI who has been working on these BT nodes for a long time. Although the information is not open sourced, so we can not make any changes to the firmware without proper software. Some of the datasheets are shared in the previous article when I am designing my own board using them.  https://github.com/halfstudents/bt5.0-NEW-PCB-DESIGN

<img width="1024" height="768" alt="Image" src="https://github.com/user-attachments/assets/5ce6b734-e5db-4558-ab76-42ad0d91643f" />

This article is sponsored by PCBWAY. I have created my own BT5.0 with USB-C, you can see the whole project in a github repo here. After plugging an external battery as a power source we can convert any wired headphones/earphones into BT controlled. The PCB is shared below. I am pleased by the quality of PCBWAY services, the PCBs are awesome and work well. 



Bluetooth 3.0 and 5.0 Testing RIG/CASE:

<img width="1179" height="1162" alt="Image" src="https://github.com/user-attachments/assets/935148e4-fa64-4097-b728-91940be9e04d" />

I am using 5.10 volts out from a constant power supply. The signal is taken from an online signal generator, maxed to all levels @3500Hz sine wave. I chose this signal specifically because it is not much low and not much high frequency comes in hearing range. If we choose between low and high frequency extremes there will be a certain kind of attenuation in signal. I do not want to go in depth but they are because of digital filters used inside the chip. They have a wavy effect in the pass and stop band. To make the test more ideal, the sine wave chosen here is sampled at 44.1KHz which surpasses the nyquist limit almost 40 times. So obviously it is an ideal signal, an ideal 3500 Hz sine wave. 

<img width="2198" height="855" alt="Image" src="https://github.com/user-attachments/assets/cac2cb6c-791d-4f96-9e78-020c3c53f97b" />

Test 1 - Peak-Peak Amplitude Test:

<img width="2037" height="652" alt="Image" src="https://github.com/user-attachments/assets/41d1aebb-5a87-4c48-8eb2-f12a473fe2dc" />

Both the bluetooth has onboard signal conditioning circuit, in 3.0 we have seen a high amplitude pulse superimposed in signal which is nothing but due to its low resolution will talk about it later. The peak-peak output of 3.0 is 1.90V and in case of 5.0 it is 2.15V. Which is 13% increment over 3.0 Gen BT. 



Test 2- Resolution and Number of Bits:

<img width="1905" height="618" alt="Image" src="https://github.com/user-attachments/assets/334e7900-2412-4ef8-a341-2a445f27da49" />

Due to not open sourced documentation we can not get the exact number of bits, and resolution but from a signal engineer perspective we can see something on a scope. It is basically the DAC resolution but here I have seen something different, A high frequency wave superimposed over 3500 Hz wave, which can be seen through FFT but here I don’t available that option. In the case of 3.0 this superimposed wave is of somewhat a lower frequency than 5.0 so it looks awful here. By the way overall 5.0 gives me a smoother signal which also I can see when hooking it with an amplifier there is no any HUM or noise in 5.0 on the other hand 3.0 performs very much worse.



Test 3 - Noise in Ideal Mode:

<img width="1887" height="615" alt="Image" src="https://github.com/user-attachments/assets/53a05697-7c26-427d-8651-c93aba4e79d1" />

Here ideal mode is defined as the bluetooth is connected to the source but there is no signal given. The noise is compared with both BT modules. Ideally we should get a straight line when there is no signal but that is not the condition with these DSPs. I have seen a P-P noise of 650mV in 3.0 and 158mV in 5.0. This is where the 5.0 dominates and eliminates the competition. It is almost a 400% reduction in noise levels.



Test 4 - Power Consumption in Ideal Mode:

<img width="1975" height="585" alt="Image" src="https://github.com/user-attachments/assets/0b906da0-9d37-4f92-98f2-4ba5eee10747" />

Here ideal mode is defined as the bluetooth is connected to the source but there is no signal given. In this both the BT modules perform the same. Both are consuming 40mW of power.



Test 5 - Power Consumption in Full Signal Mode:

<img width="2113" height="514" alt="Image" src="https://github.com/user-attachments/assets/530d7fa2-5e17-43cb-9ef8-0971d5549ac2" />

When both BT modules output full signal the scene changes, usually what we see is that a 5.0 BT comes with low power here consuming 80mW and 3.0 around 55mW. This may also depend upon the P-P output signal of both BT modules. 



Test 6 - Ideal State Signal Analysis: 

<img width="2437" height="741" alt="Image" src="https://github.com/user-attachments/assets/5f929f75-bf82-42d7-a09a-56112f99811f" />

Here ideal mode is defined as the bluetooth is connected to the source but there is no signal given. In the ideal state when bluetooth notices a no signal condition then to reduce the overall noise level the low power mode is implemented automatically inside the chip. Which cuts the power to the output hence we will see a dip in ideal state noise level after some time. In 5.0 this low power is implemented within 0.5 seconds of time in 3.0 the chip processing takes around 10 seconds time. 

<img width="1701" height="559" alt="Image" src="https://github.com/user-attachments/assets/20d17939-4094-4afc-a636-4b1270b1b4fa" />


My designed 5.0 BT: 
Get the full project from this REPO here, you can download the gerber and order the parts, assemble them and get everything done. I have a lot of them lane around. Let me know if you need a detailed comparison of any other or any specific. I designed this PCB and got it done from PCBWAY. After assembly it works fine, has USB C, onboard antenna, 3.5mm connector and key button. Connect your wired headphones, power it up with a 3.7 Lipo and you convert your headphones into wireless ones. So simple, cheaper and of superb quality.

https://github.com/halfstudents/bt5.0-NEW-PCB-DESIGN

<img width="2176" height="1048" alt="Image" src="https://github.com/user-attachments/assets/a4f76b25-f600-4a3c-a3aa-3b2a2ca49a6f" />


Need to charge the battery, the onboard circuit can do it. All this is possible due to PCBWAY services, PCBWAY is the one of topmost manufacturers in China which fulfil all the prototyping requirements of your project. Explore now and get your PCBs done, get free coupons on first sign-up. 



Outro: 

<img width="1246" height="702" alt="Image" src="https://github.com/user-attachments/assets/6a2b55db-5f6c-48ec-8b2f-33a437b31bf7" />

These are the tests I have performed using my scope, due to limitation of lab equipment I am not able to measure the fast fourier transform. These are the beauty of digital signal processing units inside these small chips. They are basically 32 BIT microcontrollers which are adapted for bluetooth and signal processing applications. I always wonder how I got my hands on them so cheaply. 3.0 costs me around $0.8 and 5.0 is around $2.5 not the chips but the whole assembled boards. If you love the work, consider supporting me through web channels. And if you are working on PCB projects try PCBWAY services to make your projects look more good.

https://www.patreon.com/THEIITBOY/membership

<img width="1024" height="768" alt="Image" src="https://github.com/user-attachments/assets/74e43154-f6c0-4f5f-9d56-356f01233d22" />

