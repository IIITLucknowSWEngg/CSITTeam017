# Software Design Description (SDD)

## 1. Introduction

### 1.1 Purpose
The purpose of this Software Design Description (SDD) is to provide a detailed design for the video conferencing application, similar to Google Meet. This document outlines the software's architecture, components, interfaces, and their interactions to ensure that the system meets the functional and non-functional requirements.

### 1.2 Scope
The video conferencing system enables users to host and join video meetings via a web and mobile application. The system supports features like scheduling, real-time video/audio communication, screen sharing, chat, and integration with calendar and messaging services.

## 4. Module Design

### 4.1 Mobile and Web Application (Frontend)

#### 4.1.1 User Interface (UI)
The UI is designed to be intuitive, responsive, and user-friendly. The UI components include:
- **Home Screen**: Displays upcoming meetings and options to schedule new meetings.
- **Join Meeting Screen**: Allows users to join scheduled meetings using a meeting code or link.
- **Meeting Screen**: Displays video feed of participants, chat, screen share controls, and participant list.
- **Profile Management**: Allows users to manage personal details, settings, and preferences.
- **Scheduling Screen**: Provides functionality for users to schedule new meetings with date, time, and invite participants.

#### 4.1.2 Controller Layer
Manages user interactions and communicates with the service layer for processing. This includes:
- **Authentication Controller**: Manages login, registration, and user authentication.
- **Meeting Controller**: Handles meeting creation, joining, and scheduling.
- **Audio/Video Controller**: Controls the video and audio streams during a meeting.
- **Notification Controller**: Handles notifications related to meeting reminders and updates.

#### 4.1.3 Service Layer
Handles the business logic, such as:
- **Meeting Management**: Creating, joining, scheduling, and updating meeting details.
- **Audio/Video Streaming**: Establishing real-time audio/video communication for meeting participants.
- **Notification Service**: Sending reminders and updates about meetings.
- **File Sharing**: Manages file sharing between participants during a meeting.

### 4.2 Backend System (Server-side)

#### 4.2.1 API Gateway
The API Gateway acts as the entry point for all requests from the frontend application, routing them to the appropriate backend services.

#### 4.2.2 Authentication Service
Handles:
- User login
- Registration
- Password reset and recovery
- Session management

#### 4.2.3 Meeting Management Service
Handles:
- **Meeting Creation**: Users create new meetings with date, time, and participant list.
- **Meeting Scheduling**: Scheduling recurring or one-time meetings with calendar integration.
- **Join Meeting**: Allows users to join scheduled meetings via a link or meeting ID.
- **Participant Management**: Adds or removes participants during meetings.

#### 4.2.4 Audio/Video Service
Handles:
- Real-time audio and video communication using WebRTC or similar technology.
- Screen sharing management.
- Mute/unmute and video on/off control for participants.

#### 4.2.5 Notification Service
Responsible for sending notifications for:
- Meeting reminders.
- Participant invitations.
- Updates on meeting schedules or cancellations.

#### 4.2.6 Calendar Integration Service
Manages:
- Synchronization with third-party calendar services (e.g., Google Calendar, Outlook).
- Scheduling meetings with automatic invites and reminders.

### 4.3 Third-Party Services

- **WebRTC**: Provides the framework for real-time video/audio streaming.
- **Calendar APIs**: For scheduling and integrating meetings with users' calendars (Google Calendar, Outlook).
- **SMS/Email Gateway**: Sends meeting invitations and reminders via SMS or email (e.g., Twilio, SendGrid).

## 5. Database Design

The video conferencing system uses a relational database (e.g., PostgreSQL) to store structured data about users, meetings, and notifications. Here is the schema for major entities:

![Design](https://github.com/user-attachments/assets/2e0649d3-c90b-45fa-96b2-26930fb27858)

### Explanation:
- **Users**: Stores user details like name, email, profile picture, and preferences.
- **Meetings**: Stores details about scheduled meetings such as title, time, participants, and meeting status.
- **Participants**: Associates users with the meetings they are attending.
- **Notifications**: Stores meeting invitations, reminders, and status updates.
- **Audio/Video Sessions**: Stores session-related information for real-time communications.

## 6. Interface Design

### 6.1 API Design

Below are some REST API endpoints for interaction:

![API Design](https://github.com/user-attachments/assets/7ce242c4-adf0-4954-a18f-e66782a6dacb)

### 6.2 External System Interfaces
- **Calendar API**: Provides integration with Google Calendar, Outlook, and other calendar services.
- **SMS/Email Gateway**: Sends notifications for meeting invitations and reminders (e.g., Twilio, SendGrid).
- **WebRTC**: Facilitates real-time communication for video/audio streaming.

### 6.3 Notification Flow Diagram
This diagram represents the flow of notifications between services, such as sending reminders or meeting invitations to users.

## 7. Non-Functional Requirements

![Design](https://github.com/user-attachments/assets/7fc22453-68b7-4634-8b21-4158d7976f6c)

### 7.1 Performance
The system should support up to 5000 concurrent users per meeting with smooth video and audio streams.

### 7.2 Scalability
The backend should be horizontally scalable to accommodate increasing users and meetings. Load balancing should be employed to manage peak usage times.

### 7.3 Availability
The system should ensure 99.9% uptime with backup servers in different geographical regions for redundancy.

### 7.4 Security
The system should implement encryption for video/audio streams, end-to-end encryption for chat messages, and secure authentication methods (OAuth, JWT).

### 7.5 Usability
The application should be responsive, providing a consistent user experience on both mobile and desktop devices.

## 8. Conclusion
This Software Design Description outlines the architecture, modules, database, and interfaces for the video conferencing system, ensuring the application is scalable, secure, and user-friendly. The modular design allows for future enhancements, including additional collaboration features such as screen sharing, file transfer, and meeting recording.
