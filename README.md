<h1>LoanMS — Loan Management System</h1>

<p>
  A <strong>sleek, role-based Loan Management System</strong> for banks and MFIs.
  Customers can apply for loans and track EMI schedules, while Admins review applications,
  approve or reject them, mark repayments as paid, and manage customers —
  all powered by a modern <strong>React UI</strong> and a secure <strong>Spring Boot API</strong>.
</p>

<hr/>

<h2>✨ Highlights</h2>
<ul>
  <li><strong>Modern UI</strong> — React + Vite + Tailwind for a fast, clean, responsive interface</li>
  <li><strong>Secure API</strong> — Spring Boot 3, Spring Security (JWT), role-based access (ADMIN / CUSTOMER)</li>
  <li><strong>EMI Engine</strong> — Accurate EMI calculation with auto-generated schedules & due dates</li>
  <li><strong>Two Portals</strong>
    <ul>
      <li><strong>Customer</strong>: Apply for loans, view “My Loans”, repayment schedule, profile</li>
      <li><strong>Admin</strong>: Review applications, approve/reject, mark repayments paid, view customers</li>
    </ul>
  </li>
  <li><strong>Clean Domain</strong> — JPA entities for User, Loan, Repayment with clear services & repositories</li>
  <li><strong>DX-Friendly</strong> — Simple setup, clean endpoints, and helpful error messages</li>
</ul>

<hr/>

<h2>🧱 Tech Stack</h2>

<h3>Frontend</h3>
<ul>
  <li>React + TypeScript + Vite</li>
  <li>TailwindCSS + Lucide Icons</li>
  <li>Axios for API calls</li>
  <li>JWT stored client-side (AuthContext)</li>
</ul>

<h3>Backend</h3>
<ul>
  <li>Spring Boot 3 (Web, Security, Validation)</li>
  <li>Spring Data JPA</li>
  <li>PostgreSQL (recommended) or H2 for quick development</li>
  <li>JWT authentication with filter chain</li>
</ul>

<hr/>

<h2>🗂️ Project Structure</h2>

<pre>
project/
├─ frontend/
│  └─ src/
│     ├─ components/
│     │  ├─ admin/        # Admin pages & modals
│     │  └─ customer/     # Customer dashboard & panels
│     ├─ contexts/        # AuthContext (login/register/JWT)
│     ├─ lib/             # API clients (admin, loans, repayments)
│     └─ utils/           # Format & calculation helpers
└─ backend/
   └─ src/main/java/com/example/loanmanagement/
      ├─ model/           # User, Loan, Repayment
      ├─ repository/      # JPA repositories
      ├─ service/         # Business logic
      ├─ controller/      # REST controllers
      ├─ security/        # JWT & Spring Security config
      └─ util/            # EMI calculator & date utilities
</pre>

<hr/>

<h2>🚀 Getting Started</h2>

<h3>1) Backend (Spring Boot)</h3>
<p><strong>Prerequisites:</strong> JDK 17+, Maven, PostgreSQL (or H2)</p>

<p><strong>application.properties (PostgreSQL example)</strong></p>
<pre>
server.port=8080

spring.datasource.url=jdbc:postgresql://localhost:5432/loanms
spring.datasource.username=postgres
spring.datasource.password=postgres
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect

# CORS
app.cors.allowed-origin=http://localhost:5173

# JWT
app.jwt.secret=change-me-super-secret
app.jwt.expiration=86400000
</pre>

<p><strong>Quick try with H2</strong></p>
<pre>
spring.datasource.url=jdbc:h2:mem:loanms;MODE=PostgreSQL;DB_CLOSE_DELAY=-1
spring.datasource.driverClassName=org.h2.Driver
spring.jpa.hibernate.ddl-auto=create-drop
</pre>

<p><strong>Run</strong></p>
<pre>
mvn spring-boot:run
</pre>
<p>API runs at <code>http://localhost:8080</code></p>

<hr/>

<h3>2) Frontend (React)</h3>

<p><strong>.env</strong></p>
<pre>
VITE_API_BASE_URL=http://localhost:8080
</pre>

<p><strong>Run</strong></p>
<pre>
npm install
npm run dev
</pre>

<p>App runs at <code>http://localhost:5173</code></p>

<hr/>

<h2>🔐 Roles & Authentication</h2>
<ul>
  <li><strong>CUSTOMER</strong> — /app: apply loans, view schedules, profile</li>
  <li><strong>ADMIN</strong> — /admin: applications, approvals, repayments, customers</li>
</ul>

<p><strong>Auth Flow</strong></p>
<ul>
  <li>Login returns JWT (stored in AuthContext)</li>
  <li>Requests send <code>Authorization: Bearer &lt;token&gt;</code></li>
  <li>Unauthorized access returns clear 401 / 403 errors</li>
</ul>

<hr/>

<h2>📡 API Quick Reference</h2>

<h3>Customer</h3>
<ul>
  <li>POST /api/auth/register</li>
  <li>POST /api/auth/login</li>
  <li>POST /api/loans/apply</li>
  <li>GET /api/loans/my</li>
  <li>GET /api/loans/{loanId}</li>
  <li>GET /api/loans/{loanId}/repayments</li>
</ul>

<h3>Admin</h3>
<ul>
  <li>GET /api/admin/loans</li>
  <li>PUT /api/admin/loans/{id}/approve</li>
  <li>PUT /api/admin/loans/{id}/reject</li>
  <li>PUT /api/admin/repayments/{repaymentId}/pay</li>
  <li>GET /api/admin/customers</li>
</ul>

<hr/>

<h2>🧮 EMI & Schedule</h2>
<ul>
  <li>EMI calculated using <code>EmiCalculator.calculateEMI()</code></li>
  <li>Schedules generated with <code>DateUtil.generateDueDates()</code></li>
  <li>Admins mark installments as PAID</li>
  <li>Customers see live totals and remaining balance</li>
</ul>

<hr/>

<h2>🧪 Troubleshooting</h2>
<ul>
  <li>CORS issues → check Vite URL</li>
  <li>401/403 → verify JWT & expiration</li>
  <li>Ports → Backend 8080, Frontend 5173</li>
  <li>Check browser Network tab for failed requests</li>
</ul>

<hr/>

<h2>🗺️ Roadmap</h2>
<ul>
  <li>Payment gateway integration</li>
  <li>CSV / PDF exports</li>
  <li>Admin analytics & charts</li>
  <li>Multi-tenancy & audit logs</li>
  <li>Email / SMS notifications</li>
</ul>

<hr/>

<h2>🤝 Contributing</h2>
<ul>
  <li>Focused PRs</li>
  <li>Clear commit messages</li>
  <li>Screenshots or GIFs for UI changes</li>
</ul>

<hr/>

<h2>📄 License</h2>
<p>MIT — free to use with attribution.</p>

<hr/>

<h2>💬 Credits</h2>
<p>
  Built with ❤️ using Spring Boot & React.<br/>
  Thanks to the open-source community.
</p>

<hr/>

<h2>⚡ Quick Start (TL;DR)</h2>
<pre>
# Backend
cd backend
mvn spring-boot:run

# Frontend
cd frontend
npm install
npm run dev
</pre>

<p>
  Open <code>http://localhost:5173</code> and you’re in.<br/>
  <strong>Happy shipping! 🚀</strong>
</p>
