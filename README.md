# Dev Portfolio — WordPress Theme

A minimal, dark-themed developer portfolio WordPress theme built with **ACF (Free)** and **Custom Post Types**.

## Requirements

- WordPress 6.0+
- [Advanced Custom Fields (Free)](https://wordpress.org/plugins/advanced-custom-fields/) plugin
- (Optional) Contact Form 7 for the contact page

## Quick Setup

### 1. Install Theme
Upload the `portfolio-theme` folder to `wp-content/themes/` and activate it.

### 2. Install ACF
Install and activate the free **Advanced Custom Fields** plugin from Plugins → Add New.

### 3. Create Pages
Create these pages in WordPress:
| Page          | Page Template        |
|---------------|----------------------|
| **Home**      | (set as Front Page)  |
| **About**     | About Page           |
| **Contact**   | Contact Page         |

Then go to **Settings → Reading** and set "Home" as your static front page.

### 4. Set Up Navigation Menu
Go to **Appearance → Menus** and create a Primary Menu with:
- Home (link to front page)
- About (link to About page)
- Works (link to Works archive: `/works/`)
- Skills (link to Skills archive: `/skills/`)
- Certificates (link to Certificates archive: `/certificates/`)
- Contact (link to Contact page)

Assign it to the **Primary Navigation** location.

### 5. Create ACF Field Groups

Go to **Custom Fields → Field Groups** and create the following 6 field groups. Use the exact **Field Name** values listed below — the theme templates depend on them.

---

#### Field Group 1: Homepage Settings
**Location Rule:** Page Type → is equal to → Front Page

| Field Label        | Field Name        | Field Type   | Notes                              |
|--------------------|-------------------|--------------|------------------------------------|
| Greeting Text      | `hero_greeting`   | Text         | Default: "Hello, I'm"             |
| Your Name          | `hero_name`       | Text         |                                    |
| Tagline / Role     | `hero_tagline`    | Text         |                                    |
| Short Description  | `hero_description`| Textarea     | Rows: 3                           |
| Hero Image / Photo | `hero_image`      | Image        | Return Format: Image Array         |
| CTA Button Text    | `hero_cta_text`   | Text         | Default: "View My Work"           |
| CTA Button Link    | `hero_cta_link`   | URL          |                                    |
| GitHub URL         | `social_github`   | URL          |                                    |
| LinkedIn URL       | `social_linkedin` | URL          |                                    |
| Email Address      | `social_email`    | Email        |                                    |
| Twitter / X URL    | `social_twitter`  | URL          |                                    |

---

#### Field Group 2: About Page Settings
**Location Rule:** Page Template → is equal to → About Page (`templates/page-about.php`)

| Field Label          | Field Name             | Field Type | Notes                              |
|----------------------|------------------------|------------|------------------------------------|
| Profile Photo        | `about_photo`          | Image      | Return Format: Image Array         |
| Bio / Long Desc      | `about_bio`            | WYSIWYG    | Media Upload: No                   |
| Resume / CV (PDF)    | `about_resume_file`    | File       | Return Format: File URL, MIME: pdf |
| Years of Experience  | `about_years_exp`      | Number     | Default: 0                         |
| Projects Completed   | `about_projects_count` | Number     | Default: 0                         |
| Happy Clients        | `about_clients_count`  | Number     | Default: 0                         |

---

#### Field Group 3: Work Details
**Location Rule:** Post Type → is equal to → Work

| Field Label        | Field Name          | Field Type  | Notes                                                |
|--------------------|---------------------|-------------|------------------------------------------------------|
| Client Name        | `work_client`       | Text        |                                                      |
| Project Date       | `work_date`         | Date Picker | Display Format: F Y, Return Format: F Y              |
| Live URL           | `work_url`          | URL         |                                                      |
| GitHub Repo URL    | `work_github_url`   | URL         |                                                      |
| Technologies Used  | `work_technologies` | Textarea    | Rows: 4, Instructions: "One technology per line"     |
| Gallery Image 1    | `work_gallery_1`    | Image       | Return Format: Image Array                           |
| Gallery Image 2    | `work_gallery_2`    | Image       | Return Format: Image Array                           |
| Gallery Image 3    | `work_gallery_3`    | Image       | Return Format: Image Array                           |

---

#### Field Group 4: Skill Details
**Location Rule:** Post Type → is equal to → Skill

| Field Label                    | Field Name          | Field Type | Notes                                                            |
|--------------------------------|---------------------|------------|------------------------------------------------------------------|
| Skill Icon (SVG or Image)      | `skill_icon`        | Image      | Return Format: Image Array                                       |
| Proficiency Level              | `skill_proficiency` | Select     | Choices: beginner, intermediate, advanced, expert. Default: intermediate |
| Proficiency % (for bar)        | `skill_percentage`  | Number     | Min: 0, Max: 100, Default: 50                                   |
| Short Description              | `skill_description` | Textarea   | Rows: 2                                                         |
| Display Order                  | `skill_order`       | Number     | Default: 0, Instructions: "Lower = shows first"                 |

---

#### Field Group 5: Certificate Details
**Location Rule:** Post Type → is equal to → Certificate

| Field Label            | Field Name            | Field Type  | Notes                               |
|------------------------|-----------------------|-------------|-------------------------------------|
| Issuing Organization   | `cert_issuer`         | Text        |                                     |
| Date Earned            | `cert_date`           | Date Picker | Display Format: F Y, Return: F Y   |
| Credential ID          | `cert_credential_id`  | Text        |                                     |
| Verification URL       | `cert_url`            | URL         |                                     |
| Certificate Image      | `cert_image`          | Image       | Return Format: Image Array          |

---

#### Field Group 6: Contact Page Settings
**Location Rule:** Page Template → is equal to → Contact Page (`templates/page-contact.php`)

| Field Label                | Field Name                 | Field Type | Notes                                            |
|----------------------------|----------------------------|------------|--------------------------------------------------|
| Section Heading            | `contact_heading`          | Text       | Default: "Get In Touch"                          |
| Description                | `contact_description`      | Textarea   | Rows: 3                                          |
| Contact Email              | `contact_email`            | Email      |                                                  |
| Phone Number               | `contact_phone`            | Text       |                                                  |
| Location                   | `contact_location`         | Text       |                                                  |
| Contact Form Shortcode     | `contact_form_shortcode`   | Text       | Instructions: "Paste CF7 or WPForms shortcode"   |

---

### 6. Add Content

**Works** (Dashboard → Works → Add New)
- Title, featured image, excerpt, and content
- Fill in ACF fields: client, date, live URL, GitHub URL, technologies (one per line), up to 3 gallery images
- Assign a Work Category

**Skills** (Dashboard → Skills → Add New)
- Title + optional featured image
- Fill in ACF fields: icon, proficiency level, percentage, description, display order
- Assign a Skill Category (e.g., Frontend, Backend, Tools)

**Certificates** (Dashboard → Certificates → Add New)
- Title + featured image
- Fill in ACF fields: issuer, date earned, credential ID, verification URL, certificate image

## Theme Structure

```
portfolio-theme/
├── assets/
│   ├── css/main.css          # All styles
│   ├── js/main.js            # Nav toggle, scroll reveal, filter
│   └── images/               # Theme images
├── inc/
│   ├── custom-post-types.php # Works, Skills, Certificates CPTs
│   ├── enqueue.php           # Asset loading
│   ├── helpers.php           # Utility functions
│   └── theme-setup.php       # Menus, thumbnails, supports
├── template-parts/
│   ├── card-work.php         # Work card component
│   ├── card-skill.php        # Skill card component
│   └── card-certificate.php  # Certificate card component
├── templates/
│   ├── page-about.php        # About page template
│   └── page-contact.php      # Contact page template
├── archive-work.php          # Works archive (with filter)
├── archive-skill.php         # Skills archive (grouped by category)
├── archive-certificate.php   # Certificates archive
├── single-work.php           # Single work detail page
├── front-page.php            # Homepage
├── header.php
├── footer.php
├── index.php                 # Fallback
├── page.php                  # Default page
├── functions.php
├── style.css                 # Theme header
└── README.md
```

## Free ACF Workarounds (No Repeater)

Since the free ACF plugin doesn't include the Repeater field:

- **Technologies**: Stored as a Textarea (one item per line), parsed via `devportfolio_parse_lines()` helper.
- **Gallery Images**: Individual image fields (`work_gallery_1`, `work_gallery_2`, `work_gallery_3`) collected via `devportfolio_get_work_gallery()`.
- **Skills list**: Each skill is its own CPT post (rather than repeater rows on a page).
- **Certificates**: Same approach — each cert is its own post.

## Customization

- **Colors/Fonts**: Edit CSS variables in `assets/css/main.css` (`:root` block)
- **Google Fonts**: Change in `inc/enqueue.php`
- **Image sizes**: Modify in `inc/theme-setup.php`
- **ACF fields**: Add/modify via Custom Fields → Field Groups in the WordPress dashboard
