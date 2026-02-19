---
name: impreza-wpbakery-dev
description: "Use this skill for WordPress development with Impreza theme and WPBakery Page Builder. Triggers include: converting designs (described, visual, or Figma) to WordPress/Impreza code, creating WPBakery shortcodes, building Impreza pages, implementing responsive layouts, customizing Impreza elements, or any WordPress development task using the Impreza theme with WPBakery. Essential for producing copy-paste ready code that works seamlessly with Impreza theme structure."
license: MIT
---

# WordPress Development: Impreza Theme + WPBakery Page Builder

## Overview

This skill enables you to transform designs into production-ready WordPress code using the Impreza theme (by UpSolution) and WPBakery Page Builder. Impreza is a multipurpose WordPress theme with a customized WPBakery implementation, offering 63+ content elements, Live Builder, and extensive WooCommerce integration.

**Current Versions (as of 2026):**
- Impreza Theme: 8.43.1 (February 2, 2026)
- WPBakery: 8.7.2 (October 27, 2025)
- PHP: 8.3 fully supported
- WordPress: 6.6+ required

## Quick Reference

| Task | Approach |
|------|----------|
| Design → Code | Use shortcode syntax with Impreza elements |
| Responsive Layout | Use Design settings with device-specific controls |
| Custom Styling | Combine Design settings + Custom CSS classes |
| Dynamic Content | Use ACF integration + Grid Layouts |
| Performance | Enable "Disable extra features of WPBakery" option |

---

## Architecture & Dual Builder System

### Live Builder (Recommended)
Impreza's native visual editor with real-time WYSIWYG editing:
- **Activation**: Theme Options > Advanced > Theme Modules
- **Features**: Section Templates, Favorite Sections, drag-and-drop interface
- **Performance**: No frontend CSS/JS overhead when element not used
- **Interchangeable**: Full compatibility with WPBakery-created content

### WPBakery Page Builder
Bundled, customized version optimized for Impreza:
- **Backend Editor**: Schematic layout view for content-rich pages
- **Frontend Editor**: Classic WYSIWYG interface
- **Modifications**: Impreza adds custom options, disables non-compatible features
- **Classic Mode**: Direct shortcode editing

**CRITICAL**: Both builders are fully interchangeable - pages created in one can be edited in the other.

---

## Core Structure: Rows, Columns & Sections

### Row/Section Element (`vc_row`)

The foundational container for all layouts.

**Basic Syntax:**
```
[vc_row]
  [vc_column width="1/1"]
    <!-- Content here -->
  [/vc_column]
[/vc_row]
```

**Full-Width Section:**
```
[vc_row el_class="separate-section" full_width="stretch_row"]
  [vc_column]
    <!-- Full-width content (Revolution Slider, Google Maps, etc.) -->
  [/vc_column]
[/vc_row]
```

**Common Row Parameters:**
- `gap` - Column spacing: `0px`, `10px`, `20px`, `30px`, `40px`, `60px`
- `columns_type` - Layout: `default`, `boxes` (with background), `small` (reduced padding)
- `height` - Row height: `default`, `auto`, `small`, `medium`, `large`, `huge`, `full` (100vh)
- `valign` - Vertical alignment: `top`, `middle`, `bottom`
- `content_placement` - Content alignment: `top`, `middle`, `bottom`
- `color_scheme` - Color scheme: `default`, `alternate`, `primary`, `secondary`, `custom`
- `bg_color` - Background color (hex or color name)
- `bg_image` - Background image URL
- `bg_size` - Background size: `cover`, `contain`, `initial`
- `bg_repeat` - Background repeat: `repeat`, `no-repeat`, `repeat-x`, `repeat-y`
- `bg_attachment` - Background attachment: `scroll`, `fixed` (parallax base)
- `parallax` - Enable parallax: `vertical`, `horizontal`, `still`, `fixed`
- `parallax_speed` - Parallax speed factor: `0.1` to `2.0` (default `1`)
- `parallax_reverse` - Reverse parallax direction: `yes`, `no`

**Advanced Row Features:**
```
[vc_row 
  gap="30px" 
  height="large" 
  valign="middle" 
  color_scheme="alternate"
  bg_image="https://example.com/bg.jpg"
  bg_size="cover"
  parallax="vertical"
  parallax_speed="0.5"
  css=".vc_custom_xxxxx{padding-top:80px;padding-bottom:80px;}"
]
  [vc_column width="1/2"]
    <!-- Left column -->
  [/vc_column]
  [vc_column width="1/2"]
    <!-- Right column -->
  [/vc_column]
[/vc_row]
```

### Column Layouts (`vc_column`)

**Standard Grid System:**
- `1/1` - Full width (100%)
- `1/2` - Half width (50%)
- `1/3`, `2/3` - Third layouts
- `1/4`, `3/4` - Quarter layouts
- `1/5`, `2/5`, `3/5`, `4/5` - Fifth layouts
- `1/6`, `5/6` - Sixth layouts

**Column Parameters:**
- `width` - Column width (see grid system above)
- `offset` - Left offset: `vc_col-sm-offset-1` through `vc_col-sm-offset-11`
- `align` - Text alignment: `left`, `center`, `right`
- `valign` - Vertical alignment: `top`, `middle`, `bottom`
- `bg_color` - Column background color
- `text_color` - Text color scheme: `primary`, `secondary`, `custom`

**Responsive Column Example:**
```
[vc_column width="1/3" width_md="1/2" width_sm="1/1"]
  <!-- Desktop: 33.33%, Tablet: 50%, Mobile: 100% -->
[/vc_column]
```

### Design Settings (Universal)

All Impreza elements support unified Design settings:

**Spacing:**
- `padding` - Internal spacing (top right bottom left)
- `margin` - External spacing (top right bottom left)
- Syntax: `10px 20px 10px 20px` or CSS calc/vars: `calc(var(--base-padding) * 2)`

**Colors & Backgrounds:**
- `bg_color` - Background color
- `bg_image` - Background image URL
- `text_color` - Text color
- `border_color` - Border color
- `border_radius` - Border radius: `0px` to `100px`

**Visibility:**
- `hide_on_desktop` - Hide on desktop: `yes`, `no`
- `hide_on_laptop` - Hide on laptops: `yes`, `no`
- `hide_on_tablet` - Hide on tablets: `yes`, `no`
- `hide_on_mobile` - Hide on mobiles: `yes`, `no`

