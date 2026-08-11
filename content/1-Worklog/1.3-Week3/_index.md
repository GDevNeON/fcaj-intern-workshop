---
title: "Week 3 Worklog"
date: 2026-07-06
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

- Complete development of NeonFoodMap application codebase (ReactJS Frontend & Django REST Backend).
- Design Database Schema, construct RESTful APIs, and integrate AWS Polly Text-to-Speech service prior to AWS cloud deployment.

### Tasks Executed During the Week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon | - Setup local development environment (Python 3.11, Django, Node.js/React, local MySQL) | 06/07/2026 | 06/07/2026 | |
| Tue | - Design DB Schema (Users, POIs, Audios, Reviews) & run Django ORM migrations | 07/07/2026 | 07/07/2026 | |
| Wed | - Build RESTful APIs: JWT Auth, POI radius search & integrate AWS Polly Text-to-Speech | 08/07/2026 | 08/07/2026 | |
| Thu | - Develop ReactJS UI: interactive map (Leaflet/Mapbox), Audio Player & POI details | 09/07/2026 | 09/07/2026 | |
| Fri | - Test APIs with Postman, verify local Frontend-Backend integration & responsive UI | 10/07/2026 | 10/07/2026 | |

### Detailed Daily Execution Breakdown:

- **Monday (06/07/2026):** Environment setup: installed Python 3.11, Django REST Framework, Node.js 18, ReactJS, local MySQL Server 8.0, and initialized Git repositories for both Backend and Frontend codebases.
- **Tuesday (07/07/2026):** Database schema modeling in Django ORM: defined tables for `Users`, `FoodPlaces` (POIs), `Categories`, `AudioCommentaries`, `Reviews`, and `Orders`. Generated initial Django migration files and applied them to local MySQL.
- **Wednesday (08/07/2026):** Implemented core RESTful APIs: Authentication endpoints (JWT token generation/refresh), location search API (GPS radius calculation for nearby POIs), order processing endpoints, and integrated AWS Boto3 SDK to call AWS Polly Text-to-Speech API for generating `.mp3` audio commentaries.
- **Thursday (09/07/2026):** Developed Frontend ReactJS user interface: embedded interactive map component (Leaflet/Mapbox), constructed location feed, built audio commentary player component, and crafted user profile management screens.
- **Friday (10/07/2026):** End-to-end local integration testing using Postman (validating JWT tokens, HTTP response statuses, JSON payloads). Verified cross-browser responsive design on desktop and mobile viewport sizes.

### Week 3 Achievements:

- Fully set up local development environments for both the Frontend and Backend components.
- Analyzed and successfully constructed the Database Schema to fulfill all business logic requirements for the NeonFoodMap project.
- Completed the development of RESTful APIs on Django REST Framework, integrating JWT authentication and AWS Polly Text-to-Speech services.
- Built a responsive and user-friendly Frontend UI using ReactJS featuring interactive map integration and audio commentary capabilities.
- Successfully integrated and tested API communication between the Frontend and Backend using Postman, ensuring accurate data retrieval and payload formatting.

