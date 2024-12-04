# Software Design Description (SDD) - Google Meet

## 1. Introduction

### 1.1 Purpose
The purpose of this Software Design Description (SDD) is to provide a detailed design for a video conferencing platform similar to Google Meet. The document outlines the software’s architecture, components, interfaces, and their interactions to ensure that the system meets both functional and non-functional requirements.

### 1.2 Scope
The Google Meet clone enables users to host and join video meetings via web and mobile applications. The system supports video/audio communication, screen sharing, real-time chat, participant management, and integrations with external services such as calendar tools. This design includes frontend and backend components, as well as the database design.

### 1.3 Design Goals
- Create a scalable and reliable video conferencing platform.
- Ensure smooth real-time communication with high video/audio quality.
- Provide a responsive, intuitive, and cross-platform user interface.
- Integrate with external services such as Google Calendar.
- Implement secure authentication and communication.

### 1.4 Architectural Principles
- **Microservices architecture** for modularity and scalability.
- **Real-time communication** using WebRTC or similar technology.
- **Event-driven design** for real-time notifications and updates.
- **Cloud-native architecture** to ensure scalability and redundancy.
- **Containerized deployment** for consistent environments.

## 2. System Architecture

### 2.1 Overview
The architecture of the Google Meet clone is based on a microservices model with key components separated into layers. These layers handle specific aspects of the application, including user interaction, video/audio communication, data storage, and third-party integrations.