**Custom Classes & IDs:**
- `el_class` - Custom CSS class
- `el_id` - Custom HTML ID

**Device-Specific Design:**
```
<!-- Mobile-only padding override -->
[us_hwrapper 
  padding="40px" 
  padding_mobiles="20px"
]
  <!-- Content -->
[/us_hwrapper]
```

---

## Impreza Content Elements (63+ Available)

### Text & Typography

#### Heading (`us_heading`)
```
[us_heading 
  tag="h2"
  title="Your Heading Text"
  size="2rem"
  align="center"
  color="primary"
  font_weight="700"
]
```

**Parameters:**
- `tag` - HTML tag: `h1`, `h2`, `h3`, `h4`, `h5`, `h6`, `p`, `div`
- `title` - Heading text
- `size` - Font size (CSS units): `1.5rem`, `32px`, `clamp(1.5rem, 4vw, 3rem)`
- `align` - Alignment: `left`, `center`, `right`
- `color` - Color: `primary`, `secondary`, `custom`, hex color
- `font_weight` - Weight: `300`, `400`, `600`, `700`, `900`
- `transform` - Text transform: `none`, `uppercase`, `lowercase`, `capitalize`
- `icon` - Icon name (Font Awesome): `fas|star`, `far|heart`

#### Text (`us_text`)
```
[us_text text="Your paragraph content here" size="1rem"]
```

#### Message Box (`us_message`)
```
[us_message 
  color="primary"
  icon="fas|info-circle"
  closing="1"
]
  Important information for users.
[/us_message]
```

**Message Types:**
- `color` - `success` (green), `attention` (yellow), `error` (red), `info` (blue)

### Buttons & CTAs

#### Button (`us_btn`)
```
[us_btn 
  text="Learn More"
  link="url:https%3A%2F%2Fexample.com|title:Learn%20More|target:_blank"
  style="raised"
  color="primary"
  size="medium"
  icon="fas|arrow-right"
  iconpos="right"
]
```

**Button Parameters:**
- `text` - Button label
- `link` - URL (encoded): `url:https%3A%2F%2Fexample.com|title:Title|target:_blank`
- `style` - Style: `raised`, `flat`, `outlined`
- `color` - Color: `primary`, `secondary`, `light`, `dark`, `custom`
- `size` - Size: `small`, `medium`, `large`
- `icon` - Icon: `fas|arrow-right`, `far|heart`
- `iconpos` - Icon position: `left`, `right`
- `align` - Alignment: `left`, `center`, `right`

#### Call to Action (`us_cta`)
```
[us_cta 
  title="Ready to Get Started?"
  message="Join thousands of satisfied customers today."
  btn_label="Sign Up Now"
  btn_link="url:https%3A%2F%2Fexample.com%2Fsignup"
  btn_style="raised"
  color_bg="primary"
]
```

### Images & Media

#### Single Image (`us_image`)
```
[us_image 
  image="12345"
  size="full"
  align="center"
  lightbox="1"
  has_ratio="1"
  ratio="16x9"
]
```

**Parameters:**
- `image` - Image ID or URL
- `size` - WordPress size: `thumbnail`, `medium`, `large`, `full`
- `align` - Alignment: `left`, `center`, `right`
- `lightbox` - Enable lightbox: `1`, `0`
- `ratio` - Aspect ratio: `1x1`, `4x3`, `16x9`, `21x9`, `2x3`, `3x2`
- `has_ratio` - Force aspect ratio: `1`, `0`

#### Gallery (`us_gallery`)
```
[us_gallery 
  ids="123,456,789"
  columns="3"
  gap="20px"
  type="masonry"
  lightbox="1"
]
```

**Gallery Types:**
- `type` - `default`, `masonry`, `carousel`, `slider`

#### Image Slider (`us_image_slider`)
```
[us_image_slider 
  ids="123,456,789"
  arrows="1"
  nav="dots"
  autoplay="1"
  autoplay_period="5"
  fullscreen="1"
  ratio="16x9"
]
```

#### Video (`vc_video`)
```
[vc_video 
  link="https://www.youtube.com/watch?v=xxxxx"
  el_aspect="16-9"
]
```

### Interactive Elements

#### Accordion (`us_accordion`)
```
[us_accordion]
  [us_accordion_item 
    title="First Section"
    active="1"
  ]
    Content of first section.
  [/us_accordion_item]
  [us_accordion_item title="Second Section"]
    Content of second section.
  [/us_accordion_item]
[/us_accordion]
```

**Parameters:**
- `active` - Initially open: `1` (first item), `0` (none)
- `title` - Section title
- `icon` - Custom icon

#### Tabs (`us_tabs`)
```
[us_tabs 
  layout="default"
  align="center"
]
  [us_tab title="Tab 1" active="1"]
    First tab content.
  [/us_tab]
  [us_tab title="Tab 2"]
    Second tab content.
  [/us_tab]
[/us_tabs]
```

**Tab Layouts:**
- `layout` - `default`, `modern`, `trendy`, `timeline`

#### Popup (`us_popup`)
```
[us_popup 
  show_on="click"
  trigger_id="open-popup-btn"
]
  Popup content goes here.
[/us_popup]
```

**Popup Triggers:**
- `show_on` - `load`, `click`, `selector`
- `trigger_id` - Element ID to trigger popup

### Counters & Progress

#### Counter (`us_counter`)
```
[us_counter 
  initial="0"
  target="1500"
  prefix="$"
  suffix="+"
  duration="2"
  color="primary"
  size="3rem"
]
```

#### Progress Bar (`us_progbar`)
```
[us_progbar 
  count="75"
  title="WordPress Development"
  style="thin"
  color="primary"
]
```

### Icons & Iconbox

#### Single Icon (`us_icon`)
```
[us_icon 
  icon="fas|rocket"
  size="3rem"
  color="primary"
  link="url:https%3A%2F%2Fexample.com"
]
```

#### Iconbox (`us_iconbox`)
```
[us_iconbox 
  icon="fas|check-circle"
  title="Feature Title"
  style="default"
  iconpos="top"
  img="12345"
]
  Feature description text goes here.
[/us_iconbox]
```

**Iconbox Styles:**
- `style` - `default`, `circle`, `outlined`
- `iconpos` - `top`, `left`
- `color` - `primary`, `secondary`, `custom`

### Social Links

