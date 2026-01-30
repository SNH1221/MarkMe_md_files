# Requirements Document

## Introduction

MarkMe is an AI-powered attendance intelligence system designed specifically for rural schools in India. The system addresses manual attendance recording issues, proxy attendance prevention, and provides meaningful insights in resource-constrained educational environments through a low-cost, RFID-based solution with cloud intelligence.

## Glossary

- **MarkMe_System**: The complete AI-powered attendance intelligence system
- **Android_App**: The mobile application running on entry-level smartphones
- **RFID_Reader**: Hardware device that reads student RFID cards
- **AWS_Backend**: Cloud infrastructure including DynamoDB, S3, and processing services
- **Attendance_Session**: A time-bounded period when students can mark attendance
- **Verification_Photo**: Random photo taken during attendance to prevent proxy attendance
- **AI_Engine**: Machine learning component that analyzes attendance patterns
- **Risk_Classification**: AI-generated categorization of students as Low/Medium/High risk
- **Dashboard**: Web interface for viewing attendance insights and reports
- **Parent_Alert**: Notification sent to parents about student absenteeism

## Requirements

### Requirement 1: Mobile Application Platform

**User Story:** As a rural school teacher, I want to use an Android application on entry-level smartphones, so that I can manage attendance without expensive hardware.

#### Acceptance Criteria

1. THE Android_App SHALL run on Android devices with API level 21 or higher
2. THE Android_App SHALL function with minimum 1GB RAM and 8GB storage
3. THE Android_App SHALL work offline and sync when connectivity is available
4. THE Android_App SHALL have a simple interface requiring minimal training
5. THE Android_App SHALL support multiple local languages including Hindi and English

### Requirement 2: Attendance Session Management

**User Story:** As a teacher, I want to start and end attendance sessions, so that I can control when students can mark their attendance.

#### Acceptance Criteria

1. WHEN a teacher starts an attendance session, THE MarkMe_System SHALL create a new session with timestamp and class details
2. WHEN an attendance session is active, THE MarkMe_System SHALL allow student check-ins via RFID
3. WHEN a teacher ends an attendance session, THE MarkMe_System SHALL close the session and prevent further check-ins
4. THE MarkMe_System SHALL automatically end sessions after 2 hours if not manually closed
5. WHEN a session is created, THE MarkMe_System SHALL generate a unique session identifier

### Requirement 3: RFID-Based Student Check-in

**User Story:** As a student, I want to mark my attendance using an RFID card, so that the process is quick and contactless.

#### Acceptance Criteria

1. WHEN a student presents an RFID card to the reader, THE MarkMe_System SHALL read the unique card identifier
2. WHEN a valid RFID card is detected during an active session, THE MarkMe_System SHALL record the attendance with timestamp
3. WHEN an invalid or unregistered RFID card is presented, THE MarkMe_System SHALL reject the attendance and display an error
4. WHEN a student attempts to mark attendance twice in the same session, THE MarkMe_System SHALL prevent duplicate entries
5. THE MarkMe_System SHALL process RFID readings within 2 seconds of card presentation

### Requirement 4: Cloud Data Storage

**User Story:** As a school administrator, I want attendance data stored securely in the cloud, so that it is accessible, backed up, and available for analysis.

#### Acceptance Criteria

1. WHEN attendance is recorded, THE MarkMe_System SHALL store the data in AWS DynamoDB within 30 seconds when online
2. WHEN the device is offline, THE MarkMe_System SHALL queue attendance data locally and sync when connectivity returns
3. THE MarkMe_System SHALL encrypt all data in transit using TLS 1.2 or higher
4. THE MarkMe_System SHALL encrypt all data at rest in the cloud storage
5. THE MarkMe_System SHALL maintain data integrity and prevent unauthorized access through IAM policies

### Requirement 5: Photo Verification System

**User Story:** As a teacher, I want random photo verification during attendance, so that I can prevent proxy attendance and ensure authenticity.

#### Acceptance Criteria

1. WHEN a student marks attendance, THE MarkMe_System SHALL randomly trigger photo verification for 20% of check-ins
2. WHEN photo verification is triggered, THE Android_App SHALL capture a photo using the device camera
3. WHEN a verification photo is taken, THE MarkMe_System SHALL store it securely in AWS S3
4. THE MarkMe_System SHALL associate verification photos with the corresponding attendance record
5. WHEN photo verification fails or is skipped, THE MarkMe_System SHALL flag the attendance record for review

### Requirement 6: Attendance Summaries and Reports

