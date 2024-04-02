# Symmetrium app project 

## Requirements
1. Xcode 12.1 or later
2. iOS 12 or later
3. Node.js + npm (For NodeJS Signaling server)  
**- OR -**  
macOS 10.15 (For Swift signaling server)

## Setup instructions
1. Start the signaling server (Either NodeJS or Swift)
2. Navigate to `WebRTC-Demo-app` folder
3. Open `WebRTC-Demo.xcworkspace`
4. Open `Config.swift` and set the `defaultSignalingServerUrl` variable to your signaling server ip/host. Don't use `localhost` or `127.0.0.1` if you plan to connect other devices in your network to your mac.
5. Build and run on devices or on a simulator (video capture is not supported on a simulator).

## Starting NodeJS signaling server
    1. Navigate to the `signaling/NodeJS` folder.
    2. Run `npm install` to install all dependencies.
    3. Run `node app.js` to start the server.


## Starting Swift signaling server
Note: This step requires MacOS 10.15

    1. Navigate to the `signaling/Swift` folder.
    2. Run `make`
    3. Run `./server` to start the server


## Run instructions
1. Run the app on two physical devices (Or one physical device and one simulator) with the signaling server running.
2. Make sure both of the devices are connected to the signaling server.
3. On the first device, click on 'Send offer' - this will generate a local offer SDP and send it to the other client using the signaling server. If you're using a simulator as one of the peers - click on 'Send offer' on the simulator.
4. Wait until the second device receives the offer from the first device (you should see that a remote SDP has arrived).
5. Click on 'Send answer' on the second device.
6. when the answer arrives to the first device, both of the devices should be now connected to each other using webRTC, try to talk or click on the 'video' button to start capturing video.

# Assignment
1. There's a bug in the code. Video stream from the camera should work from the physical device to the simulator or to a physical device (simulator should not send video stream in our case), but due to a bug, the video stream is not working. Find the bug and fix it. You should make the stream from the iphone's camera sent to the device of the simulator (or the other pysical device).
2. Create a new button named "touch" that will:
    1. Open a new white and empty screen
    2. Capture the user's touch on that screen (x and y coordinates only)
    3. Coordinates will be sent to the other peer using a data channel from webrtc protocol
    4. Only if the other peer will press on the "touch" button on his phone, that will open the white screen, a small red circle will be drawn on the screen every time it gets a new x,y coordinates. The circle will be with a fixed size such that the center of the circle is x,y
    5. Of course, both peers will be able to touch their screens and see the touchs of the other peer
    6. If you're using a simulator as one of the peers - it is not mandatory to support touch events from the simulator. only from the pysical device.
    