```
[us_socials 
  items="%5B%7B%22type%22%3A%22facebook%22%2C%22url%22%3A%22https%3A%2F%2Ffacebook.com%2Fyourpage%22%7D%2C%7B%22type%22%3A%22twitter%22%2C%22url%22%3A%22https%3A%2F%2Ftwitter.com%2Fyouraccount%22%7D%5D"
  style="colored"
  size="1.5rem"
]
```

**Available Networks:**
facebook, twitter, instagram, linkedin, youtube, pinterest, tiktok, discord, telegram, whatsapp, email

### Contact & Forms

#### Contact Form (`us_cform`)
```
[us_cform 
  receiver_email="info@example.com"
  fields="%5B%7B%22type%22%3A%22text%22%2C%22label%22%3A%22Name%22%2C%22required%22%3A%221%22%7D%2C%7B%22type%22%3A%22email%22%2C%22label%22%3A%22Email%22%2C%22required%22%3A%221%22%7D%2C%7B%22type%22%3A%22textarea%22%2C%22label%22%3A%22Message%22%2C%22required%22%3A%221%22%7D%5D"
  button_text="Send Message"
]
```

**Field Types:**
- `text` - Single-line text
- `email` - Email validation
- `textarea` - Multi-line text
- `select` - Dropdown
- `checkbox` - Checkbox
- `radio` - Radio buttons

**Contact Form 7 Integration:**
```
[contact-form-7 id="1234"]
```

#### Google Maps (`us_gmaps`)
```
[us_gmaps 
  address="1600 Amphitheatre Parkway, Mountain View, CA"
  latitude="37.4220"
  longitude="-122.0841"
  zoom="15"
  height="450px"
  marker="1"
]
```

### Testimonials

```
[us_testimonial 
  author="John Doe"
  company="Acme Corp"
  rating="5"
  img="12345"
]
  "Amazing product! Highly recommend to anyone looking for quality service."
[/us_testimonial]
```

### Person Card (`us_person`)
```
[us_person 
  name="Jane Smith"
  role="CEO & Founder"
  image="12345"
  email="jane@example.com"
  phone="+1-555-0123"
  socials="%5B%7B%22type%22%3A%22linkedin%22%2C%22url%22%3A%22https%3A%2F%2Flinkedin.com%2Fin%2Fjanesmith%22%7D%5D"
]
  Short bio about the person.
[/us_person]
```

### Separators & Spacers

#### Separator (`us_separator`)
```
[us_separator 
  type="default"
  size="medium"
  icon="fas|star"
]
```

**Separator Types:**
- `type` - `default`, `fullwidth`, `short`, `invisible`
- `size` - `small`, `medium`, `large`, `huge`

#### Vertical Wrapper (`us_hwrapper`)
Horizontal container with vertical alignment control:
```
[us_hwrapper 
  valign="middle"
  wrap="1"
]
  <!-- Inline elements with vertical centering -->
[/us_hwrapper]
```

#### Vertical Wrapper (`us_vwrapper`)
Vertical stacking container:
```
[us_vwrapper]
  <!-- Stacked elements -->
[/us_vwrapper]
```

---

## Dynamic Content & Grid Layouts

### Post Grid (`us_grid`)

Display posts, custom post types, or WooCommerce products in customizable grids.

**Basic Post Grid:**
```
[us_grid 
  post_type="post"
  items_qty="9"
  columns="3"
  items_gap="30px"
  pagination="ajax"
  filter="1"
  filter_taxonomy="category"
]
```

**Parameters:**
- `post_type` - `post`, `page`, `product`, `portfolio`, `us_testimonial`, or custom post type
- `items_qty` - Number of items to show
- `columns` - Grid columns: `1`, `2`, `3`, `4`, `5`, `6`
- `items_gap` - Gap between items: `0px` to `60px`
- `type` - Grid type: `grid`, `masonry`, `carousel`
- `pagination` - Pagination: `regular`, `ajax`, `load_more`, `infinite`
- `filter` - Enable filter: `1`, `0`
- `filter_taxonomy` - Filter by: `category`, `post_tag`, `product_cat`, custom taxonomy
- `orderby` - Order by: `date`, `title`, `rand`, `menu_order`, `modified`
- `order` - Sort direction: `DESC`, `ASC`

**Grid with Custom Query:**
```
[us_grid 
  post_type="post"
  taxonomy_category="featured,news"
  items_qty="6"
  columns="3"
  img_size="large"
  title_size="1.5rem"
  meta="date,author,comments"
  excerpt_length="20"
]
```

**WooCommerce Product Grid:**
```
[us_grid 
  post_type="product"
  items_qty="12"
  columns="4"
  show_add_to_cart="1"
  show_price="1"
  filter="1"
  filter_taxonomy="product_cat"
  orderby="popularity"
]
```

### Grid Layouts (Templates)

Create reusable grid item templates at **Templates > Grid Layouts**.

**Using Custom Layout:**
```
[us_grid 
  post_type="post"
  items_layout="12345"
  items_qty="9"
  columns="3"
]
```

### Post List (`us_post_list`)

Alternative to grid with different styling options:
```
[us_post_list 
  query_args="post_type=post&posts_per_page=5&category_name=news"
  show_thumbnails="1"
  show_date="1"
  show_author="1"
]
```

### User List (`us_user_list`)

Display team members or users:
```
[us_user_list 
  role="author"
  items_qty="8"
  columns="4"
  show_avatar="1"
  show_bio="1"
]
```

---

## WooCommerce Integration

### Product Elements

#### Single Product (`us_single_product`)
```
[us_single_product 
  product_id="123"
  show_title="1"
  show_price="1"
  show_add_to_cart="1"
  show_rating="1"
]
```

#### Products Carousel
```
[us_grid 
  post_type="product"
  type="carousel"
  items_qty="8"
  columns="4"
  arrows="1"
  dots="1"
  autoplay="1"
]
```

#### Add to Cart Button
```
[us_add_to_cart 
  product_id="123"
  style="raised"
  color="primary"
]
```

### WooCommerce Pages

Impreza allows custom WooCommerce page templates via **Grid Layouts**:

- **Product Page**: Customize with Page Template Builder
- **Cart Page**: Custom layout via Templates
- **Checkout Page**: Custom design options
- **My Account**: Full customization support
- **Thank You Page**: Custom success page

---

## Advanced Features

### Reusable Blocks (`us_page_block`)

Create reusable content blocks at **Templates > Reusable Blocks**.

