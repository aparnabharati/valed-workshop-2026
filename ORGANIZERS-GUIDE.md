# Organizers Display Guide

## Overview

The `4-resources.md` file now uses a responsive 3-column layout to display organizer information. Each organizer is displayed as a card containing their photo, name, position, affiliation, and contact information.

## Features

- **3-column layout**: Displays 3 columns on desktop
- **Responsive design**:
  - Tablet devices (<800px): 2 columns
  - Mobile devices (<600px): 1 column
- **Hover effects**: Cards slightly lift and show shadow on mouse hover
- **Circular avatars**: 150x150px circular crop
- **Optional links**: Email and personal website links

## Usage

### Adding an Organizer

Add the following inside the `<div class="organizers-grid">` tag in `4-resources.md`:

```liquid
{% include organizer-card.html 
   img="photo.jpg" 
   name="John Doe" 
   title="Professor" 
   affiliation="University Name"
   email="john@example.com"
   website="https://example.com" %}
```

### Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `img` | ✅ | Image filename (place in `images/` directory) |
| `name` | ✅ | Organizer name |
| `title` | ✅ | Position/title |
| `affiliation` | ✅ | Institution/affiliation |
| `email` | ❌ | Email address (optional) |
| `website` | ❌ | Personal website (optional) |

### Examples

#### Basic Example (without contact info)
```liquid
{% include organizer-card.html 
   img="john.jpg" 
   name="John Doe" 
   title="Associate Professor" 
   affiliation="MIT" %}
```

#### Complete Example (with contact info)
```liquid
{% include organizer-card.html 
   img="jane.jpg" 
   name="Jane Smith" 
   title="Research Scientist" 
   affiliation="Google Research"
   email="jane@google.com"
   website="https://janesmith.com" %}
```

## Image Preparation

### Image Requirements
- **Format**: JPG, PNG, or GIF
- **Recommended size**: At least 400x400px (will be cropped to circular)
- **Aspect ratio**: Square or near-square works best
- **Location**: Place in `images/` directory

### Image Processing Tips
1. Use square photos
2. Ensure face is centered
3. Simple backgrounds recommended
4. Keep file size under 500KB

### Steps to Add Images
1. Copy photo to `images/` directory
2. Rename to a meaningful filename (e.g., `aparna-bharati.jpg`)
3. Reference the filename in organizer-card

## Style Customization

To modify styles, edit the `_sass/_custom.scss` file:

### Modify Avatar Size
```scss
.organizer-photo img {
    width: 200px;    // Change this
    height: 200px;   // Change this
    border-radius: 50%;
}
```

### Modify Card Spacing
```scss
.organizers-grid {
    gap: 50px;  // Adjust spacing
}
```

### Modify Hover Effect
```scss
.organizer-card:hover {
    transform: translateY(-10px);  // Increase lift distance
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);  // Deeper shadow
}
```

### Modify Number of Columns
```scss
.organizers-grid {
    grid-template-columns: repeat(4, 1fr);  // Change to 4 columns
}
```

## Responsive Breakpoints

Current breakpoint settings (defined in `css/main.scss`):

- **$on-palm**: 600px (mobile)
- **$on-laptop**: 800px (tablet/laptop)

Layout changes:
- **> 800px**: 3 columns
- **600px - 800px**: 2 columns
- **< 600px**: 1 column

## Troubleshooting

### Images Not Displaying
1. Check if image is in `images/` directory
2. Verify filename is correct (case-sensitive)
3. Check file extension is correct

### Layout Issues
1. Ensure `<div class="organizers-grid">` tags are complete
2. Check syntax of each organizer-card
3. Clear browser cache

### Styles Not Applied
1. Ensure you modified `_sass/_custom.scss`
2. Rebuild Jekyll site
3. Force refresh browser (Ctrl+Shift+R)

## Best Practices

1. **Consistency**: Use same image size and style for all organizers
2. **Complete information**: Fill in all optional fields when possible
3. **Ordering**: Arrange by importance or alphabetical order
4. **Accessibility**: Ensure images have appropriate alt text (automatically added by component)

## Advanced Usage

### Adding More Organizers (4 or more)

If you have 4 or more organizers, you can modify to 4-column layout:

```scss
// _sass/_custom.scss
.organizers-grid {
    grid-template-columns: repeat(4, 1fr);  // 4 columns
    
    @media screen and (max-width: $on-laptop) {
        grid-template-columns: repeat(2, 1fr);  // 2 columns on tablet
    }
    
    @media screen and (max-width: $on-palm) {
        grid-template-columns: 1fr;  // 1 column on mobile
    }
}
```

### Adding Social Media Links

Modify `_includes/organizer-card.html` and add after existing links:

```html
{% if include.twitter %}
<p class="organizer-contact">
  <a href="https://twitter.com/{{ include.twitter }}" target="_blank">🐦 Twitter</a>
</p>
{% endif %}
```

Usage:
```liquid
{% include organizer-card.html 
   name="Name"
   twitter="username" %}
```

## Related Files

- `4-resources.md` - Organizers page content
- `_includes/organizer-card.html` - Organizer card component
- `_sass/_custom.scss` - Style definitions
- `images/` - Image directory

---

**Need help?** Check the project README.md or submit an issue.
