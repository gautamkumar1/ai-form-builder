# AI Form Builder 🚀

[![Next.js](https://img.shields.io/badge/Next.js-14.2.3-black.svg)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-18.3.1-blue.svg)](https://reactjs.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind%20CSS-3.4.1-38B2AC.svg)](https://tailwindcss.com/)
[![Clerk](https://img.shields.io/badge/Clerk-5.0.12-purple.svg)](https://clerk.dev/)
[![Drizzle ORM](https://img.shields.io/badge/Drizzle%20ORM-0.30.10-green.svg)](https://orm.drizzle.team/)

An intelligent form builder that uses AI to generate dynamic forms based on natural language descriptions. Create, customize, and share forms in seconds with advanced styling options and real-time analytics.

## ✨ Features

### 🤖 AI-Powered Form Generation
- Generate forms instantly using natural language descriptions
- Powered by Google Gemini AI for intelligent field creation
- Supports various field types: text, select, radio, checkbox, and more

### 🎨 Advanced Customization
- **30+ Pre-built Themes**: From aqua to sunset, choose from a wide variety of color schemes
- **Gradient Backgrounds**: 11 beautiful gradient options including sunrise, ocean, forest, and neon
- **Style Options**: Default, retro, and bordered styling with custom shadows and borders
- **Real-time Preview**: See changes instantly as you customize

### 🔐 Authentication & Security
- Seamless authentication with Clerk
- Optional social authentication before form submission
- Protected routes and user session management
- Secure user data handling

### 📊 Form Management
- Personal dashboard with form overview
- Form limit management (3 forms for free users)
- Edit forms after creation
- Delete and manage existing forms
- Real-time form statistics

### 🌐 Form Sharing & Responses
- Public form URLs for easy sharing
- Anonymous response collection
- Response analytics and data export
- Form embedding capabilities

### 📱 Responsive Design
- Mobile-first approach with Tailwind CSS
- Cross-platform compatibility
- Modern UI with shadcn/ui components
- DaisyUI integration for enhanced styling

## 🛠️ Tech Stack

### Frontend
- **Framework**: Next.js 14 with App Router
- **Language**: JavaScript (JSX)
- **Styling**: Tailwind CSS + DaisyUI
- **UI Components**: Radix UI + shadcn/ui
- **Icons**: Lucide React
- **Notifications**: Sonner

### Backend & Database
- **Database**: PostgreSQL (Neon)
- **ORM**: Drizzle ORM
- **Authentication**: Clerk
- **AI Integration**: Google Gemini AI

### Additional Libraries
- **Date Handling**: Moment.js
- **File Operations**: File-saver, XLSX
- **Sharing**: React Web Share
- **Form Handling**: Custom React hooks

## 🚀 Getting Started

### Prerequisites
- Node.js 18+ 
- npm or yarn
- PostgreSQL database (Neon recommended)
- Google Gemini API key
- Clerk account for authentication

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd ai-form-builder
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment Setup**
   Create a `.env.local` file in the root directory:
   ```env
   # Clerk Authentication
   NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
   CLERK_SECRET_KEY=your_clerk_secret_key

   # Google Gemini AI
   NEXT_PUBLIC_GEMINI_API_KEY=your_gemini_api_key

   # Database
   DATABASE_URL=your_postgresql_connection_string
   ```

4. **Database Setup**
   ```bash
   npm run db:push
   ```

5. **Run the development server**
   ```bash
   npm run dev
   ```

6. **Open your browser**
   Navigate to `http://localhost:3000`

## 📁 Project Structure

```
ai-form-builder/
├── app/                          # Next.js App Router
│   ├── (auth)/                   # Authentication routes
│   │   ├── sign-in/             # Sign-in page
│   │   └── sign-up/             # Sign-up page
│   ├── _components/             # Shared components
│   │   ├── Header.jsx           # Navigation header
│   │   └── Hero.jsx             # Landing page hero
│   ├── _data/                   # Static data files
│   │   ├── GradientBg.jsx       # Background gradients
│   │   ├── PricingPlan.jsx      # Pricing tiers
│   │   ├── Style.jsx            # Form styles
│   │   └── Themes.jsx           # Color themes
│   ├── aiform/                  # Public form display
│   │   └── [formid]/            # Dynamic form pages
│   ├── dashboard/               # User dashboard
│   │   ├── _components/         # Dashboard components
│   │   ├── responses/           # Response analytics
│   │   └── upgrade/             # Upgrade page
│   ├── edit-form/               # Form editor
│   │   ├── _components/         # Editor components
│   │   └── [formId]/            # Dynamic editor
│   └── globals.css              # Global styles
├── components/                  # Reusable UI components
│   └── ui/                      # shadcn/ui components
├── configs/                     # Configuration files
│   ├── AiModal.js              # AI integration
│   ├── index.js                # Database connection
│   └── schema.js               # Database schema
├── lib/                        # Utility functions
└── public/                     # Static assets
```

## 🎯 Core Features Deep Dive

### AI Form Generation
The AI form builder uses Google Gemini to convert natural language descriptions into structured JSON forms:

```javascript
const PROMPT = ",On Basis of description create JSON form with formTitle, formHeading along with fieldName, FieldTitle,FieldType, Placeholder, label , required fields, and checkbox and select field type options will be in array only and in JSON format"
```

### Database Schema
Two main tables power the application:

**JsonForms Table:**
- `id`: Primary key
- `jsonform`: Stores the AI-generated form structure
- `theme`: Selected color theme
- `background`: Chosen gradient background
- `style`: Applied styling options
- `createdBy`: User email
- `createdAt`: Creation timestamp
- `enabledSignIn`: Authentication requirement flag

**UserResponses Table:**
- `id`: Primary key
- `jsonResponse`: User form submissions
- `createdBy`: Respondent identifier
- `createdAt`: Submission timestamp
- `formRef`: Foreign key to JsonForms

### Customization System
The app offers three layers of customization:

1. **Themes**: 30+ predefined color schemes using DaisyUI
2. **Backgrounds**: Linear gradients for visual appeal
3. **Styles**: CSS modifications (shadows, borders, etc.)

## 🔧 Available Scripts

```bash
# Development
npm run dev          # Start development server
npm run build        # Build for production
npm run start        # Start production server
npm run lint         # Run ESLint

# Database
npm run db:push      # Push schema changes
npm run db:studio    # Open Drizzle Studio
```

## 🌟 Key Components

### CreateForm Component
- AI integration for form generation
- Form limit enforcement
- User input validation
- Loading states and error handling

### FormUi Component
- Dynamic form rendering
- Multiple field type support
- Real-time data collection
- Conditional authentication

### Controller Component
- Theme selection interface
- Background customization
- Style options management
- Real-time preview updates

## 📊 Usage Analytics

The application tracks:
- Form creation statistics
- Response collection metrics
- User engagement data
- Popular themes and styles

## 🔒 Security Features

- **Authentication**: Clerk-based user management
- **Route Protection**: Middleware-based access control
- **Data Validation**: Server-side form validation
- **SQL Injection Prevention**: Drizzle ORM parameterized queries

## 🚀 Deployment

### Vercel (Recommended)
1. Connect your GitHub repository to Vercel
2. Configure environment variables
3. Deploy automatically on push

### Manual Deployment
```bash
npm run build
npm run start
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Commit changes: `git commit -am 'Add feature'`
4. Push to branch: `git push origin feature-name`
5. Submit a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

For support, email [your-email] or create an issue in the GitHub repository.

## 🔮 Future Enhancements

- [ ] Advanced analytics dashboard
- [ ] Form templates library
- [ ] Multi-language support
- [ ] API integrations
- [ ] Advanced field types
- [ ] Team collaboration features
- [ ] Form versioning
- [ ] Custom CSS injection

## 🙏 Acknowledgments

- [Next.js](https://nextjs.org/) for the amazing React framework
- [Clerk](https://clerk.dev/) for seamless authentication
- [Google Gemini](https://ai.google.dev/) for AI capabilities
- [Tailwind CSS](https://tailwindcss.com/) for utility-first styling
- [DaisyUI](https://daisyui.com/) for beautiful components
- [Drizzle ORM](https://orm.drizzle.team/) for type-safe database operations

---

Built with ❤️ using AI and modern web technologies.