**Usage:**
```
[us_page_block id="1234"]
```

**Exclude Rows/Columns:**
```
[us_page_block 
  id="1234"
  exclude_rows_columns="inside"
]
```

Options:
- `none` - Keep all structure
- `inside` - Remove rows/columns inside block
- `around` - Remove rows/columns around block

**Use in Menus:**
Add reusable blocks as menu items for mega menus or custom navigation.

### Custom HTML & Code

#### Custom HTML Element
```
[us_html]
<div class="custom-component">
  <!-- Your custom HTML -->
</div>
[/us_html]
```

#### JavaScript Execution
```
[us_html]
<script>
// Your JavaScript code
jQuery(document).ready(function($) {
  // Initialize custom functionality
});
</script>
[/us_html]
```

### ACF (Advanced Custom Fields) Integration

Impreza natively supports ACF custom fields in:
- Grid Layouts
- Dynamic Values
- Page Templates

**Display ACF Field:**
```
[us_text 
  text="{{post:acf_field_name}}"
]
```

**ACF Repeater in Grid:**
Use Grid Layout Builder to display ACF repeater fields in custom layouts.

### Display Logic

Show/hide elements based on conditions:

**Logged-in Users Only:**
```
[us_iconbox 
  title="Member Dashboard"
  show_if="{{user:logged_in}}"
]
  Exclusive content for members.
[/us_iconbox]
```

**Device-Specific:**
```
[us_image 
  image="12345"
  hide_on_mobile="yes"
]
```

**Conditional Display:**
- User logged in/out
- Page types (archive, single, front page)
- Date ranges
- User roles
- Custom conditions

---

## Responsive Design Best Practices

### Device Breakpoints

Impreza uses these breakpoints:
- **Desktop**: 1280px+
- **Laptop**: 1024px - 1279px
- **Tablet**: 768px - 1023px
- **Mobile**: < 768px

### Responsive Strategies

#### 1. Column Width Adjustments
```
[vc_row]
  [vc_column width="1/3" width_md="1/2" width_sm="1/1"]
    <!-- Desktop: 33%, Tablet: 50%, Mobile: 100% -->
  [/vc_column]
  [vc_column width="1/3" width_md="1/2" width_sm="1/1"]
    <!-- Responsive columns -->
  [/vc_column]
  [vc_column width="1/3" width_md="1/2" width_sm="1/1"]
    <!-- Auto-stack on mobile -->
  [/vc_column]
[/vc_row]
```

#### 2. Device-Specific Padding/Margin
```
[us_hwrapper 
  padding="60px"
  padding_tablets="40px"
  padding_mobiles="20px"
]
  <!-- Content with responsive spacing -->
[/us_hwrapper]
```

#### 3. Hide on Devices
```
<!-- Desktop-only image -->
[us_image 
  image="12345"
  hide_on_tablet="yes"
  hide_on_mobile="yes"
]

<!-- Mobile-only CTA -->
[us_btn 
  text="Call Now"
  hide_on_desktop="yes"
  hide_on_laptop="yes"
]
```

#### 4. Responsive Typography
```
[us_heading 
  title="Responsive Heading"
  size="clamp(1.5rem, 4vw, 3rem)"
]
```

Use CSS clamp() for fluid typography:
- `clamp(min, preferred, max)`
- Example: `clamp(1.5rem, 4vw, 3rem)` scales between 1.5rem and 3rem

#### 5. Image Aspect Ratios
```
[us_image 
  image="12345"
  has_ratio="1"
  ratio="16x9"
  ratio_tablets="4x3"
  ratio_mobiles="1x1"
]
```

---

## Performance Optimization

### Essential Settings

Navigate to **Impreza > Theme Options > Advanced Settings > Website Performance**:

#### 1. Disable Extra WPBakery Features
✅ **ALWAYS ENABLE** (unless you specifically need Grid Builder)

```
Theme Options > Advanced Settings > Website Performance
☑ Disable extra features of WPBakery Page Builder
```

This prevents WPBakery from loading heavy CSS/JS on frontend, improving load times significantly.

#### 2. Assets Optimization
```
Theme Options > Advanced Settings > Website Performance
☑ Optimize CSS Output
☑ Optimize JavaScript Output
☑ Lazy Load Images
☑ Minify HTML Output
```

#### 3. Icon Library
Load only icons actually used:
```
Theme Options > Advanced Settings > Icon Sets
☑ Load only used icons (automatic detection)
```

#### 4. Google Fonts
Avoid loading unused fonts:
```
Theme Options > Typography
- Set "Regular Text" to Arial (web-safe)
- Set headings to system fonts or minimal Google Fonts
- Or upload custom WOFF2 fonts locally
```

### Code-Level Optimization

#### Use Inline Critical CSS
```
<!-- In theme functions.php or child theme -->
<?php
add_action('wp_head', 'custom_critical_css', 1);
function custom_critical_css() {
    echo '<style>
        /* Critical above-the-fold CSS */
        .header { /* styles */ }
        .hero { /* styles */ }
    </style>';
}
?>
```

#### Defer Non-Critical CSS
```
<!-- Use Custom Code area in Impreza -->
<link rel="preload" href="styles.css" as="style" onload="this.onload=null;this.rel='stylesheet'">
```

#### Lazy Load Background Images
```
[vc_row 
  bg_image=""
  el_class="lazy-bg"
  css=".lazy-bg{background-image:none;}"
]
```

Then use JavaScript to load on scroll.

### Image Optimization

- **Use WebP format** (with JPG fallback)
- **Compress before upload** (TinyPNG, Squoosh)
- **Use appropriate sizes**:
  - Full-width hero: 1920px width
  - Grid items: 800px width
  - Thumbnails: 400px width
- **Enable lazy loading**: Impreza has built-in lazy load
- **Use CDN**: Cloudflare, CloudFront, or similar

### Caching Strategy

**Recommended Plugins:**
1. **WP Rocket** (premium) - most comprehensive
2. **Hummingbird** - WPMU DEV (works great with Impreza)
3. **WP Super Cache** - free alternative

**Settings:**
- Page caching: ✅ Enable
- Object caching: ✅ Enable
- Database optimization: ✅ Enable
- GZIP compression: ✅ Enable
- Browser caching: ✅ Enable
- Minification: ✅ Enable (HTML, CSS, JS)
- Lazy loading: ✅ Enable

