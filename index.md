# Isaac's Project
Replace this text with a brief description (2-3 sentences) of your project. This description should draw the reader in and make them interested in what you've built. You can include what the biggest challenges, takeaways, and triumphs from completing the project were. As you complete your portfolio, remember your audience is less familiar than you are with all that your project entails!

You should comment out all portions of your portfolio that you have not completed yet, as well as any instructions:
```HTML 
<!--- This is an HTML comment in Markdown -->
<!--- Anything between these symbols will not render on the published site -->
```

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Isaac H | Lynbrook | Electrical Engineering | Senior

**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](logo.svg)
  
# Final Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE



# Second Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/y3VAmNlER5Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your second milestone, explain what you've worked on since your previous milestone. You can highlight:

My goal for Milestone 2 was at least getting the bare minimum done---that was, connecting my camera sensor and Raspberry Pi together and getting live heatmaps displayed on my monitor. After that, I planned to add some elementary modifications that would mainly improve user interface and performance.  There was a specific way the MLX90640 and the Pi had to be connected for the whole system to work. Using an online diagram as my reference (I will also put it on the bottom of the page), I learned about the 40 different GPIO pins on the Raspberry Pi 4. Pins 1 and 2 (from the top) were the power pins (3.3V and 5V outputs), which would supply the voltage and current needed for the circuit to continue running. I used the 3.3 V power because the Adafruit MLX90640 normally operates at 3.3 V (using 5 V could permanently dammage the sensor). I then used GPIO 2 (SDA), labeled as Pin 3, and GPIO 3 (SCL) labeled as Pin 5, to enable I2C communication. The last pin I used was the GND or ground pin, labeled Pin 6, which acts as a return to the power supply.

I successfully integrated the Adafruit MLX90640 with the Raspberry Pi with the help of the STEMMA QT/Qwiic cable and female jumper wires. It was important to match the correct wires with the correct pins otherwise the sensor would not activate. 
It goes:

Red (VIN) ---> Pin 1 (3.3 V)

Black (GND) ---> Pin 6

Blue (SDA) --->	Pin 3 (GPIO 2)*

Yellow (SCL) --->	Pin 5 (GPIO 3)*

*these two pins are interchangeable

I then had to enable X11 Forwarding, a feature of the SSH protocol that allowed me use my remote server to display the image on my monitor. I also installed matplotlib on Python, a library capable of creating animated images and viualizations. In my code, I also used the modules board and busio. The board module essentially creates a bridge between my code on the physical pins on the Raspberry Pi. The busio module is responsible for handling the I2C protocol connections which as what will let me communicate with the MLX90640 camera sensor. So far, most of the live display code is identical to what was provided in the original script. I added a few modifications improve user interface such as numerical temperature readings from the center pixel, an overheat warning, and a button to save any specific frame. 


A surprising discovery that I learned one my way to Milestone 2 is how sensitive accurate fire detection was. Although not noticeable at face value, upon further research, it came to my knowledge that small environmental changes within the sensor's scope of detection could trigger false positives and inaccurate data readings. Additionally, when experimenting with one of my modification ideas, I discovered that the Raspberry Pi 4 had its own sound system and was able to produce audio when paired with the correct equipment, that being the Actuve Buzzer (expanded on further later).

Unfortunately, the classic issue of rage-inducing installation and runtime errors in code persisted. X11 Forwarding and display was by far the most frustrating as it was still a new concept to me. Getting all the display settings was incredibly difficult as I would usually run into error messages such as "localhost:0 unavailable" or "cannot open display" in my terminal. Lastly, I spent a good amount of time on my own trying to understand the sample code and writing my own sections to adjust the heatmap to my own liking.

My first priority now is to finalize my sound system with my buzzers arriving this weekend. After that. Then, I hope to get one more "real-life applicable" modifcation such as being able to detect false-positive errors producing "true" temperatures. Lastly, I hope to conduct field testing on different objects and in environmental conditions so that I can ensure that the sensor is both reliable and ready to be presented next Thursday.

# First Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/Hfg3s7IIhXs?si=laaw-9Sbskkp3eVx" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


Milestone 1 was all about getting my compartments laid out and ready to be used. There are two notable components in terms of size and appearance. The first is the Adafruit MLX90640 infrared camera sensor---this is the module that makes thermal imaging possible. Its purpose is to detect temperature variations across an image. The second is the Raspberry Pi 4. It is a small yet powerful computer that is able to create an interface with the MLX90640 sensor. Its connectivity options along with SSH server support will allow me to display the camera image on my monitor using my laptop.
The SD card also plays a vital role. Inside it holds the entire Raspberry Pi OS. This acts as the Pi's storage device and is responsible for keeping all of the libraries. project files, and configuration settings that I will be using throughout the next few weeks. Some essential libraries I have installed are CircuitPython and Blinka. CircuitPython is the main language I’ll use to write scripts for the sensor, and Blinka acts as a compatibility layer that allows CircuitPython to run on the Raspberry Pi while giving access to standard communication protocols like GPIO, I2C, and SPI.

So far, I have successfully assembled the hardware components and installed the entire OS operating system on my SD card. After that, I configured the necessary libraries including CircuitPython and Blinka to make programming possible. Lastly, I started basic integration and circuitry between my camera sensor and Raspberry Pi.

The main challenge I faced was getting all of the modules, packages, and libraries installed and updated to their newest versions. I frequently ran into issues where the SD cards would be corrupted or improperly formatted, which prevented the Raspberry Pi from powering on or being detected by my laptop, either on my file manager or Raspberry Pi Imager. Fixing these problems often meant restarting the entire installation, putting a true test to my patience.

Next up, my immediate goal is to get the circuitry working. Doing this will allow me to display the thermal image on my monitor. While that is being done, I also need investigate the "Electronics Fun Kit". There are still many different wiring components inside I have never had hands-on experience with until now, such as the breadboard, jumper wires, resistors, LEDs, and more. Learning about the functions and compatibilities of these numerous pieces could help me decide what kind of modifications I would like to add. One feature I am planning to implement is a temperature readout mode. With this feature, the temperature can be displayed next to the cursor in real time, based on its location on the thermal image.

# Schematics 
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 

# Code
Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. 

```c++
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  Serial.println("Hello World!");
}

void loop() {
  // put your main code here, to run repeatedly:

}
```

# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Adafruit MLX90640 Thermal Camera Lens| Utilizes I2C to detect and interpret temperature variations across a scene and creates a 24x32 pixels thermal image from that temperature data| $74.95 | <a href="https://www.adafruit.com/product/4407?srsltid=AfmBOop8JiOR0H0jArvrvqGnvUHS1d8SkR2zLZA57effkyM_DrBYPCIz"> Link </a> |
| Raspberry Pi 4 Model B | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |

# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Main Tutorial](https://learn.adafruit.com/adafruit-mlx90640-ir-thermal-camera)
- [CircuitPython & Blinka](https://learn.adafruit.com/circuitpython-on-raspberrypi-linux/installing-circuitpython-on-raspberry-pi)
- [X11 Forwarding to Monitor Display](https://some-natalie.dev/blog/ssh-x11-forwarding/)
- [Ideas for Thermal Camera Modifications](https://techimaging.com/applications/infrared-thermal-imaging-applications)
