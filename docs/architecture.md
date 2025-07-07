# Rakshak Live – System Architecture

## Overview

Rakshak Live is a secure, real-time emergency livestreaming platform connecting citizens with police control rooms. This document describes the core components, data flow, and integration points necessary to build a scalable and secure system.

---

## Core Components

### 1. Mobile Client (Android App)
- Developed in Kotlin/Java.
- Features:
  - One-tap livestreaming using WebRTC or HLS.
  - Real-time GPS and landmark overlays.
  - User authentication via Aadhaar/DigiLocker APIs.
  - Local buffering for connectivity resilience.
  - Silent/safe mode for covert activation.

### 2. Backend Services
- Developed using Spring Boot or Node.js.
- Responsibilities:
  - User authentication and session management.
  - Stream ingestion, chunk processing, and secure upload to storage.
  - Metadata extraction (GPS, timestamp).
  - Alert routing to police control rooms.
  - Abuse detection and flagging logic.
  - API endpoints for police dashboard.

### 3. Cloud Storage
- Hosted on NIC/MeghRaj cloud infrastructure.
- Secure, encrypted storage for live stream chunks.
- Supports immutable logging and evidence integrity.
- Enables secure access for authorized personnel only.

### 4. Police Control Room Dashboard
- Web application built with ReactJS and TailwindCSS.
- Features:
  - Live stream viewing with embedded geolocation and landmarks.
  - Dynamic routing interface for responder navigation.
  - Multi-responder coordination tools.
  - Alert prioritization display.
  - Access controls with detailed audit logging.

### 5. Maps & Routing Services
- Integration with Google Maps API and/or ISRO Bhuvan platform.
- Real-time route calculation and traffic data.
- Landmark identification for better situational awareness.

---

## Data Flow

1. User initiates livestream on mobile app.
2. Video and metadata (GPS, timestamp) stream securely to backend.
3. Backend uploads stream chunks to government cloud storage.
4. Alerts are triggered and routed to police control room(s).
5. Police dashboard fetches live stream and metadata.
6. Police use dashboard routing to reach incident location.
7. Administrative actions (flagging, escalation) are logged immutably.

---

## Security Considerations

- End-to-end encryption (AES-256) for video and metadata.
- Strict access control with role-based permissions.
- Audit trails for all data access and admin activities.
- Compliance with Indian data privacy laws.
- Lawful interception coordination for device tracking in later phases.

---

## Scalability & Reliability

- Stateless backend services support horizontal scaling.
- CDN-backed streaming to minimize latency.
- Local caching on client ensures smooth experience during intermittent connectivity.
- Load balancers route alerts efficiently to multiple control rooms.
- Failover mechanisms in cloud storage for data redundancy.

---

## Integration Points

| Integration              | Description                               | Status            |
|-------------------------|-------------------------------------------|-------------------|
| Aadhaar/DigiLocker APIs | User identity verification and KYC        | Planned Phase 1   |
| Police IT Systems       | Incident management and case tracking     | Future integration |
| Telco Operators         | Device tracking (IMEI) for silent witnesses| Phase 2 & beyond  |
| Social Media APIs       | Controlled public broadcast by police     | Phase 3           |

---

## Diagram

*(Insert system architecture diagram here showing components and data flow)*

---

## Summary

This architecture ensures Rakshak Live delivers secure, reliable, and scalable emergency livestreaming. It balances real-time performance with strict privacy and legal compliance — providing a foundation for expanding advanced AI and tracking features in future phases.
