# Image streaming using a realtime protocol  
This project aims at designing and assessing the functioning of an enhanced protocol for image transmission over loss-prone crowded or wireless networks. The usual approach to transporting images uses TCP. The main motivation to undertake this project starts with stressing on the disadvantages of using TCP. The main drawback of using TCP for image downloads is that its in-order delivery model interferes with interactivity. TCP provides a general reliable, in-order byte- stream abstraction, but which 
is excessively restrictive for image data. TCP is not suitable for real-time applications as the retransmissions can lead to high delay and cause delay 
jitter, which significantly degrades the quality. On the other hand , UDP is a connectionless protocol and is not dedicated to end-to-end communications, nor does it check the readiness of the receiver (requiring fewer overheads and taking up less space). Hence, UDP is a much faster, simpler, and efficient protocol for streaming processes, but it does come with a concerning drawback, prone to packet losses. Packet losses can lead to corrupt images, which is something we want to avoid. Therefore this project is a step taken at tackling that very issue. Although it's built on UDP, it also uses a small programmatically written optimizer that can also be considered as a protocol running on top of UDP. Hence, enhancing and optimizing its features according to our objective. This project enables high quality image streaming without exhausting the buffer , therefore giving us a higher chance of receiving images wihout corrupting them.

## Technolgies and Libraries
Environment Software : Anaconda   
IDE: Jupyter Notebook   
Language : Python    
Libraries: 
- Imported **socket** for socket programming eg: creation of sockets, etc.  
- Imported  **PIL** library that is PYTHON IMAGE LIBRARY for opening and closing images via path 
- Imported **tkinter** for making the client login. popup and server login GUI.
- Imported  **sys** for accessing system specific functions. 
- Imported **cv2**, the OpenCV library which in our project is used for handling the images such as encoding, decoding it and the streaming it through a netwrok.  
- Imported  **numpy** for creating multi-dimensional arrays  
- Imported **struct** for packing data into structures.

## The Implementation , Code Logic and Workflow
- There’s Two GUI Interfaces for Client and Server Login.
- Once the Client and Server is successfully logged in , the server starts listening and the 
client accepts the connection respectively. 
- The client then asks for the user’s input for an Image through a file dialog 
- Once the image is received the client prints out the location path and the image type 
- Then the image is compressed and converted into a numpy array using the Open CV 
Library. 
- The numpy array is a three-dimensional array in height, width and channel format. 
- The encoded numpy array is then converted into string ready for streaming. 
- In the meanwhile, the client also outputs the length of string and the encoded data for 
demonstration purposes. 
- The Length of data/string is sent as a file header to the server from the client before the 
actual streaming , enabling the server to know the time till when to keep the channel open 
and the amount of data to be received. 
- The server receives the file header reads the length and prepares to receive the data in 
each stream in a cyclic way. 
- The client starts streaming the data in batch of size 1024 bytes (The buffer size) it also at 
the end of the transmission checks for any remaining data less than 1024 Bytes and if 
found streams them as well. 
- The server prints out each stream it receives with the particular size of data received 
along with the total amount of data received till then. 
- The server also outputs in the end an confirmation message, along with the total streams received 
, the amount of lost packets, loss percentage and Success percentage. 
10
- The Client and Server Primarily run on UDP but since we have defined how the data should be 
transferred this can also be considered as a small protocol that sits on top of UDP. 
- By Using UDP for streaming rather than TCP/IP as it supports 3 Way handshake which could 
lead to long idle times while also writing a optimization in the streaming process to stream 
images in a cyclic way instead of directly exhausting the buffer by trying to transfer it in a single 
go, Our project has a higher rate of success for image streaming and transferring


## Results
### The Client and Server GUI POPUPS
<p float="left" align="center">
 <img src="https://user-images.githubusercontent.com/77877486/140919322-f0a103f5-42f1-4c69-9d67-14386bb92c9b.jpg">  
 <img src="https://user-images.githubusercontent.com/77877486/140919550-afc471ae-fd3f-4e8f-84d0-407d60852e51.png">
 <img src= "https://user-images.githubusercontent.com/77877486/140919965-de821979-272d-4297-8c74-ed06a08208e0.png">
</p>

### Output by client (encoding image data):
<p align="center">
<img src="https://user-images.githubusercontent.com/77877486/140920239-db3929bd-8291-4124-894e-7feb2b25ec6c.png">
</p>

### Image sent by client :
<p align="center">
<img src="https://user-images.githubusercontent.com/77877486/140920480-c99b88a2-fd60-4cf1-8291-debc5aedd394.png">
</p>

### Output By Server ( No. of Streams , Packet losses and Percentages received):
<p align="center">
<img src="https://user-images.githubusercontent.com/77877486/140920709-cda34744-c1c4-45de-ae40-f443545ddc0e.png">
</p>

### Final Image Received By Server ( No data loss , No quality loss and No color loss):
<p align="center">
<img src="https://user-images.githubusercontent.com/77877486/140920985-7d888f86-50bf-49c1-80bb-618708fc639b.png">
</p>

### Result Analysis 
Our results satisfy the purpose of our project and shows the successful transmission of images between 
client and server in an optimized way. There isn’t any data loss or packet loss in the transmissions we 
performed. Although the project is prone to packet loss as it runs on UDP, because of the optimizer we 
wrote we decrease that amount significantly. The Image received on the server side had no loss in quality 
or size. The color values and details of the image was not lost in transmission. We also displayed the 
number of streams , packet loss, packets received and also the percentages for the same.

## Contributors
<div align="center">
<table>
  <tbody><tr>
     <td align="center"><a href="https://github.com/everly-gif"><img alt="https://avatars.githubusercontent.com/u/77877486?v=4" src="https://avatars.githubusercontent.com/u/77877486?v=4" width="130px;"><br><sub><b>Everly Precia Suresh</b></sub></a><br></td>
    <td align="center"><a href="https://github.com/vb6539"><img alt="https://avatars.githubusercontent.com/u/80880872?v=4" src="https://avatars.githubusercontent.com/u/80880872?v=4" width="130px;"><br><sub><b>Vivek Singh Baghel </b></sub></a><br></td>
    <td align="center"><a href="https://github.com/RPK2103"><img alt="https://avatars.githubusercontent.com/u/60558428?v=4" src="https://avatars.githubusercontent.com/u/60558428?v=4" width="130px;"><br><sub><b>Kaviyashre Ragupathy</b></sub></a><br></td>
  </tr>
  
</tbody></table>
</div>


