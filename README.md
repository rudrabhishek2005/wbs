# Doobots - AI Automation Marketplace

A comprehensive full-stack web application for buying and selling AI automation tools. Built with React, TypeScript, Tailwind CSS, and Supabase.

## Features

### 🔐 Authentication & User Management
- Email/password authentication
- Role-based access (Seller/Buyer)
- User profiles and dashboards

### 🛍️ Marketplace
- Browse all automation listings
- Advanced search and filtering
- Detailed listing pages with download functionality
- Tag-based categorization

### 👤 Seller Features
- Create and manage automation listings
- Upload automation files (.json, .zip)
- Track downloads and performance
- Edit and delete listings

### 🛒 Buyer Features
- Browse and search automations
- Download free automations instantly
- Filter by price, tags, and keywords
- View detailed automation information

## Tech Stack

- **Frontend**: React 18, TypeScript, Tailwind CSS
- **Backend**: Supabase (Database, Authentication, Storage)
- **Routing**: React Router v6
- **Icons**: Lucide React
- **Build Tool**: Vite

## Database Schema

### Profiles Table
```sql
- id (uuid, references auth.users)
- name (text)
- email (text)
- role ('seller' | 'buyer')
- created_at (timestamp)
- updated_at (timestamp)
```

### Automation Listings Table
```sql
- id (uuid)
- title (text)
- description (text)
- tags (text[])
- price (numeric)
- file_url (text)
- file_type ('json' | 'zip')
- file_name (text)
- seller_id (uuid, references profiles)
- status ('draft' | 'published')
- download_count (integer)
- created_at (timestamp)
- updated_at (timestamp)
```

## Getting Started

### Prerequisites
- Node.js (v18 or higher)
- Supabase account

### Installation

1. Clone the repository
2. Install dependencies:
   ```bash
   npm install
   ```

3. Set up Supabase:
   - Create a new Supabase project
   - Run the database migration from `supabase/migrations/create_doobots_schema.sql`
   - Create a storage bucket named `automation-files`

4. Configure environment variables:
   ```env
   VITE_SUPABASE_URL=your_supabase_url
   VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
   ```

5. Start the development server:
   ```bash
   npm run dev
   ```

## Project Structure

```
src/
├── components/           # Reusable UI components
│   ├── Auth/            # Authentication forms
│   ├── Dashboard/       # Dashboard components
│   ├── Forms/           # Form components
│   ├── Layout/          # Layout components
│   └── Marketplace/     # Marketplace components
├── contexts/            # React contexts
├── hooks/               # Custom hooks
├── lib/                # Utility libraries
├── pages/              # Page components
└── types/              # TypeScript type definitions
```

## Key Features Explained

### Role-Based Access
- **Sellers** can create, edit, and manage automation listings
- **Buyers** can browse, search, and download automations
- Different dashboard experiences based on user role

### File Upload System
- Secure file storage using Supabase Storage
- Support for JSON (low-code) and ZIP (code-based) files
- File validation and error handling

### Search & Filtering
- Full-text search across titles and descriptions
- Tag-based filtering
- Price filtering (free vs paid)
- Real-time search results

### Security
- Row Level Security (RLS) enabled on all tables
- Users can only access/modify their own data
- Public read access for published listings only

## Design System

### Color Palette
- **Primary**: Emerald (#10B981)
- **Secondary**: Gray (#6B7280)
- **Background**: Light gray (#F9FAFB)
- **Text**: Dark gray (#1F2937)

### Typography
- **Headings**: Bold, clear hierarchy
- **Body**: Readable, well-spaced
- **UI Elements**: Consistent sizing and spacing

## Deployment

### Frontend (Vercel/Netlify)
1. Build the project:
   ```bash
   npm run build
   ```
2. Deploy the `dist` folder to your preferred hosting platform

### Database (Supabase)
- Database and authentication are handled by Supabase
- No additional backend deployment needed

## Future Enhancements

- [ ] Payment integration (Stripe)
- [ ] Advanced analytics for sellers
- [ ] Rating and review system
- [ ] Automation categories
- [ ] User following/favorites
- [ ] API documentation
- [ ] Mobile app

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License

This project is licensed under the MIT License.