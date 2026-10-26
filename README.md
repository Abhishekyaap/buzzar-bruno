# Buzzar Admin App API - Bruno Collection

Official [Bruno](https://www.usebruno.com/) API collection for **Buzzar API** (`admin-app-api`).

This collection covers all endpoints for both the Admin Dashboard and Creator Mobile App, with automated token extraction, pre-configured sample request payloads, query parameters, and multipart uploads.

---

## 🚀 Getting Started

1. **Install Bruno**: Download and install the latest Bruno client from [usebruno.com](https://www.usebruno.com/).
2. **Open Collection**:
   - In Bruno, click **"Open Collection"**.
   - Browse to this directory (`buzzar-bruno`) and select it.
3. **Select Environment**:
   - In the top-right environment dropdown, choose:
     - **Local**: Points to `http://localhost:3000`
     - **Production**: Points to `https://admin.buzzar.co`

---

## 🔑 Authentication Workflows

This API uses JWT Bearer authentication with two separate roles/tokens:

| Token Variable | Used For | How to Obtain |
|---|---|---|
| `{{adminToken}}` | Dashboard & Admin actions (`AuthGuard('admin-jwt')`) | Run `01-Admin-Auth / Admin Login` |
| `{{userToken}}` | Creator & Mobile App actions (`AuthGuard('jwt')`) | Run `02-User-Auth / Verify OTP` |

### Automated Token Extraction
- **Admin Login**: Automatically saves `data.access_token` into your environment variable `{{adminToken}}`.
- **User Verify OTP**: Automatically saves `data.token` into your environment variable `{{userToken}}`.
- Subsequent authenticated requests automatically inherit and send these tokens.

---

## 📂 Collection Structure

```
buzzar-bruno/
├── bruno.json                      # Bruno collection config
├── environments/
│   ├── Local.bru                   # Local development environment
│   └── Production.bru              # Production environment
├── 00-System/                      # Health check & root endpoints
├── 01-Admin-Auth/                  # Admin auth, user management & RBAC
├── 02-User-Auth/                   # WhatsApp OTP login & user token validation
├── 03-User-Campaigns/              # Campaigns for creators (listing, apply, tasks)
├── 04-Admin-Campaigns/             # Admin campaign creation, review, payouts
├── 05-Brand/                       # Brand discovery endpoints
├── 06-User-Profile/                # User profile steps, address, KYC, bank/UPI
├── 07-Admin-Profile/               # Dashboard analytics, profiles table, KYC approvals
├── 08-Social/                      # Instagram OAuth, stats, audience sync, admin verify
├── 09-External-Influencers/        # External influencer pipeline & public submission
├── 10-Notifications/               # In-app notifications, push broadcast, reminders
├── 11-Device-Tokens/               # Expo push notification tokens
├── 12-Master-Data/                 # Cities, categories, languages, skills
├── 13-Storage-Upload/              # Azure Blob storage image uploads
├── 14-Registration/                # Tournament / user registrations
├── 15-App-Version/                 # Mobile app update enforcement
├── 16-Website/                     # Public website contact forms
└── 17-WhatsApp/                    # Bulk WhatsApp outreach CSV runner
```

---

## 🧪 Running with Bruno CLI

You can execute the entire collection or specific folders via the CLI for CI/CD or automated sanity testing:

```bash
# Install CLI
npm install -g @usebruno/cli

# Run all requests against Local environment
bru run --env Local

# Run specific folder
bru run 00-System --env Local
```

---

## 🛡️ License
Private repository for Buzzar development team.