---

## Design-to-Code Workflow

### From Visual Design

#### Step 1: Analyze Layout Structure
Identify:
- Number of sections/rows
- Column layouts per row
- Element types (heading, text, button, image, etc.)
- Spacing and alignment
- Color scheme
- Typography (sizes, weights)

#### Step 2: Create Row Structure
```
[vc_row gap="30px" height="medium"]
  [vc_column width="1/2"]
    <!-- Left content -->
  [/vc_column]
  [vc_column width="1/2"]
    <!-- Right content -->
  [/vc_column]
[/vc_row]
```

#### Step 3: Add Content Elements
Map design elements to Impreza shortcodes:
- Headlines → `[us_heading]`
- Paragraphs → `[us_text]`
- Buttons → `[us_btn]`
- Images → `[us_image]`
- Icons → `[us_icon]` or `[us_iconbox]`

#### Step 4: Apply Styling
Use Design settings for:
- Colors: `color="primary"` or hex values
- Spacing: `padding="40px"`, `margin="20px"`
- Backgrounds: `bg_color="#f5f5f5"`
- Custom classes: `el_class="custom-section"`

#### Step 5: Make Responsive
Add device-specific parameters:
- Column widths: `width_md="1/2"`, `width_sm="1/1"`
- Spacing: `padding_tablets="30px"`, `padding_mobiles="20px"`
- Visibility: `hide_on_mobile="yes"`

### From Figma Design

#### Step 1: Export Design Specs
- Extract colors (hex values)
- Note font sizes and weights
- Measure spacing (padding, margins)
- Identify breakpoints
- Export images in optimal sizes

#### Step 2: Map Figma Components to Impreza
| Figma Element | Impreza Shortcode |
|---------------|-------------------|
| Frame/Section | `[vc_row]` |
| Auto Layout | `[vc_column]` with grid |
| Text heading | `[us_heading]` |
| Text body | `[us_text]` |
| Button | `[us_btn]` |
| Image | `[us_image]` |
| Icon | `[us_icon]` |
| Card | `[us_iconbox]` or custom with `[us_hwrapper]` |

#### Step 3: Implement Design System
Create reusable components:
- Define color palette in Theme Options
- Set up typography styles
- Create button presets
- Build section templates

#### Step 4: Build Shortcode
```
[vc_row 
  bg_color="#FFFFFF"
  padding="80px 0"
  padding_tablets="60px 0"
  padding_mobiles="40px 0"
]
  [vc_column width="1/1"]
    [us_heading 
      tag="h2"
      title="Features That Matter"
      size="2.5rem"
      size_tablets="2rem"
      size_mobiles="1.75rem"
      align="center"
      color="#1A1A1A"
      font_weight="700"
    ]
    [us_text 
      text="Discover powerful tools designed for success"
      size="1.125rem"
      align="center"
      color="#666666"
    ]
  [/vc_column]
[/vc_row]

[vc_row 
  gap="30px"
  padding="0 0 80px 0"
]
  [vc_column width="1/3" width_md="1/2" width_sm="1/1"]
    [us_iconbox 
      icon="fas|zap"
      title="Lightning Fast"
      style="circle"
      iconpos="top"
      color="primary"
    ]
      Optimized for speed and performance from day one.
    [/us_iconbox]
  [/vc_column]
  <!-- Repeat for other features -->
[/vc_row]
```

### From Written Description

#### Example Input:
"Create a hero section with a large heading, subheading, two CTAs side by side, and a background image with overlay"

#### Output Code:
```
[vc_row 
  height="large"
  valign="middle"
  bg_image="https://example.com/hero-bg.jpg"
  bg_size="cover"
  bg_attachment="fixed"
  color_scheme="dark"
  parallax="vertical"
  parallax_speed="0.3"
]
  [vc_column width="1/1" align="center"]
    [us_heading 
      tag="h1"
      title="Transform Your Business Today"
      size="3.5rem"
      size_tablets="2.5rem"
      size_mobiles="2rem"
      color="#FFFFFF"
      font_weight="700"
    ]
    [us_text 
      text="Join thousands of companies already succeeding with our platform"
      size="1.25rem"
      color="#FFFFFF"
      margin="0 0 30px 0"
    ]
    [us_hwrapper 
      valign="middle"
      wrap="1"
    ]
      [us_btn 
        text="Get Started Free"
        style="raised"
        color="primary"
        size="large"
        el_class="hero-btn"
      ]
      [us_btn 
        text="Watch Demo"
        style="outlined"
        color="light"
        size="large"
        icon="fas|play"
        el_class="hero-btn"
        margin="0 0 0 20px"
      ]
    [/us_hwrapper]
  [/vc_column]
[/vc_row]
```

---

## Common Patterns & Templates

### Hero Section (Full Height with CTA)
```
[vc_row 
  height="full"
  valign="middle"
  bg_image="URL_HERE"
  bg_size="cover"
  color_scheme="dark"
]
  [vc_column width="1/1" align="center"]
    [us_heading 
      tag="h1"
      title="Your Main Headline"
      size="clamp(2rem, 5vw, 4rem)"
      color="#FFFFFF"
    ]
    [us_text 
      text="Compelling subheadline goes here"
      size="1.25rem"
      color="#FFFFFF"
    ]
    [us_btn 
      text="Call to Action"
      style="raised"
      color="primary"
      size="large"
    ]
  [/vc_column]
[/vc_row]
```

### Feature Grid (3 Columns)
```
[vc_row gap="30px"]
  [vc_column width="1/3" width_md="1/2" width_sm="1/1"]
    [us_iconbox 
      icon="fas|rocket"
      title="Fast Performance"
      iconpos="top"
    ]
      Lightning-fast load times guaranteed.
    [/us_iconbox]
  [/vc_column]
  [vc_column width="1/3" width_md="1/2" width_sm="1/1"]
    [us_iconbox 
      icon="fas|shield-alt"
      title="Secure Platform"
      iconpos="top"
    ]
      Enterprise-grade security measures.
    [/us_iconbox]
  [/vc_column]
  [vc_column width="1/3" width_md="1/2" width_sm="1/1"]
    [us_iconbox 
      icon="fas|headset"
      title="24/7 Support"
      iconpos="top"
    ]
      Always here when you need us.
    [/us_iconbox]
  [/vc_column]
[/vc_row]
```

