# 🛍️ Wishlistz Backend  
A modular, scalable backend for the Wishlistz Shopping Assistant Chatbot.  
Built with **Node.js**, **Express**, and **MongoDB (Mongoose)**.  

The system powers intelligent shopping assistance including:
- Personalized recommendations  
- Trip/Gift/Theme planning  
- Chat-based interaction  
- Navigation inside app  
- Wishlist & user activity tracking  

---

## 🚀 Features

### 🔹 Chat System  
- Understands user messages using custom NLU  
- Supports shopping queries (trending, search, category-based)  
- Handles planners (Trip, Gift, Theme)  
- Navigation queries (e.g., "Where is men's section?")  

### 🔹 Planner Engine  
- **Trip Planner** – suggests checklist + missing items  
- **Gift Planner** – suggests gifts by age, relation, budget  
- **Theme Planner** – outfits, decoration, color theme suggestions  

### 🔹 Recommendation Engine  
- Personalized recommendations  
- Trending product suggestions  
- Gap-based recommendations (based on user history & wishlist)  

### 🔹 User & Product Management  
- Auth (JWT)  
- Wishlist  
- UserActivity logs  
- Product catalog  

### 🔹 MongoDB + Mongoose  
Clean schemas for all business entities.

---

## 🏗️ System Architecture

Frontend (HTML, CSS, JS)
↓ API Requests (REST)
Node.js + Express Backend
↓
Routes → Controllers → Services → Models
↓
MongoDB Atlas (wishlistz_chatbot)

yaml
Copy code

---

## 📁 Project Structure

wishlistz-backend/
│
├── src/
│ ├── app.js
│ ├── server.js
│ │
│ ├── config/
│ │ ├── env.js
│ │ └── db.js
│ │
│ ├── routes/
│ │ ├── auth.routes.js
│ │ ├── user.routes.js
│ │ ├── product.routes.js
│ │ ├── chat.routes.js
│ │ ├── planner.routes.js
│ │ └── navigate.routes.js
│ │
│ ├── controllers/
│ │ ├── auth.controller.js
│ │ ├── user.controller.js
│ │ ├── product.controller.js
│ │ ├── chat.controller.js
│ │ ├── planner.controller.js
│ │ └── navigate.controller.js
│ │
│ ├── services/
│ │ ├── auth.service.js
│ │ ├── user.service.js
│ │ ├── product.service.js
│ │ │
│ │ ├── chat/
│ │ │ ├── chatOrchestrator.service.js
│ │ │ ├── nlu.service.js
│ │ │ └── contextManager.service.js
│ │ │
│ │ ├── planner/
│ │ │ ├── tripPlanner.service.js
│ │ │ ├── giftPlanner.service.js
│ │ │ └── themePlanner.service.js
│ │ │
│ │ ├── recommender/
│ │ │ ├── personalizedRecommender.service.js
│ │ │ ├── trendingRecommender.service.js
│ │ │ └── gapRecommender.service.js
│ │ │
│ │ └── navigation/
│ │ └── navigation.service.js
│ │
│ ├── models/
│ │ ├── User.js
│ │ ├── Product.js
│ │ ├── UserActivity.js
│ │ ├── Wishlist.js
│ │ ├── ChatSession.js
│ │ ├── Message.js
│ │ ├── PlannerSession.js
│ │ ├── NavigationMap.js
│ │ └── RecommendationLog.js
│ │
│ ├── middlewares/
│ │ ├── auth.middleware.js
│ │ └── errorHandler.js
│ │
│ └── utils/
│ ├── logger.js
│ └── response.js
│
├── package.json
└── .env

yaml
Copy code

---

## 🛠️ Tech Stack

- **Node.js + Express** – Backend framework  
- **MongoDB Atlas** – Cloud database  
- **Mongoose** – Schema modeling  
- **JWT Authentication**  
- **Custom NLU Engine**  
- **Modular Service Architecture**  

---

## ⚙️ Setup Instructions

### 1️⃣ Clone the Repository
```sh
git clone https://github.com/yourusername/wishlistz-backend.git
cd wishlistz-backend
2️⃣ Install Dependencies
sh
Copy code
npm install
3️⃣ Create .env File
env
Copy code
PORT=5000
MONGO_URI=your_mongodb_uri_here
JWT_SECRET=your_secret_key
4️⃣ Start the Server
sh
Copy code
npm run dev
The server will run at:

arduino
Copy code
http://localhost:5000
🧪 Testing with Postman
You can test all APIs without frontend:

POST /api/auth/register

POST /api/auth/login

POST /api/chat/message

GET /api/products

GET /api/navigation/<section>

🤖 Chat Workflow Example
User:
perl
Copy code
Suggest gifts for my sister under 1000
Backend:
NLU detects intent = Gift Planner

Extracts relation = sister, budget = 1000

Searches products

Returns curated list