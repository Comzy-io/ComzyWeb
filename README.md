
# Comzy WebSDK

The **Comzy WebSDK** is a simple and lightweight WebRTC-based video/audio calling library.
It allows you to quickly integrate **1:1 video/audio calls** into your website or web application with minimal setup.

You can include the SDK by using our hosted minified JS:

```html
<script src="https://sdk.comzy.io/comzy-web.min.js"></script>
```

---

## Features

- Peer-to-peer  video/audio calling
- Simple API — start and end calls easily
- Call status monitoring and event hooks
- Built-in support for camera/microphone toggle
- Lightweight, no UI — you design your own interface

---

## Quick Start

### 1️⃣ Include the SDK

```html
<script src="https://sdk.comzy.io/comzy-web.min.js"></script>
```

### 2️⃣ HTML Elements

```html
<video id="localVideo" autoplay muted playsinline></video>
<video id="remoteVideo" autoplay playsinline></video>
```

### 3️⃣ Initialize the SDK

```js
const comzy = new Comzy();

comzy.init('YOUR_API_KEY', 'YOUR_USER_ID', 'REMOTE_USER_ID');
```

### 4️⃣ Start a call

```js
comzy.startCall('#localVideo', '#remoteVideo');
```

### 5️⃣ End a call

```js
comzy.endCall();
```

---

## Full Example

```html
<!DOCTYPE html>
<html>
<head>
    <title>Comzy WebSDK Demo</title>
</head>
<body>
    <video id="localVideo" autoplay muted playsinline style="width: 300px;"></video>
    <video id="remoteVideo" autoplay playsinline style="width: 300px;"></video>

    <button onclick="start()">Start Call</button>
    <button onclick="end()">End Call</button>
    <button onclick="toggleAudio()">Toggle Audio</button>
    <button onclick="toggleVideo()">Toggle Video</button>

    <script src="https://sdk.comzy.io/comzy-web.min.js"></script>
    <script>
        const comzy = new Comzy();

        comzy.on('callStarted', () => console.log('Call started'));
        comzy.on('callEnded', () => console.log('Call ended'));
        comzy.on('error', (err) => console.error('Error:', err));
        comzy.on('userJoined', (data) => console.log('User joined', data));
        comzy.on('userLeft', () => console.log('User left'));
        comzy.on('connectionStateChange', (state) => console.log('Connection state:', state));

        comzy.init('YOUR_API_KEY', 'user1', 'user2');

        function start() {
            comzy.startCall('#localVideo', '#remoteVideo');
        }

        function end() {
            comzy.endCall();
        }

        function toggleAudio() {
            const enabled = comzy.toggleAudio();
            console.log('Audio enabled:', enabled);
        }

        function toggleVideo() {
            const enabled = comzy.toggleVideo();
            console.log('Video enabled:', enabled);
        }
    </script>
</body>
</html>
```

---

## API Reference

### `init(apiKey, userId, remoteId, config?)`

Initializes the SDK.

* `apiKey` (string) - Your API key provided by Comzy.
* `userId` (string) - Your local user ID.
* `remoteId` (string) - The remote user ID you want to call.
* `config` (optional object) - Reserved for future options.

### `startCall(localVideoSelector, remoteVideoSelector)`

Starts a video/audio call.

### `endCall()`

Ends the ongoing call and cleans up.

### `on(eventName, callback)`

Registers event listeners.

Supported events:

* `callStarted`
* `callEnded`
* `error`
* `userJoined`
* `userLeft`
* `connectionStateChange`

### `toggleVideo()`

Toggles the local camera (returns new state: `true` or `false`).

### `toggleAudio()`

Toggles the local microphone (returns new state: `true` or `false`).

### `getCallStatus()`

Returns an object:

```js
{
    isActive: true/false,
    connectionState: 'new' | 'connecting' | 'connected' | 'disconnected' | 'failed' | 'closed',
    iceConnectionState: 'new' | 'checking' | 'connected' | 'completed' | 'disconnected' | 'failed' | 'closed'
}
```

---


> **Note:** If you wish to use our API, please email us at [hello@comzy.io](mailto:hello@comzy.io) with the following details:
>
> * Your full name
> * Your app's name
> * The purpose of your app
>
> API access will be reviewed and granted based on your submission.(The purpose of the API key is solely to track user, it is not being sold its totally free)


---

## 📞 Support

Need help? Contact our support team at [hello@comzy.io](mailto:hello@comzy.io) 

---

