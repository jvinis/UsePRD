### Implementation Plan

This plan outlines the steps to develop the DJ CRM application based on the provided Product Requirements Document (PRD).

**Phase 1: Project Setup & Core Infrastructure**

*   **Step 1.1: Initialize Project & Basic Structure**
    *   **Key Tasks:**
        *   Choose and set up the primary tech stack (e.g., frontend framework like React/Vue/Angular, backend framework like Node.js/Express, Python/Django/Flask, etc.).
        *   Initialize the project repository with Git.
        *   Create the basic directory structure for frontend, backend, shared components, and database-related files.
    *   **Manual Tests:**
        *   Verify that the project can be built and run locally (e.g., `npm start` or equivalent shows a basic placeholder page).
        *   Confirm the Git repository is initialized and initial commit is made.
        *   Check if the directory structure is logical and as planned.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "chore: Initialize project structure and basic setup for DJ CRM".*

*   **Step 1.2: Database Setup & Initial Schema Design**
    *   **Key Tasks:**
        *   Select a database system (e.g., PostgreSQL, MySQL, MongoDB) based on project needs.
        *   Install and configure the database.
        *   Define and implement the initial database schema for a `User` model (e.g., `id`, `email`, `password_hash`, `name`).
        *   Set up database migration tools if applicable.
    *   **Manual Tests:**
        *   Verify that the application can connect to the database.
        *   Check that the `Users` table (or collection) is created with the correct columns/fields and types.
        *   If using migrations, test that a migration can be run successfully.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "chore: Setup database and initial User schema".*

*   **Step 1.3: User Authentication**
    *   **Key Tasks:**
        *   Implement user registration functionality (e.g., endpoint for creating new users, UI form).
        *   Implement secure password hashing and storage.
        *   Implement user login functionality (e.g., endpoint for validating credentials, UI form).
        *   Implement session management (e.g., cookies) or token-based authentication (e.g., JWT) to protect routes.
    *   **Manual Tests:**
        *   User Registration: Attempt to register a new user with valid data. -> User should be created, password should be hashed in DB.
        *   User Registration (Invalid Data): Attempt to register with invalid/missing email, weak password. -> Appropriate error messages should be shown.
        *   User Login (Valid Credentials): Attempt to log in with a registered user. -> Login should be successful, session/token generated.
        *   User Login (Invalid Credentials): Attempt to log in with incorrect password or non-existent user. -> Login should fail with an error message.
        *   Protected Route Access: Attempt to access a protected route without logging in. -> Access should be denied. After login, access should be granted.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Auth): Implement user registration, login, and session management".*

**Phase 2: Contact Management (PRD Section 4.1)**

*   **Step 2.1: Contact Model, API Endpoints (CRUD)**
    *   **Key Tasks:**
        *   Define and implement the `Contact` model in the database. Fields: `Name` (Individual/Organization), `ContactType` (e.g., Venue, Promoter, Client), `EmailAddress(es)`, `PhoneNumber(s)`, `PhysicalAddress`, `SocialMediaProfileLinks`, `GeneralNotes`, `tags` (array of strings for grouping), `userId` (to associate with the logged-in user).
        *   Create backend API endpoints for Contacts: `POST /api/contacts` (Create), `GET /api/contacts` (Read all), `GET /api/contacts/:id` (Read one), `PUT /api/contacts/:id` (Update), `DELETE /api/contacts/:id` (Delete).
        *   Ensure endpoints are protected and operate on contacts belonging to the authenticated user.
    *   **Manual Tests:**
        *   API Test (Create): Send a POST request with valid contact data. -> New contact should be created in the DB and returned with a 201 status.
        *   API Test (Read All): Send a GET request. -> List of user's contacts should be returned.
        *   API Test (Read One): Send a GET request with a valid contact ID. -> Specific contact details should be returned.
        *   API Test (Update): Send a PUT request with updated data for an existing contact. -> Contact should be updated in the DB.
        *   API Test (Delete): Send a DELETE request for an existing contact. -> Contact should be removed from the DB.
        *   Attempt to access/modify another user's contact. -> Access should be denied.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Contacts): Implement Contact model and CRUD API endpoints".*