### Testimonial Section
```
[vc_row 
  bg_color="#F8F9FA"
  padding="80px 0"
]
  [vc_column width="1/1"]
    [us_heading 
      title="What Our Clients Say"
      align="center"
      size="2.5rem"
    ]
  [/vc_column]
[/vc_row]
[vc_row 
  gap="30px"
  bg_color="#F8F9FA"
  padding="0 0 80px 0"
]
  [vc_column width="1/3" width_md="1/1"]
    [us_testimonial 
      author="John Doe"
      company="Acme Corp"
      rating="5"
    ]
      "Excellent service and outstanding results!"
    [/us_testimonial]
  [/vc_column]
  <!-- Repeat for more testimonials -->
[/vc_row]
```

### Pricing Table (3 Tiers)
```
[vc_row gap="30px"]
  [vc_column width="1/3" width_md="1/1"]
    [us_pricing_table 
      title="Starter"
      price="$29"
      period="/month"
      features="10 Users|50GB Storage|Email Support"
      button_text="Get Started"
      button_link="url:signup"
    ]
  [/vc_column]
  [vc_column width="1/3" width_md="1/1"]
    [us_pricing_table 
      title="Professional"
      price="$79"
      period="/month"
      featured="1"
      features="50 Users|500GB Storage|Priority Support|Advanced Analytics"
      button_text="Start Free Trial"
      button_link="url:trial"
    ]
  [/vc_column]
  [vc_column width="1/3" width_md="1/1"]
    [us_pricing_table 
      title="Enterprise"
      price="$199"
      period="/month"
      features="Unlimited Users|Unlimited Storage|24/7 Support|Custom Integration"
      button_text="Contact Sales"
      button_link="url:contact"
    ]
  [/vc_column]
[/vc_row]
```

### Image + Text Split (50/50)
```
[vc_row gap="60px" valign="middle"]
  [vc_column width="1/2" width_md="1/1"]
    [us_image 
      image="IMAGE_ID"
      size="full"
      ratio="16x9"
      has_ratio="1"
    ]
  [/vc_column]
  [vc_column width="1/2" width_md="1/1"]
    [us_heading 
      tag="h2"
      title="Why Choose Us"
      size="2.5rem"
    ]
    [us_text 
      text="We provide innovative solutions that drive real results for your business."
    ]
    [us_btn 
      text="Learn More"
      style="raised"
      color="primary"
    ]
  [/vc_column]
[/vc_row]
```

### Blog Post Grid
```
[us_grid 
  post_type="post"
  items_qty="9"
  columns="3"
  columns_tablets="2"
  columns_mobiles="1"
  items_gap="30px"
  img_size="large"
  title_size="1.5rem"
  excerpt_length="20"
  meta="date,author,comments"
  pagination="load_more"
  filter="1"
  filter_taxonomy="category"
]
```

### Contact Section with Form
```
[vc_row 
  gap="60px"
  padding="80px 0"
]
  [vc_column width="1/2" width_md="1/1"]
    [us_heading 
      title="Get in Touch"
      size="2.5rem"
    ]
    [us_text 
      text="Have questions? We'd love to hear from you."
    ]
    [us_iconbox 
      icon="fas|phone"
      title="+1 (555) 123-4567"
      iconpos="left"
    ]
    [/us_iconbox]
    [us_iconbox 
      icon="fas|envelope"
      title="info@example.com"
      iconpos="left"
    ]
    [/us_iconbox]
  [/vc_column]
  [vc_column width="1/2" width_md="1/1"]
    [us_cform 
      receiver_email="info@example.com"
      button_text="Send Message"
    ]
  [/vc_column]
[/vc_row]
```

---

## Troubleshooting

### Common Issues & Solutions

#### Issue: Shortcodes Visible on Frontend
**Cause**: Content not processed by WordPress
**Solution**:
```php
// Process shortcodes in custom areas
echo do_shortcode('[your_shortcode]');
```

#### Issue: Columns Not Responsive
**Cause**: Missing width parameters for devices
**Solution**: Always add device-specific widths:
```
[vc_column width="1/3" width_md="1/2" width_sm="1/1"]
```

#### Issue: Background Image Not Showing
**Cause**: Incorrect image URL or missing row height
**Solution**:
```
[vc_row 
  bg_image="https://full-url-here.jpg"
  bg_size="cover"
  height="medium"  <!-- Add explicit height -->
]
```

#### Issue: Parallax Not Working
**Cause**: Conflicting CSS or JavaScript
**Solution**:
1. Clear all caches
2. Disable conflicting plugins
3. Check `bg_attachment="scroll"` is not set
```
[vc_row 
  parallax="vertical"
  parallax_speed="0.5"
  bg_attachment=""  <!-- Leave empty for parallax -->
]
```

#### Issue: Icons Not Displaying
**Cause**: Icon library not loaded
**Solution**:
Check **Theme Options > Advanced Settings > Icon Sets**
```
☑ Font Awesome 5 Pro (included with Impreza)
```

#### Issue: Custom CSS Not Applying
**Cause**: Specificity issues or caching
**Solution**:
```css
/* Use !important sparingly */
.custom-class {
    color: #FF0000 !important;
}

/* Or increase specificity */
.vc_row .custom-class {
    color: #FF0000;
}
```

#### Issue: Form Submissions Not Sending
**Cause**: Email configuration
**Solution**:
1. Install WP Mail SMTP plugin
2. Configure SMTP settings
3. Test email delivery
4. Check spam folders

#### Issue: Slow Page Load
**Cause**: Unoptimized assets
**Solution**:
1. Enable **Disable extra features of WPBakery**
2. Use caching plugin (WP Rocket, Hummingbird)
3. Optimize images (WebP, compression)
4. Enable lazy loading
5. Minimize plugins

---

## Custom CSS Integration

### Adding Custom Styles

#### Global Custom CSS
Navigate to **Impreza > Theme Options > Custom CSS**:
```css
/* Custom button hover effect */
.us-btn-container .us-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 10px 20px rgba(0,0,0,0.1);
    transition: all 0.3s ease;
}

/* Custom heading underline */
.us-heading .us-heading-title::after {
    content: '';
    display: block;
    width: 60px;
    height: 3px;
    background: var(--color-primary);
    margin: 20px auto 0;
}

/* Responsive utilities */
@media (max-width: 767px) {
    .hide-mobile {
        display: none !important;
    }
}
```

