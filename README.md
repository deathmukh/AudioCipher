
# AudioCipher- A Real-Time Audio Transcription with Twilio Media Streams and Spring Boot

This project demonstrates how to create a WebSocket server in Java using Spring Boot. The WebSocket server receives real-time audio from a phone call via Twilio Media Streams and forwards the audio data to Google’s Speech-to-Text service to provide live transcription of voices during the call.

## Table of Contents

- [Introduction](#introduction)
- [Requirements](#requirements)
- [Configuring Twilio](#configuring-twilio-with-ngrok-for-public-access)
- [Usage](#usage)
- [Interpreting Live Transcriptions](#interpreting-live-transcriptions)


## Introduction

WebSockets are a web technology used to establish bidirectional connections between a client and a web server over the internet. Twilio Media Streams leverages WebSockets to stream real-time audio from a phone call to a web application.

This project utilizes Spring Boot to create a WebSocket server in Java. The server receives audio data from Twilio Media Streams and forwards it to Google’s Speech-to-Text service. Consequently, the application provides live transcription of voices from the ongoing call.

## Requirements

To set up and run this project, you'll need:

- Java 8 or later
- A free Twilio account for accessing Media Streams
- A Google Cloud account to utilize the Speech-to-Text service
- Ngrok for tunneling to expose local servers to the internet
It seems like you're configuring Twilio to work with your locally hosted Spring Boot application using Ngrok to create a temporary tunnel for public access. To help users follow these steps, here's a guide you can include in your project documentation or README:

---

## Configuring Twilio with Ngrok for Public Access

For Twilio to interact with your application, it needs to access a publicly available URL. Follow these steps to use Ngrok for temporary public access:

#### 1. Start Your Spring Boot Application

Run the following command in your terminal or through your IDE to start your Spring Boot application:

```bash
./mvnw spring-boot:run
```

#### 2. Start Ngrok

Launch Ngrok to create a temporary tunnel from a public URL to your local server:

```bash
ngrok http 8080
```

This command will display a public URL in the output (e.g., `https://<YOUR_NGROK_SUBDOMAIN>.ngrok.io`).

#### 3. Testing with Twilio

Once Ngrok is running, test the setup by accessing the TwiML URL in your browser:

```plaintext
https://<YOUR_NGROK_SUBDOMAIN>.ngrok.io/twiml
```

You should see a response similar to:

```xml
<Response>
  <Say>Hello! Start talking and the live audio will be streamed to your app</Say>
  <Start><Stream url="wss://<NGROK_SUBDOMAIN>.ngrok.io/messages" /></Start>
  <Pause length="30" />
</Response>
```

#### 4. Restarting and Testing

Ensure Ngrok is still running, and restart your server using `./mvnw spring-boot:run`. Initiate a call to your number again and start speaking.

As you talk, your console should display live transcriptions from Google's Speech-to-Text service.

---

   
## Usage

Once the setup is complete, initiate a phone call that utilizes Twilio Media Streams. The WebSocket server will receive real-time audio from the call and provide live transcription using Google’s Speech-to-Text service.

---

## Interpreting Live Transcriptions

Upon successful reception and processing of the live audio stream from a phone call using Twilio and Google's Speech-to-Text service, your console output might resemble the following:

```plaintext
Transcription:  The
Transcription:  The quick
Transcription:  The quick brown
Transcription:  The quick brown fox
Transcription:  The quick brown fox
Transcription:  The quick brown fox jumps
Transcription:  The quick brown fox jumps
Transcription:  The quick brown fox jumps over
Transcription:  The quick brown fox jumps over
Transcription:  The quick brown fox jumps over the
Transcription:  The quick brown fox jumps over the
Transcription:  The quick brown fox jumps over the lazy
Transcription:  The quick brown fox jumps over the lazy
Transcription:  The quick brown fox jumps over the lazy dog.
```

#### Interpretation:

- The displayed output illustrates sequential fragments of the ongoing transcription process as spoken words are converted to text in real time.
- Each line in the console output signifies an incremental update in the transcription, gradually forming a complete sentence.

#### Note:

- The purpose of these transcriptions is to showcase the real-time transcription capability of the application, providing a demonstration of accurately transcribed spoken words during the live phone call.

---
