# ShopSphere - Enterprise E-Commerce Platform

[![Django](https://img.shields.io/badge/Django-3.1-green.svg)](https://www.djangoproject.com/)
[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Latest-blue.svg)](https://www.postgresql.org/)
[![AWS](https://img.shields.io/badge/AWS-S3%20%7C%20EB-orange.svg)](https://aws.amazon.com/)

## 🎯 Project Overview

ShopSphere is a **production-ready, full-stack e-commerce platform** built with Django, featuring advanced shopping cart functionality, secure payment integration, user authentication, and comprehensive order management. The platform demonstrates enterprise-level architecture with cloud deployment capabilities.

**Live Demo:** [Deploy URL] | **Project Duration:** [Timeline]

---

## 🚀 Key Technical Achievements

### 1. **Advanced Authentication System**
- Custom user model extending Django's AbstractBaseUser
- Email-based authentication with token verification
- Password reset functionality with secure token generation
- Session management with automatic timeout
- Profile management with image uploads to AWS S3

### 2. **Intelligent Shopping Cart**
- Session-based cart for anonymous users
- Persistent cart with database integration for authenticated users
- **Cart Merge Logic**: Seamlessly merges anonymous cart with user cart on login
- Product variation handling (size, color) with dynamic pricing
- Real-time cart count displayed across all pages
- Context processors for global cart availability

### 3. **Payment Integration**
- PayPal SDK integration for secure transactions
- AJAX-based payment processing without page reload
- Transaction tracking with unique payment IDs
- Order confirmation emails with order details
- Payment status verification and error handling

### 4. **Product Management System**
- Category-based product organization
- Product variations (color, size) with inventory tracking
- Image gallery with multiple product images
- Search functionality with Q objects for complex queries
- Pagination for improved performance
- Average rating calculation using Django aggregation

### 5. **Review & Rating System**
- Star rating system (0.5 to 5 stars with half-star precision)
- Review submission with subject and detailed feedback
- Update existing reviews instead of duplicates
- Display average rating and review count per product
- Conditional review submission (only for purchased products - optional)

### 6. **Order Management**
- Comprehensive order tracking with status updates
- Order history dashboard for users
- Detailed order invoices with product variations
- Email notifications for order confirmation
- Admin panel with inline order products

### 7. **AWS Cloud Integration**
- **S3 Bucket**: Static files and media storage
- **Elastic Beanstalk**: Production deployment
- **PostgreSQL RDS**: Production database (configured)
- boto3 SDK for programmatic AWS access
- Environment-based configuration with python-decouple

### 8. **Security Implementation**
- CSRF protection on all forms
- django-admin-honeypot for admin security
- Session timeout for inactive users
- Secure password hashing with PBKDF2
- Environment variables for sensitive data
- SQL injection prevention with ORM

---

## 💼 Technical Skills Demonstrated

### Backend Development
- **Django Framework**: Models, Views, Templates, Forms, Admin customization
- **Database Design**: One-to-Many, Many-to-Many relationships, Foreign Keys
- **ORM Queries**: Complex queries, aggregation, Q objects, filtering
- **User Authentication**: Custom user models, permissions, decorators
- **Email Services**: SMTP configuration, HTML email templates
- **File Handling**: Image uploads, validation, AWS S3 integration

### Frontend Development
- **Template Inheritance**: Base templates, includes, blocks
- **Dynamic UI**: AJAX for cart updates, PayPal button integration
- **Bootstrap 4**: Responsive design, cards, forms, modals
- **JavaScript/jQuery**: DOM manipulation, event handling, AJAX calls
- **CSS**: Custom styling, animations, responsive design

### DevOps & Deployment
- **AWS Services**: S3, Elastic Beanstalk, RDS (configured)
- **Environment Management**: .env files, python-decouple
- **Static File Management**: Collectstatic, whitenoise (optional)
- **Database Migration**: Django migrations, data fixtures
- **Version Control**: Git, .gitignore configuration

### Architecture & Design
- **MVT Pattern**: Clean separation of concerns
- **Context Processors**: Global data availability
- **Custom Managers**: QuerySet optimization
- **Signals**: Automated profile creation (configured)
- **Middleware**: Session management, security headers

---

## 📊 Database Schema Highlights

### Key Models Implemented:
1. **Account** (Custom User Model)
   - Email-based authentication
   - Phone number, address fields
   - Boolean flags for permissions

2. **Product**
   - Category relationship
   - Stock management
   - Average review calculation method

3. **Variation**
   - Product relationship (color, size)
   - Custom manager for filtering

4. **Cart & CartItem**
   - Anonymous and authenticated user handling
   - Many-to-Many with Variation

5. **Order & OrderProduct**
   - Payment relationship
   - Order status tracking
   - Variation preservation

6. **Payment**
   - Transaction ID tracking
   - Payment method and status

7. **ReviewRating**
   - User and Product relationship
   - Rating validation (0.5 - 5.0)

---

## 🛠️ Technologies & Tools

| Category | Technologies |
|----------|-------------|
| **Backend** | Python 3.8+, Django 3.1, Django ORM |
| **Database** | PostgreSQL (Production), SQLite (Development) |
| **Cloud** | AWS S3, AWS Elastic Beanstalk |
| **Payment** | PayPal SDK |
| **Frontend** | HTML5, CSS3, JavaScript, jQuery, Bootstrap 4 |
| **Libraries** | Pillow, boto3, python-decouple, psycopg2-binary |
| **Security** | django-admin-honeypot, django-session-timeout |
| **Other** | django-admin-thumbnails, django-storages |

---

## 📁 Project Structure

```
shopsphere/
├── accounts/           # User authentication & profiles
├── carts/             # Shopping cart functionality
├── category/          # Product categories
├── orders/            # Order management & payments
├── store/             # Product catalog & reviews
├── templates/         # HTML templates
│   ├── accounts/
│   ├── orders/
│   ├── store/
│   └── includes/      # Reusable components
├── static/            # CSS, JS, Images
├── media/             # User uploads
├── greatkart/         # Project settings
├── .ebextensions/     # AWS EB configuration
├── requirements.txt
└── manage.py
```

---

## 🎨 Key Features Implementation

### Feature 1: Cart Merge on Login
**Challenge**: How to handle anonymous shopping cart when user logs in?

**Solution**: 
- Implemented cart merging logic in login view
- Compare product variations between session cart and user cart
- Increment quantity if item exists, otherwise create new cart item
- Delete session cart after successful merge

### Feature 2: Dynamic Product Variations
**Challenge**: Handle multiple product attributes (color, size) with different pricing?

**Solution**:
- Created Variation model with category and value fields
- Custom manager methods (colors(), sizes()) for filtering
- Many-to-Many relationship with CartItem
- Display variations in cart and order templates

### Feature 3: PayPal Integration
**Challenge**: Secure payment processing without storing card details?

**Solution**:
- Integrated PayPal JavaScript SDK
- AJAX-based payment capture
- Server-side verification of transaction
- Store payment ID and status in database
- Send confirmation email after successful payment

### Feature 4: Review System
**Challenge**: Prevent duplicate reviews and allow updates?

**Solution**:
- Check if user already reviewed the product
- Update existing review instead of creating duplicate
- Use try-except block for DoesNotExist handling
- Calculate average rating using Django aggregation

---

## 🔒 Security Measures

- ✅ CSRF tokens on all POST forms
- ✅ Environment variables for secrets (.env)
- ✅ Admin honeypot to catch brute force attempts
- ✅ Session timeout after inactivity
- ✅ Password hashing with PBKDF2
- ✅ Email verification for registration
- ✅ SQL injection prevention via ORM
- ✅ XSS protection with Django templates

---

## 📈 Performance Optimizations

- **Database**: Select_related and Prefetch_related for query optimization
- **Pagination**: Limit products per page to reduce load time
- **Static Files**: AWS S3 CDN for faster asset delivery
- **Caching**: Context processors reduce redundant queries
- **Image Optimization**: Thumbnail generation for admin panel

---

## 🚀 Deployment Process

### AWS Elastic Beanstalk Setup:
1. Created `.ebextensions` folder for configuration
2. `db-migrate.config` - Automatic migrations on deployment
3. `django.config` - WSGI path configuration
4. Environment variables set in EB console
5. Database migration command runs on leader instance only

### AWS S3 Integration:
- django-storages for S3 backend
- boto3 for AWS SDK
- Separate buckets for static and media files
- Proper IAM permissions configured

---

## 🎓 Learning Outcomes & Business Impact

### Technical Growth:
- Mastered Django MVT architecture
- Learned payment gateway integration
- Implemented cloud deployment (AWS)
- Enhanced security best practices
- Database relationship modeling

### Business Value:
- **Scalable**: Can handle increasing traffic with cloud infrastructure
- **Secure**: Multiple security layers protect user data
- **User-Friendly**: Intuitive UI with seamless cart experience
- **Monetizable**: Payment system ready for real transactions
- **Maintainable**: Clean code structure for future enhancements

---

## 🔮 Future Enhancements

- [ ] Implement wishlist functionality
- [ ] Add social authentication (Google, Facebook)
- [ ] Product recommendation engine
- [ ] Real-time inventory updates with WebSockets
- [ ] Multi-vendor marketplace support
- [ ] Coupon and discount system
- [ ] Order tracking with shipping API integration
- [ ] Mobile app using Django REST Framework

---

## 📝 Installation & Setup

### Prerequisites:
- Python 3.8+
- PostgreSQL (for production)
- AWS Account (for S3 and EB)

### Local Development:
```bash
# Clone repository
git clone <repository-url>
cd shopsphere

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Create .env file
cp .env-sample .env
# Add your configuration

# Run migrations
python manage.py migrate

# Load sample data
python manage.py loaddata data.json

# Create superuser
python manage.py createsuperuser

# Run development server
python manage.py runserver
```

### AWS Deployment:
```bash
# Initialize EB
eb init

# Create environment
eb create shopsphere-env

# Deploy
eb deploy

# Check status
eb status
```

---

## 👨‍💻 Developer

**[Your Name]**
- Email: [your.email@example.com]
- LinkedIn: [linkedin.com/in/yourprofile]
- GitHub: [github.com/yourusername]
- Portfolio: [yourportfolio.com]

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## 🙏 Acknowledgments

- Django Documentation
- PayPal Developer Documentation
- AWS Documentation
- Bootstrap Framework
- Stack Overflow Community

---

## 📞 Contact

For any queries regarding this project, please reach out via:
- **Email**: [surajk86808@gmail.com]
- **LinkedIn**: [https://www.linkedin.com/in/suraj-y-756a11233/]

**⭐ If you find this project impressive, please consider starring the repository!**
