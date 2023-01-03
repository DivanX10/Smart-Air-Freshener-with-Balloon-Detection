# Smart air freshener with detection of the presence of the balloon and the aroma of the balloon

The project used an automatic air freshener from the company Glade with replaceable cylinders at 2400 spray, which I redesigned and integrated into the Home Assistant.
![image](https://user-images.githubusercontent.com/64090632/210274020-c190c6f2-04a1-47cf-8b0d-a1e1ef07811d.png)


### What opportunities does the redesigned air freshener provide?
1) Spray the balloon with Home Assistant automation tools
2) Spray the balloon with a built-in timer 
3) Sensor pressing the physical button on the air fresheners
4) Determines the presence of a balloon
5) Determines the aroma of the balloon
6) It is possible to keep a record of the consumption of each cylinder or only a single one
7) Write your own code for sensor output and air freshener control in ESP Home
8) Battery powered
9) Mains power


---

### Necessary details

<details>
  <summary><b>1)</b> Glade Automatic Air Freshener - 1 pc.</summary>
  
![image](https://user-images.githubusercontent.com/64090632/210275338-a8fec7c1-8eed-4a49-8b24-a9cbae35a92a.png)
</details>
<details>
  <summary><b>2)</b> ESP Wemos mini - 1 pc.</summary>
  
![image](https://user-images.githubusercontent.com/64090632/210275136-fc39e573-aa01-4fbe-ae14-a6298901a5f6.png)
</details>

<details>
  <summary><b>3)</b> Step-down voltage converter GSMIN MP1584EN DC-DC - 1 pc.</summary>
  
![image](https://user-images.githubusercontent.com/64090632/210275257-8ff22857-6f0d-442b-9d0e-46a37332211f.png)
</details>

<details>
  <summary><b>4)</b> Resistors, of any nominal value from 100 kOhm to 2 ohms, you can take a set of resistors</summary>
  
![image](https://user-images.githubusercontent.com/64090632/210275290-bc112a78-67a6-4a23-9d01-e9ef3382d7b0.png)
</details>

<details>
  <summary><b>5)</b> Connector power socket 5.5mm - 1 pc.</summary>
  
![image](https://user-images.githubusercontent.com/64090632/210274879-f41c1f5a-a022-4f81-aa65-9595111f19fa.png)
</details>

<details>
  <summary><b>6)</b> Conductive glue for heating threads (with nickel) NANOPROTECH - N pieces to choose from</summary>
  
![image](https://user-images.githubusercontent.com/64090632/210275453-94cdc468-aa54-40ab-9ec9-fdf4335e0812.png)
</details>

<details>
  <summary><b>7)</b> Any power supply 9V 2A (9V/2A), plug 5.5*2.1mm </summary>
  
![image](https://user-images.githubusercontent.com/64090632/210275605-cd81f509-ec63-4d81-9459-8ff40caa6f0b.png)
</details>

<details>
  <summary><b>8)</b> Neodymium Powerful Flat Magnets Rectangles Rosmagnit 5x5x1 mm - 20pcs </summary>
  
![image](https://user-images.githubusercontent.com/64090632/210276697-9c7320e6-8819-46c7-978b-151042579ff6.png)
</details>

<details>
  <summary><b>9)</b> Print the platform on a 3D printer </summary>
  
![image](https://user-images.githubusercontent.com/64090632/210276971-7149593f-cffe-45b2-ae90-71349b066ec9.png)

</details>

---

### Filling on ESP Wemos mini firmware to control the air freshener
In ESP Home, we create a project to control the air freshener, [**copy the code**](https://github.com/DivanX10/Smart-Air-Freshener-with-Balloon-Detection/blob/main/air-freshener-glade.yaml) and we fill it on the board

---

### Assembling

We extract the native board and do as in the diagram
![image](https://user-images.githubusercontent.com/64090632/210287139-fc2f2cd4-e036-49a3-a701-29d2234140ee.png)

Increased native board size for understanding.
1) The yellow wire is soldered to the second leg on the right to the chip. This wire is soldered to the esp board, to the contacts D8 GPIO15
2) Solder the resistor to 1K, and a green wire to it. Next, solder the wire from the resistor to the esp board, to the contacts D7 GPIO13
3) The orange wire is +3.3V and soldered to the esp board, to the contacts +3.3V
4) The blue wire is soldered to the esp board, to the GND contacts
5) We cut the contact on the track of the textolite coming from the yellow wire. This is necessary so that we can control the dispenser when the timer is off

![image](https://user-images.githubusercontent.com/64090632/210275721-a08a3a74-0b19-419d-b336-99912dc7a1f0.png)

6) We cut the spring with the + contact for the battery compartment and solder the diode (highlighted with a red marker). Why is this necessary? This is necessary to protect the esp board from failure for the reason that if there are batteries in the air freshener and we still connect it to the network, then the chip responsible for voltage conversion will not try to charge the battery and will not get very hot, which can fail. The diode prevents current from flowing in the opposite direction to the battery

![image](https://user-images.githubusercontent.com/64090632/210277101-1be5b60b-3c46-44ad-9fe9-774a9652f727.png)

7) On the esp, we solder wires and a 5.1 kOhm resistor (there are resistors included) or 5.6 kOhm. The resistor is soldered to contacts A0 and GND. Solder two wires from contacts A0 (brown wire in the photo) and to +3.3V (black wire in the photo) and stretch to the very bottom of the cylinder body

![image](https://user-images.githubusercontent.com/64090632/210277241-fe4dfb8f-bc95-4cc8-bb74-df4d2110848c.png)

8) We install a 5.5 mm power socket connector into the housing hole, solder the wires from the connector to the step-down of the GSMIN MP1584EN DC-DC voltage converter, and from the step-down to the esp. On the step-down we set the voltage 2.2-3.3v and check the motor power. If the lever is pressed hard into the limiter and starts to crack, then lower the voltage to 2.2V and it should be so that the lever rests against the limiter and at the same time the motor does not have enough strength to push the lever and could not wear off the gears

![image](https://user-images.githubusercontent.com/64090632/210278174-10582517-9206-448b-834d-a3b9750d9eb2.png)

10) We stretch two wires from contacts A 0 and +3.3V and apply hot glue so that there is a circle in the center and an arc at the back. I filled the wires with conductive glue - there is no need to solder.
> Important! Conductive glue does not fit well on the smooth surface of the plastic, it begins to swell and peel off. Be sure to sand or scratch the smooth surface thoroughly, then the conductive glue will lie perfectly

![image](https://user-images.githubusercontent.com/64090632/210277467-12c2e240-952f-4ab6-b7bf-b121e80a0ca5.png)
![image](https://user-images.githubusercontent.com/64090632/210277657-3d1cc3c7-f971-48de-bc78-308dd1ec1f5b.png)

10) We print the platform on a 3d printer, install 2 magnets to enhance magnetization, install a resistor in the hole and cover it with conductive glue. The consumption of conductive glue can be different, therefore, if there are several platforms, it is advisable to take several pieces. I took 5 packs.

![image](https://user-images.githubusercontent.com/64090632/210278033-ac35a90f-8700-4062-8e59-537360ee1ea5.png)