#### Element-Specific CSS
Use `el_class` parameter:
```
[us_heading 
  title="Custom Styled Heading"
  el_class="custom-heading-style"
]
```

Then in Custom CSS:
```css
.custom-heading-style {
    background: linear-gradient(45deg, #FF6B6B, #4ECDC4);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
}
```

### CSS Variables (Custom Properties)

Impreza uses CSS variables for theming:
```css
:root {
    --color-primary: #1E88E5;
    --color-secondary: #FF6F00;
    --font-heading: 'Poppins', sans-serif;
    --font-body: 'Open Sans', sans-serif;
    --base-padding: 20px;
}

/* Use in elements */
.custom-section {
    padding: calc(var(--base-padding) * 2);
    color: var(--color-primary);
    font-family: var(--font-heading);
}
```

### Animation Classes
```css
/* Fade in on scroll */
@keyframes fadeInUp {
    from {
        opacity: 0;
        transform: translateY(30px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.fade-in-up {
    animation: fadeInUp 0.6s ease-out;
}

/* Pulse effect */
@keyframes pulse {
    0% { transform: scale(1); }
    50% { transform: scale(1.05); }
    100% { transform: scale(1); }
}

.pulse-effect {
    animation: pulse 2s infinite;
}
```

---

## JavaScript Integration

### Custom JavaScript

Add to **Impreza > Theme Options > Custom Code > Before </body>**:

```javascript
<script>
jQuery(document).ready(function($) {
    
    // Smooth scroll to anchor
    $('a[href^="#"]').on('click', function(e) {
        e.preventDefault();
        var target = $(this.getAttribute('href'));
        if(target.length) {
            $('html, body').stop().animate({
                scrollTop: target.offset().top - 100
            }, 1000);
        }
    });
    
    // Number counter animation
    $('.us_counter').each(function() {
        var $this = $(this);
        var countTo = $this.attr('data-count');
        $({ countNum: 0 }).animate({
            countNum: countTo
        }, {
            duration: 2000,
            easing: 'swing',
            step: function() {
                $this.text(Math.floor(this.countNum));
            },
            complete: function() {
                $this.text(this.countNum);
            }
        });
    });
    
    // Parallax mouse effect
    $('.parallax-mouse').on('mousemove', function(e) {
        var x = (e.pageX / $(window).width()) - 0.5;
        var y = (e.pageY / $(window).height()) - 0.5;
        $(this).find('.parallax-layer').css({
            'transform': 'translate(' + (x * 30) + 'px, ' + (y * 30) + 'px)'
        });
    });
    
});
</script>
```

### Intersection Observer (Scroll Animations)
```javascript
<script>
// Fade in elements on scroll
const observerOptions = {
    threshold: 0.1,
    rootMargin: '0px 0px -100px 0px'
};

const observer = new IntersectionObserver(function(entries) {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.classList.add('visible');
            observer.unobserve(entry.target);
        }
    });
}, observerOptions);

document.querySelectorAll('.animate-on-scroll').forEach(el => {
    observer.observe(el);
});
</script>

<style>
.animate-on-scroll {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.6s ease, transform 0.6s ease;
}
.animate-on-scroll.visible {
    opacity: 1;
    transform: translateY(0);
}
</style>
```

---

## Version Control & Deployment

### Export/Import Pages

#### Export Single Page:
1. Edit page in WPBakery Backend Editor
2. Click "Classic Mode" tab
3. Copy all shortcode content
4. Save to version control

#### Import Page:
1. Create new page
2. Switch to "Classic Mode"
3. Paste shortcode content
4. Update to Frontend/Backend editor
5. Publish

### Reusable Templates

Create at **Templates > Section Templates**:
- Save frequently used sections
- Export/import across sites
- Version control JSON exports

### Child Theme Development

Always use child theme for customizations:

**style.css:**
```css
/*
Theme Name: Impreza Child
Template: Impreza
Version: 1.0.0
*/
```

**functions.php:**
```php
<?php
add_action('wp_enqueue_scripts', 'impreza_child_enqueue_styles');
function impreza_child_enqueue_styles() {
    wp_enqueue_style('parent-style', get_template_directory_uri() . '/style.css');
    wp_enqueue_style('child-style',
        get_stylesheet_directory_uri() . '/style.css',
        array('parent-style'),
        wp_get_theme()->get('Version')
    );
}

// Custom shortcodes
add_shortcode('custom_element', 'custom_element_function');
function custom_element_function($atts) {
    $atts = shortcode_atts(array(
        'title' => 'Default Title',
        'color' => '#000000'
    ), $atts);
    
    return '<div class="custom-element" style="color:' . esc_attr($atts['color']) . '">' 
           . esc_html($atts['title']) 
           . '</div>';
}
?>
```

---

## Security Best Practices

### Sanitization & Escaping

Always sanitize user inputs:
```php
// Sanitize text input
$clean_text = sanitize_text_field($_POST['input']);

// Sanitize URL
$clean_url = esc_url($_POST['url']);

// Sanitize email
$clean_email = sanitize_email($_POST['email']);

// Escape output
echo esc_html($user_content);
echo esc_attr($attribute_value);
echo esc_url($url);
```

### Nonce Verification
```php
// Add nonce to form
wp_nonce_field('custom_form_action', 'custom_form_nonce');

// Verify nonce
if (!wp_verify_nonce($_POST['custom_form_nonce'], 'custom_form_action')) {
    wp_die('Security check failed');
}
```

### SQL Injection Prevention
```php
global $wpdb;

// WRONG
$results = $wpdb->get_results("SELECT * FROM table WHERE id = " . $_GET['id']);

// RIGHT
$results = $wpdb->get_results($wpdb->prepare(
    "SELECT * FROM table WHERE id = %d",
    $_GET['id']
));
```

---

## Accessibility (a11y) Guidelines

### ARIA Labels
```
[us_btn 
  text="Submit"
  aria_label="Submit contact form"
]

[us_icon 
  icon="fas|search"
  aria_label="Search icon"
]
```

### Keyboard Navigation
Ensure all interactive elements are keyboard accessible:
```css
.us-btn:focus,
.us-iconbox:focus {
    outline: 2px solid var(--color-primary);
    outline-offset: 2px;
}
```

### Color Contrast
Maintain WCAG AA standards (4.5:1 for normal text):
```css
/* Good contrast */
.text-primary {
    color: #1E88E5; /* on white background */
}

/* Check contrast ratios at: */
/* https://webaim.org/resources/contrastchecker/ */
```