*   **Step 2.2: Contact List View & Basic UI**
    *   **Key Tasks:**
        *   Develop a UI page/component to display a list of contacts.
        *   Fetch and display key contact information (e.g., Name, Contact Type, Email, Phone) in a table or card layout.
        *   Include buttons/links for viewing details, editing, and deleting each contact.
        *   Add a button/link to navigate to the 'Create Contact' form.
    *   **Manual Tests:**
        *   Navigate to the contact list page. -> All contacts for the logged-in user should be displayed.
        *   Verify that key information for each contact is visible and correct.
        *   Confirm that 'View', 'Edit', 'Delete', and 'Create New Contact' buttons/links are present.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Contacts): Implement UI for Contact list view".*

*   **Step 2.3: Contact Create/Edit Form & Validation**
    *   **Key Tasks:**
        *   Develop a UI form for creating new contacts and editing existing ones.
        *   Include input fields for all `Contact` model attributes (Name, Type, Email, Phone, Address, Social Media, Notes, Tags).
        *   Implement client-side and server-side validation for required fields and data formats (e.g., email format).
    *   **Manual Tests:**
        *   Create Contact (Valid Data): Fill and submit the form with valid data. -> Contact should be created, user redirected to list or detail view, success message shown.
        *   Create Contact (Invalid Data): Submit form with missing required fields or invalid email. -> Validation errors should be displayed, contact not created.
        *   Edit Contact: Open an existing contact in the form, modify data, and submit. -> Contact should be updated, changes reflected.
        *   Tags: Test adding, editing, and removing tags for a contact.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Contacts): Implement Contact create/edit form with validation".*

*   **Step 2.4: Contact Detail View**
    *   **Key Tasks:**
        *   Develop a UI page/component to display the full details of a single selected contact.
        *   Display all fields from the `Contact` model.
        *   (Placeholders for future: display linked Gigs/Events and Communication Logs).
    *   **Manual Tests:**
        *   From the contact list, click to view a contact's details. -> All stored information for that contact should be displayed correctly.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Contacts): Implement Contact detail view page".*

*   **Step 2.5: Contact Deletion Functionality**
    *   **Key Tasks:**
        *   Implement the delete functionality triggered from the contact list or detail view.
        *   Include a confirmation dialog before actual deletion.
    *   **Manual Tests:**
        *   Attempt to delete a contact. -> Confirmation dialog should appear.
        *   Confirm deletion. -> Contact should be removed from the list and database.
        *   Cancel deletion. -> Contact should remain.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Contacts): Implement Contact deletion with confirmation".*

*   **Step 2.6: Search, Sort, and Filter Contacts**
    *   **Key Tasks:**
        *   Implement a search bar on the contact list view to search by name, type, or other relevant fields.
        *   Implement sorting options for the contact list (e.g., by Name A-Z, by Date Created).
        *   Implement filtering options (e.g., by Contact Type, by Tags).
    *   **Manual Tests:**
        *   Search: Enter a search term (e.g., part of a name). -> Only matching contacts should be displayed.
        *   Sort: Change sort order. -> List should re-order correctly.
        *   Filter: Apply a filter (e.g., 'Venue' type). -> Only contacts matching the filter should be displayed.
        *   Combine search and filters. -> Results should be accurate.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Contacts): Implement search, sort, and filter functionality for contacts".*

**Phase 3: Gig/Event Management (PRD Section 4.2)**

*   **Step 3.1: Gig/Event Model & API Endpoints (CRUD)**
    *   **Key Tasks:**
        *   Define and implement `GigEvent` model. Fields: `EventName`, `DateStart`, `TimeStart`, `DateEnd`, `TimeEnd`, `VenueContactId` (links to Contact), `ClientContactId` (links to Contact), `EventType`, `Status` (e.g., Inquiry, Quoted, Confirmed), `AgreedFee`, `DepositInfo`, `ContractLink` (URL or text), `EventNotes`, `userId`.
        *   Create backend API endpoints for Gigs/Events: `POST /api/gigs`, `GET /api/gigs`, `GET /api/gigs/:id`, `PUT /api/gigs/:id`, `DELETE /api/gigs/:id`.
        *   Ensure endpoints are protected and operate on gigs belonging to the authenticated user.
    *   **Manual Tests:**
        *   API Test (Create): Send POST with valid gig data. -> New gig created, linked to user.
        *   API Test (Read All): Send GET. -> List of user's gigs returned.
        *   API Test (Update): Send PUT with updated data. -> Gig updated.
        *   API Test (Delete): Send DELETE. -> Gig removed.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Gigs): Implement Gig/Event model and CRUD API endpoints".*

