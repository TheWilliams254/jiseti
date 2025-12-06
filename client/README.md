Jiseti Frontend Documentation
📌 Project Overview
Jiseti is a civic tech platform that empowers citizens to report corruption or request government intervention. The frontend is built with React, Tailwind CSS, and Vite, and communicates with a Flask backend. It supports role-based access (users and admins), protected routes, media uploads, geolocation, and a status update system.
🗂️ Project Structure
src/
├── assets/                  # Static files (images, logos)
├── components/              # Reusable UI components
│   ├── shared/              # Header, Footer, ProtectedRoute, AdminRoute, etc.
│   ├── posts/               # PostList, PostItem, PostDetail, etc.
├── context/                 # Auth context for login state management
├── hooks/                   # Custom hooks like useAuth
├── pages/                   # Route-level components (HomePage, Profile, Admin)
├── utils/                   # Utility functions (e.g., API handlers)
├── App.jsx                  # Routes for login, register, and fallback
├── InApp.jsx                # Routes after authentication
├── main.jsx                 # React entry point
├── index.css                # Tailwind and global styles
📄 Main Files Explained
main.jsx - ReactDOM entry point. Wraps the app with <BrowserRouter> and <AuthProvider>.

App.jsx - Contains public routes: /login, /register, and fallback *. Uses <Navigate /> to redirect authenticated users to /.

InApp.jsx - All protected routes post-login. Includes standard routes like /posts, /create, /profile and admin-only routes like /admin, /admin/reports/:id. Uses <ProtectedRoute /> and <AdminRoute />.

AuthContext.jsx - Provides global authentication state, stores user in localStorage, exposes login/logout/isAdmin.

useAuth.js - Custom hook to consume auth context.

ProtectedRoute.jsx - Prevents access to certain routes if user is not logged in.

AdminRoute.jsx - Ensures user has an admin role before accessing admin pages.
🧩 Shared Components
Header.jsx - Top navigation bar including Home, Posts, Profile, Admin (if isAdmin), and Logout.

Footer.jsx - Site-wide footer with credits and contact info.
📝 Pages
Public:
- LandingPage: Introduction to the platform (/landing)
- LoginPage & RegisterPage

Authenticated:
- HomePage: Dashboard overview
- PostListPage: All posts by the user
- PostDetailPage: Individual report with media and status
- CreatePostPage: Submit new report/request
- EditPostPage: Modify an existing post
- ProfilePage: User info, change password, etc.

Admin:
- AdminDashboardPage: Admin overview, stats, flagged posts
- ReviewReportPage: Post moderation and status updates
🔧 Utilities
api.js - Contains all API calls grouped by resource: authApi, postsApi, adminApi.

utils.js - Utility functions like token management and validators.
🎨 Styling
Tailwind CSS is configured in vite.config.js and index.css.

Example:
@tailwind base;
@tailwind components;
@tailwind utilities;
🔐 Authentication Flow
1. User logs in → AuthContext stores token + user info.
2. All protected routes check user via useAuth.
3. Admin access is validated by user.role === 'admin'.
🚧 Future Improvements
✅ Add toast notifications
✅ Add offline handling
🚀 WebSocket for live updates
🔒 Role-based field editing (e.g., only admin can change status)
📦 Deployment
Vite for frontend dev server. Works well on Vercel or Netlify.
Use vite.config.js to ensure correct base path and CORS support.
🤝 Team Collaboration
This README was written for team collaboration in Canvas and supports easy editing and documentation of changes.

If you're using this in GitHub, commit often and tag pull requests with the correct feature (feature/post-form, fix/admin-route, etc.).