### Alt Text for Images
```
[us_image 
  image="12345"
  alt="Descriptive alt text for screen readers"
]
```

### Semantic HTML
Use proper heading hierarchy:
```
[us_heading tag="h1" title="Main Page Title"]
[us_heading tag="h2" title="Section Title"]
[us_heading tag="h3" title="Subsection Title"]
```

---

## SEO Optimization

### Schema Markup

Impreza includes automatic Schema.org markup. Enhance with custom schemas:

```html
[us_html]
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "Your Business Name",
  "image": "https://example.com/logo.jpg",
  "@id": "https://example.com",
  "url": "https://example.com",
  "telephone": "+1-555-0123",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "123 Main St",
    "addressLocality": "City",
    "addressRegion": "State",
    "postalCode": "12345",
    "addressCountry": "US"
  }
}
</script>
[/us_html]
```

### Meta Tags

Set in **Impreza > Theme Options > SEO** or use Yoast SEO/Rank Math plugin.

### Heading Structure

Maintain proper hierarchy:
- One H1 per page (page title)
- H2 for main sections
- H3 for subsections
- Never skip levels

### Performance = SEO

- Page speed impacts rankings
- Use caching, optimization plugins
- Optimize images (WebP, lazy load)
- Minimize HTTP requests
- Enable GZIP compression

---

## Quick Tips & Tricks

### 1. Copy Sections from Demos
Visit Impreza demo sites → Right-click section → Inspect → Find `vc_row` → Copy entire shortcode → Paste in your page

### 2. Use Section Templates
Save commonly used sections to **Templates > Section Templates** → Reuse across pages

### 3. Global Color Palette
Define colors once in **Theme Options > Colors** → Use across all elements

### 4. Custom Fonts
Upload WOFF2 fonts at **Theme Options > Typography > Uploaded Fonts** → Faster than Google Fonts

### 5. Sticky Elements
```
[vc_column el_class="sticky-sidebar"]
  <!-- Sidebar content -->
[/vc_column]
```

CSS:
```css
@media (min-width: 1024px) {
    .sticky-sidebar {
        position: sticky;
        top: 100px;
    }
}
```

### 6. Custom Cursor
```css
body {
    cursor: url('cursor.png'), auto;
}
a:hover {
    cursor: url('pointer.png'), pointer;
}
```

### 7. Scroll Progress Bar
```javascript
<script>
window.addEventListener('scroll', function() {
    var winScroll = document.body.scrollTop || document.documentElement.scrollTop;
    var height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
    var scrolled = (winScroll / height) * 100;
    document.querySelector('.progress-bar').style.width = scrolled + "%";
});
</script>

<style>
.progress-container {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 3px;
    background: #f1f1f1;
    z-index: 9999;
}
.progress-bar {
    height: 3px;
    background: var(--color-primary);
    width: 0%;
}
</style>
```

### 8. Lazy Load Background Images
```
[vc_row 
  el_class="lazy-bg"
  data-bg="https://example.com/image.jpg"
]
```

JavaScript:
```javascript
document.addEventListener('DOMContentLoaded', function() {
    var lazyBgs = document.querySelectorAll('.lazy-bg');
    var observer = new IntersectionObserver(function(entries) {
        entries.forEach(function(entry) {
            if (entry.isIntersecting) {
                var bg = entry.target.dataset.bg;
                entry.target.style.backgroundImage = 'url(' + bg + ')';
                observer.unobserve(entry.target);
            }
        });
    });
    lazyBgs.forEach(function(bg) {
        observer.observe(bg);
    });
});
```

---

## Resources & Documentation

### Official Resources
- **Impreza Documentation**: https://help.us-themes.com/impreza/
- **WPBakery Knowledge Base**: https://kb.wpbakery.com/
- **Impreza Support**: https://support.us-themes.com/
- **Changelog**: https://help.us-themes.com/impreza/changelog/

### Recommended Plugins
- **WP Rocket** - Caching & performance
- **Smush** - Image optimization
- **Yoast SEO** / **Rank Math** - SEO optimization
- **WP Mail SMTP** - Email deliverability
- **UpdraftPlus** - Backups
- **Wordfence** - Security

### Learning Resources
- WordPress Codex: https://codex.wordpress.org/
- WPBakery Tutorials: https://wpbakery.com/features/
- Impreza Video Tutorials: Built into theme dashboard

### Community
- ThemeForest Comments: Product support & discussion
- WordPress.org Forums: General WordPress help
- Stack Overflow: Coding questions

---

## Best Practices Summary

### DO:
✅ Use Impreza's performance optimization settings
✅ Always create responsive layouts with device-specific settings
✅ Leverage built-in elements before custom code
✅ Use Live Builder for best performance
✅ Test on multiple devices and browsers
✅ Optimize images before upload
✅ Use caching plugins
✅ Create child theme for customizations
✅ Use section templates for reusable content
✅ Follow semantic HTML structure
✅ Implement proper heading hierarchy
✅ Add alt text to all images
✅ Sanitize all user inputs
✅ Use CSS variables for theming
✅ Document custom code

### DON'T:
❌ Load unnecessary Google Fonts
❌ Use inline styles excessively
❌ Forget device-specific responsive settings
❌ Skip image optimization
❌ Use too many heavy plugins
❌ Modify parent theme files directly
❌ Ignore caching configuration
❌ Overcomplicate layouts with excessive nesting
❌ Use outdated PHP functions
❌ Hardcode values that should be dynamic
❌ Ignore accessibility guidelines
❌ Skip security best practices
❌ Forget to test thoroughly before launch

---

## Conclusion

This skill equips you to transform any design—whether described, visual, or from Figma—into production-ready WordPress code using the Impreza theme and WPBakery Page Builder. Follow the patterns, use the comprehensive element library, optimize for performance, and always prioritize responsive design and accessibility.

**Remember**: Impreza's strength lies in its flexibility and optimization. Use the Live Builder for the best performance, leverage built-in elements, and only use custom code when absolutely necessary.

---

## Version History

- **v1.0.0** (2026-02-19): Initial comprehensive skill release
  - Complete element reference
  - Responsive design patterns
  - Performance optimization
  - Design-to-code workflows
  - Best practices & security
  - 63+ Impreza elements documented
  - WPBakery 8.7.2 compatibility
  - Impreza 8.43.1 compatibility
