# MediBio - Medical Bio Web App

**Nền tảng lưu trữ và chia sẻ hồ sơ y tế cá nhân an toàn**, dành cho cấp cứu, bác sĩ, và tra cứu nhanh thông tin y tế.

## ✨ Tính Năng Chính

- 🔐 **Bảo mật cao** - Mã hóa AES-256-GCM cho dữ liệu y tế
- ⚡ **Truy cập nhanh** - QR code và link bio cá nhân
- 🏥 **Thông tin y tế** - Nhóm máu, dị ứng, thuốc, bệnh lý nền
- 🚑 **Cấp cứu** - Thông tin liên hệ khẩn cấp
- 🔒 **Quyền riêng tư** - 3 cấp độ: Công khai, Link only, PIN protection
- 🌙 **Dark Mode** - Giao diện đẹp, responsive mobile-first

## 🏗️ Tech Stack

### Frontend
- **Next.js 14** (App Router, TypeScript)
- **Tailwind CSS** - Styling
- **React Query** - Data fetching & caching
- **Framer Motion** - Animations
- **QRCode.react** - QR code generation

### Backend
- **Node.js + Express** - REST API
- **PostgreSQL** - Database
- **JWT** - Authentication
- **AES-256-GCM** - Data encryption
- **Cloudinary** - Image storage
- **Bcrypt** - Password hashing

## 🚀 Quick Start

### Prerequisites
- Node.js 18+
- PostgreSQL 14+
- Cloudinary account (free tier)

### 1. Clone & Install

```bash
# Clone repository
git clone <your-repo-url>
cd medibio

# Install backend dependencies
cd server
npm install

# Install frontend dependencies
cd ../client
npm install
```

### 2. Setup Database

```bash
# Create PostgreSQL database
createdb medibio

# Run schema
cd server
psql -d medibio -f schema.sql
```

### 3. Configure Environment Variables

**Backend** (`server/.env`):
```env
DATABASE_URL=postgresql://user:password@localhost:5432/medibio
JWT_SECRET=your-super-secret-jwt-key-change-this
ENCRYPTION_SECRET=your-32-character-encryption-key-here
CLOUDINARY_CLOUD_NAME=your-cloud-name
CLOUDINARY_API_KEY=your-api-key
CLOUDINARY_API_SECRET=your-api-secret
PORT=5000
FRONTEND_URL=http://localhost:3000
```

**Frontend** (`client/.env.local`):
```env
NEXT_PUBLIC_API_URL=http://localhost:5000
```

### 4. Run Development Servers

**Terminal 1 - Backend:**
```bash
cd server
npm run dev
```

**Terminal 2 - Frontend:**
```bash
cd client
npm run dev
```

- Frontend: http://localhost:3000
- Backend API: http://localhost:5000

## 📁 Project Structure

```
medibio/
├── server/                 # Backend API
│   ├── src/
│   │   ├── config/        # Database, Cloudinary config
│   │   ├── controllers/   # Route handlers
│   │   ├── middleware/    # Auth, rate limiting, errors
│   │   ├── models/        # Database queries
│   │   ├── routes/        # API routes
│   │   ├── utils/         # Encryption, JWT, validation
│   │   └── index.ts       # Express server
│   ├── schema.sql         # Database schema
│   └── package.json
│
├── client/                # Frontend Next.js app
│   ├── app/
│   │   ├── auth/         # Login, Register pages
│   │   ├── dashboard/    # User dashboard
│   │   ├── bio/          # Public bio pages
│   │   ├── layout.tsx    # Root layout
│   │   ├── page.tsx      # Homepage
│   │   └── globals.css   # Styles
│   ├── lib/
│   │   ├── api.ts        # API client
│   │   └── hooks.ts      # React Query hooks
│   └── package.json
│
└── README.md
```

## 🔐 Security Features

1. **Data Encryption**: Medical data encrypted with AES-256-GCM before storage
2. **JWT Authentication**: Secure token-based auth with 7-day expiration
3. **Password Hashing**: Bcrypt with salt rounds
4. **Rate Limiting**: Prevent brute force attacks
5. **PIN Protection**: Optional 4-digit PIN for bio pages
6. **Access Logging**: Track who accessed medical profiles
7. **Helmet.js**: Security headers
8. **No Index**: Bio pages not indexed by search engines

## 📱 Usage Flow

1. **Register** → Create account with email/username
2. **Create Profile** → Add medical info (encrypted)
3. **Set Privacy** → Choose: Public, Link only, or PIN protected
4. **Get Bio URL** → Share link or QR code
5. **Access Anytime** → View bio from any device

## 🎨 Features In Detail

### Medical Profile includes:
- ✅ Avatar photo
- ✅ Full name & DOB
- ✅ Blood type
- ✅ Medical conditions
- ✅ Drug/food allergies
- ✅ Current medications
- ✅ Medical history
- ✅ Doctor notes
- ✅ Emergency contacts

### Privacy Levels:
1. **Public** - Anyone can view
2. **Link Only** - Only with direct link (not searchable)
3. **PIN Protected** - Requires 4-digit PIN

## 🚀 Deployment

### Backend (Railway/Render)
1. Create PostgreSQL database
2. Set environment variables
3. Deploy from GitHub
4. Run `schema.sql` on production DB

### Frontend (Vercel)
1. Connect GitHub repository
2. Set `NEXT_PUBLIC_API_URL`
3. Deploy automatically

## 📝 API Endpoints

### Authentication
- `POST /api/auth/register` - Register
- `POST /api/auth/login` - Login
- `GET /api/auth/me` - Current user
- `POST /api/auth/logout` - Logout

### Profile
- `POST /api/profile` - Create profile
- `GET /api/profile` - Get own profile
- `PUT /api/profile` - Update profile
- `POST /api/profile/avatar` - Upload avatar

### Public Bio
- `GET /api/bio/:username` - View bio
- `POST /api/bio/:username/verify-pin` - Verify PIN

### Contacts
- `GET /api/contacts` - List contacts
- `POST /api/contacts` - Add contact
- `PUT /api/contacts/:id` - Update
- `DELETE /api/contacts/:id` - Delete

## 🔮 Future Enhancements

- [ ] PDF export
- [ ] Emergency view mode
- [ ] Multi-language (EN/VI)
- [ ] Medical timeline
- [ ] Email notifications
- [ ] Mobile app (React Native)
- [ ] Hospital integration (HL7/FHIR)

## 📄 License

MIT

## 🤝 Contributing

Contributions welcome! Please open an issue or PR.

---

**Made with ❤️ for healthcare**
