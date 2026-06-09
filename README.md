# Face Detection Full Stack App

A full-stack web application that detects human faces in uploaded images using the **Face++ API**, built with **Next.js**, **Prisma**, and **PostgreSQL**.

---

## Features

- Upload any image and detect human faces instantly
- Visual bounding boxes drawn over detected faces
- Displays face count and coordinate details per face
- Stores every scan result in a PostgreSQL database
- Detection history log shown in a table on the homepage

---

## Tech Stack

| Layer      | Technology              |
|------------|-------------------------|
| Frontend   | Next.js 16, React 19, TypeScript |
| Backend    | Next.js API Routes      |
| Database   | PostgreSQL + Prisma ORM |
| Face AI    | Face++ Detect API       |

---

## Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/SECE-24-28/face-detection-full-stack-app-Neemasree.git
cd face-detection-full-stack-app-Neemasree
```

### 2. Install dependencies

```bash
npm install
```

### 3. Set up environment variables

Create a `.env` file in the root:

```env
DATABASE_URL=postgresql://<user>:<password>@<host>:<port>/<dbname>
FACEPP_API_KEY=your_facepp_api_key
FACEPP_API_SECRET=your_facepp_api_secret
```

> Get your Face++ API credentials at [https://www.faceplusplus.com](https://www.faceplusplus.com)

### 4. Set up the database

```bash
npx prisma migrate dev --name init
```

### 5. Run the development server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## API Endpoints

| Method | Endpoint          | Description                        |
|--------|-------------------|------------------------------------|
| POST   | `/api/detect`     | Upload image and detect faces      |
| GET    | `/api/detections` | Fetch all past detection records   |

---

## Database Schema

```prisma
model Detection {
  id        Int      @id @default(autoincrement())
  imageName String
  isHuman   Boolean
  createdAt DateTime @default(now())
}
```

---

## Project Structure

```
├── app/
│   ├── api/
│   │   ├── detect/route.ts       # Face++ detection API handler
│   │   └── detections/route.ts   # Fetch history from DB
│   ├── page.tsx                  # Main UI
│   └── globals.css
├── lib/
│   └── db.ts                     # Prisma client instance
├── prisma/
│   └── schema.prisma             # Database schema
├── .env                          # Environment variables (not committed)
└── package.json
```

---

## Scripts

```bash
npm run dev      # Start development server
npm run build    # Build for production
npm run start    # Start production server
npm run lint     # Run ESLint
```
