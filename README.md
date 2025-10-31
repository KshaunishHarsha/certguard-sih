# CertGuard: AI-Powered Secure Certificate Issuance & Verification Platform

CertGuard is a comprehensive, enterprise-grade platform designed to definitively combat academic and professional certificate fraud. It modernizes and secures the entire lifecycle of a credential—from issuance to verification—by integrating multiple layers of cutting-edge security technology, including AI, cryptographic hashing, and immutable blockchain principles.

## ✨ Key Features

### 🔐 Secure & Intelligent Issuance Workflow

- **Role-Based Access**: Secure portals for Institutions, Verifiers, and Administrators with distinct permissions.
- **Digitize Legacy Documents**: Use AI-powered OCR (via Google's Gemini) to scan physical certificates, automatically extract details, and pre-fill the digital issuance form.
- **Issue New Secure Certificates**: Create new, digitally native certificates with robust, multi-layered security applied instantly.

### 🛡️ Multi-Layered Security Protocol

- **PKI-based Hashing**: Core certificate data is signed with a SHA-256 hash, creating a unique, tamper-proof digital fingerprint.
- **Immutable Hash Chain**: Inspired by blockchain, certificate hashes are linked in a chronological chain in Firestore. Any attempt to alter a past record breaks the chain, making tampering immediately evident.
- **Dual Embedded Signatures**: The unique cryptographic signature is embedded in two redundant ways:
  1. A secure, scannable **QR code** on the face of the document.
  2. An **invisible digital watermark** (using steganography) hidden within the document file's pixels.

### 🔍 Real-Time, Multi-Factor Verification

- **Flexible Verification Methods**: Verifiers can either scan a QR code with their device's camera or upload a digital file (PDF, PNG, JPG).
- **Comprehensive Validation Check**: The system performs a multi-factor check in seconds:
  - Validates signatures from both the QR code and the invisible watermark.
  - Compares both signatures against the authoritative hash in the central Firestore registry.
  - Verifies the integrity of the entire hash chain to detect systemic tampering.
  - Cross-references the institution against pre-approved lists and a real-time admin-managed blacklist.

## 🚀 Technology Stack

- **Framework**: [Next.js](https://nextjs.org/) (App Router)
- **Language**: [TypeScript](https://www.typescriptlang.org/)
- **Styling**: [Tailwind CSS](https://tailwindcss.com/)
- **UI Components**: [ShadCN/UI](https://ui.shadcn.com/)
- **Database / Backend**: [Firebase](https://firebase.google.com/) (Firestore for the immutable registry)
- **Generative AI**: [Genkit](https://firebase.google.com/docs/genkit) (Google's GenAI toolkit)
- **AI Models**: [Google Gemini](https://deepmind.google/technologies/gemini/) for multimodal OCR and data extraction.

## 🏁 Getting Started

### Prerequisites

- Node.js (v18 or later)
- npm or yarn
- A Firebase project with Firestore enabled.

### Setup

1. **Clone the repository:**

   ```bash
   git clone https://github.com/your-username/certguard.git
   cd certguard
   ```

2. **Install dependencies:**

   ```bash
   npm install
   ```

3. **Configure Firebase:**

   - Create a file `src/lib/firebase-config.ts`.
   - Add your Firebase project configuration to this file. It should look like this:

     ```typescript
     // src/lib/firebase-config.ts
     import { initializeApp, getApps, getApp } from "firebase/app";
     import { getFirestore } from "firebase/firestore";

     const firebaseConfig = {
       apiKey: "YOUR_API_KEY",
       authDomain: "YOUR_AUTH_DOMAIN",
       projectId: "YOUR_PROJECT_ID",
       storageBucket: "YOUR_STORAGE_BUCKET",
       messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
       appId: "YOUR_APP_ID",
     };

     const app = getApps().length ? getApp() : initializeApp(firebaseConfig);
     const db = getFirestore(app);

     export { app, db };
     ```

4. **Configure Environment Variables:**

   - Create a `.env.local` file in the root of your project.
   - If you are using Google AI Studio for Genkit, add your API key:
     ```
     GEMINI_API_KEY=YOUR_GOOGLE_AI_STUDIO_API_KEY
     ```

5. **Run the development server:**
   ```bash
   npm run dev
   ```
   Open [http://localhost:9002](http://localhost:9002) to view the application.

### Demo User Credentials

You can use the following credentials to log in and test the different roles:

- **Role:** `Admin`
  - **Email:** `admin@certguard.com`
  - **Password:** `password123`
- **Role:** `Institution`
  - **Email:** `mit@edu`
  - **Password:** `password123`
- **Role:** `Verifier`
  - **Email:** `verifier@google.com`
  - **Password:** `password123`

---

This project showcases a powerful, real-world application of modern web technologies, AI, and cryptographic principles to solve a significant problem.