*   **Step 3.2: Gig/Event Create/Edit Form & Validation**
    *   **Key Tasks:**
        *   Develop UI form for creating/editing gigs.
        *   Fields for all `GigEvent` attributes.
        *   Dropdowns/selectors to link Venue and Client from existing Contacts (populated from Contacts module).
        *   Implement client-side and server-side validation.
    *   **Manual Tests:**
        *   Create Gig (Valid Data): Fill form, select venue/client from contacts, submit. -> Gig created, linked correctly.
        *   Create Gig (Invalid Data): Submit with missing required fields. -> Validation errors shown.
        *   Edit Gig: Modify an existing gig's details. -> Changes saved and reflected.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Gigs): Implement Gig/Event create/edit form with contact linking".*

*   **Step 3.3: Gig/Event List View**
    *   **Key Tasks:**
        *   Develop UI to display a list of gigs/events.
        *   Show key info: Event Name, Date, Venue, Status.
        *   Links/buttons for view, edit, delete.
    *   **Manual Tests:**
        *   Navigate to gig list page. -> All user's gigs displayed.
        *   Verify key information is correct.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Gigs): Implement UI for Gig/Event list view".*

*   **Step 3.4: Gig/Event Detail View**
    *   **Key Tasks:**
        *   Develop UI to display full details of a single gig/event.
        *   Display all fields, including linked Venue and Client names (with links to their detail pages if possible).
    *   **Manual Tests:**
        *   Click to view a gig's details. -> All stored information displayed correctly.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Gigs): Implement Gig/Event detail view page".*

*   **Step 3.5: Gig/Event Deletion Functionality**
    *   **Key Tasks:**
        *   Implement delete functionality with confirmation.
    *   **Manual Tests:**
        *   Attempt to delete a gig. -> Confirmation dialog appears.
        *   Confirm deletion. -> Gig removed.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Gigs): Implement Gig/Event deletion with confirmation".*

*   **Step 3.6: Basic Calendar View for Gigs**
    *   **Key Tasks:**
        *   Integrate a calendar component (e.g., FullCalendar, react-big-calendar).
        *   Fetch and display gigs on the calendar, using start/end dates.
        *   Color-code gigs by status (e.g., Confirmed, Inquiry).
        *   Clicking a gig on the calendar could navigate to its detail view or show a popover with basic info.
    *   **Manual Tests:**
        *   Navigate to calendar view. -> Gigs should be displayed on correct dates.
        *   Verify color-coding by status is working.
        *   Test navigation/popover on clicking a gig.
        *   Add/edit/delete a gig and verify calendar updates.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Gigs): Implement basic calendar view for gigs with status color-coding".*

*   **Step 3.7: Gig Reminders (Data Storage)**
    *   **Key Tasks:**
        *   Add fields to `GigEvent` model for reminder settings (e.g., `reminderDate`, `reminderNote`, `isReminderSet`).
        *   Update Gig create/edit form to allow setting these reminder details.
        *   (Actual notification system is out of scope for V1, this step focuses on data capture).
    *   **Manual Tests:**
        *   Create/edit a gig and set a reminder date/note. -> Data should be saved correctly.
        *   View gig details. -> Reminder information should be displayed if set.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Gigs): Add data storage for gig reminders".*

*   **Step 3.8: Update Contact View to Show Linked Gigs**
    *   **Key Tasks:**
        *   Modify the Contact Detail View (Step 2.4) to list gigs/events associated with that contact (as Venue or Client).
        *   Fetch and display a summary of linked gigs (e.g., Event Name, Date, Status).
    *   **Manual Tests:**
        *   Create a gig and link it to a contact as a client.
        *   Navigate to that contact's detail page. -> The newly created gig should be listed under a 'Linked Gigs/Events' section.
        *   Verify the displayed gig information is correct.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Contacts): Display linked gigs on contact detail view".*

**Phase 4: Financial Tracking (PRD Section 4.3)**

