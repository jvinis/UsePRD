
### PRD: DJ CRM Application

**Version:** 1.0
**Last Updated:** 2024-03-15

**1. Introduction**

This document outlines the product requirements for a new Customer Relationship Management (CRM) application specifically designed for DJs. The application aims to provide DJs with a centralized platform to manage their professional activities, including contacts, gigs, finances, music, and communications. Based on user input, this project is considered a new application, with any pre-existing codebase being minimal or serving primarily as a foundational starting point rather than a complex system to integrate with.

**2. Goals**

*   To develop a comprehensive CRM tool tailored to the unique needs of DJs.
*   To streamline the management of DJ-related contacts, including venues, promoters, and clients.
*   To simplify the booking, scheduling, tracking, and overall management of gigs and events, including DJ availability.
*   To provide robust tools for financial tracking, encompassing invoices, payments, and expenses related to DJing activities.
*   To offer functionality for organizing music libraries and planning/managing setlists for events.
*   To enable efficient tracking and logging of communications (e.g., emails, notes) with key contacts.

**3. Target Audience**

*   **Primary:** Individual professional DJs (e.g., mobile DJs, club DJs, wedding DJs, event DJs) seeking an all-in-one solution to manage their business.
*   **Secondary (Potential Future Scope):** DJ agencies or managers requiring a tool to manage multiple artists.

**4. Product Features**

The DJ CRM will include the following core modules, based on user selections:

**4.1. Contact Management**
*   **Objective:** Allow DJs to efficiently create, manage, and organize all their professional contacts (venues, promoters, clients, etc.).
*   **Key Functionalities:**
    *   Create, view, edit, and delete contacts.
    *   Store comprehensive contact details:
        *   Name (Individual/Organization)
        *   Contact Type (e.g., Venue, Promoter, Client, Fellow Artist, Supplier)
        *   Email Address(es)
        *   Phone Number(s)
        *   Physical Address
        *   Social Media Profile Links
        *   General notes and relationship history.
    *   Search, sort, and filter contacts by various criteria (e.g., type, name, location).
    *   Ability to group or tag contacts.
    *   Link contacts to relevant gigs/events and communication logs.

**4.2. Gig/Event Management**
*   **Objective:** Provide a robust system for managing all aspects of DJ bookings, scheduling, and event details, including availability.
*   **Key Functionalities:**
    *   Create, view, edit, and delete gig/event entries.
    *   Store detailed event information:
        *   Event Name/Title
        *   Date(s) and Times (Start/End)
        *   Venue (can be linked from Contacts)
        *   Client (can be linked from Contacts)
        *   Event Type (e.g., Wedding, Corporate, Club Night, Private Party)
        *   Status (e.g., Inquiry, Quoted, Confirmed, Completed, Cancelled, Postponed).
        *   Booking details: Agreed Fee, Deposit Information, Contract (e.g., attach file or link).
        *   Notes specific to the event (e.g., equipment requirements, dress code, specific requests).
    *   Calendar view: Display all gigs, color-coded by status, to visualize bookings and manage availability.
    *   Set reminders for upcoming gigs or related tasks.
    *   Ability to link gigs to financial records (invoices, payments) and setlists.

**4.3. Financial Tracking**
*   **Objective:** Enable DJs to track their income and expenses, manage invoices, and get an overview of their financial health related to their DJing business.
*   **Key Functionalities:**
    *   Invoice Management:
        *   Create professional invoices for gigs (linkable to Gig/Event entries).
        *   Customize invoice templates (basic customization).
        *   Track invoice status (e.g., Draft, Sent, Paid, Partially Paid, Overdue).
        *   Record payments received against invoices.
    *   Expense Tracking:
        *   Log business-related expenses.
        *   Categorize expenses (e.g., Travel, Music Purchases, Equipment, Software, Marketing).
        *   Store expense details: Date, Amount, Vendor, Description, attach receipts (optional).
    *   Basic Financial Reporting:
        *   View income/expense summaries over specified periods.
        *   Profit/loss overview per gig (calculated from gig fee and linked expenses).

**4.4. Music/Setlist Management**
*   **Objective:** Help DJs organize their music information and plan/manage setlists for their events.
*   **Key Functionalities:**
    *   Create, save, edit, and manage multiple setlists.
    *   Add tracks to setlists with details such as:
        *   Track Title
        *   Artist
        *   Duration (optional)
        *   BPM (optional)
        *   Key (optional)
        *   Custom notes per track within a setlist.
    *   Ability to reorder tracks within a setlist.
    *   Associate setlists with specific gigs/events.
    *   Add general notes or themes to a setlist.
    *   Option to export or print setlists (e.g., as PDF or plain text).
    *   (Assumption: Initial version may rely on manual track data entry; integration with music library software is a future consideration).

**4.5. Communication Tracking**
*   **Objective:** Provide a centralized way to log and review important communications (emails, notes from calls/meetings) with contacts.
*   **Key Functionalities:**
    *   Log communication activities: date, type (e.g., Email, Call, Meeting, Note), direction (Incoming/Outgoing).
    *   Record a summary or detailed notes for each communication log.
    *   Link communication logs to relevant contacts and/or gigs/events.
    *   Set follow-up reminders or tasks based on communications.
    *   Search and filter communication logs.

**5. Assumptions**

*   The primary user (DJ) is comfortable using web-based applications for managing their business.
*   The application will be developed as a web application, accessible via modern web browsers on desktop and laptop computers. Mobile responsiveness for viewing is desirable, but a dedicated mobile app is out of scope for V1.0.
*   The initial version will focus on the core functionalities listed. Advanced integrations (e.g., direct email sending/receiving within the app, bank feed synchronization, deep DJ software integration) are considered future enhancements.
*   User authentication and data security are fundamental requirements, though specific technical details are TBD.

**6. Future Considerations (Out of Scope for V1.0 unless re-prioritized)**

*   Advanced reporting and analytics dashboards.
*   Direct email integration (sending/receiving) from within the CRM.
*   Client portal for sharing event details, contracts, invoices, and setlists.
*   Contract generation templates and e-signature capabilities.
*   Dedicated mobile applications (iOS/Android) for full functionality on the go.
*   Integration with popular DJ software or music streaming services for track import/metadata.
*   Team features for DJ agencies or multi-DJ operations.
*   Calendar synchronization with external calendar services (e.g., Google Calendar, Outlook Calendar).
