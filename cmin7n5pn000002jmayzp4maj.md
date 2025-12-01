---
title: "I Built a Modern Clinic Management System with React & TypeScript — Here's How"
seoTitle: "Building a Clinic System with React & TypeScript"
seoDescription: "Discover how I built DocBook, a powerful clinic management system using React and TypeScript, streamlining appointments and administrative processes"
datePublished: Mon Dec 01 2025 13:54:12 GMT+0000 (Coordinated Universal Time)
cuid: cmin7n5pn000002jmayzp4maj
slug: i-built-a-modern-clinic-management-system-with-react-and-typescript-heres-how
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1764597126868/99e5d011-17c7-466a-a358-97dfc0967c3b.png
tags: technology, databases, full-stack, reactjs, testing, typescript, admin, vite, clinic

---

## **Introduction**

I built **DocBook** – a full-featured clinic management system that streamlines healthcare operations for both patients and administrators. The platform offers real-time appointment booking, live queue management, and a comprehensive admin dashboard with emergency case handling.

**Role:** Full-Stack Developer (solo)  
**Timeline:** 2 weeks  
**Tech:** React 18, TypeScript, Vite, TailwindCSS, shadcn/ui, TanStack Query  
**Live Demo:** [https://docbook.abdultalha.tech/](https://docbook.abdultalha.tech/)  
**GitHub Repo:** [https://github.com/abdultalha0862/docbook](https://github.com/abdultalha0862/docbook)

## **The Problem**

Managing clinic appointments is often chaotic:

* Patients wait endlessly without knowing their queue position
    
* No real-time availability for booking slots
    
* Administrators juggle multiple systems for appointments, patients, and emergencies
    
* Emergency cases get lost in the regular queue
    
* No unified dashboard for clinic metrics
    

I wanted to build a solution that addresses these real healthcare challenges.

## **The Solution**

A modern clinic management platform with real-time queue tracking, instant booking, and separate portals for patients and administrators.

## **Key Features**

### **For Patients**

* **Instant Slot Booking** – Real-time availability with immediate confirmation
    
* **Live Queue Tracking** – Know your exact position with automatic updates
    
* **Doctor Discovery** – Browse specialists with ratings and experience
    
* **Emergency Priority Booking** – Special handling for urgent medical cases
    
* **Appointment History** – Track past and upcoming visits
    

### **For Administrators**

* **Real-Time Dashboard** – Live metrics on appointments, doctors, and emergencies
    
* **Queue Management** – Control patient flow with status updates
    
* **Patient Database** – Comprehensive patient records
    
* **Emergency Handling** – Priority workflows for urgent cases
    
* **Appointment Lifecycle Control** – Approve, modify, or cancel appointments
    

## **Technical Architecture**

### **Frontend Stack**

* **React 18 + TypeScript:** Type-safe, modular components
    
* **Vite:** Lightning-fast development and build
    
* **TailwindCSS:** Rapid, responsive UI styling
    
* **shadcn/ui + Radix UI:** Accessible, modern component library
    
* **TanStack Query:** Efficient server state management
    

### **Key Engineering Decisions**

* **Component-Based Architecture:** 13 core components + 40+ reusable UI components
    
* **Custom Hooks Pattern:** Separated data logic from UI (useAppointments, useDoctors, useDepartments)
    
* **First-Come-First-Serve Queue System:** Global counter ensures fair appointment ordering
    
* **Optimistic Updates:** Instant UI feedback with background sync
    
* **Separate Portals:** Distinct user experiences for patients and admins
    

## **Core Implementations**

### **Queue Management System**

* Global queue counter for fair appointment ordering
    
* Real-time status updates (pending → confirmed → in-progress → completed)
    
* Emergency flag for priority handling
    

### **Appointment Booking Flow**

1. Patient authentication (sign in/sign up)
    
2. Doctor selection with speciality filtering
    
3. Real-time slot availability check
    
4. Information collection (symptoms, reason, emergency flag)
    
5. Queue number assignment with instant confirmation
    

### **Admin Dashboard**

* Live metrics cards showing today's appointments, pending approvals, active doctors, and emergency cases
    
* Categorised appointment views (pending, in-progress, completed)
    
* One-click status updates with toast notifications
    

### **State Management**

* TanStack Query for data fetching and caching
    
* Query invalidation for real-time updates
    
* Mutation hooks for optimistic updates
    

## **Testing**

Developed a comprehensive test suite with Vitest + React Testing Library:

* **Component Tests:** DoctorCard, AppointmentCard UI testing
    
* **Hook Tests:** useAppointments data logic validation
    
* **Integration Tests:** Full booking form workflow
    
* **E2E Tests:** Complete booking flow simulation
    
* **Utility Tests:** Mock data validation
    

## **Challenges & Solutions**

🔹 **Real-time queue position updates**  
Fix: Implemented query invalidation with TanStack Query for automatic data refresh on status changes.

🔹 **Emergency case prioritisation**  
Fix: Added `isEmergency` flag with visual indicators and separate admin view sections.

🔹 **Managing complex appointment states**  
Fix: Created typed status enum (pending, confirmed, in-progress, completed, cancelled) with strict state transitions.

🔹 **Responsive admin dashboard**  
Fix: Used CSS Grid with breakpoint-specific layouts (1-col mobile, 2-col tablet, 4-col desktop).

## **Results**

| Metric | Outcome |
| --- | --- |
| Core Components | 13 |
| UI Components | 40+ |
| Custom Hooks | 6 |
| Test Categories | 5 |
| Appointment States | 5 |
| User Portals | 2 (Patient + Admin) |
| Page Load Time | &lt; 2s |
| Backend Required | None (demo mode) |

The platform provides a complete clinic management experience with minimal setup.

## **What I Learned**

* **TanStack Query** simplifies complex data fetching and cache invalidation
    
* **Separate portals** improve UX by tailoring interfaces to user roles
    
* **Emergency handling** in healthcare apps requires careful visual hierarchy
    
* **shadcn/ui + Radix** accelerates development while maintaining accessibility
    
* **Comprehensive testing** is essential for healthcare applications where reliability matters
    

## **Future Enhancements**

* Backend integration with real database (Supabase/PostgreSQL)
    
* SMS/Email notifications for appointment reminders
    
* Multi-doctor scheduling with time slot conflicts
    
* Patient's medical history and records
    
* Analytics dashboard with appointment trends
    
* Payment gateway integration
    
* Mobile app (React Native)
    

## **Call To Action (CTA)**

If you want to:

* Build a modern healthcare or booking application like this
    
* Collaborate on open-source projects
    
* Hire me to create high-performance React applications
    

**Let's connect!**

📧 Email: abdul@abdultalha.tech  
🌐 Portfolio: [https://abdultalha.tech/](https://abdultalha.tech/)  
💼 LinkedIn: [https://www.linkedin.com/in/abdul-talha/](https://www.linkedin.com/in/abdul-talha/)  
⭐ GitHub: [https://github.com/abdultalha0862](https://github.com/abdultalha0862)

If you found this project interesting,  
⭐ **Star the repository on GitHub,** it genuinely helps!