*   **Step 4.1: Invoice Model & API Endpoints (CRUD)**
    *   **Key Tasks:**
        *   Define `Invoice` model: `InvoiceNumber`, `GigEventId` (links to Gig), `IssueDate`, `DueDate`, `Status` (Draft, Sent, Paid, Partially Paid, Overdue), `LineItems` (array of objects: description, quantity, unit_price, total), `TotalAmount`, `Notes`, `userId`.
        *   Create API endpoints for Invoices: `POST /api/invoices`, `GET /api/invoices`, `GET /api/invoices/:id`, `PUT /api/invoices/:id`, `DELETE /api/invoices/:id`.
    *   **Manual Tests:**
        *   API Test (Create): Send POST with valid invoice data. -> New invoice created.
        *   API Test (Read All): Send GET. -> List of user's invoices returned.
        *   API Test (Update): Send PUT with updated data. -> Invoice updated.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Finances): Implement Invoice model and CRUD API endpoints".*

*   **Step 4.2: Invoice Create/Edit Form & Basic Customization**
    *   **Key Tasks:**
        *   Develop UI form for creating/editing invoices.
        *   Allow linking to a Gig/Event (populates client info, gig details).
        *   Fields for line items, dates, status.
        *   Store basic DJ info (name, address, logo URL - perhaps in user profile) to be used on invoices.
    *   **Manual Tests:**
        *   Create Invoice: Fill form, link to a gig, add line items. -> Invoice created, total calculated correctly.
        *   Edit Invoice: Modify an existing invoice. -> Changes saved.
        *   Check that DJ's info (if set in profile) appears on a preview or generated invoice.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Finances): Implement Invoice create/edit form with basic customization".*

*   **Step 4.3: Record Payments Against Invoices**
    *   **Key Tasks:**
        *   In the Invoice view/edit UI, add functionality to record payments (amount, date, method).
        *   Update Invoice status based on payments (e.g., to 'Partially Paid', 'Paid').
    *   **Manual Tests:**
        *   Record a partial payment for an invoice. -> Invoice status updates to 'Partially Paid', payment recorded.
        *   Record full payment. -> Invoice status updates to 'Paid'.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Finances): Implement payment recording for invoices".*

*   **Step 4.4: Expense Model & API Endpoints (CRUD)**
    *   **Key Tasks:**
        *   Define `Expense` model: `Date`, `Amount`, `Vendor`, `Description`, `Category` (e.g., Travel, Music), `ReceiptLink` (URL), `GigEventId` (optional, links to Gig), `userId`.
        *   Create API endpoints for Expenses: `POST /api/expenses`, `GET /api/expenses`, `PUT /api/expenses/:id`, `DELETE /api/expenses/:id`.
    *   **Manual Tests:**
        *   API Test (Create): Send POST with valid expense data. -> New expense created.
        *   API Test (Read All): Send GET. -> List of user's expenses returned.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Finances): Implement Expense model and CRUD API endpoints".*

*   **Step 4.5: Expense Logging Form & List View**
    *   **Key Tasks:**
        *   Develop UI form for logging new expenses.
        *   Fields for all `Expense` attributes, including category selection and optional Gig linking.
        *   Develop UI to list all logged expenses.
    *   **Manual Tests:**
        *   Log Expense: Fill and submit the expense form. -> Expense created and appears in list.
        *   Edit/Delete Expense: Test modifying and removing an expense.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Finances): Implement expense logging form and list view".*

*   **Step 4.6: Basic Financial Reporting View**
    *   **Key Tasks:**
        *   Develop a UI page for basic financial reports.
        *   Display income/expense summaries for selected periods (e.g., monthly, yearly).
        *   Display profit/loss per gig (Gig Fee from `GigEvent` - sum of linked `Expense` amounts for that gig).
    *   **Manual Tests:**
        *   Navigate to reporting page. -> Summaries should be displayed.
        *   Select a period. -> Data should update correctly.
        *   Verify profit/loss calculation for a gig with income and linked expenses.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Finances): Implement basic financial reporting view".*

*   **Step 4.7: Update Gig View to Show Linked Financials**
    *   **Key Tasks:**
        *   Modify the Gig Detail View (Step 3.4) to show linked invoices and expenses.
        *   Display a summary of financial items related to the gig.
    *   **Manual Tests:**
        *   Create an invoice and an expense, linking both to the same gig.
        *   Navigate to that gig's detail page. -> The linked invoice and expense should be listed.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Gigs): Display linked financials on gig detail view".*

**Phase 5: Music/Setlist Management (PRD Section 4.4)**

