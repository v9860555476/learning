---
title: 'Ekaxa Master Prompt Document'
---

# **Ekaxa Master Prompt Document**

**Version:** 2.0  
**Date:** November 15, 2025  
**Purpose:** Complete instruction set for generating individual web page development prompts, database creation prompts, and integration instructions for Ekaxa (Numerology and Rudraksha Consulting Services)

## 📋 **TABLE OF CONTENTS**

1. [Project Overview](#1-project-overview)
2. [Design System](#2-design-system)
3. [Domain Models & Database Schema](#3-domain-models--database-schema)
4. [User Roles & Permissions](#4-user-roles--permissions)
5. [Page Specifications](#5-page-specifications)
6. [Development Platform Guidelines](#6-development-platform-guidelines)
7. [Instructions for LLM: Generate Page Development Prompts](#7-instructions-for-llm-generate-page-development-prompts)
8. [Instructions for LLM: Generate Database Creation Prompts](#8-instructions-for-llm-generate-database-creation-prompts)
9. [Instructions for LLM: Generate Integration Prompts](#9-instructions-for-llm-generate-integration-prompts)
10. [Instructions for LLM: Generate Implementation Checklist](#10-instructions-for-llm-generate-implementation-checklist)

---

## 1. PROJECT OVERVIEW

### 1.1 What is Ekaxa?

**Ekaxa** is a comprehensive digital platform specializing in Numerology, Rudraksha, and Vastu consultation services. The platform blends ancient spiritual wisdom with contemporary design, providing visitors with educational content, interactive tools, and easy access to professional consultation services.

**Brand Name:** Ekaxa  
**Tagline:** "Embrace Grace"  
**Mission Statement:** To provide authentic, personalized guidance in numerology, rudraksha selection, and vastu consultation that empowers individuals and businesses to align with natural cosmic energies for prosperity, health, and spiritual growth.

**Core Value Propositions:**

- 🔮 **Authentic Numerology Consultations:** Life path analysis, name numerology, compatibility readings with personalized insights
- 📿 **Rudraksha Guidance:** Authentic bead selection, verification services, and wearing recommendations based on individual needs
- 🏠 **Vastu Consultations:** Residential and commercial space harmonization following ancient architectural science
- 🧮 **Interactive Tools:** Free calculators for immediate insights and engagement
- 📚 **Educational Resources:** Comprehensive blog and learning materials about ancient wisdom

### 1.2 Target Users

**Primary Audience:**
1. **Individual Seekers** - People seeking spiritual guidance and self-discovery (25-60 years)
2. **Business Owners** - Entrepreneurs wanting prosperity and success through numerology and vastu
3. **Homeowners** - Property buyers and owners interested in vastu harmonization
4. **Spiritual Practitioners** - People interested in rudraksha and holistic lifestyle improvements
5. **Corporate Clients** - Organizations seeking workplace harmony through vastu

**User Characteristics:**
- Middle to upper-middle class demographic
- Spiritually curious and value traditional wisdom
- Seeking practical applications of ancient sciences
- Value authenticity and scientific approach
- Privacy-conscious regarding personal information

### 1.3 Tech Stack

**Frontend:**
- React.js with Next.js (for SEO optimization and server-side rendering)
- Tailwind CSS for utility-first styling
- Framer Motion for smooth animations
- React Hook Form for form handling
- Lucide React for consistent iconography

**Backend:**
- Supabase (PostgreSQL database)
- Supabase Authentication (email/password with email verification)
- Row Level Security (RLS) for data protection
- Supabase Storage for document and image uploads
- Real-time subscriptions for booking updates
- Auto-generated REST APIs

**Third-Party Integrations:**
- **Payment Processing:** Stripe for secure payments
- **Booking System:** Calendly API or custom booking solution
- **Email Service:** SendGrid for transactional emails
- **Analytics:** Google Analytics 4 for tracking
- **Email Marketing:** Mailchimp or ConvertKit for newsletters

### 1.4 Development Approach

**Phase 1: Frontend Development (Weeks 1-3)**
- Build all static pages with sample data
- Implement responsive design and animations
- Create reusable component library
- Integrate interactive calculators with client-side logic
- Ensure accessibility compliance (WCAG 2.1 AA)
- Push to GitHub repository

**Phase 2: Database & Authentication (Week 4)**
- Design and implement complete database schema
- Set up Supabase authentication
- Configure user registration and login flows
- Implement email verification system
- Set up Row Level Security policies
- Create storage buckets for files

**Phase 3: Backend Integration (Weeks 5-6)**
- Connect all pages to Supabase data
- Implement CRUD operations for all entities
- Build booking system with payment integration
- Set up file upload functionality
- Create admin dashboard for content management
- Implement search and filtering

**Phase 4: Advanced Features (Week 7)**
- Email automation workflows
- Newsletter integration
- Blog CMS functionality
- Advanced calculator features
- Analytics integration
- Performance optimization

**Phase 5: Testing & Deployment (Week 8)**
- End-to-end testing
- Cross-browser testing
- Mobile responsiveness verification
- Security audit
- Performance optimization
- Production deployment

### 1.5 User Authentication & Authorization Flow

**Authentication Method:**
Email and password authentication with email verification through Supabase Auth.

**New User Registration Flow:**

1. **User Initiates Signup**
   - User provides email and password on signup page
   - Client-side validation (email format, password strength)
   - Form submits to Supabase Auth

2. **Email Verification**
   - Supabase sends verification email automatically
   - User clicks verification link in email
   - Email is confirmed in Supabase auth.users table
   - User redirected to login page with success message

3. **First Login After Verification**
   - User logs in with verified email and password
   - System checks if user profile exists in profiles table
   - **If no profile:** Redirect to profile completion page (`/profile/complete`)
   - **If profile exists:** Redirect to user dashboard

4. **Profile Completion (First-Time Users)**
   - User provides required information:
     - Full name (required)
     - Phone number (optional)
     - Date of birth (required for numerology services)
     - Birth time (optional, enhances readings)
     - Birth place (optional)
     - Primary interest (dropdown: Numerology, Rudraksha, Vastu, All)
   - System creates profile record with user_id from auth.users
   - User redirected to personalized dashboard

5. **Returning User Flow**
   - User enters email and password
   - Supabase Auth validates credentials
   - If email not verified: Show message to check email
   - If verified: Check profile existence
   - Redirect to dashboard with personalized experience

**User Access by State:**

| Authentication State | Can Access | Cannot Access |
|---------------------|-----------|---------------|
| **Guest (Not Logged In)** | Homepage, service pages, blog, calculators, login, signup | User dashboard, booking, consultation history, saved calculations |
| **Authenticated (No Profile)** | Profile completion page, logout | All other authenticated features |
| **Authenticated (With Profile)** | All features, personal dashboard, booking, consultation history | Admin features (if not admin) |
| **Admin Users** | All user features plus admin dashboard, user management, content management | N/A |

**Security Features:**
- Password requirements: minimum 8 characters, at least one number
- Supabase Row Level Security enforces data access policies
- Sensitive data (birth details) encrypted at rest
- HTTPS only for all communications
- Session management through Supabase Auth
- Automatic session timeout after inactivity

---

## 2. DESIGN SYSTEM

### 2.1 Brand Identity

**Brand Name:** Ekaxa  
**Tagline:** "Embrace Grace"  
**Alternative Tagline:** "Harmonizing Ancient Wisdom with Modern Living"  
**Visual Theme:** Spiritual elegance meets modern minimalism - clean, professional, trustworthy, and calming

**Design Philosophy:**
- Blend traditional spiritual elements with contemporary design
- Premium and trustworthy appearance
- Calming and inviting atmosphere that promotes reflection
- Scientific approach to ancient sciences
- Mobile-first, fully responsive design
- Accessibility compliant (WCAG 2.1 AA standards)

### 2.2 Color Palette

```css
/* Primary Colors */
--primary-purple: #4A1D7E;        /* Deep Royal Purple - spirituality, wisdom, transformation */
--primary-purple-dark: #371560;   /* Darker purple for hover states */
--primary-purple-light: #E8DFF5;  /* Light purple for backgrounds */

/* Secondary Colors */
--secondary-gold: #D4AF37;        /* Rich Gold - prosperity, divine energy */
--secondary-gold-dark: #B8941F;   /* Darker gold for hover states */
--secondary-gold-light: #F5EDD6;  /* Light gold for accents */

/* Accent Colors */
--accent-medium-purple: #8B4789;  /* Medium Purple - balance, mysticism */
--accent-teal: #14B8A6;          /* Teal for positive actions */

/* Neutral Colors */
--cream-white: #F9F7F4;          /* Warm Cream White - peace, purity */
--white: #FFFFFF;                /* Pure white */
--charcoal: #2C2C2C;            /* Primary text */
--gray-medium: #6B6B6B;          /* Secondary text */
--gray-light: #E5E7EB;           /* Borders, dividers */
--gray-lighter: #F3F4F6;         /* Card backgrounds */

/* Semantic Colors */
--success: #4CAF50;              /* Success messages, completed */
--warning: #FF9800;              /* Warning, pending states */
--error: #F44336;                /* Error messages */
--info: #3B82F6;                 /* Information */
```

**Color Usage Guidelines:**
- Primary Purple: Main CTAs, headings, brand elements
- Secondary Gold: Highlights, premium features, special elements
- Neutral Cream: Page backgrounds
- White: Content cards, form backgrounds
- Charcoal: Primary text for maximum readability
- Use purple-gold gradient for hero sections and premium elements

### 2.3 Typography

**Font Families:**

**Headings:** 'Playfair Display', 'Cinzel', or 'Cormorant Garamond' (serif, elegant, spiritual feel)
- Conveys tradition, wisdom, and sophistication
- Particularly effective for large headings and page titles

**Body Text:** 'Inter', 'Open Sans', or 'Lato' (sans-serif, highly readable)
- Ensures excellent readability for long-form content
- Modern and clean appearance

**Special/Numbers:** 'Montserrat' (bold, modern, geometric)
- Used for calculator results and numerical displays
- Strong, clear presentation of numbers

**Font Sizes (Tailwind Classes):**

Desktop:
- `text-5xl` (48px) - Hero headings (H1)
- `text-4xl` (36px) - Page headings (H1)
- `text-3xl` (30px) - Section headings (H2)
- `text-2xl` (24px) - Subsection headings (H3)
- `text-xl` (20px) - Card titles (H4)
- `text-lg` (18px) - Large body text, emphasis
- `text-base` (16px) - Default body text
- `text-sm` (14px) - Small text, captions
- `text-xs` (12px) - Labels, fine print

Mobile:
- `text-3xl` (30px) - Hero headings
- `text-2xl` (24px) - Page headings
- `text-xl` (20px) - Section headings
- `text-lg` (18px) - Subsection headings
- `text-base` (16px) - Default body text
- `text-sm` (14px) - Small text
- `text-xs` (12px) - Labels

**Font Weights:**
- `font-light` (300) - Subtle text, decorative elements
- `font-normal` (400) - Body text
- `font-medium` (500) - Emphasis, button text
- `font-semibold` (600) - Headings, strong emphasis
- `font-bold` (700) - Hero headings, very strong emphasis

**Line Heights:**
- Body text: `leading-relaxed` (1.625)
- Headings: `leading-tight` (1.25)
- Buttons: `leading-none` (1)

### 2.4 Component Styling

**Primary Button:**
```jsx
className="bg-primary-purple hover:bg-primary-purple-dark text-white font-medium px-8 py-3 rounded-lg transition-all duration-300 shadow-md hover:shadow-xl transform hover:-translate-y-0.5"
```

**Secondary Button:**
```jsx
className="bg-white hover:bg-gray-lighter text-primary-purple font-medium px-8 py-3 rounded-lg border-2 border-primary-purple transition-all duration-300 shadow-sm hover:shadow-md"
```

**Gold Accent Button (Premium):**
```jsx
className="bg-secondary-gold hover:bg-secondary-gold-dark text-white font-semibold px-8 py-3 rounded-lg transition-all duration-300 shadow-md hover:shadow-xl"
```

**Standard Card:**
```jsx
className="bg-white rounded-2xl shadow-sm border border-gray-light p-6 hover:shadow-lg transition-shadow duration-300"
```

**Premium Card (with gradient):**
```jsx
className="bg-gradient-to-br from-primary-purple to-accent-medium-purple text-white rounded-2xl p-8 shadow-xl hover:shadow-2xl transition-all duration-300"
```

**Service Card:**
```jsx
className="bg-white rounded-2xl shadow-md border-2 border-gray-light p-8 hover:border-primary-purple hover:shadow-xl transition-all duration-300 transform hover:-translate-y-1"
```

**Text Input:**
```jsx
className="w-full px-4 py-3 border-2 border-gray-light rounded-lg focus:ring-2 focus:ring-primary-purple focus:border-primary-purple outline-none transition-all duration-200 bg-white text-charcoal placeholder-gray-medium"
```

**Select Dropdown:**
```jsx
className="w-full px-4 py-3 border-2 border-gray-light rounded-lg focus:ring-2 focus:ring-primary-purple focus:border-primary-purple outline-none transition-all duration-200 bg-white text-charcoal appearance-none cursor-pointer"
```

**Textarea:**
```jsx
className="w-full px-4 py-3 border-2 border-gray-light rounded-lg focus:ring-2 focus:ring-primary-purple focus:border-primary-purple outline-none transition-all duration-200 bg-white text-charcoal placeholder-gray-medium resize-vertical min-h-32"
```

**Badge/Tag:**
```jsx
className="inline-block px-3 py-1 bg-primary-purple-light text-primary-purple rounded-full text-sm font-medium"
```

**Calculator Result Display:**
```jsx
className="text-center bg-gradient-to-br from-primary-purple to-accent-medium-purple text-white rounded-2xl p-12 shadow-2xl"
```

### 2.5 Layout & Spacing

**Container Widths:**
- Full width: `max-w-full`
- Extra wide: `max-w-7xl` (1280px)
- Standard: `max-w-6xl` (1152px)
- Narrow: `max-w-4xl` (896px)
- Article: `max-w-3xl` (768px)

**Consistent Padding:**
- Section padding: `py-16 md:py-24` (vertical)
- Container padding: `px-4 md:px-6 lg:px-8` (horizontal)
- Card padding: `p-6 md:p-8`
- Button padding: `px-6 py-3 md:px-8 md:py-4`

**Spacing Scale (using Tailwind):**
- Extra small: `space-y-2` (8px)
- Small: `space-y-4` (16px)
- Medium: `space-y-6` (24px)
- Large: `space-y-8` (32px)
- Extra large: `space-y-12` (48px)
- Section spacing: `space-y-16` (64px)

### 2.6 Visual Elements

**Sacred Geometry & Patterns:**
- Subtle background patterns featuring mandalas and Sri Yantra
- Geometric shapes as section dividers
- Sacred geometry SVG overlays (10-15% opacity)
- Use as decorative elements, not overwhelming

**Gradients:**
- Primary gradient: `bg-gradient-to-br from-primary-purple to-accent-medium-purple`
- Gold gradient: `bg-gradient-to-r from-secondary-gold to-secondary-gold-dark`
- Soft gradient backgrounds: `bg-gradient-to-b from-white to-cream-white`

**Shadows:**
- Light: `shadow-sm`
- Medium: `shadow-md`
- Large: `shadow-lg`
- Extra large: `shadow-xl`
- Double extra large: `shadow-2xl`

**Border Radius:**
- Small: `rounded-lg` (8px)
- Medium: `rounded-xl` (12px)
- Large: `rounded-2xl` (16px)
- Full: `rounded-full` (999px) for pills and badges

**Icons:**
Use Lucide React icons throughout:
- Calculator: `Calculator`
- User: `User`
- Calendar: `Calendar`
- Book: `BookOpen`
- Heart: `Heart`
- Star: `Star`
- Check: `Check`
- X: `X`
- Menu: `Menu`
- Search: `Search`
- Phone: `Phone`
- Mail: `Mail`
- MapPin: `MapPin`
- ChevronRight: `ChevronRight`
- ChevronDown: `ChevronDown`
- ExternalLink: `ExternalLink`

**Animations:**
- Fade in on scroll: Use Framer Motion with `initial`, `whileInView`, `viewport`
- Hover transitions: `transition-all duration-300`
- Page transitions: Fade between routes
- Smooth scroll: `scroll-smooth` on html element
- Micro-interactions on buttons: Transform and shadow changes

**Imagery Guidelines:**
- High-quality, professional photography
- Authentic representations of consultations
- Close-ups of rudraksha beads
- Beautiful architectural spaces for vastu
- Abstract number visualizations
- Diverse client representation
- Avoid overly mystical or clichéd imagery
- Maintain warm, inviting color tones in photos

---

## 3. DOMAIN MODELS & DATABASE SCHEMA

### 3.1 Database Overview

The Ekaxa platform requires a comprehensive PostgreSQL database (via Supabase) to manage users, consultations, bookings, blog content, and e-commerce transactions (for rudraksha products).

**Key Principles:**
- Use UUID for all primary keys
- Include created_at and updated_at timestamps
- Implement soft deletes where appropriate
- Use enums for status fields
- Enforce referential integrity
- Apply Row Level Security (RLS) policies

### 3.2 Core Tables

#### 3.2.1 Users & Profiles

**auth.users** (Supabase managed table)
- id: UUID (PK)
- email: TEXT (unique)
- encrypted_password: TEXT
- email_confirmed_at: TIMESTAMP
- created_at: TIMESTAMP
- updated_at: TIMESTAMP

**public.profiles**
```sql
CREATE TABLE profiles (
  id UUID PRIMARY KEY REFERENCES auth.users(id) ON DELETE CASCADE,
  full_name TEXT NOT NULL,
  phone TEXT,
  date_of_birth DATE NOT NULL,
  birth_time TIME,
  birth_place TEXT,
  primary_interest TEXT CHECK (primary_interest IN ('numerology', 'rudraksha', 'vastu', 'all')),
  avatar_url TEXT,
  bio TEXT,
  is_admin BOOLEAN DEFAULT FALSE,
  created_at TIMESTAMPTZ DEFAULT NOW(),
  updated_at TIMESTAMPTZ DEFAULT NOW()
);

-- RLS Policies
ALTER TABLE profiles ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Users can view their own profile"
  ON profiles FOR SELECT
  USING (auth.uid() = id);

CREATE POLICY "Users can update their own profile"
  ON profiles FOR UPDATE
  USING (auth.uid() = id);

CREATE POLICY "Admins can view all profiles"
  ON profiles FOR SELECT
  USING (EXISTS (
    SELECT 1 FROM profiles
    WHERE id = auth.uid() AND is_admin = TRUE
  ));
```

#### 3.2.2 Consultations & Bookings

**consultations**
```sql
CREATE TYPE consultation_type AS ENUM ('numerology', 'rudraksha', 'vastu', 'comprehensive');
CREATE TYPE consultation_status AS ENUM ('pending', 'confirmed', 'completed', 'cancelled', 'rescheduled');
CREATE TYPE consultation_format AS ENUM ('video', 'phone', 'in_person');

CREATE TABLE consultations (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  user_id UUID NOT NULL REFERENCES profiles(id) ON DELETE CASCADE,
  consultation_type consultation_type NOT NULL,
  consultation_format consultation_format NOT NULL,
  scheduled_at TIMESTAMPTZ NOT NULL,
  duration_minutes INTEGER NOT NULL,
  price DECIMAL(10, 2) NOT NULL,
  status consultation_status DEFAULT 'pending',
  payment_status TEXT CHECK (payment_status IN ('pending', 'paid', 'refunded')),
  payment_id TEXT,
  specific_concerns TEXT,
  notes TEXT,
  zoom_link TEXT,
  recording_url TEXT,
  report_url TEXT,
  created_at TIMESTAMPTZ DEFAULT NOW(),
  updated_at TIMESTAMPTZ DEFAULT NOW()
);

CREATE INDEX idx_consultations_user_id ON consultations(user_id);
CREATE INDEX idx_consultations_status ON consultations(status);
CREATE INDEX idx_consultations_scheduled_at ON consultations(scheduled_at);

-- RLS Policies
ALTER TABLE consultations ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Users can view their own consultations"
  ON consultations FOR SELECT
  USING (auth.uid() = user_id);

CREATE POLICY "Users can insert their own consultations"
  ON consultations FOR INSERT
  WITH CHECK (auth.uid() = user_id);

CREATE POLICY "Admins can view all consultations"
  ON consultations FOR ALL
  USING (EXISTS (
    SELECT 1 FROM profiles
    WHERE id = auth.uid() AND is_admin = TRUE
  ));
```

#### 3.2.3 Numerology Calculations

**numerology_calculations**
```sql
CREATE TABLE numerology_calculations (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  user_id UUID REFERENCES profiles(id) ON DELETE SET NULL,
  calculation_type TEXT NOT NULL CHECK (calculation_type IN ('life_path', 'expression', 'soul_urge', 'personality', 'personal_year')),
  input_date DATE,
  input_name TEXT,
  result_number INTEGER NOT NULL,
  is_master_number BOOLEAN DEFAULT FALSE,
  saved BOOLEAN DEFAULT FALSE,
  created_at TIMESTAMPTZ DEFAULT NOW()
);

CREATE INDEX idx_numerology_calculations_user_id ON numerology_calculations(user_id);

-- RLS Policies
ALTER TABLE numerology_calculations ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Users can view their own calculations"
  ON numerology_calculations FOR SELECT
  USING (auth.uid() = user_id OR user_id IS NULL);

CREATE POLICY "Users can insert calculations"
  ON numerology_calculations FOR INSERT
  WITH CHECK (auth.uid() = user_id OR user_id IS NULL);
```

#### 3.2.4 Rudraksha Products & Orders

**rudraksha_products**
```sql
CREATE TABLE rudraksha_products (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  mukhi_type INTEGER NOT NULL CHECK (mukhi_type BETWEEN 1 AND 14),
  product_name TEXT NOT NULL,
  description TEXT,
  price DECIMAL(10, 2) NOT NULL,
  origin TEXT CHECK (origin IN ('nepal', 'indonesia', 'india')),
  size_mm DECIMAL(5, 2),
  is_certified BOOLEAN DEFAULT TRUE,
  stock_quantity INTEGER DEFAULT 0,
  image_urls TEXT[],
  benefits TEXT[],
  ruling_deity TEXT,
  associated_planet TEXT,
  chakra TEXT,
  is_active BOOLEAN DEFAULT TRUE,
  created_at TIMESTAMPTZ DEFAULT NOW(),
  updated_at TIMESTAMPTZ DEFAULT NOW()
);

CREATE INDEX idx_rudraksha_products_mukhi_type ON rudraksha_products(mukhi_type);
CREATE INDEX idx_rudraksha_products_is_active ON rudraksha_products(is_active);

-- RLS Policies
ALTER TABLE rudraksha_products ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Anyone can view active products"
  ON rudraksha_products FOR SELECT
  USING (is_active = TRUE);

CREATE POLICY "Admins can manage products"
  ON rudraksha_products FOR ALL
  USING (EXISTS (
    SELECT 1 FROM profiles
    WHERE id = auth.uid() AND is_admin = TRUE
  ));
```

**rudraksha_orders**
```sql
CREATE TYPE order_status AS ENUM ('pending', 'processing', 'shipped', 'delivered', 'cancelled');

CREATE TABLE rudraksha_orders (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  user_id UUID NOT NULL REFERENCES profiles(id) ON DELETE CASCADE,
  order_number TEXT UNIQUE NOT NULL,
  total_amount DECIMAL(10, 2) NOT NULL,
  payment_status TEXT CHECK (payment_status IN ('pending', 'paid', 'refunded')),
  payment_id TEXT,
  status order_status DEFAULT 'pending',
  shipping_address JSONB NOT NULL,
  tracking_number TEXT,
  notes TEXT,
  created_at TIMESTAMPTZ DEFAULT NOW(),
  updated_at TIMESTAMPTZ DEFAULT NOW()
);

CREATE INDEX idx_rudraksha_orders_user_id ON rudraksha_orders(user_id);
CREATE INDEX idx_rudraksha_orders_status ON rudraksha_orders(status);

-- RLS Policies
ALTER TABLE rudraksha_orders ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Users can view their own orders"
  ON rudraksha_orders FOR SELECT
  USING (auth.uid() = user_id);
```

**rudraksha_order_items**
```sql
CREATE TABLE rudraksha_order_items (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  order_id UUID NOT NULL REFERENCES rudraksha_orders(id) ON DELETE CASCADE,
  product_id UUID NOT NULL REFERENCES rudraksha_products(id),
  quantity INTEGER NOT NULL CHECK (quantity > 0),
  unit_price DECIMAL(10, 2) NOT NULL,
  subtotal DECIMAL(10, 2) NOT NULL,
  created_at TIMESTAMPTZ DEFAULT NOW()
);

CREATE INDEX idx_rudraksha_order_items_order_id ON rudraksha_order_items(order_id);

-- RLS Policies
ALTER TABLE rudraksha_order_items ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Users can view their own order items"
  ON rudraksha_order_items FOR SELECT
  USING (EXISTS (
    SELECT 1 FROM rudraksha_orders
    WHERE id = order_id AND user_id = auth.uid()
  ));
```

#### 3.2.5 Blog & Content Management

**blog_posts**
```sql
CREATE TYPE post_status AS ENUM ('draft', 'published', 'archived');
CREATE TYPE post_category AS ENUM ('numerology', 'rudraksha', 'vastu', 'spiritual_living', 'how_to', 'success_stories');

CREATE TABLE blog_posts (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  author_id UUID NOT NULL REFERENCES profiles(id),
  title TEXT NOT NULL,
  slug TEXT UNIQUE NOT NULL,
  excerpt TEXT,
  content TEXT NOT NULL,
  featured_image_url TEXT,
  category post_category NOT NULL,
  tags TEXT[],
  status post_status DEFAULT 'draft',
  read_time_minutes INTEGER,
  views INTEGER DEFAULT 0,
  published_at TIMESTAMPTZ,
  created_at TIMESTAMPTZ DEFAULT NOW(),
  updated_at TIMESTAMPTZ DEFAULT NOW()
);

CREATE INDEX idx_blog_posts_slug ON blog_posts(slug);
CREATE INDEX idx_blog_posts_category ON blog_posts(category);
CREATE INDEX idx_blog_posts_status ON blog_posts(status);
CREATE INDEX idx_blog_posts_published_at ON blog_posts(published_at DESC);

-- RLS Policies
ALTER TABLE blog_posts ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Anyone can view published posts"
  ON blog_posts FOR SELECT
  USING (status = 'published');

CREATE POLICY "Admins can manage all posts"
  ON blog_posts FOR ALL
  USING (EXISTS (
    SELECT 1 FROM profiles
    WHERE id = auth.uid() AND is_admin = TRUE
  ));
```

#### 3.2.6 Testimonials & Reviews

**testimonials**
```sql
CREATE TABLE testimonials (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  user_id UUID REFERENCES profiles(id) ON DELETE SET NULL,
  consultation_id UUID REFERENCES consultations(id) ON DELETE SET NULL,
  name TEXT NOT NULL,
  location TEXT,
  service_type TEXT NOT NULL CHECK (service_type IN ('numerology', 'rudraksha', 'vastu', 'comprehensive')),
  rating INTEGER NOT NULL CHECK (rating BETWEEN 1 AND 5),
  title TEXT,
  content TEXT NOT NULL,
  before_situation TEXT,
  results_achieved TEXT,
  is_featured BOOLEAN DEFAULT FALSE,
  is_approved BOOLEAN DEFAULT FALSE,
  created_at TIMESTAMPTZ DEFAULT NOW(),
  updated_at TIMESTAMPTZ DEFAULT NOW()
);

CREATE INDEX idx_testimonials_is_approved ON testimonials(is_approved);
CREATE INDEX idx_testimonials_is_featured ON testimonials(is_featured);

-- RLS Policies
ALTER TABLE testimonials ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Anyone can view approved testimonials"
  ON testimonials FOR SELECT
  USING (is_approved = TRUE);

CREATE POLICY "Users can insert their own testimonials"
  ON testimonials FOR INSERT
  WITH CHECK (auth.uid() = user_id);
```

#### 3.2.7 Newsletter Subscribers

**newsletter_subscribers**
```sql
CREATE TABLE newsletter_subscribers (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  email TEXT UNIQUE NOT NULL,
  is_active BOOLEAN DEFAULT TRUE,
  subscribed_at TIMESTAMPTZ DEFAULT NOW(),
  unsubscribed_at TIMESTAMPTZ
);

CREATE INDEX idx_newsletter_subscribers_email ON newsletter_subscribers(email);

-- RLS Policies
ALTER TABLE newsletter_subscribers ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Anyone can subscribe"
  ON newsletter_subscribers FOR INSERT
  WITH CHECK (TRUE);

CREATE POLICY "Admins can view subscribers"
  ON newsletter_subscribers FOR SELECT
  USING (EXISTS (
    SELECT 1 FROM profiles
    WHERE id = auth.uid() AND is_admin = TRUE
  ));
```

#### 3.2.8 Contact Form Submissions

**contact_submissions**
```sql
CREATE TYPE submission_status AS ENUM ('new', 'in_progress', 'resolved', 'archived');

CREATE TABLE contact_submissions (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  name TEXT NOT NULL,
  email TEXT NOT NULL,
  phone TEXT,
  interest_area TEXT,
  message TEXT NOT NULL,
  status submission_status DEFAULT 'new',
  admin_notes TEXT,
  created_at TIMESTAMPTZ DEFAULT NOW(),
  updated_at TIMESTAMPTZ DEFAULT NOW()
);

CREATE INDEX idx_contact_submissions_status ON contact_submissions(status);
CREATE INDEX idx_contact_submissions_created_at ON contact_submissions(created_at DESC);

-- RLS Policies
ALTER TABLE contact_submissions ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Anyone can submit contact form"
  ON contact_submissions FOR INSERT
  WITH CHECK (TRUE);

CREATE POLICY "Admins can view all submissions"
  ON contact_submissions FOR SELECT
  USING (EXISTS (
    SELECT 1 FROM profiles
    WHERE id = auth.uid() AND is_admin = TRUE
  ));
```

### 3.3 Storage Buckets

**Supabase Storage Buckets:**

1. **avatars**
   - User profile pictures
   - Max file size: 2MB
   - Allowed types: image/jpeg, image/png, image/webp
   - Public access for viewing

2. **consultation-reports**
   - PDF reports generated after consultations
   - Max file size: 10MB
   - Allowed types: application/pdf
   - Private access (user-specific RLS)

3. **blog-images**
   - Featured images and content images for blog posts
   - Max file size: 5MB
   - Allowed types: image/jpeg, image/png, image/webp
   - Public access

4. **product-images**
   - Rudraksha product photos
   - Max file size: 3MB
   - Allowed types: image/jpeg, image/png, image/webp
   - Public access

5. **certificates**
   - Rudraksha authentication certificates
   - Max file size: 5MB
   - Allowed types: application/pdf, image/jpeg, image/png
   - Private access (order-specific RLS)

### 3.4 Database Functions & Triggers

**Auto-update updated_at timestamp:**
```sql
CREATE OR REPLACE FUNCTION update_updated_at_column()
RETURNS TRIGGER AS $$
BEGIN
  NEW.updated_at = NOW();
  RETURN NEW;
END;
$$ LANGUAGE plpgsql;

-- Apply to all tables with updated_at
CREATE TRIGGER update_profiles_updated_at BEFORE UPDATE ON profiles
  FOR EACH ROW EXECUTE FUNCTION update_updated_at_column();

CREATE TRIGGER update_consultations_updated_at BEFORE UPDATE ON consultations
  FOR EACH ROW EXECUTE FUNCTION update_updated_at_column();

-- Repeat for other tables...
```

**Generate order number:**
```sql
CREATE OR REPLACE FUNCTION generate_order_number()
RETURNS TRIGGER AS $$
BEGIN
  NEW.order_number = 'EKX-' || TO_CHAR(NOW(), 'YYYYMMDD') || '-' || LPAD(nextval('order_number_seq')::TEXT, 6, '0');
  RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE SEQUENCE order_number_seq;

CREATE TRIGGER set_order_number BEFORE INSERT ON rudraksha_orders
  FOR EACH ROW EXECUTE FUNCTION generate_order_number();
```

---

## 4. USER ROLES & PERMISSIONS

### 4.1 User Role Definitions

**Guest Users (Not Authenticated)**
- Can view all public content (homepage, service pages, blog, calculators)
- Can use free numerology calculators
- Can view rudraksha product catalog
- Can access educational content
- Cannot save calculations or access personalized features
- Cannot book consultations or make purchases
- Must register to access advanced features

**Registered Users (Authenticated)**
- All Guest permissions plus:
- Personal dashboard with consultation history
- Save numerology calculations for future reference
- Book and manage consultations
- Purchase rudraksha products
- Access consultation reports and recordings
- Manage profile and personal information
- Submit testimonials
- Save favorite blog posts
- Receive personalized recommendations

**Admin Users**
- All Registered User permissions plus:
- Access admin dashboard
- Manage all user accounts
- View and manage all consultations
- Approve and schedule consultation requests
- Upload consultation reports and recordings
- Manage blog posts (create, edit, publish, delete)
- Manage testimonials (approve, feature, remove)
- Manage rudraksha products (add, edit, pricing, inventory)
- View and process orders
- Access analytics and reports
- Manage newsletter subscribers
- View and respond to contact form submissions
- Configure site settings

### 4.2 Permission Matrix

| Feature | Guest | Registered User | Admin |
|---------|-------|----------------|-------|
| **General Access** |
| View public pages | ✓ | ✓ | ✓ |
| Use free calculators | ✓ | ✓ | ✓ |
| Read blog posts | ✓ | ✓ | ✓ |
| **User Features** |
| Save calculations | ✗ | ✓ | ✓ |
| Personal dashboard | ✗ | ✓ | ✓ |
| Book consultations | ✗ | ✓ | ✓ |
| Purchase products | ✗ | ✓ | ✓ |
| View order history | ✗ | ✓ | ✓ |
| Submit testimonials | ✗ | ✓ | ✓ |
| **Admin Features** |
| Admin dashboard | ✗ | ✗ | ✓ |
| Manage users | ✗ | ✗ | ✓ |
| Manage consultations | ✗ | ✗ | ✓ |
| Manage blog | ✗ | ✗ | ✓ |
| Manage products | ✗ | ✗ | ✓ |
| View analytics | ✗ | ✗ | ✓ |

---

## 5. PAGE SPECIFICATIONS

### 5.1 Complete Page List

The Ekaxa website consists of the following pages, organized by functional area:

**Public Pages (No Authentication Required):**
1. Homepage (Landing Page)
2. Numerology Service Page
3. Rudraksha Service Page
4. Vastu Service Page
5. About Us Page
6. Blog Homepage
7. Individual Blog Post Page
8. Contact Page
9. Login Page
10. Signup Page
11. Email Verification Page
12. Forgot Password Page

**Interactive Tools (Public Access):**
13. Free Numerology Calculator Page (multiple calculators on one page)

**User Dashboard Pages (Authentication Required):**
14. User Dashboard (Overview)
15. Profile Management Page
16. Profile Completion Page (first-time users)
17. My Consultations Page
18. Consultation Booking Page
19. My Orders Page
20. Saved Calculations Page

**E-Commerce Pages:**
21. Rudraksha Shop Page (Product Catalog)
22. Product Detail Page
23. Shopping Cart Page
24. Checkout Page
25. Order Confirmation Page

**Admin Pages (Admin Role Only):**
26. Admin Dashboard
27. User Management Page
28. Consultation Management Page
29. Blog Management Page
30. Product Management Page
31. Order Management Page
32. Analytics Page

**Legal & Support Pages:**
33. Privacy Policy Page
34. Terms of Service Page
35. Cancellation Policy Page
36. FAQ Page

**Total: 36 Pages**

### 5.2 Page Hierarchy & Navigation

**Primary Navigation (Header):**
- Logo → Homepage
- Services → Dropdown
  - Numerology
  - Rudraksha
  - Vastu
- Resources → Dropdown
  - Blog
  - Free Calculator
  - FAQ
- About
- Contact
- Login / Dashboard (if logged in)

**Footer Navigation:**
- Services (Numerology, Rudraksha, Vastu)
- Resources (Blog, Calculator, FAQ)
- Company (About, Contact)
- Legal (Privacy Policy, Terms of Service, Cancellation Policy)
- Newsletter Signup
- Social Media Links

**User Dashboard Navigation:**
- Overview
- My Profile
- My Consultations
- Book Consultation
- My Orders
- Saved Calculations
- Logout

**Admin Dashboard Navigation:**
- Dashboard Overview
- Users
- Consultations
- Blog Posts
- Products
- Orders
- Analytics
- Settings

### 5.3 Detailed Page Specifications

For each page, the following information must be generated in individual page prompts:

**Page Information:**
- Page number and name
- URL/Route
- User access level (Guest, User, Admin)
- Purpose and goals

**Layout Structure:**
- Header/Navigation (if different from global)
- Hero section (if applicable)
- Main content sections
- Sidebar content (if applicable)
- Footer (if different from global)

**Content Elements:**
- Headings and copy
- Sample data structures
- Form fields and validation
- Interactive elements
- Images and media
- Call-to-action buttons

**Styling Requirements:**
- Color scheme usage
- Typography specifications
- Component styles
- Responsive breakpoints
- Animations and transitions

**Functionality Requirements:**
- User interactions
- Form submissions
- Data display
- Navigation flows
- State management
- Loading states
- Error handling
- Success states

**Technical Notes:**
- API endpoints (to be connected later)
- State management needs
- Performance considerations
- SEO requirements
- Accessibility requirements

---

## 6. DEVELOPMENT PLATFORM GUIDELINES

### 6.1 Frontend Framework: Next.js with React

**Key Features to Leverage:**
- Server-Side Rendering (SSR) for SEO optimization
- Static Site Generation (SSG) for blog pages
- API Routes for serverless functions
- Image optimization with next/image
- Automatic code splitting
- Built-in routing

**Project Structure:**
```
ekaxa-webapp/
├── public/
│   ├── images/
│   ├── icons/
│   └── fonts/
├── src/
│   ├── app/
│   │   ├── (auth)/
│   │   │   ├── login/
│   │   │   └── signup/
│   │   ├── (dashboard)/
│   │   │   ├── profile/
│   │   │   ├── consultations/
│   │   │   └── orders/
│   │   ├── (admin)/
│   │   │   ├── dashboard/
│   │   │   ├── users/
│   │   │   └── blog/
│   │   ├── services/
│   │   │   ├── numerology/
│   │   │   ├── rudraksha/
│   │   │   └── vastu/
│   │   ├── blog/
│   │   ├── calculator/
│   │   ├── about/
│   │   ├── contact/
│   │   └── page.tsx
│   ├── components/
│   │   ├── ui/ (reusable UI components)
│   │   ├── layout/ (header, footer, navigation)
│   │   ├── forms/ (form components)
│   │   └── calculators/ (calculator logic)
│   ├── lib/
│   │   ├── supabase/ (Supabase client)
│   │   ├── utils/ (utility functions)
│   │   └── hooks/ (custom React hooks)
│   ├── styles/
│   │   └── globals.css
│   └── types/
│       └── database.types.ts
├── tailwind.config.js
├── next.config.js
└── package.json
```

### 6.2 Styling: Tailwind CSS

**Configuration:**
```javascript
// tailwind.config.js
module.exports = {
  content: [
    './src/**/*.{js,ts,jsx,tsx,mdx}',
  ],
  theme: {
    extend: {
      colors: {
        'primary-purple': '#4A1D7E',
        'primary-purple-dark': '#371560',
        'primary-purple-light': '#E8DFF5',
        'secondary-gold': '#D4AF37',
        'secondary-gold-dark': '#B8941F',
        'secondary-gold-light': '#F5EDD6',
        'accent-medium-purple': '#8B4789',
        'accent-teal': '#14B8A6',
        'cream-white': '#F9F7F4',
        'charcoal': '#2C2C2C',
        'gray-medium': '#6B6B6B',
      },
      fontFamily: {
        heading: ['Playfair Display', 'serif'],
        body: ['Inter', 'sans-serif'],
        numbers: ['Montserrat', 'sans-serif'],
      },
    },
  },
  plugins: [
    require('@tailwindcss/forms'),
    require('@tailwindcss/typography'),
  ],
}
```

### 6.3 State Management

**For Simple State:**
- React useState and useContext
- Local component state for UI interactions

**For Complex State:**
- Zustand (lightweight state management)
- TanStack Query (React Query) for server state

**Example Store Structure:**
```typescript
// stores/useAuthStore.ts
import create from 'zustand';

interface AuthStore {
  user: User | null;
  setUser: (user: User | null) => void;
  logout: () => void;
}

export const useAuthStore = create<AuthStore>((set) => ({
  user: null,
  setUser: (user) => set({ user }),
  logout: () => set({ user: null }),
}));
```

### 6.4 Supabase Integration

**Client Setup:**
```typescript
// lib/supabase/client.ts
import { createClient } from '@supabase/supabase-js';
import { Database } from '@/types/database.types';

const supabaseUrl = process.env.NEXT_PUBLIC_SUPABASE_URL!;
const supabaseKey = process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY!;

export const supabase = createClient<Database>(supabaseUrl, supabaseKey);
```

**Authentication Helpers:**
```typescript
// lib/supabase/auth.ts
import { supabase } from './client';

export const signUp = async (email: string, password: string) => {
  const { data, error } = await supabase.auth.signUp({
    email,
    password,
    options: {
      emailRedirectTo: `${window.location.origin}/auth/callback`,
    },
  });
  return { data, error };
};

export const signIn = async (email: string, password: string) => {
  const { data, error } = await supabase.auth.signInWithPassword({
    email,
    password,
  });
  return { data, error };
};

export const signOut = async () => {
  const { error } = await supabase.auth.signOut();
  return { error };
};

export const getCurrentUser = async () => {
  const { data: { user } } = await supabase.auth.getUser();
  return user;
};
```

### 6.5 Form Handling

**Using React Hook Form:**
```typescript
import { useForm } from 'react-hook-form';
import { zodResolver } from '@hookform/resolvers/zod';
import * as z from 'zod';

const contactSchema = z.object({
  name: z.string().min(2, 'Name must be at least 2 characters'),
  email: z.string().email('Invalid email address'),
  message: z.string().min(10, 'Message must be at least 10 characters'),
});

type ContactFormData = z.infer<typeof contactSchema>;

export function ContactForm() {
  const { register, handleSubmit, formState: { errors } } = useForm<ContactFormData>({
    resolver: zodResolver(contactSchema),
  });

  const onSubmit = async (data: ContactFormData) => {
    // Handle form submission
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      {/* Form fields */}
    </form>
  );
}
```

### 6.6 API Routes & Serverless Functions

**Example API Route:**
```typescript
// app/api/newsletter/route.ts
import { NextRequest, NextResponse } from 'next/server';
import { supabase } from '@/lib/supabase/client';

export async function POST(request: NextRequest) {
  const { email } = await request.json();

  const { data, error } = await supabase
    .from('newsletter_subscribers')
    .insert([{ email }]);

  if (error) {
    return NextResponse.json({ error: error.message }, { status: 400 });
  }

  return NextResponse.json({ success: true, data });
}
```

### 6.7 Performance Optimization

**Image Optimization:**
```tsx
import Image from 'next/image';

<Image
  src="/images/hero-background.jpg"
  alt="Ekaxa spiritual consultation"
  width={1920}
  height={1080}
  priority
  quality={85}
  placeholder="blur"
/>
```

**Code Splitting:**
```tsx
import dynamic from 'next/dynamic';

const Calculator = dynamic(() => import('@/components/calculators/LifePathCalculator'), {
  loading: () => <CalculatorSkeleton />,
  ssr: false,
});
```

**Font Optimization:**
```tsx
// app/layout.tsx
import { Inter, Playfair_Display } from 'next/font/google';

const inter = Inter({ subsets: ['latin'], variable: '--font-inter' });
const playfair = Playfair_Display({ subsets: ['latin'], variable: '--font-playfair' });
```

### 6.8 SEO Best Practices

**Metadata Configuration:**
```typescript
// app/services/numerology/page.tsx
export const metadata = {
  title: 'Numerology Consultations | Ekaxa - Discover Your Life Path',
  description: 'Professional numerology readings and consultations. Discover your life path number, destiny number, and unlock the sacred power of numbers.',
  keywords: 'numerology, life path number, numerology consultation, destiny number',
  openGraph: {
    title: 'Numerology Consultations | Ekaxa',
    description: 'Unlock the sacred power of numbers in your life',
    images: ['/images/og-numerology.jpg'],
  },
};
```

**Structured Data:**
```tsx
<script type="application/ld+json">
  {JSON.stringify({
    "@context": "https://schema.org",
    "@type": "Service",
    "name": "Numerology Consultation",
    "provider": {
      "@type": "Organization",
      "name": "Ekaxa"
    }
  })}
</script>
```

---

## 7. INSTRUCTIONS FOR LLM: GENERATE PAGE DEVELOPMENT PROMPTS

When the user requests page development prompts, you will generate comprehensive, standalone prompts for building each page with sample data and static functionality.

### 7.1 Prompt Generation Guidelines

**Each Page Prompt Must Include:**

1. **Page Header Information**
   - Page number and name
   - URL/route
   - Purpose and user value
   - User access level

2. **Design System Reference**
   - Colors to use (from Section 2.2)
   - Typography specifications (from Section 2.3)
   - Component styles to apply (from Section 2.4)
   - Required icons from Lucide React

3. **Layout Structure**
   - Overall page structure with semantic HTML
   - Responsive grid/flexbox layout
   - Spacing and padding guidelines
   - Mobile-specific adaptations

4. **Content Sections**
   - All text content with placeholder copy
   - Heading hierarchy
   - Sample data structures
   - Image placeholders with descriptions

5. **Interactive Elements**
   - Buttons and their states
   - Forms with field specifications
   - Validation rules (client-side for MVP)
   - User interaction flows

6. **Sample Data**
   - Realistic placeholder content
   - Data structures matching database schema
   - Sufficient variety for testing

7. **States & Behaviors**
   - Loading states with skeletons
   - Empty states with helpful messaging
   - Error states with clear feedback
   - Success states with confirmations

8. **Mobile Responsiveness**
   - Breakpoint-specific layouts
   - Touch-friendly interactions
   - Optimized for mobile viewports

9. **Accessibility**
   - ARIA labels where needed
   - Semantic HTML
   - Keyboard navigation
   - Focus management

10. **Implementation Notes**
    - No backend integration for MVP
    - Use sample data (hard-coded)
    - Console logging for form submissions
    - Navigation using Next.js Link component

11. **Acceptance Criteria Checklist**
    - Design system compliance
    - Responsive design verification
    - Accessibility checks
    - Interactive element testing
    - Clean code standards

### 7.2 Sample Data Guidelines

**For Numerology Calculations:**
```javascript
const sampleCalculations = [
  {
    id: '1',
    type: 'life_path',
    inputDate: '1990-05-15',
    result: 3,
    isMasterNumber: false,
    date: '2024-11-01'
  },
  {
    id: '2',
    type: 'expression',
    inputName: 'John Smith',
    result: 11,
    isMasterNumber: true,
    date: '2024-11-05'
  }
];
```

**For Consultations:**
```javascript
const sampleConsultations = [
  {
    id: '1',
    type: 'numerology',
    date: '2024-11-25T10:00:00Z',
    duration: 60,
    status: 'confirmed',
    format: 'video',
    price: 149.00
  },
  {
    id: '2',
    type: 'vastu',
    date: '2024-11-20T14:00:00Z',
    duration: 90,
    status: 'completed',
    format: 'in_person',
    price: 299.00
  }
];
```

**For Rudraksha Products:**
```javascript
const sampleProducts = [
  {
    id: '1',
    mukhiType: 5,
    name: '5 Mukhi Rudraksha - Nepal',
    price: 45.00,
    origin: 'nepal',
    benefits: ['General wellness', 'Health', 'Peace'],
    inStock: true,
    imageUrl: '/images/rudraksha-5-mukhi.jpg'
  }
];
```

**For Blog Posts:**
```javascript
const sampleBlogPosts = [
  {
    id: '1',
    title: 'Understanding Your Life Path Number',
    slug: 'understanding-life-path-number',
    excerpt: 'Discover what your life path number reveals about your purpose...',
    category: 'numerology',
    author: 'Ekaxa Team',
    publishedAt: '2024-11-01',
    readTime: 8,
    featuredImage: '/images/blog/life-path-number.jpg'
  }
];
```

**For Testimonials:**
```javascript
const sampleTestimonials = [
  {
    id: '1',
    name: 'Sarah M.',
    location: 'San Francisco, CA',
    service: 'numerology',
    rating: 5,
    content: 'The numerology consultation changed my perspective on my career path. Within three months of implementing the recommendations, I received a promotion!',
    date: '2024-10-15'
  }
];
```

### 7.3 Prompt Template Structure

```markdown
# [Page Number]: [Page Name]

## Page Overview
**URL:** /[route]
**Access Level:** [Guest/User/Admin]
**Purpose:** [What this page accomplishes for the user]

## Design System Requirements

### Colors
[List specific colors from palette to use]

### Typography
[Specify heading levels and body text styles]

### Components
[List component styles from Section 2.4 to use]

## Layout Structure

[Detailed description of page sections and layout]

## Content Sections

### [Section Name 1]
[Content specifications, sample copy, structure]

### [Section Name 2]
[Content specifications, sample copy, structure]

## Sample Data

```javascript
[Provide realistic sample data structures]
```

## Interactive Elements

### [Element Name]
[Functionality, states, validation]

## Mobile Responsiveness

[Specific adaptations for mobile devices]

## Accessibility Requirements

[ARIA labels, semantic HTML, keyboard navigation]

## Implementation Notes

**For MVP:**
- Use sample data provided above
- No real authentication checks
- Forms log to console
- Mock success messages
- React Router for navigation

**What NOT to Include:**
- Real Supabase integration
- Backend API calls
- Complex state management
- Payment processing

## Acceptance Criteria

- [ ] Design system colors and typography correct
- [ ] All sections present and styled
- [ ] Responsive on mobile, tablet, desktop
- [ ] Interactive elements have proper states
- [ ] Sample data displays correctly
- [ ] Forms have client-side validation
- [ ] Lucide React icons used
- [ ] No console errors
- [ ] Clean, commented code
- [ ] Matches Ekaxa branding

## Additional Context

[Any page-specific guidance or considerations]
```

### 7.4 Output Format

- Create each prompt as a separate downloadable .md file
- Name format: `[page-number]_[page-name-kebab-case].md`
  - Example: `01_homepage.md`, `02_numerology_service.md`
- Provide clickable download links for each file
- OR create a single .ZIP file containing all prompts

### 7.5 Page Prioritization

Generate prompts in this order for sequential development:

**Priority 1 (Core Public Pages):**
1. Homepage
2. Numerology Service Page
3. Rudraksha Service Page
4. Vastu Service Page
5. Free Calculator Page
6. About Us Page
7. Contact Page

**Priority 2 (Authentication & User Pages):**
8. Login Page
9. Signup Page
10. Profile Completion Page
11. User Dashboard
12. Consultation Booking Page

**Priority 3 (Content & Commerce):**
13. Blog Homepage
14. Blog Post Page
15. Rudraksha Shop Page
16. Product Detail Page
17. Shopping Cart Page
18. Checkout Page

**Priority 4 (Admin & Management):**
19. Admin Dashboard
20. User Management Page
21. Consultation Management Page
22. Blog Management Page
23. Product Management Page

**Priority 5 (Additional Pages):**
24-36. Remaining pages as listed in Section 5.1

---

## 8. INSTRUCTIONS FOR LLM: GENERATE DATABASE CREATION PROMPTS

When the user requests database creation prompts, you will generate comprehensive SQL scripts and setup instructions for the complete Supabase database.

### 8.1 Database Prompt Components

**The database creation prompt should include:**

1. **Complete SQL Schema**
   - All table definitions from Section 3
   - Data types, constraints, and indexes
   - Foreign key relationships
   - Check constraints and defaults

2. **Row Level Security Policies**
   - Enable RLS on all tables
   - Policies for users to access their own data
   - Policies for admin access to all data
   - Policies for public read access where appropriate

3. **Database Functions**
   - Trigger functions (updated_at timestamps)
   - Helper functions (generate_order_number)
   - Utility functions as needed

4. **Storage Bucket Configuration**
   - Bucket creation statements
   - Access policies for each bucket
   - File size and type restrictions

5. **Indexes for Performance**
   - Indexes on foreign keys
   - Indexes on frequently queried columns
   - Composite indexes where beneficial

6. **Seed Data (Optional)**
   - Sample admin user
   - Sample blog categories
   - Initial rudraksha products
   - Example consultations for testing

7. **Setup Instructions**
   - Step-by-step Supabase project setup
   - Environment variable configuration
   - How to run the SQL scripts
   - How to verify the setup

### 8.2 Database Prompt Template

```markdown
# Ekaxa Database Creation Guide

## Overview
This document provides complete instructions for setting up the Ekaxa PostgreSQL database in Supabase, including all tables, relationships, security policies, and storage buckets.

## Prerequisites
- Supabase account created
- New Supabase project initialized
- Supabase project URL and API keys available

## Step 1: Environment Setup

Create a `.env.local` file with:
```
NEXT_PUBLIC_SUPABASE_URL=your-project-url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key
SUPABASE_SERVICE_ROLE_KEY=your-service-role-key
```

## Step 2: Run SQL Scripts

Execute the following SQL scripts in the Supabase SQL Editor in order:

### 2.1 Enable Extensions
```sql
-- Enable UUID generation
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";
```

### 2.2 Create Custom Types
```sql
[All ENUM type definitions]
```

### 2.3 Create Tables
```sql
[All table creation statements with detailed comments]
```

### 2.4 Create Indexes
```sql
[All index creation statements]
```

### 2.5 Create Functions and Triggers
```sql
[All function and trigger definitions]
```

### 2.6 Enable Row Level Security
```sql
[All RLS enable statements and policies]
```

## Step 3: Configure Storage Buckets

[Instructions for creating and configuring storage buckets via Supabase dashboard]

## Step 4: Seed Initial Data (Optional)

```sql
[INSERT statements for initial data]
```

## Step 5: Verification

Run these queries to verify setup:
```sql
[Verification queries]
```

## Step 6: Generate TypeScript Types

[Instructions for generating TypeScript types from database schema]

## Troubleshooting

[Common issues and solutions]

## Security Checklist

- [ ] RLS enabled on all tables
- [ ] Policies tested for user access
- [ ] Storage bucket policies configured
- [ ] Service role key secured
- [ ] No sensitive data in client-accessible tables
```

### 8.3 RLS Policy Examples

**User accessing own data:**
```sql
CREATE POLICY "Users can view their own consultations"
  ON consultations FOR SELECT
  USING (auth.uid() = user_id);
```

**Admin accessing all data:**
```sql
CREATE POLICY "Admins can manage all consultations"
  ON consultations FOR ALL
  USING (
    EXISTS (
      SELECT 1 FROM profiles
      WHERE id = auth.uid() AND is_admin = TRUE
    )
  );
```

**Public read access:**
```sql
CREATE POLICY "Anyone can view published blog posts"
  ON blog_posts FOR SELECT
  USING (status = 'published');
```

### 8.4 Output Format

Create as a single comprehensive markdown file:
- Filename: `Ekaxa_Database_Setup.md`
- Include complete SQL scripts
- Include step-by-step instructions
- Include verification queries
- Provide as downloadable artifact

---

## 9. INSTRUCTIONS FOR LLM: GENERATE INTEGRATION PROMPTS

When the user requests integration prompts, you will generate modular, step-by-step prompts for connecting the built pages to Supabase, payment systems, and external services.

### 9.1 Integration Layers

**Layer 1: Authentication Integration**
- Connect login page to Supabase Auth
- Connect signup page to Supabase Auth
- Implement email verification flow
- Protect authenticated routes
- Create profile completion workflow
- Implement logout functionality
- Handle session management

**Layer 2: Database Integration**
- Connect all pages to real Supabase data
- Replace sample data with database queries
- Implement data fetching with loading states
- Add error handling for database operations
- Implement search and filtering
- Add pagination for lists

**Layer 3: Form Submissions & CRUD**
- Connect all forms to Supabase inserts/updates
- Implement consultation booking flow
- Handle file uploads (avatars, reports)
- Implement rudraksha order creation
- Handle success/error states
- Refresh data after mutations

**Layer 4: Payment Integration**
- Set up Stripe account and keys
- Create payment intent for consultations
- Handle consultation payment flow
- Create checkout session for products
- Handle payment webhooks
- Update order status after payment

**Layer 5: Email Automation**
- Set up SendGrid account
- Create email templates
- Send booking confirmation emails
- Send payment receipt emails
- Send consultation reminders
- Send report delivery notifications

**Layer 6: Admin Features**
- Build admin dashboard with analytics
- Implement user management
- Create consultation management interface
- Build blog post editor
- Implement product inventory management
- Create order fulfillment workflow

**Layer 7: Advanced Features**
- Implement newsletter subscription
- Add social sharing functionality
- Create testimonial submission flow
- Build saved calculations feature
- Add search functionality
- Implement analytics tracking

### 9.2 Integration Prompt Template

```markdown
# Integration Layer [X]: [Layer Name]

## Overview
[Description of what this integration layer accomplishes]

## Prerequisites
- All frontend pages built and tested
- Database schema created and verified
- [Other specific prerequisites]

## Step-by-Step Implementation

### Step 1: [First Implementation Step]
[Detailed instructions with code examples]

### Step 2: [Second Implementation Step]
[Detailed instructions with code examples]

[Continue for all steps...]

## Code Examples

### [Feature Name]
```typescript
[Complete, working code example]
```

## Testing Instructions

1. [How to test this integration]
2. [Expected behavior]
3. [How to verify success]

## Common Issues & Solutions

**Issue:** [Description]
**Solution:** [How to fix]

## Next Steps

After completing this layer, proceed to [Next Integration Layer]
```

### 9.3 Specific Integration Examples

**Authentication Integration Example:**

```typescript
// lib/supabase/auth-helpers.ts
export async function signUpWithEmail(email: string, password: string) {
  const { data, error } = await supabase.auth.signUp({
    email,
    password,
    options: {
      emailRedirectTo: `${window.location.origin}/auth/callback`,
    },
  });

  if (error) throw error;
  return data;
}

// components/SignupForm.tsx
const handleSignup = async (formData: SignupFormData) => {
  try {
    await signUpWithEmail(formData.email, formData.password);
    // Show success message
    router.push('/auth/verify-email');
  } catch (error) {
    // Handle error
  }
};
```

**Database Query Integration Example:**

```typescript
// lib/supabase/consultations.ts
export async function getUserConsultations(userId: string) {
  const { data, error } = await supabase
    .from('consultations')
    .select('*')
    .eq('user_id', userId)
    .order('scheduled_at', { ascending: false });

  if (error) throw error;
  return data;
}

// app/dashboard/consultations/page.tsx
const { data: consultations, isLoading, error } = useQuery({
  queryKey: ['consultations', user.id],
  queryFn: () => getUserConsultations(user.id),
});
```

### 9.4 Output Format

Create separate integration prompts as markdown files:
- Naming: `Integration_Layer[X]_[Name].md`
- Examples:
  - `Integration_Layer1_Authentication.md`
  - `Integration_Layer2_Database.md`
  - `Integration_Layer3_Forms_CRUD.md`
  - `Integration_Layer4_Payment.md`

Provide as:
- Individual downloadable files with links
- OR single ZIP archive containing all integration prompts

---

## 10. INSTRUCTIONS FOR LLM: GENERATE IMPLEMENTATION CHECKLIST

When the user requests the implementation checklist, you will generate a comprehensive, hierarchical task list for the entire Ekaxa project from start to deployment.

### 10.1 Checklist Structure

**The checklist should include:**

1. **Phase-based organization** matching development approach (Section 1.4)
2. **Hierarchical task breakdown** with main tasks, subtasks, and sub-subtasks
3. **Clear dependencies** showing what must be completed before other tasks
4. **Estimated time allocations** for realistic planning
5. **Checkboxes** for tracking progress
6. **Responsible party indicators** (if team-based)
7. **Quality gates** at key milestones

### 10.2 Checklist Template

```markdown
# Ekaxa Implementation Checklist

**Project Duration:** 8 weeks
**Start Date:** [TBD]
**Target Launch:** [TBD]

## Phase 1: Frontend Development (Weeks 1-3)

### Week 1: Foundation & Core Public Pages
**Goal:** Set up project and build primary public-facing pages

#### Project Setup
- [ ] Initialize Next.js project with TypeScript
- [ ] Configure Tailwind CSS with custom theme
- [ ] Set up ESLint and Prettier
- [ ] Create Git repository and initial commit
- [ ] Set up project folder structure
- [ ] Install core dependencies (Framer Motion, Lucide React, React Hook Form)
- [ ] Configure environment variables template

#### Design System Implementation
- [ ] Create color variables in Tailwind config
- [ ] Set up custom fonts (Playfair Display, Inter, Montserrat)
- [ ] Build reusable UI component library
  - [ ] Button component with variants
  - [ ] Card component with variants
  - [ ] Input component with validation states
  - [ ] Form components
  - [ ] Badge/Tag component
- [ ] Create layout components
  - [ ] Header with navigation
  - [ ] Footer
  - [ ] Page container wrapper

#### Core Public Pages
- [ ] **Page 01: Homepage**
  - [ ] Hero section with CTA
  - [ ] Services overview cards
  - [ ] How it works section
  - [ ] Testimonials carousel
  - [ ] Statistics section
  - [ ] Latest blog posts preview
  - [ ] Final CTA section
  - [ ] Test responsive design
  - [ ] Verify all links work

[Continue with detailed breakdown for all pages...]

## Phase 2: Database & Authentication (Week 4)

### Supabase Setup
- [ ] Create Supabase project
- [ ] Configure project settings
- [ ] Note project URL and API keys
- [ ] Set up environment variables in Next.js

### Database Schema
- [ ] Run SQL scripts to create all tables
- [ ] Verify table creation
- [ ] Create indexes
- [ ] Set up database functions and triggers
- [ ] Enable Row Level Security
- [ ] Create and test RLS policies
- [ ] Verify foreign key relationships

### Storage Buckets
- [ ] Create avatars bucket
- [ ] Create consultation-reports bucket
- [ ] Create blog-images bucket
- [ ] Create product-images bucket
- [ ] Create certificates bucket
- [ ] Configure bucket policies
- [ ] Test file upload and retrieval

### Authentication
- [ ] Configure Supabase Auth settings
- [ ] Set up email templates
- [ ] Test signup flow
- [ ] Test email verification
- [ ] Test login flow
- [ ] Test password reset
- [ ] Implement protected route middleware
- [ ] Create auth context/store
- [ ] Build auth helper functions

## Phase 3: Backend Integration (Weeks 5-6)

[Detailed integration tasks...]

## Phase 4: Advanced Features (Week 7)

[Advanced feature implementation tasks...]

## Phase 5: Testing & Deployment (Week 8)

### Testing
- [ ] **Functional Testing**
  - [ ] Test all user flows
  - [ ] Test admin workflows
  - [ ] Test edge cases
  - [ ] Test error scenarios

- [ ] **Cross-Browser Testing**
  - [ ] Chrome
  - [ ] Firefox
  - [ ] Safari
  - [ ] Edge

- [ ] **Responsive Design Testing**
  - [ ] Mobile (375px, 414px)
  - [ ] Tablet (768px, 1024px)
  - [ ] Desktop (1280px, 1920px)

- [ ] **Performance Testing**
  - [ ] Run Lighthouse audits
  - [ ] Optimize images
  - [ ] Minimize bundle size
  - [ ] Test page load times

- [ ] **Accessibility Testing**
  - [ ] WAVE tool audit
  - [ ] Screen reader testing
  - [ ] Keyboard navigation
  - [ ] Color contrast verification

- [ ] **Security Testing**
  - [ ] Verify RLS policies
  - [ ] Check for exposed API keys
  - [ ] Test authentication flows
  - [ ] Review data validation

### Pre-Deployment
- [ ] Final content review
- [ ] SEO metadata verification
- [ ] Privacy policy and terms finalization
- [ ] Backup database
- [ ] Document deployment process

### Deployment
- [ ] Set up production Vercel project
- [ ] Configure environment variables
- [ ] Set up custom domain
- [ ] Configure DNS
- [ ] Enable SSL certificate
- [ ] Deploy to production
- [ ] Run smoke tests on production
- [ ] Set up monitoring (Sentry, etc.)
- [ ] Configure analytics (Google Analytics 4)

### Post-Deployment
- [ ] Monitor for errors
- [ ] Check all forms working
- [ ] Verify payment processing
- [ ] Test email delivery
- [ ] Submit sitemap to Google
- [ ] Set up uptime monitoring
- [ ] Create backup schedule

## Quality Gates

### After Phase 1
✓ All public pages render correctly
✓ Responsive design works on all devices
✓ No console errors
✓ Design system applied consistently

### After Phase 2
✓ Database schema created and verified
✓ Authentication flows working
✓ RLS policies tested and secure

### After Phase 3
✓ All data displays from database
✓ Forms submit successfully
✓ File uploads working

### After Phase 4
✓ Payments processing correctly
✓ Emails sending properly
✓ Admin features functional

### Before Deployment
✓ All tests passing
✓ Performance metrics meet targets
✓ Security audit completed
✓ Content finalized

## Success Metrics

**Launch Day Goals:**
- [ ] Zero critical bugs
- [ ] Page load time < 3 seconds
- [ ] Lighthouse score > 90
- [ ] All core user flows tested

**Week 1 Post-Launch:**
- [ ] 50+ unique visitors
- [ ] 5+ consultation bookings
- [ ] 10+ newsletter signups

**Month 1 Post-Launch:**
- [ ] 500+ unique visitors
- [ ] 20+ consultation bookings
- [ ] 100+ newsletter subscribers

## Notes
- Update this checklist as tasks are completed
- Document any blockers or challenges
- Adjust timeline if needed based on progress
```

### 10.3 Output Format

Create as a single comprehensive markdown file:
- Filename: `Ekaxa_Implementation_Checklist.md`
- Include checkboxes for all tasks
- Organize hierarchically with clear indentation
- Include time estimates
- Provide as downloadable artifact

---

## APPENDIX A: PROJECT TIMELINE

**Total Duration:** 8 weeks (November 18, 2025 - January 12, 2026)

**Phase 1: Frontend Development** (Weeks 1-3)
- Week 1: Project setup + Core public pages (Homepage, Services, About)
- Week 2: User pages (Dashboard, Profile, Booking) + Calculator
- Week 3: E-commerce pages (Shop, Cart, Checkout) + Blog

**Phase 2: Database & Authentication** (Week 4)
- Database schema creation
- Supabase Auth setup
- Storage bucket configuration
- RLS policy implementation

**Phase 3: Backend Integration** (Weeks 5-6)
- Week 5: Authentication integration + Database queries + CRUD operations
- Week 6: Payment integration + Email automation + Admin features

**Phase 4: Advanced Features** (Week 7)
- Newsletter integration
- Analytics implementation
- Performance optimization
- Additional features

**Phase 5: Testing & Deployment** (Week 8)
- Comprehensive testing (functional, cross-browser, responsive)
- Bug fixes
- Production deployment
- Post-launch monitoring

**Launch Date:** January 12, 2026

---

## APPENDIX B: TECHNOLOGY STACK SUMMARY

**Frontend:**
- Next.js 14+ (React 18+)
- TypeScript
- Tailwind CSS
- Framer Motion
- React Hook Form
- Zod (validation)
- TanStack Query
- Zustand (state management)
- Lucide React (icons)

**Backend:**
- Supabase (PostgreSQL)
- Supabase Auth
- Supabase Storage
- Supabase Realtime

**Integrations:**
- Stripe (payments)
- SendGrid (emails)
- Mailchimp/ConvertKit (newsletter)
- Google Analytics 4
- Vercel (hosting/deployment)

**Development Tools:**
- Git & GitHub
- ESLint & Prettier
- VS Code
- Supabase CLI
- Vercel CLI

---

## APPENDIX C: KEY DECISIONS & RATIONALE

**Authentication:**
- Supabase Auth with email/password for simplicity
- Email verification required for security
- Profile completion step for personalized experience

**Database:**
- PostgreSQL via Supabase for robust relational data
- Row Level Security for data protection
- UUID primary keys for security and scalability

**Frontend Framework:**
- Next.js for SEO optimization and performance
- Server-side rendering for public pages
- Static generation for blog content

**Styling:**
- Tailwind CSS for rapid development and consistency
- Custom color palette aligned with brand
- Mobile-first responsive design

**Payment Processing:**
- Stripe for reliability and ease of integration
- Separate flows for consultations vs products
- Webhook handling for order updates

**Content Management:**
- Database-driven blog for flexibility
- Admin dashboard for content management
- Rich text editor for blog posts

---

## END OF MASTER PROMPT DOCUMENT v1.0

**Document Status:** Ready for Implementation  
**Next Steps:**
1. Review and approve master prompt
2. Generate individual page development prompts
3. Generate database creation prompt
4. Generate integration prompts
5. Generate implementation checklist
6. Begin Phase 1 development

**For Questions or Clarifications:**
Refer back to specific sections of this master prompt or request additional detail on any component.