### 2.2 Frontend Architecture
![frontendArchitecture](https://github.com/user-attachments/assets/f7c4443e-0cd8-42a7-a38a-007f87351587)

The frontend architecture includes:
- **Presentation Layer**: 
  - User Interface (UI) components built with React and React Native.
  - Responsive layouts using **Tailwind CSS** for styling.
  - Real-time video and audio control using **WebRTC**.
  
- **State Management**:
  - **Redux** for managing global state (e.g., user data, meeting state).
  - **Context API** for local component-level states.

- **Services Layer**:
  - APIs to interact with backend services like authentication, meeting scheduling, and video/audio handling.
  
- **Routing**:
  - **React Router** for web application navigation.
  - **React Navigation** for mobile apps.

#### Key Components:
- **Meeting Screen**: Displays video feed, chat, participant list, and control buttons.
- **Join Screen**: Allows users to enter meeting ID/link.
- **Scheduling Screen**: For creating and managing meetings.
- **Profile and Settings**: To manage user settings and preferences.

### 2.3 Backend System Architecture
![backendArchitecture](https://github.com/user-attachments/assets/47a53e3a-6e00-47bf-be9a-c210285a9555)

```plantuml
@startuml
title Backend Architecture of Google Meet

skinparam componentStyle rectangle

package "Frontend" {
  component "Web App" as WebApp
  component "Mobile App" as MobileApp
  component "Desktop App" as DesktopApp
}

package "Backend" {
  package "Signaling Layer" {
    component "Signaling Server" as SignalingServer {
      component "Session Manager" as SessionManager
    }
  }

  package "Media Layer" {
    component "Media Server" as MediaServer {
      component "SFU (Selective Forwarding Unit)" as SFU
      component "Transcoder" as Transcoder
    }
    component "TURN Server" as TURNServer
    component "STUN Server" as STUNServer
  }

  package "Auxiliary Services" {
    component "Authentication Service" as AuthService
    component "Authorization Service" as AuthorizationService
    component "Database" as Database
    component "Chat Service" as ChatService
    component "Recording Service" as RecordingService
    component "Storage Service" as StorageService
    component "Real-time Analytics Service" as AnalyticsService
    component "Notifications Service" as NotificationsService
  }

  package "Monitoring and Logs" {
    component "Log Aggregator" as LogAggregator
    component "Monitoring Dashboard" as Monitoring
  }
}

cloud "Internet" {
  component "Client Devices" as Clients
}

Clients --> WebApp : Connects via Internet
Clients --> MobileApp : Connects via Internet
Clients --> DesktopApp : Connects via Internet

WebApp --> SignalingServer
MobileApp --> SignalingServer
DesktopApp --> SignalingServer

SignalingServer --> SessionManager
SessionManager --> MediaServer
SignalingServer --> TURNServer
SignalingServer --> STUNServer
SignalingServer --> AuthService
AuthService --> Database
AuthService --> AuthorizationService

MediaServer --> SFU
MediaServer --> Transcoder
SFU --> TURNServer : Relay Media
SFU --> STUNServer : Establish P2P
Transcoder --> RecordingService
RecordingService --> StorageService

WebApp --> ChatService : Real-time Chat
MobileApp --> ChatService : Real-time Chat
DesktopApp --> ChatService : Real-time Chat

AnalyticsService --> Database : Collect Metrics
RecordingService --> NotificationsService : Notify on Recording
Monitoring --> LogAggregator : Collect Logs
LogAggregator --> Database : Store Logs

@enduml
```

### 2.3.1 Distributed Service Ecosystem
### Microservices Architecture
- Independently scalable services

### Event-Driven Communication
- Kafka/RabbitMQ for inter-service messaging

### Service Discovery
- Consul/Kubernetes for dynamic service registration

### 2.3.2 Authentication and Security Layer

### 1. Identity Management
- JWT-based authentication
- Role-based access control
- OAuth 2.0 and OpenID Connect support
- Passwordless authentication options

### 2. Security Mechanisms
- Encrypted token storage
- Brute-force protection
- Cross-Site Scripting (XSS) prevention
- SQL injection safeguards


### 2.3.3 Content Management Services

### 1. Video Processing Service
- Multi-format video transcoding
- Adaptive bitrate streaming
- Thumbnail generation
- Metadata extraction
- Content moderation

### 2. Storage Management
- Distributed file storage (AWS S3/Google Cloud Storage)
- Content Delivery Network (CDN) integration
- Efficient storage tiering
- Backup and disaster recovery


### 2.3.4 Recommendation and Discovery Engine

### 1. Machine Learning Models
- Collaborative filtering
- Content-based recommendation
- Hybrid recommendation algorithms
- User behavior analysis

### 2. Personalization Mechanisms
- Real-time preference tracking
- Contextual recommendation
- A/B testing recommendation strategies
- Diversity and serendipity in suggestions



### 2.3.5 Interaction and Engagement Services

### 1. User Interaction Tracking
- Like, comment, and share mechanisms
- Notification dispatch system
- Engagement metrics collection
- Community interaction workflows

### 2. Social Features
- Follow/subscribe functionality
- User-generated playlists
- Community content curation
- Collaborative viewing experiences



### 2.4 Cross-Cutting Concerns

### 2.4.1 Observability and Monitoring
- Distributed tracing
- Performance metrics collection
- Log aggregation
- Real-time alerting systems

### 2.4.2 Scalability Strategies
- Horizontal service scaling
- Load balancing
- Caching mechanisms
- Auto-scaling configuration

### 2.4.3 Compliance and Privacy
- GDPR compliance
- Data anonymization
- User consent management
- Transparent data handling



### 2.5 Advertising Ecosystem

### 2.5.1 Ad Targeting Strategy
- Demographic-based targeting
- Interest and behavior profiling
- Geographic location targeting
- Device-specific ad delivery

### 2.5.2 Ad Placement Types

#### Video Ad Formats
- Pre-roll ads
- Mid-roll ads
- Post-roll ads
- Overlay advertisements

#### Additional Placement Channels
- Sidebar recommendations
- Banner advertisements
- Sponsored content sections

### 2.5.3 Revenue Generation
- Impression-based pricing (CPM)
- Performance-based pricing (CPC)
- Revenue sharing with content creators
- Conversion tracking

### 2.5.4 Compliance and User Experience
- User ad preference settings
- Opt-out mechanisms
- Ad frequency capping
- Content moderation
- Brand safety filters

### 2.5.5 Technical Infrastructure
- Low-latency ad delivery
- Real-time bidding integration
- Fraud detection mechanisms
- Cross-platform ad compatibility

### 2.5.6 Advertiser Tools
- Self-service ad creation platform
- Campaign management dashboard
- Performance analytics
- A/B testing capabilities


### 2.6 Data Layer
The system will utilize a relational or NoSQL database for structured storage and fast access. Components include:

- **Primary Database**: **MongoDB** (NoSQL) for storing user data, meeting details, and session records.
- **Caching Layer**: **Redis** for fast access to frequently queried data like user sessions and meeting metadata.
- **File Storage**: **Amazon S3** or **Google Cloud Storage** for storing recorded meetings and user profile pictures.

### 3. System Components

### 3.1 Frontend Components
- **Home Screen**: Lists upcoming meetings and options to schedule new ones.
- **Meeting Screen**: Displays video feeds, chat, and controls for participants, screen sharing, and audio/video settings.
- **Join Screen**: Allows users to join meetings using meeting codes/links.
- **Settings/Profile**: Enables users to manage their profile, settings, and preferences.
  
### 3.2 Backend Components
- **API Gateway**: Handles routing for incoming requests and forwards them to the correct service.
- **Authentication Service**: Provides secure login and user management features.
- **Meeting Service**: Manages meeting data, schedules, and participants.
- **Real-time Communication Service**: Facilitates video/audio communication using **WebRTC**.
- **Notification Service**: Sends reminders, invites, and real-time updates to users.
  
## 4. Database Design
![databaseDesgin](https://github.com/user-attachments/assets/84fe7f08-4ccb-455c-88f2-90bfabd2d001)
```plantuml
@startuml
entity "Users" {
    * user_id : UUID [PK]
    * email : String [Unique]
    * password_hash : String
    * full_name : String
    * profile_picture_url : String
    * role : Enum('User', 'Host', 'Admin')
    * created_at : Timestamp
    * updated_at : Timestamp
}

entity "Meetings" {
    * meeting_id : UUID [PK]
    * host_id : UUID [FK -> Users.user_id]
    * title : String
    * description : String
    * start_time : Timestamp
    * end_time : Timestamp
    * is_recorded : Boolean
    * recording_url : String
    * created_at : Timestamp
    * updated_at : Timestamp
}

entity "Participants" {
    * participant_id : UUID [PK]
    * meeting_id : UUID [FK -> Meetings.meeting_id]
    * user_id : UUID [FK -> Users.user_id]
    * join_time : Timestamp
    * leave_time : Timestamp
    * role : Enum('Host', 'Participant')
}

entity "Chats" {
    * chat_id : UUID [PK]
    * meeting_id : UUID [FK -> Meetings.meeting_id]
    * sender_id : UUID [FK -> Users.user_id]
    * message : Text
    * sent_at : Timestamp
}

entity "Devices" {
    * device_id : UUID [PK]
    * user_id : UUID [FK -> Users.user_id]
    * device_type : Enum('Desktop', 'Mobile', 'Tablet')
    * os : String
    * last_used_at : Timestamp
}

entity "Settings" {
    * settings_id : UUID [PK]
    * user_id : UUID [FK -> Users.user_id]
    * theme : Enum('Light', 'Dark')
    * notifications_enabled : Boolean
    * language : String
    * time_zone : String
}

entity "MeetingAnalytics" {
    * analytics_id : UUID [PK]
    * meeting_id : UUID [FK -> Meetings.meeting_id]
    * participants_count : Integer
    * avg_speaking_time : Decimal
    * total_duration : Decimal
    * bandwidth_usage : Decimal
    * created_at : Timestamp
}

entity "Recordings" {
    * recording_id : UUID [PK]
    * meeting_id : UUID [FK -> Meetings.meeting_id]
    * file_url : String
    * file_size : Decimal
    * created_at : Timestamp
}

entity "Roles" {
    * role_id : UUID [PK]
    * role_name : String [Unique]
    * permissions : Text
}

entity "Logs" {
    * log_id : UUID [PK]
    * user_id : UUID [FK -> Users.user_id]
    * action : String
    * description : Text
    * logged_at : Timestamp
}

Users "1" -- "0..*" Meetings : "Hosts"
Meetings "1" -- "0..*" Participants : "Includes"
Users "1" -- "0..*" Participants : "Joins"
Meetings "1" -- "0..*" Chats : "Has"
Users "1" -- "0..*" Chats : "Sends"
Users "1" -- "0..*" Devices : "Uses"
Users "1" -- "0..*" Settings : "Configures"
Meetings "1" -- "0..*" MeetingAnalytics : "Generates"
Meetings "1" -- "0..*" Recordings : "Records"
Users "1" -- "0..*" Logs : "Generates"
Roles "1" -- "0..*" Users : "Assigned"
@enduml
```

### 4.1 Database Schema
The database will be structured to store and retrieve data related to users, meetings, participants, and notifications. The major collections or tables will include:

- **Users**: Stores user profile data, including name, email, password, preferences, and authentication tokens.
- **Meetings**: Stores meeting details, such as title, scheduled time, participants, and status.
- **Participants**: A mapping of which users are participating in which meetings.
- **Notifications**: Stores meeting-related notifications like reminders and updates.
- **Meeting Recordings**: Metadata about recordings, such as file location, meeting ID, and participant list.

### 4.2 Data Flow
- Users will create and schedule meetings, which will be stored in the **Meetings** collection.
- When a user joins a meeting, the participant is recorded in the **Participants** table.
- Notifications are stored in the **Notifications** collection, which is sent via email/SMS or real-time channels.
- Meeting recordings and associated data will be stored in a cloud storage solution like **Amazon S3**.

## 5. Interface Design
![interfaceDesign](https://github.com/user-attachments/assets/c012197d-f387-4b62-8a24-8ce0bed7f913)

```plantuml
@startuml
skinparam linetype polyline
title Google Meet - Interface Design

rectangle "Authentication Screens" {
    (Login Screen) as Login
    (Sign-up Screen) as Signup
    (Password Recovery) as PasswordRecovery
}

rectangle "Main Application Screens" {
    (Home/Dashboard) as Home
    (Meeting Room) as MeetingRoom
    (Scheduled Meetings) as ScheduledMeetings
    (Meeting Details) as MeetingDetails
}

rectangle "Meeting Features Screens" {
    (Chat Window) as Chat
    (Participants List) as Participants
    (Screen Sharing) as ScreenShare
    (Recording Management) as Recording
    (Settings/Preferences) as Preferences
}

rectangle "User Profile Screens" {
    (User Profile) as Profile
    (Account Settings) as AccountSettings
    (Meeting History) as MeetingHistory
}

rectangle "Navigation Components" {
    (Sidebar Menu) as Sidebar
    (Top Navigation Bar) as TopNav
    (Join Meeting Button) as JoinButton
    (Schedule Meeting Button) as ScheduleButton
}

rectangle "UI Components" {
    (Video Grid) as VideoGrid
    (Mute/Unmute Button) as MuteButton
    (Video On/Off Button) as VideoButton
    (End Call Button) as EndCall
    (Raise Hand Button) as RaiseHand
    (Chat Icon) as ChatIcon
}

' Navigation Flows
Login --> Home
Signup --> Home
Home --> MeetingRoom
MeetingRoom --> Chat
MeetingRoom --> Participants
MeetingRoom --> ScreenShare
Sidebar --> Home
Sidebar --> ScheduledMeetings
Home --> MeetingDetails
MeetingDetails --> JoinButton

note right of "UI Components"
    Design Principles:
    - Responsive Design
    - Mobile-First Approach
    - Consistent UI/UX
    - Accessibility
    - Performance Optimized

    Breakpoints:
    - Mobile: <600px
    - Tablet: 600-1024px
    - Desktop: >1024px
end note
@enduml

```
### 5.1 API Design
The system will expose REST APIs and GraphQL endpoints for the frontend and third-party integrations:

- **POST /users/register**: Registers a new user.
- **POST /users/login**: Authenticates a user and returns a token.
- **POST /meetings**: Creates a new meeting.
- **GET /meetings/{id}**: Retrieves meeting details.
- **POST /join**: Allows a user to join an existing meeting using a meeting ID/link.
- **GET /notifications**: Fetches unread notifications.

### 5.2 Real-Time Communication
The backend will use **WebSocket** or **WebRTC signaling** to facilitate real-time communication for audio/video and chat functionalities. Additionally, the backend will support sending real-time notifications to the frontend when there are updates to meetings or user activities.

### 5.3 Third-Party Integration
- **Google Calendar API**: Sync meetings and send calendar invites.
- **WebRTC**: Real-time communication protocol for video/audio streaming and screen sharing.
- **Twilio/SendGrid**: For sending SMS and email notifications.

## 6. Non-Functional Requirements

### 6.1 Performance
- The system should support **up to 1000 concurrent participants** in a single meeting with minimal latency.
- Video and audio streams should have **low latency**, providing a seamless experience.

### 6.2 Scalability
- The system must be horizontally scalable, able to handle a growing number of users and meetings.
- Load balancing should be implemented to manage user traffic efficiently across multiple servers.

### 6.3 Availability
- The system must ensure **99.9% uptime** with backup servers and automatic failover mechanisms.

### 6.4 Security
- The system must implement **end-to-end encryption** for video/audio streams and chat messages.
- Secure authentication and authorization using **OAuth 2.0** and **JWT**.
- Data should be encrypted both at rest and in transit.

### 6.5 Usability
- The platform should offer a **responsive design** for both desktop and mobile devices.
- The UI must be **intuitive** and user-friendly, providing clear instructions for joining and scheduling meetings.

## 7. Conclusion
This Software Design Description (SDD) outlines the architecture, components, database design, and interfaces for the Google Meet-like video conferencing system. The design ensures scalability, security, and real-time communication, while providing a smooth and responsive user experience. The modular architecture allows easy maintenance and future enhancements, such as adding new features like recording, live captions, or enhanced collaboration tools.