**User Story:** As a school administrator, I want automatic daily and weekly attendance summaries, so that I can track attendance patterns without manual calculation.

#### Acceptance Criteria

1. THE MarkMe_System SHALL generate daily attendance summaries for each class automatically
2. THE MarkMe_System SHALL generate weekly attendance summaries showing trends and patterns
3. WHEN summaries are generated, THE MarkMe_System SHALL store them in AWS S3 for retrieval
4. THE MarkMe_System SHALL calculate attendance percentages for individual students and classes
5. THE MarkMe_System SHALL format reports in government-compliant formats for official submission

### Requirement 7: AI Pattern Analysis

**User Story:** As an educator, I want AI analysis of attendance patterns, so that I can identify at-risk students and intervention opportunities.

#### Acceptance Criteria

1. WHEN sufficient historical data exists, THE AI_Engine SHALL analyze attendance patterns weekly
2. THE AI_Engine SHALL detect irregular attendance patterns including sudden drops and chronic absenteeism
3. THE AI_Engine SHALL identify students with declining attendance trends over time
4. WHEN pattern analysis is complete, THE AI_Engine SHALL generate insights and recommendations
5. THE AI_Engine SHALL process only attendance data and timestamps, not personal or biometric information

### Requirement 8: Student Risk Classification

**User Story:** As a teacher, I want students classified by attendance risk levels, so that I can prioritize intervention efforts effectively.

#### Acceptance Criteria

1. THE AI_Engine SHALL classify students into Low, Medium, or High risk categories based on attendance patterns
2. WHEN a student's risk level changes, THE MarkMe_System SHALL update their classification within 24 hours
3. THE MarkMe_System SHALL base risk classification on attendance percentage, pattern consistency, and recent trends
4. WHEN risk classification is updated, THE MarkMe_System SHALL notify relevant teachers and administrators
5. THE MarkMe_System SHALL maintain historical risk classification data for trend analysis

### Requirement 9: Dashboard and Insights

**User Story:** As a school administrator, I want a dashboard with attendance insights, so that I can make data-driven decisions about student engagement.

#### Acceptance Criteria

1. THE Dashboard SHALL display real-time attendance statistics for current sessions
2. THE Dashboard SHALL show historical attendance trends with visual charts and graphs
3. WHEN accessing the dashboard, THE MarkMe_System SHALL display student risk classifications and counts
4. THE Dashboard SHALL provide filtering options by class, date range, and risk level
5. THE Dashboard SHALL be accessible via web browser on both desktop and mobile devices

### Requirement 10: Parent Notification System

**User Story:** As a parent, I want to receive alerts about my child's absenteeism, so that I can address attendance issues promptly.

#### Acceptance Criteria

1. WHEN a student is absent for 2 consecutive days, THE MarkMe_System SHALL send a Parent_Alert via SMS
2. WHEN a student's risk classification changes to Medium or High, THE MarkMe_System SHALL notify parents within 24 hours
3. THE MarkMe_System SHALL send weekly attendance summaries to parents via SMS or email
4. WHEN sending notifications, THE MarkMe_System SHALL use the preferred communication method specified by parents
5. THE MarkMe_System SHALL respect parent privacy preferences and allow opt-out from non-critical notifications

### Requirement 11: Low Connectivity Operation

**User Story:** As a rural school teacher, I want the system to work with limited internet connectivity, so that attendance tracking continues even with network issues.

#### Acceptance Criteria

1. WHEN internet connectivity is unavailable, THE Android_App SHALL continue recording attendance locally
2. THE Android_App SHALL store up to 1000 attendance records locally when offline
3. WHEN connectivity returns, THE Android_App SHALL automatically sync all pending data to AWS_Backend
4. THE MarkMe_System SHALL handle intermittent connectivity gracefully without data loss
5. WHEN sync conflicts occur, THE MarkMe_System SHALL prioritize local records and flag discrepancies for review

### Requirement 12: Data Security and Privacy

**User Story:** As a school administrator, I want robust data security and privacy protection, so that student information remains confidential and compliant with regulations.

#### Acceptance Criteria

1. THE MarkMe_System SHALL implement role-based access control for all user types
2. THE MarkMe_System SHALL log all data access and modification activities for audit purposes
3. WHEN handling student data, THE MarkMe_System SHALL comply with applicable privacy regulations
4. THE MarkMe_System SHALL provide data export capabilities for school records and compliance
5. THE MarkMe_System SHALL allow secure data deletion when students leave the school