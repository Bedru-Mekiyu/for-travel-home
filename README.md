# Dream Nest 🏡

Dream Nest is a full-stack real estate listing and property booking web application built using the MERN stack (MongoDB, Express, React, Node.js). It provides a seamless experience for users to browse property listings, filter by categories or search keywords, view property details, host properties, and manage bookings and trip reservations.

---

## Key Features

- **User Authentication:** Secure user registration, login, and JWT-based session authorization.
- **Property Listings:** Browse available rental properties filtered by property types (e.g., Beachfront, Countryside, Villas, Cabins).
- **Property Search & Filtering:** Search properties by keyword, location, or category.
- **Listing Creation (Hosting):** Registered users can list properties with photo upload capabilities and detailed dynamic amenity selection.
- **Booking Management:** Reserve property stay dates and manage personal booking history ("Trip List") and host reservations ("Reservation List").
- **Favorites & Wishlists:** Add or remove listings to/from user wishlists.
- **Responsive Interface:** Modern frontend built with React, Material-UI (MUI), and SCSS styling.

---

## Tech Stack

### Frontend
- **Framework:** React 18
- **State Management:** Redux Toolkit & Redux Persist
- **Routing:** React Router v6
- **UI Components & Icons:** Material-UI (`@mui/material`), React Icons
- **Styling:** Sass / SCSS, CSS

### Backend
- **Runtime:** Node.js
- **Framework:** Express.js
- **Database:** MongoDB with Mongoose ODM
- **Authentication:** JSON Web Tokens (JWT) & bcryptjs
- **File Uploads:** Multer

---

## Architecture & Project Structure

```
.
├── client/                 # React frontend application
│   ├── public/             # Static public assets
│   └── src/
│       ├── components/     # Reusable UI components (Navbar, Footer, ListingCard, etc.)
│       ├── pages/          # Application views (HomePage, ListingDetails, RegisterPage, etc.)
│       ├── redux/          # Redux Toolkit store and state slices
│       ├── styles/         # SCSS and component styling
│       ├── App.js          # Main app component & routes
│       └── index.js        # Frontend entry point
│
├── server/                 # Express backend application
│   ├── models/             # Mongoose schemas (User, Listing, Booking)
│   ├── routes/             # Express route handlers (auth, user, listing, booking)
│   ├── public/uploads/     # Upload directory for listing photos
│   └── index.js            # Server entry point & DB connection setup
│
└── .github/
    └── workflows/
        └── ci.yml          # GitHub Actions CI workflow
```

---

## Getting Started

### Prerequisites

- **Node.js**: v16+ or v18+ recommended
- **npm**: v8+
- **MongoDB Database**: Local instance or MongoDB Atlas cluster URL

---

### Installation & Local Setup

#### 1. Clone the Repository
```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
```

#### 2. Configure Backend Environment
Navigate to the `server/` directory and set up environment variables:
```bash
cd server
cp .env.example .env
```
Edit `.env` to configure your MongoDB connection URI and JWT Secret key:
```env
MONGO_URL=mongodb+srv://<username>:<password>@cluster.mongodb.net/Dream_Nest?retryWrites=true&w=majority
JWT_SECRET=your_jwt_secret_key
PORT=3001
```

#### 3. Install Dependencies

**Backend:**
```bash
cd server
npm install
```

**Frontend:**
```bash
cd client
npm install
```

---

### Running the Application

1. **Start the Backend Server:**
   ```bash
   cd server
   npm start
   ```
   The backend API runs at `http://localhost:3001`.

2. **Start the Frontend Client:**
   ```bash
   cd client
   npm start
   ```
   The React web app will open at `http://localhost:3000`.

---

## API Routes Overview

| Endpoint | Method | Description | Auth Required |
| --- | --- | --- | --- |
| `/auth/register` | `POST` | Register a new user with profile picture | No |
| `/auth/login` | `POST` | Authenticate user and issue JWT | No |
| `/properties/create` | `POST` | Create a new property listing with images | Yes |
| `/properties` | `GET` | Fetch property listings (filterable by category) | No |
| `/properties/search/:search` | `GET` | Search listings by title or category | No |
| `/properties/:listingId` | `GET` | Retrieve detailed listing information | No |
| `/bookings/create` | `POST` | Book stay dates for a property listing | Yes |
| `/users/:userId/trips` | `GET` | Retrieve booked trips for user | Yes |
| `/users/:userId/wishList` | `PATCH` | Add/remove listing from user wishlist | Yes |
| `/users/:userId/properties` | `GET` | Retrieve properties hosted by user | Yes |
| `/users/:userId/reservations` | `GET` | Retrieve incoming reservations for host | Yes |

---

## CI/CD Workflow

Continuous Integration is configured via **GitHub Actions** (`.github/workflows/ci.yml`).

Every push or pull request runs automated checks:
- **Client Build:** Verifies React app compilation (`npm run build`).
- **Server Verification:** Runs syntax validation across backend route and model files (`node -c`).

---

## License

This project is open source and available under the [ISC License](server/package.json).