*   **Step 5.1: Setlist & Track Models & API Endpoints**
    *   **Key Tasks:**
        *   Define `Setlist` model: `Name`, `GigEventId` (optional, links to Gig), `GeneralNotes`, `userId`.
        *   Define `TrackInSetlist` (or embed in `Setlist`): `TrackTitle`, `Artist`, `Duration` (string, e.g., "3:45"), `BPM` (number), `Key` (string), `CustomNotes`, `Order` (number for sorting).
        *   Create API endpoints for Setlists (CRUD) and for managing tracks within a setlist (add, remove, reorder, update track details).
    *   **Manual Tests:**
        *   API Test (Create Setlist): Send POST with setlist name. -> New setlist created.
        *   API Test (Add Track to Setlist): Send POST to add a track with details to a setlist. -> Track added.
        *   API Test (Get Setlist with Tracks): Send GET for a setlist. -> Setlist details and its tracks returned in correct order.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Music): Implement Setlist and Track models and API endpoints".*

*   **Step 5.2: Setlist Create/Edit View & Track Management**
    *   **Key Tasks:**
        *   Develop UI for creating/editing setlists (name, notes, link to gig).
        *   Implement UI for adding tracks to a setlist (manual entry for Title, Artist, Duration, BPM, Key, Notes).
        *   Implement UI for reordering tracks within a setlist (e.g., drag-and-drop).
        *   Implement UI for editing/deleting tracks from a setlist.
    *   **Manual Tests:**
        *   Create a new setlist, add a name and notes.
        *   Add multiple tracks with all details. -> Tracks appear in the setlist.
        *   Reorder tracks. -> Order updates correctly.
        *   Edit a track's details. -> Changes saved.
        *   Delete a track. -> Track removed.
        *   Link setlist to a gig. -> Association saved.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Music): Implement Setlist create/edit UI with track management".*

*   **Step 5.3: Setlist List & Detail View**
    *   **Key Tasks:**
        *   Develop UI to list all created setlists (Name, associated Gig if any).
        *   Develop UI to view a single setlist's details, including all its tracks and their information.
    *   **Manual Tests:**
        *   Navigate to setlist list. -> All setlists displayed.
        *   Click to view a setlist. -> All tracks and setlist details are shown correctly.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Music): Implement Setlist list and detail views".*

*   **Step 5.4: Export/Print Setlist (Basic)**
    *   **Key Tasks:**
        *   Add a button/function to export a setlist to plain text or a simple HTML format suitable for printing.
        *   Output should include setlist name, notes, and all tracks with their details in order.
    *   **Manual Tests:**
        *   Open a setlist and click 'Export/Print'. -> A plain text or simple HTML version of the setlist is generated/displayed.
        *   Verify all information is present and correctly formatted.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Music): Implement basic setlist export/print functionality".*

*   **Step 5.5: Update Gig View to Show Linked Setlist**
    *   **Key Tasks:**
        *   Modify the Gig Detail View (Step 3.4) to show any setlist linked to it.
        *   Display setlist name with a link to the setlist detail view.
    *   **Manual Tests:**
        *   Create a setlist and link it to a gig.
        *   Navigate to that gig's detail page. -> The linked setlist name should appear, possibly as a link.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Gigs): Display linked setlist on gig detail view".*

**Phase 6: Communication Tracking (PRD Section 4.5)**

*   **Step 6.1: Communication Log Model & API Endpoints**
    *   **Key Tasks:**
        *   Define `CommunicationLog` model: `Date`, `Type` (Email, Call, Meeting, Note), `Direction` (Incoming/Outgoing), `Summary`, `Details`, `ContactId` (links to Contact), `GigEventId` (optional, links to Gig), `FollowUpDate`, `FollowUpNotes`, `userId`.
        *   Create API endpoints for Communication Logs (CRUD).
    *   **Manual Tests:**
        *   API Test (Create Log): Send POST with valid log data. -> New log created.
        *   API Test (Read Logs for Contact): Send GET with contactId. -> Logs for that contact returned.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Comms): Implement Communication Log model and API endpoints".*

*   **Step 6.2: Communication Log Create/Edit Form**
    *   **Key Tasks:**
        *   Develop UI form for logging/editing communication activities.
        *   Fields for all attributes, including linking to Contact and optionally to Gig.
        *   Fields for follow-up date and notes.
    *   **Manual Tests:**
        *   Log a new communication (e.g., an email summary) linked to a contact. -> Log saved.
        *   Edit an existing log. -> Changes saved.
        *   Set a follow-up date for a log. -> Data saved.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Comms): Implement Communication Log create/edit form".*

