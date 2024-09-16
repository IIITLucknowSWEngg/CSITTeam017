# Software Requirements Specification (SRS)

## Project Title: **Google Meet Clone**

### Version: 1.0


---

## 1. Introduction

### 1.1 Purpose
The purpose of this document is to outline the software requirements for the development of a Google Meet-like video conferencing application. The system will enable users to create, join, and manage online meetings with audio and video capabilities, chat features, and screen sharing.

### 1.2 Scope
This software will be a web-based platform that allows users to:
- Host and join video/audio meetings.
- Use chat features during meetings.
- Share their screen with participants.
- Manage participants and meeting settings.

### 1.3 Definitions, Acronyms, and Abbreviations
- **SRS**: Software Requirements Specification
- **UI**: User Interface
- **API**: Application Programming Interface
- **Host**: The user who creates the meeting
- **Participant**: Any user joining the meeting

### 1.4 References
- [WebRTC Documentation](https://webrtc.org/)
- [Google Meet API Reference](https://developers.google.com/meet)

---

## 2. Overall Description

### 2.1 Product Perspective
The application is an independent web application that uses WebRTC for real-time communication. It will provide seamless video conferencing capabilities with integrated chat and screen sharing features.

### 2.2 Product Functions
- **User Registration and Login**: Users can register or log in to the application.
- **Create Meeting**: Users can create a new meeting and invite others.
- **Join Meeting**: Users can join existing meetings via a unique meeting link.
- **Video and Audio Communication**: Real-time audio and video communication.
- **Screen Sharing**: Users can share their screen during meetings.
- **Chat Feature**: Text chat functionality within meetings.
- **Mute/Unmute and Video On/Off**: Control audio and video during the meeting.
- **End Meeting**: Hosts can end the meeting for all participants.

### 2.3 User Classes and Characteristics
- **Host**: Users who create meetings.
- **Participant**: Users who join meetings.
- **Admin**: Users who manage the system (optional).

### 2.4 Operating Environment
- **Client Side**: Web browser (Chrome, Firefox, Edge)
- **Server Side**: Node.js, WebRTC for communication, MongoDB for database management
- **Platform**: Web application

### 2.5 Design and Implementation Constraints
- WebRTC will be used for real-time communication.
- Application must support multiple participants with low latency.
- Should be compatible with modern web browsers.

---

## 3. Specific Requirements

### 3.1 Functional Requirements
1. **User Registration and Login**
    - Users must be able to register with email and password.
    - Users must be able to log in using valid credentials.
    
2. **Meeting Creation**
    - Hosts can create a new meeting and get a unique link.
    - The system should generate a unique meeting ID for every new meeting.
    
3. **Join Meeting**
    - Users can join a meeting by entering the meeting ID or link.
    - The system should validate the meeting link before allowing access.
    
4. **Video/Audio Communication**
    - Enable real-time video and audio communication using WebRTC.
    - Participants can mute/unmute their microphone and turn on/off their camera.

5. **Chat Feature**
    - Users can send text messages to all participants during a meeting.
    
6. **Screen Sharing**
    - Users can share their screen with other participants during the meeting.
    
7. **End Meeting**
    - Hosts can end the meeting for all participants, and the meeting should close for all users.

### 3.2 Non-Functional Requirements
1. **Performance**
    - The system should support up to 50 participants in a meeting without significant performance degradation.
    
2. **Usability**
    - The user interface should be simple and intuitive for non-technical users.
    
3. **Reliability**
    - The system should maintain a stable connection during meetings.
    
4. **Security**
    - The application should use secure communication protocols (e.g., HTTPS, encryption for data transmission).

5. **Scalability**
    - The application should be scalable to support more users and meetings over time.

### 3.3 System Requirements
- **Front-End**: HTML, CSS, JavaScript (React/Angular)
- **Back-End**: Node.js, WebRTC for real-time communication
- **Database**: MongoDB for storing user and meeting data

---

## 4. External Interface Requirements

### 4.1 User Interfaces
- **Login/Registration Screen**: A simple form for users to register and log in.
- **Dashboard**: Shows a list of meetings the user has hosted or joined.
- **Meeting Interface**: Contains video feeds, mute/unmute buttons, chat box, screen share option, and an end meeting button.

### 4.2 Hardware Interfaces
- Supports devices with a camera and microphone, such as laptops, desktops, and smartphones.

### 4.3 Software Interfaces
- WebRTC API for real-time video/audio communication.
- MongoDB for database management.

---

## 5. Other Non-Functional Requirements

### 5.1 Performance Requirements
- The system should load the meeting interface within 2 seconds on a good internet connection.

### 5.2 Security Requirements
- User authentication must be done using JWT (JSON Web Token).
- Meetings should be password-protected or link-based for security.

### 5.3 Maintainability
- The codebase should follow standard coding practices and be well-documented for future developers.

