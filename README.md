# EEFCI School Managament System

![Project Banner] (images/school-logo.png)

This document details the development of a School Management System (SMS) designed to simplify student registration and deliver an intuitive web interface using React and SQL. The system enhances operational efficiency, improves user experience, and supports the administrative functions of educational institutions.

## Current System

- Excel files for data organization.
- Facebook for communication and school information.
- Google Forms for student registration

## Proposed System

- **Online Registration Form:** An easy-to-fill, online registration form for new students.
- **Document Upload:** Secure upload feature for necessary documents (e.g., birth certificate, previous school records).
- **Automated Verification:** Automated system for verifying submitted documents and data.
- **Status Tracking:** Real-time status updates on registration progress.
- **Notifications:** Automated email/SMS notifications to inform students and parents of registration status and required actions.
- **User Accounts:** Secure login for students, parents, and administrators.
- **Dashboard:** Personalized dashboards displaying relevant information (e.g., registration status, upcoming deadlines).
- **Information Portal:** Access to school policies, academic calendars, and contact information.
- **Interactive Forms:** Forms for additional requests, feedback, and communication with the school.
- **Event Calendar:** Display upcoming events, deadlines, and school activities.
- **Responsive Design:** Mobile-friendly design to ensure accessibility on various devices.
- **Data Management:** Tools for administrators to view, edit, and manage student records.
- **Reporting:** Generate reports on registration statistics, student demographics, and other key metrics.
- **User Management:** Control access levels and permissions for different user roles (e.g., administrators, teachers)

## Advantages of Proposed System

The proposed School Management System (SMS) revolutionizes student registration and elevates the user experience through a modern, web-based platform. By implementing this system, institutions will benefit from:

- Streamlined operations (reduced manual workload)
- Enhanced data management (secure, centralized, and scalable)
- Improved communication (real-time updates for staff, students, and parents)

## Code Snipets

**PRISMA SQL**

```sql
model User {
  id           Int         @id @default(autoincrement())
  username     String      @unique
  email        String      @unique
  password     String
  role         String      @default("student") // 'student', 'admin', or 'instructor'
  createdAt    DateTime    @default(now())

  student     Student?    @relation("UserToStudent")

  // Notifications
  notifications Notification[]
}
```

**JavaScript**

```javascript
const AdminPage = () => {
  return (
    <div className="p-4 flex gap-4 flex-col md:flex-row">
      {/* LEFT */}
      <div className="w-full lg:w-2/3 flex flex-col gap-8">
        {/* USER CARDS */}
        <div className="flex gap-4 justify-between flex-wrap">
          <UserCardStudent />
          <UserCardInstructor />
          <UserCardEmployee />
        </div>
        {/* MIDDLE CHARTS */}
        <div className="flex gap-4 flex-col lg:flex-row">
          {/* COUNT CHART */}
          <div className="w-full lg:w-1/3 h-[450px]">
            <CountChart />
          </div>
          {/* ATTENDANCE CHART */}
          <div className="w-full lg:w-2/3 h-[450px]">
            <Announcements />
          </div>
        </div>
      </div>
      {/* RIGHT */}
      <div className="w-full lg:w-1/3 flex flex-col gap-8">
        <EventCalendar />
        <Notification />
      </div>
    </div>
  );
};
```

## Documentation

Full documentation available at:  
[📂 Software Analysis and Design Project Documentation](/docs/SAD_Documentation.pdf)
