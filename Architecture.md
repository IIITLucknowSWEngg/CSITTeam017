# System Context Diagram code

![architecture](https://github.com/user-attachments/assets/3b1e6caa-5cbe-427e-aeac-8e2e529028eb)


```plantuml
@startuml

    ' External Actors
    actor "User" as User
    actor "Admin" as Admin
    actor "Third-Party Auth Service" as AuthService
    actor "Notification Service" as NotificationService
    actor "Video Streaming Service" as StreamingService
    actor "Cloud Storage Service" as CloudStorage
    actor "Support Team" as SupportTeam

    ' System Boundary: Google Meet Clone
    package "Google Meet Clone" {

        ' Subsystems
        rectangle "User Registration \nand Authentication" as Registration
        rectangle "Meeting Management" as MeetingManagement
        rectangle "Video and Audio Processing" as VideoAudioProcessing
        rectangle "Screen Sharing \nand Collaboration" as ScreenSharing
        rectangle "Push Notifications" as PushNotifications
        rectangle "Recording and Storage" as Recording
        rectangle "Admin Panel" as AdminPanel
        rectangle "In-App Chat \nand Support" as ChatSupport
    }

    ' Relationships between actors and system components
    User --> Registration : Sign Up/Login
    User --> MeetingManagement : Create/Join Meetings
    User --> VideoAudioProcessing : Stream Video and Audio
    User --> ScreenSharing : Share Screen/Documents
    User --> PushNotifications : Receive Meeting Notifications
    User --> Recording : Start/Stop Meeting Recordings
    User --> ChatSupport : In-App Chat with Support

    Admin --> AdminPanel : Manage Users/Meetings
    Admin --> MeetingManagement : Monitor/Manage Meetings
    Admin --> PushNotifications : Send Notifications
    Admin --> Recording : Access Recorded Meetings

    ' External Interactions
    Registration --> AuthService : Authenticate Users
    MeetingManagement --> StreamingService : Handle Video/Audio Streams
    PushNotifications --> NotificationService : Send Notifications
    Recording --> CloudStorage : Store Meeting Recordings
    ChatSupport --> SupportTeam : Handle User Issues

@enduml
