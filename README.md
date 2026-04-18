# DineHub — Your Culinary Marketplace

A centralized food ordering platform built for the GIKI campus. Students browse menus, place orders, and pay digitally. Vendors manage orders, track sales, and update menus — all in one place.

> Live at [dinehub.giki.edu.pk](http://dinehub.giki.edu.pk) (only in GIKI campus)

---

## What it does

The manual food ordering system at GIKI — phone calls, cash-only payments, missed orders during peak hours — needed replacing. DineHub digitizes the entire flow end-to-end.

**For students:** Browse menus from all campus vendors, place orders, track status in real time, pay through JazzCash / Easypaisa / SadaPay / wallet, and leave reviews.

**For vendors:** Manage incoming orders, update menus and availability, track earnings, view per-item analytics.

**For admins:** Oversee the platform, verify vendor registrations, allocate funds to societies/faculty for events.

---

## Tech stack

| Layer | Technology |
|---|---|
| Frontend | Flutter (PWA + APK) |
| Backend | Node.js + Express.js |
| Database | MongoDB |
| Auth | JWT + bcrypt |
| Deployment | Docker + NGINX on GIKI server |
| AI Chatbot | Meta Llama 3 (via LangChain + Pinecone) |
| Security | SSL / HTTPS |
| Payments | JazzCash, Easypaisa, SadaPay, Cash on Delivery |

---

## Key features

- **Multi-role system** — separate apps for users, vendors, and admins, each with role-specific dashboards
- **AI chatbot** — context-aware assistant that helps users decide what to order and can place orders on their behalf
- **Digital wallet** — supports offline payments when internet connectivity is limited
- **Real-time order tracking** — live status updates with push notifications
- **PWA support** — works on iOS and Android directly from the browser, no app store required
- **Containerized deployment** — NGINX + Node.js + MongoDB each in isolated Docker containers
- **Analytics** — vendors can pull per-item sales data by date range

---

## Architecture

```
Users / Vendors
      │
      ▼ (HTTPS + SSL)
   NGINX (reverse proxy, port 3000)
      │
      ├──▶ Flutter Frontend (static assets)
      │
      └──▶ Node.js Backend (port 3001)
                │
                ├──▶ MongoDB (port 27017)
                ├──▶ Payment APIs (JazzCash, Easypaisa, Stripe)
                └──▶ LangChain + Pinecone (chatbot)
```

All services run as Docker containers defined in `docker-compose.yml` and are hosted on the GIKI university server.

---

## Running locally (please request for access)

```bash
# Clone the repo
git clone https://github.com/moizg7/dinehub.git
cd dinehub

# Start all services
docker-compose up --build
```

The app will be available at `http://localhost:3000`.

> Note: The app is designed for the GIKI campus network. Some features (payments, live chatbot) require valid API keys in your `.env` file.

---

## Contributors

| Name | Role |
|---|---|
| Abdul Moiz Ghumman | Backend, Deployment |
| Muhammad Waiz Hamid | Frontend (User App) |
| Rayyan Hassan | Frontend (Vendor App) |

**Supervisors:** Mr. Muhammad Sajid Ali · Mr. Qasim Riaz  
**Institution:** GIK Institute of Engineering Sciences and Technology, Faculty of Computer Science and Engineering

---

## API docs

All endpoints are documented and tested via Postman.
---

*Final Year Project — BS Computer Engineering, GIKI · 2025*
