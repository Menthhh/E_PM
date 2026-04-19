# E_PM — Electronic Preventive Maintenance Checklist System

A web-based Preventive Maintenance (PM) checklist management platform built with **Next.js 14**, **MongoDB**, and a role-based workflow engine. It digitizes the full lifecycle of preventive maintenance work orders — from template creation through activation, execution, approval, and reporting.

---

## Features

- **Dashboard** — Real-time summary of active checklists, cards, and job statuses
- **Template Management** — Create and manage reusable job templates and job item templates
- **Checklist Management** — Activate, plan, renew, and remove checklists with recurrence support
- **Approval Workflow** — Serial/parallel approver chains with email notifications to checkers
- **Job Calendar** — Monthly/weekly calendar view of scheduled maintenance jobs per workgroup
- **Preventive Checklist Execution** — Field checkers fill in results, attach photos via webcam
- **Report** — Bar-chart summaries of checklist completion data
- **Role-Based Access Control** — Granular permissions per role (Owner, Approver, Checker, Admin, Super Admin, etc.)
- **User & Workgroup Management** — Manage accounts, workgroups, departments, and line names
- **Machine & Location Registry** — Track equipment and test locations
- **Email Notifications** — Nodemailer integration for approval and assignment alerts
- **MQTT Integration** — Real-time event publishing
- **Elasticsearch Integration** — Push job execution data for analytics

---

## Tech Stack

| Layer | Technology |
|---|---|
| Framework | Next.js 14 (App Router) |
| Database | MongoDB + Mongoose |
| Styling | Tailwind CSS, Chakra UI, MUI, Bootstrap 5 |
| Charts | Chart.js + react-chartjs-2 |
| Calendar | react-big-calendar + SyncFusion Scheduler |
| Auth | JWT (jose / jsonwebtoken) |
| Forms | react-hook-form, react-select |
| Email | Nodemailer |
| Messaging | MQTT |
| Search | Elasticsearch |
| API Docs | Swagger (next-swagger-doc + swagger-ui-react) |
| Animations | Framer Motion |

---

## System Roles

| Role | Capabilities |
|---|---|
| **Super Admin** | Full system access, manage all accounts, define roles |
| **Admin** | CRUD templates, manage users and workgroups |
| **Owner / Master Plan** | Activate templates into jobs, plan recurrence |
| **Approver** | Approve or reject submitted checklists |
| **Checker** | Execute and fill in checklist job items |
| **User** | Log in, view assigned jobs |

> See the use case diagram in [`diagrams/E_PM.drawio.png`](diagrams/E_PM.drawio.png) for a full overview of role interactions.

---

## Project Structure

```
src/
├── app/
│   ├── api/              # REST API routes (Next.js route handlers)
│   │   ├── job/
│   │   ├── job-template/
│   │   ├── job-item-template/
│   │   ├── user/
│   │   ├── approval/
│   │   ├── machine/
│   │   ├── location/
│   │   ├── workgroup/
│   │   ├── role/
│   │   ├── elasticsearch/
│   │   └── ...
│   └── pages/            # UI pages
│       ├── dashboard/
│       ├── job-manage/
│       ├── job-template/
│       ├── job-item-template/
│       ├── job-approve/
│       ├── job-calendar/
│       ├── job-review/
│       ├── activate-remove-job/
│       ├── report/
│       ├── admin/
│       ├── SA/            # Super Admin
│       └── ...
├── components/           # Shared UI components
└── lib/
    ├── hooks/            # Custom React data-fetching hooks
    ├── models/           # Mongoose schemas
    ├── context/
    └── utils/
```

---

## Getting Started

### Prerequisites

- Node.js 18+
- MongoDB instance (local or Atlas)
- (Optional) MQTT broker, Elasticsearch node

### Installation

```bash
git clone <repo-url>
cd E_PM
npm install
# or
pnpm install
```

### Environment Variables

Create a `.env.local` file in the project root:

```env
MONGODB_URI=mongodb://localhost:27017/e_pm
JWT_SECRET=your_jwt_secret

# Nodemailer
MAIL_HOST=smtp.example.com
MAIL_PORT=587
MAIL_USER=your@email.com
MAIL_PASS=yourpassword

# Optional
MQTT_BROKER_URL=mqtt://localhost:1883
ELASTICSEARCH_URL=http://localhost:9200
```

### Run Development Server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### Build for Production

```bash
npm run build
npm start
```

---

## API Documentation

Swagger UI is available at:

```
http://localhost:3000/doc
```

---

## License

Private — all rights reserved.
