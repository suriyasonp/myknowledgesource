# Custom Home Page Layout Documentation

This Hugo blog now features a custom home page layout with the following characteristics:

## Layout Structure

### Main Content Area (~65%)
- Displays the 5 most recent posts with enhanced spacing
- Each post shows title, summary, metadata, and cover image
- Generous padding and margins for better readability
- Larger typography and improved line spacing
- Includes a "View All Posts" button if there are more than 5 posts
- Responsive design that adapts to different screen sizes

### Sidebar (~35% or 400px width)
- **Categories Section**: Lists all post categories with post counts
- **Popular Tags Section**: Shows the 8 most popular tags
- Enhanced spacing and larger clickable areas
- Sticky positioning on desktop (stays in view when scrolling)
- Fixed width for better control across screen sizes

## Files Created/Modified

### 1. `/layouts/index.html`
- Custom home page template
- Replaces the default PaperMod home layout
- Fetches recent posts and displays categories/tags

### 2. `/assets/css/custom.css`
- All custom styling for the home layout
- Responsive design breakpoints
- Dark/light theme compatibility

### 3. `/layouts/partials/extend_head.html`
- Includes the custom CSS in the site header
- Integrates with Hugo's asset pipeline

### 4. `/hugo.toml` (modified)
- Added `mainSections = ["posts"]` parameter
- Added `customCSS = ["css/custom.css"]` to assets configuration

## Customization Options

### Changing the Number of Posts
To display a different number of recent posts, edit line 15 in `/layouts/index.html`:
```html
{{- $recentPosts := first 5 $pages }}
```
Change `5` to your desired number.

### Modifying Sidebar Content
You can customize the sidebar sections in `/layouts/index.html`:
- Add new sections after line 68
- Modify the tag count (line 70) to show more/fewer tags
- Add custom widgets or information

### Styling Adjustments
All visual customizations can be made in `/assets/css/custom.css`:
- Colors and spacing
- Typography
- Layout proportions
- Responsive breakpoints

### Layout Proportions
To change the main content/sidebar ratio, modify these CSS rules:
```css
.home-main {
    flex: 1; /* Main content takes remaining space */
}

.home-sidebar {
    flex: 0 0 400px; /* Fixed sidebar width of 400px */
}
```

### Container Width and Spacing
The layout now uses a wider container with better spacing:
```css
.home-layout {
    max-width: 1400px; /* Increased from 1200px */
    gap: 3rem; /* Larger gap between main and sidebar */
    padding: 0 2rem; /* More generous outer padding */
}
```

## Categories

The blog currently includes two main categories:
- **Technology**: Tech-related posts
- **Stay Reading**: Personal development and mindfulness posts

Categories are automatically populated from your post front matter.

## Responsive Behavior

- **Large Desktop (>1200px)**: Full 1400px width with 400px sidebar
- **Medium Desktop (≤1200px)**: Reduced to 1200px width with 350px sidebar  
- **Tablet (≤1024px)**: 300px sidebar with reduced post padding
- **Mobile (≤768px)**: Single column with full-width sidebar below main content
- **Small Mobile (≤480px)**: Optimized spacing and typography

## Browser Compatibility

The layout uses modern CSS features but includes fallbacks for:
- CSS Grid and Flexbox
- CSS Custom Properties (variables)
- Modern viewport units

## Future Enhancements

Potential improvements you could add:
- Featured posts section
- Recent comments widget
- Social media links
- Newsletter signup
- Search functionality in sidebar
- Related posts suggestions

## Troubleshooting

If the layout doesn't appear correctly:
1. Check that Hugo server is running
2. Verify CSS file is being loaded in browser dev tools
3. Ensure `/layouts/partials/extend_head.html` exists
4. Check Hugo console for any build errors
