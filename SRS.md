# Software Requirements Specification (SRS) for Meeting Application Project

## 1.1 Introduction

### 1.1.1 Purpose
A new meeting application designed to transform how your team connects. This document explores features, user needs, and technical specifications for a user-friendly platform to schedule, conduct, and manage productive virtual meetings. The project aims to foster collaboration and address remote communication challenges, offering an application that empowers seamless connection and efficient collaboration.

### 1.1.2 Scope of the Project
The Meeting Application is a web-based platform modernizing meeting organization. It provides a user-friendly interface for scheduling, managing, and documenting meetings. Built with HTML, CSS, JavaScript, Tailwind CSS, Node.js, MongoDB, Socket.io, and Peer.js, it ensures cross-platform compatibility and scalability. The application streamlines meeting management, replacing manual processes, and boosting productivity through an intuitive interface and efficient features.

### 1.1.3 References
1. *Software Requirements* (Microsoft), Second Edition, by Karl E. Wiegers
2. *Fundamentals of Database Systems* by Elmasri
3. *Software Requirements and Specifications: A Lexicon of Practice, Principles, and Prejudices* (ACM Press) by Michael Jackson
4. *Fundamentals of Software Engineering* by Rajib Mall
5. *Software Engineering: A Practitioner’s Approach*, Fifth Edition, by Roger S. Pressman

---

## 1.2 Overall Description

### 1.2.1 Product Perspective
The Meeting Application replaces traditional meeting management methods with an advanced scheduling and documentation system. It streamlines processes from scheduling to recording minutes, tracking attendance, and generating analytics.

### 1.2.2 Product Functions
#### For Users:
- **New User Registration**: Sign-up with required details.
- **User Login**: Secure access for registered users.
- **Schedule Meeting**: Create meetings with title, time, agenda, and participants.
- **View Meetings**: Access details of past and upcoming meetings.
- **Join Meeting**: Participate in video conferencing.
- **Meeting Agenda**: Share meeting agendas with participants.
- **Minutes of Meeting**: Document and distribute meeting minutes.
- **Receive Notifications**: Automated alerts for meetings.

#### For Admins:
- **Record Meeting Activities**: Track schedules and attendance.
- **Manage Users**: Administer user accounts and permissions.
- **Manage Meetings**: Oversee meeting schedules and updates.
- **Room and Resource Booking**: Allocate resources efficiently.
- **View Meeting Analytics**: Analyze attendance and frequency.
- **Defaulter List**: Track habitual absentees.
- **Send Broadcast Notifications**: Share announcements with users.

### 1.2.3 Class Diagram and Characteristics
The class diagram defines the structure and relationships among classes, showcasing aggregation and multiplicity for effective meeting management.
<img width="354" alt="Screenshot 2024-12-02 at 10 42 27 PM" src="https://github.com/user-attachments/assets/2460a1e8-7fda-4f26-a647-cba31c69c616">

---

## 1.3 Designing the Meeting Application

### Use Case Diagram
The diagram outlines user and admin interactions, ensuring streamlined workflows with distinct roles.
<img width="307" alt="Screenshot 2024-12-02 at 10 43 44 PM" src="https://github.com/user-attachments/assets/108b240f-8d37-4e32-be35-98c54367b72c">



### ER Model
The ER diagram defines entities like User, Meeting, Participant, Recording, and Chat, detailing their relationships for efficient database management.
<img width="282" alt="Screenshot 2024-12-02 at 10 44 37 PM" src="https://github.com/user-attachments/assets/82762651-5864-4434-a43b-25978829f998">




### Data Flow Diagram (DFD)
The DFD represents information flow within the system across processes like scheduling, attendance tracking, and analytics generation:
- **Level 0**: Overview of system functionality.
- **Level 1**: Details user and admin interactions.
- **Level 2**: Highlights backend processes and database operations.
- 
<img width="871" alt="Screenshot 2024-12-02 at 10 45 34 PM" src="https://github.com/user-attachments/assets/6b0ef8b0-dc87-4b82-83b9-96d7bc9d2ee5">

---

## 1.4 Functional Requirements

- **User Authentication and Authorization**: Secure account creation and role-based access.
- **Video Conferencing**: Host and join meetings with audio, video, and screen sharing.
- **Meeting Scheduling**: Set meeting topics, dates, times, and invite participants.
- **Notification System**: Alerts for meeting updates and reminders.
- **Collaboration Features**: Share screens, documents, and virtual whiteboards.
- **Recording and Playback**: Record and replay meetings.
- **Integration**: Sync with Google Calendar or Outlook.

### 1.4.1 Software Requirements
- **Frontend**: HTML, CSS, JavaScript, Tailwind CSS
- **Backend**: Node.js, MongoDB, Peer.js, Socket.io
- **Operating System**: Windows 7 or above

### 1.4.2 Hardware Requirements
- **Processor**: Intel Core i3 or higher
- **Hard Disk**: 40GB or more
- **RAM**: 256MB (2GB recommended)

---

## 1.5 Non-Functional Requirements

### 1.5.1 Usability
The system should be user-friendly and handle errors efficiently.

### 1.5.2 Security
- Secure database with role-based access.
- Robust user authentication mechanisms.

### 1.5.3 Performance
- Handle large datasets and users without faults.
- Display information within 5 seconds.

### 1.5.4 Error Handling
Prevent information loss and minimize downtime during unexpected errors.

---
## 1.Appendices
- **Appendix A** : Abuse case Diagram

- **Appendix B** : Error case diagram

### Abuse case Diagram
![abusecaseDIagram](https://github.com/user-attachments/assets/823f29e7-d044-472d-99c6-5a5356a47556)
### Error case diagram
![error case diagram](https://github.com/user-attachments/assets/b92cecfa-1df9-4c3a-bb0d-6030371583e5)

