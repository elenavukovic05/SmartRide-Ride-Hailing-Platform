# SmartRide Ride-Hailing Platform

> A full-stack ride-hailing platform with a Spring Boot backend, an Angular web client and a native Android app, where passengers order rides and the system automatically assigns drivers.

## Overview

This project was developed as a team project (team of 3) across several university courses: server-side engineering, client-side engineering, mobile applications and software testing.

The platform is inspired by Uber. Passengers can order rides with multiple stops and track them live, drivers are assigned automatically by the system, and administrators manage users, prices and support.

---

# Architecture

```
   Angular Web Client        Android App (Java)
           │                        │
           └──────────┬─────────────┘
                      ▼
        Spring Boot REST API (JWT security)
                      │
        ┌─────────────┼─────────────┐
        ▼             ▼             ▼
   Relational DB   Email service   Notifications
   (rides, users,                  (stored in DB,
    vehicles)                      shown in app)
```

Maps and routing are integrated through OpenStreetMap (Leaflet on the web).

---

# Technologies

- Java
- Spring Boot
- Spring Security (JWT)
- Spring Data JPA
- Relational database (H2 / PostgreSQL)
- Angular (TypeScript)
- Angular Material
- Leaflet / OpenStreetMap
- Android (Java), Material Design 3
- JUnit 5 and Mockito
- Spring MockMvc and `@DataJpaTest`
- Jasmine
- Selenium

---

# Project Features

## Users and Accounts

- Public map with active vehicles and ride estimate for unregistered users
- Registration with email activation, login, password reset
- Driver onboarding by an administrator with a time-limited activation link
- Profile management, driver profile changes require admin approval
- Blocking users and drivers with admin notes

## Rides

- Ride ordering with multiple stops, vehicle type, baby and pet options, linked passengers
- Scheduled rides up to 5 hours ahead with reminders
- Automatic driver assignment
- Live ride tracking, ride start, stop and cancellation
- PANIC button, ratings, favorite routes

## Reports and Support

- Ride history with filtering and sorting
- Reports with charts: rides per day, distance, spending / earnings, cumulative sum and average
- Live support chat and price management for administrators

## Automatic Driver Assignment

When a ride is ordered, the backend:

1. Filters drivers by vehicle type, seat count, baby and pet support
2. Skips drivers who already have a scheduled ride
3. Considers a driver with an active ride only if it ends within 10 minutes
4. Rejects drivers who would exceed the 8-hour working limit within 24 hours
5. Prefers free drivers closest to the pickup point, otherwise the busy driver whose current ride ends closest to the new pickup

---

# My Contribution

This is a fork of a team project. Below are the parts I implemented across the backend, Angular web client and Android app.

- **Driver registration**: administrator creates a driver and vehicle, driver receives a time-limited activation email and sets a password
- **Profile management**: profile editing with an admin approval workflow for driver changes
- **Ride ordering and driver assignment**: multi-stop rides, price calculation, scheduling rules and the automatic assignment algorithm
- **Favorite routes**: saving routes and ordering rides from them
- **Starting a ride**
- **Ride reports**: charts for rides, distance and spending / earnings, with cumulative sums and averages, for users and administrators
- **User blocking**: blocking users and drivers with admin notes
- **Testing**:
  - Ride ordering: unit tests for `RideService.createRide` (JUnit, Mockito), repository tests (`@DataJpaTest`) and controller tests (MockMvc)
  - Driver registration: Angular component tests (Jasmine)
  - Selenium end-to-end test for ordering a ride from favorite routes, using the Page Object pattern

---

# Learning Outcomes

This project demonstrates practical experience with:

- Full-stack application design
- REST API design and JWT security
- Business logic and scheduling rules
- Native Android development
- Test automation at multiple levels
- Working in a team with split feature ownership

---
