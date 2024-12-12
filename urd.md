# User Requirements Document (URD)

## 1. Introduction

### 1.1 Purpose
This document outlines the user requirements for the **Google Meet** application. It serves as a guide for the design, development, and testing of the application to ensure it meets the needs of its users, including hosts, participants, and administrators.

### 1.2 Scope
The Google Meet Clone will be a web and mobile-based video conferencing application that enables users to schedule, host, and join virtual meetings. Key features include real-time video and audio streaming, screen sharing, chat functionality, meeting recordings, and user management.

### 1.3 Definitions, Acronyms, and Abbreviations
- **Host**: A user who schedules and manages meetings.
- **Participant**: A user who joins meetings hosted by others.
- **Admin**: An entity responsible for overseeing the platform’s operations.
- **Recording**: Capturing and storing the audio and video of a meeting session.

### 1.4 References
- [Stakeholders.md](https://github.com/IIITLucknowSWEngg/CSITTeam017/blob/main/Stakeholders.md)
- [Project.md](https://github.com/IIITLucknowSWEngg/CSITTeam017/blob/main/project.md)

---

## 2. User Characteristics

### 2.1 Hosts
- Typically tech-savvy users comfortable with managing meetings.
- Require scheduling options, participant management, and control over meeting settings.

### 2.2 Participants
- General users, including non-technical individuals.
- Expect a straightforward interface for joining and participating in meetings.

### 2.3 Admins
- Responsible for user and platform management.
- Require access to analytics, logs, and controls to ensure smooth operation.

---

## 3. Functional Requirements

### 3.1 User Registration and Login
**All Users:**
- Register using email, phone number, or third-party authentication (e.g., Google).
- Log in using credentials or single sign-on (SSO).
- Password reset and account recovery options.

### 3.2 User Profiles
- **Hosts**: Manage profile information, meeting history, and preferences.
- **Participants**: View profile details and manage preferences.

### 3.3 Meeting Management
**Hosts:**
- Schedule meetings with date, time, and participant invites.
- Configure meeting settings (e.g., mute participants on entry, enable waiting rooms).
- Share meeting links or codes with participants.

**Participants:**
- Join meetings using a link or meeting code.
- Interact with hosts and other participants during the meeting.

### 3.4 Video and Audio Streaming
**All Users:**
- Real-time video and audio streaming with low latency.
- Option to mute/unmute and enable/disable video.

### 3.5 Collaboration Features
**All Users:**
- Share screens or specific application windows.
- Use in-meeting chat for messages and file sharing.
- Annotate shared screens or documents.

### 3.6 Notifications
**All Users:**
- Receive notifications for scheduled meetings, updates, and reminders.

### 3.7 Recording and Storage
**Hosts:**
- Start, pause, and stop meeting recordings.
- Access stored recordings in the cloud or local storage.

### 3.8 Admin Panel
**Admins:**
- Manage users, meetings, and recordings.
- Monitor platform usage and generate reports.
- Configure system-wide settings (e.g., security policies).

### 3.9 Customer Support
**All Users:**
- Access FAQs, help documentation, and live support chat.

---

## 4. Non-Functional Requirements

### 4.1 Performance
- Meetings must support up to 100 participants without latency.
- Video and audio quality must adjust dynamically based on network conditions.

### 4.2 Security
- End-to-end encryption for all meetings.
- Secure storage for meeting recordings and user data.
- Multi-factor authentication for user accounts.

### 4.3 Usability
- Intuitive interfaces for web and mobile platforms.
- Accessibility features, including keyboard navigation and screen reader support.

### 4.4 Reliability
- 99.9% uptime with fallback mechanisms.
- Automatic failover for critical services.

### 4.5 Scalability
- Support for up to 10,000 simultaneous users.
- Dynamic resource allocation to handle high demand.

---

## 5. Assumptions and Dependencies
- The application will rely on third-party services for video streaming, notifications, and cloud storage.
- Users are assumed to have stable internet connections and access to modern devices.

---

## 6. Acceptance Criteria
- The application must pass all functional and non-functional tests.
- User feedback from the beta phase must be addressed before the final release.
- The app must meet all security, usability, and performance benchmarks outlined in this document.

---

## 7. Conclusion
This document defines the user requirements for the Google Meet Clone application. It serves as a comprehensive guide for the development team to ensure the final product meets user needs and aligns with the project’s goals.
