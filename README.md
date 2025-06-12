# Admin VPS Automation Portal

This is an internal admin portal built to **automate VPS provisioning and deprovisioning** based on client activity in **Go High Level**. The app integrates with **Sangfor SCP APIs** to create and manage virtual private servers automatically.

---

Note: third party apps such as Go High level are simply used as an example to convey the main idea.

## 🚀 Core Use Cases

### 1. VPS Provisioning
When a user subscribes to a service in **Go High Level**, a webhook is triggered to:
- Parse subscription details
- Map to a pre-defined VPS template
- Call Sangfor APIs to spin up a new VPS instance
- Store VPS metadata in the database for admin visibility

### 2. VPS Deletion
When a user unsubscribes or cancels:
- A webhook is triggered
- The VPS tied to that user is destroyed via the Sangfor API
- Records are updated in the system

### 3. Admin Dashboard
A secure web interface is available to:
- View all active and past VPS instances
- Manually create, reset, or delete VPS
- Monitor activity logs and errors
- Configure VPS templates and settings

---

## 🔄 Workflow

### VPS Provisioning Flow
1. **User Subscribes (Go High Level)**
   - A webhook is triggered to your backend (e.g., `/api/vps/provision`)
2. **Backend Processes the Payload**
   - Subscription details are extracted (user ID, plan, etc.)
3. **Template Match**
   - The plan is mapped to a pre-configured VPS template
4. **Sangfor API Call**
   - VPS is provisioned using the Sangfor SCP API
5. **Database Update**
   - VPS metadata (IP, credentials, ID) is saved
6. **Notification (optional)**
   - Admin is notified via email or UI message

### VPS Deletion Flow
1. **User Cancels Subscription (Go High Level)**
   - Webhook is sent to `/api/vps/deprovision`
2. **Backend Locates VPS Record**
   - Finds associated VPS via user ID or subscription ID
3. **Sangfor API Call**
   - VPS is destroyed via Sangfor SCP
4. **Cleanup**
   - Database entry is marked inactive or deleted

---

## 🛠️ Technologies Used
- **Backend**: Django / FastAPI (TBD)
- **Frontend**: React / Next.js (optional)
- **Asynchronous Tasks**: Celery with Redis
- **Database**: PostgreSQL / MySQL
- **Auth**: Admin-only login (JWT/session)

---

## 🔗 Integrations
- **Go High Level** (Webhooks for user activity)
- **Sangfor SCP API** (for VPS control)
- **Email or Notifications** (optional admin alerts)

---

## 🧪 Development Roadmap
- [ ] Create webhook endpoints for GHL triggers
- [ ] Build Sangfor API abstraction layer
- [ ] Setup admin panel for VPS tracking
- [ ] Add logging, retries, and failure handling
- [ ] Optional: Add metrics dashboard

## Secondary features (brainstorming)
- Stripe payment for immediate hardware upgrades


---

## KPIs and OKRs
https://github.com/andreisovidiu/vmautomation/blob/main/KPIs_OKRs.md


