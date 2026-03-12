# Copilot Instructions - Restoran Template

## Project Overview
**Restoran** is a Bootstrap-based restaurant website template for "Urban Grill," a modern Nairobi restaurant. The codebase is a static HTML/CSS/JS site focused on showcasing restaurant services, menus, team, bookings, and testimonials.

**Key Stack:**
- Bootstrap 5 (custom compilation via SCSS)
- jQuery for DOM manipulation and event handling
- Third-party libraries: WOW.js (animations), Owl Carousel (sliders), Tempusdominus (date picker), CounterUp (number animations)
- Font Awesome icons & Google Fonts (Heebo, Nunito, Pacifico)

## Architecture & Key Components

### Page Structure
The site consists of 10 main HTML pages:
- `index.html` - Homepage with hero section, services, testimonials carousel
- `about.html` - Restaurant information
- `service.html` - Service offerings
- `menu.html` - Food menu
- `booking.html` - Table reservation form (integrated with Tempusdominus date picker)
- `team.html` - Staff showcase
- `testimonial.html` - Customer reviews
- `contact.html` - Contact & location
- Each page follows the same navbar structure (brand: "Urban Grill" with fire icon)

### CSS Architecture (`css/` and `scss/`)
- **`css/style.css`** (478 lines) - Main template stylesheet with custom theming:
  - CSS variables: `--primary` (#FEA116 orange), `--light` (#F1F8FF), `--dark` (#0F172B)
  - Custom utility classes: `.ff-secondary` (Pacifico font), `.fw-semi-bold`, `.text-luminous-green`
  - Spinner, navbar, button, and animation styles
- **`scss/bootstrap.scss`** - Imported Bootstrap 5 framework (customizable)
- **`css/bootstrap.min.css`** - Pre-compiled minified Bootstrap

### JavaScript Behavior (`js/main.js`)
jQuery-based client-side logic (120 lines):
- **Spinner**: Hide loading spinner after page load
- **Animations**: WOW.js initialization for scroll-triggered CSS animations
- **Sticky navbar**: Add `sticky-top shadow-sm` classes on scroll > 45px
- **Dropdown hover**: Desktop hover behavior for navbar dropdowns (disabled on mobile < 992px)
- **Back-to-top button**: Fade in/out at 300px scroll, smooth scroll to top (easeInOutExpo)
- **Counter animations**: Activate with `[data-toggle="counter-up"]` attribute
- **Modal video**: `btn-play` elements with `data-src` attribute populate YouTube modal
- **Testimonial carousel**: Owl Carousel config with responsive breakpoints (1 item @0px, 2 @768px, 3 @992px)

### External Libraries
- **`lib/animate/`** - Animate.css (scroll animations via WOW.js)
- **`lib/owlcarousel/`** - Slider/carousel for testimonials (default config in main.js)
- **`lib/tempusdominus/`** - DateTime picker (used in booking.html for date selection)
- **`lib/waypoints/`** - Scroll trigger support (dependency for other libraries)
- **`lib/counterup/`** - Number counter animation (uses data attribute trigger)
- **`lib/easing/`** - jQuery easing functions (used in back-to-top smooth scroll)

## Developer Workflows

### Local Development
No build process is required. All files are served as-is:
1. Open any `.html` file directly in browser OR use a simple HTTP server
2. CSS/JS changes reflect immediately (no compilation needed for CSS edits)
3. SCSS edits require recompilation to `css/bootstrap.min.css` if modifying Bootstrap

### Customization Points
- **Colors**: Edit CSS variables in `css/style.css` (lines 2-5) or override in specific rules
- **Typography**: Font imports are in HTML `<head>` (Google Fonts links) and Pacifico font utility class
- **Content**: Replace text directly in HTML pages (all content is hardcoded, no templating)
- **Images**: Add images to `img/` folder and reference with relative paths
- **Icons**: Font Awesome 5.10.0 class names (e.g., `fa fa-fire`, `fa fa-bars`)

## Common Patterns

### Data-Attribute Driven Behavior
The codebase uses `data-*` attributes to trigger jQuery behaviors without writing code:
- `data-toggle="counter-up"` - Activates CounterUp animation on number elements
- `data-src="[YOUTUBE_URL]"` on `.btn-play` - Sets video source for modal playback
- `data-wow-delay="0.1s"` on `.wow` elements - Controls scroll animation timing

### Responsive Design
Bootstrap grid system used throughout:
- `.col-lg-*` (≥992px), `.col-sm-*` (≥576px) for layout
- `.d-sm-none`, `.d-lg-block` for visibility control
- Navbar collapses to hamburger menu on mobile (no custom breakpoint)

### Animation Patterns
1. **CSS Animations**: Applied via Animate.css classes + WOW.js trigger
   - Example: `class="wow fadeInUp" data-wow-delay="0.1s"`
2. **jQuery Animations**: 
   - Navbar sticky class: `addClass()` / `removeClass()`
   - Back-to-top: `fadeIn()` / `fadeOut()`
   - Scroll animation: `.animate({scrollTop: 0}, 1500, 'easeInOutExpo')`

## Integration Points

### Third-Party Services
- **WhatsApp Booking**: CTA buttons link to `https://wa.me/254700000000` (update phone number as needed)
- **Bootstrap CDN**: Fallback to local `bootstrap.min.css` if needed
- **Google Fonts**: No fallback; ensure network access or preload fonts locally

### File Dependencies
- All HTML pages depend on:
  - `css/bootstrap.min.css` (required before style.css)
  - `css/style.css`
  - `js/main.js` (loaded at end of body)
  - jQuery (loaded via CDN in HTML head)
- Sidebar/utility JS loaded via `lib/` folder references (order matters for Owl, WOW, Tempusdominus)

## Notes for AI Agents

- **No templating**: All content is hardcoded HTML; changes require direct HTML edits
- **jQuery-dependent**: All JavaScript functionality relies on jQuery; avoid replacing with vanilla JS without careful testing
- **Minified assets**: `bootstrap.min.css` and library `.min.js` files are production-ready; edit source SCSS if modifying Bootstrap
- **Mobile-first approach**: Responsive design requires testing at 576px, 768px, 992px breakpoints
- **Accessibility**: Uses semantic HTML and ARIA attributes (e.g., `aria-expanded` on dropdowns)