*   **Step 6.3: Communication Log List/View (Integrated)**
    *   **Key Tasks:**
        *   Integrate display of communication logs into Contact Detail View and Gig Detail View.
        *   List logs relevant to the current contact/gig, showing key info (Date, Type, Summary).
        *   Allow viewing full details of a log entry.
    *   **Manual Tests:**
        *   Navigate to a Contact's detail page. -> Associated communication logs should be listed.
        *   Navigate to a Gig's detail page. -> Associated communication logs should be listed.
        *   Click a log to view its full details.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Comms): Display communication logs on Contact and Gig detail views".*

*   **Step 6.4: Search/Filter Communication Logs (Basic)**
    *   **Key Tasks:**
        *   Implement basic search/filter functionality for logs, perhaps within the context of a contact or gig view (e.g., filter by type, search summary).
    *   **Manual Tests:**
        *   On a contact's detail page, filter communication logs by 'Email' type. -> Only email logs shown.
        *   Search logs by a keyword in the summary. -> Matching logs shown.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(Comms): Implement basic search/filter for communication logs".*

**Phase 7: General Features & Refinements**

*   **Step 7.1: UI/UX Polish & Navigation**
    *   **Key Tasks:**
        *   Review overall application flow, navigation structure (e.g., main menu, breadcrumbs).
        *   Ensure consistent styling, button placement, and user experience across all modules.
        *   Improve clarity of labels, messages, and instructions.
    *   **Manual Tests:**
        *   Navigate through all parts of the application. -> Flow should be intuitive, no dead ends.
        *   Check for consistent design and layout.
        *   Verify all interactive elements are clear and responsive.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "refactor(UI): General UI/UX polish and navigation improvements".*

*   **Step 7.2: Basic Mobile Responsiveness (Viewing)**
    *   **Key Tasks:**
        *   Ensure all views are readable and key information is accessible on common tablet and mobile screen sizes.
        *   Focus on responsive layouts for viewing data; complex editing forms might be less optimized for small screens in V1.
    *   **Manual Tests:**
        *   Open the application on various screen sizes (using browser dev tools or actual devices).
        *   Check list views, detail views, calendar for readability and basic usability.
        *   Ensure no major layout breaks or horizontal scrolling for primary content.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "feat(UI): Implement basic mobile responsiveness for viewing".*

*   **Step 7.3: Comprehensive End-to-End Testing**
    *   **Key Tasks:**
        *   Perform thorough testing of all features and user flows from start to finish.
        *   Test interactions between modules (e.g., creating a contact, then a gig for that contact, then an invoice for that gig).
        *   Test edge cases and error handling.
        *   Test in modern browsers (e.g., Chrome, Firefox, Safari, Edge).
    *   **Manual Tests:**
        *   Execute a predefined set of end-to-end test scenarios covering all PRD features.
        *   Example Scenario: Register new DJ -> Create a Promoter Contact -> Create a Client Contact -> Log a Gig for the Client, at Promoter's Venue -> Add a Setlist to the Gig -> Create an Invoice for the Gig -> Record a Payment -> Log an Expense for the Gig -> View Financial Report -> View Gig on Calendar -> Log a follow-up call with Client.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "test: Conduct comprehensive end-to-end testing for V1.0".*

*   **Step 7.4: Basic User Documentation**
    *   **Key Tasks:**
        *   Prepare a simple user guide explaining core features and how to use them.
        *   This could be a Markdown file in the repository or a few help pages within the app.
    *   **Manual Tests:**
        *   Review the user guide for clarity, accuracy, and completeness regarding V1.0 features.
        *   Ask a new user (if possible) to try using the app with the guide.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "docs: Create basic user documentation for V1.0".*

*   **Step 7.5: Deployment Preparation & V1.0 Release**
    *   **Key Tasks:**
        *   Choose a hosting environment and prepare deployment scripts/configurations.
        *   Set up production database.
        *   Perform a trial deployment to a staging environment if possible.
        *   Deploy the application to the production environment.
        *   Final smoke testing on the live environment.
    *   **Manual Tests:**
        *   Verify the deployment process runs successfully.
        *   Access the live application URL. -> Application loads and is functional.
        *   Test core functionalities (login, create a contact, view a gig) on the live environment.
    *   **Git Commit Prompt:** *After all tests for this step pass, prompt the development assistant AI to create a Git commit. For example: "chore: Prepare and deploy DJ CRM V1.0 to production".*
