# QR Code Redirect Service

A simple, free QR code redirect service that allows you to use one QR code but change the destination URL by updating a configuration file.

## How It Works

1. **Single QR Code**: Generate one QR code that points to your GitHub Pages URL
2. **Dynamic Redirects**: Change where the QR code redirects by editing `config.json`
3. **Instant Updates**: Changes take effect immediately after committing to GitHub

## Quick Start

### 1. Deploy to GitHub Pages

1. Create a new GitHub repository (e.g., `qr-redirect`)
2. Upload all files from this directory to your repository
3. Go to **Settings** → **Pages** 
4. Select **Deploy from a branch** → **main** → **/ (root)**
5. Your redirect service will be available at: `https://yourusername.github.io/qr-redirect`

### 2. Generate Your QR Code

1. Go to any QR code generator (like [qr-code-generator.com](https://qr-code-generator.com))
2. Enter your GitHub Pages URL: `https://yourusername.github.io/qr-redirect`
3. Generate and download your QR code
4. **Important**: This is the only QR code you'll ever need!

### 3. Update Redirect Destination

To change where your QR code redirects:

1. Edit `config.json` in your GitHub repository
2. Change the `redirectUrl` to your new destination
3. Commit the changes
4. Your QR code will now redirect to the new URL!

## Configuration

Edit `config.json` to customize the redirect behavior:

```json
{
  "redirectUrl": "https://your-destination.com",
  "message": "Redirecting to my website...",
  "delay": 2000,
  "destinations": {
    "product1": "https://yourstore.com/product1",
    "product2": "https://yourstore.com/product2",
    "special": "https://yourstore.com/special-offer"
  },
  "destinationMessages": {
    "product1": "Loading Product 1...",
    "product2": "Loading Product 2...",
    "special": "Special offer loading..."
  }
}
```

### Configuration Options

**Root Level (Default Profile):**
- **`redirectUrl`**: The default destination URL (required)
- **`message`**: Default message shown during redirect (optional)
- **`delay`**: Redirect delay in milliseconds (optional, default: 2000)
- **`destinations`**: Map of destination keys to URLs for query string routing (optional)
- **`destinationMessages`**: Custom messages for specific destinations (optional)

**Profiles:**
- **`profiles`**: Object containing multiple redirect configurations (optional)
- Each profile can have its own `redirectUrl`, `message`, `delay`, `destinations`, and `destinationMessages`

### Query String Routing

You can create multiple QR codes that all point to your service but redirect to different destinations using query parameters:

**Basic Destination Routing:**
- `https://yourusername.github.io/qr-redirect` (uses default `redirectUrl`)
- `https://yourusername.github.io/qr-redirect?dest=product1` (redirects to destinations.product1)
- `https://yourusername.github.io/qr-redirect?dest=product2` (redirects to destinations.product2)

**Profile-Based Routing:**
- `https://yourusername.github.io/qr-redirect?profile=restaurant` (uses restaurant profile default)
- `https://yourusername.github.io/qr-redirect?profile=restaurant&dest=menu` (restaurant profile, menu destination)
- `https://yourusername.github.io/qr-redirect?profile=business&dest=portfolio` (business profile, portfolio destination)
- `https://yourusername.github.io/qr-redirect?profile=event&dest=schedule` (event profile, schedule destination)

**Benefits:**
- Create multiple QR codes for different purposes
- Manage all destinations from one config file
- Use different profiles for different contexts (restaurant, business, event)
- Track which QR codes are being used
- Easy to add new destinations without creating new services

## Examples

### Simple Single Redirect
```json
{
  "redirectUrl": "https://yourportfolio.com",
  "message": "Welcome! Taking you to my portfolio...",
  "delay": 1500
}
```

### Multiple Profiles with Complete Redirect Configurations
```json
{
  "redirectUrl": "https://yourstore.com",
  "message": "Redirecting...",
  "delay": 2000,
  "profiles": {
    "restaurant": {
      "redirectUrl": "https://yourrestaurant.com/menu",
      "message": "Welcome to our restaurant!",
      "delay": 1500,
      "destinations": {
        "menu": "https://yourrestaurant.com/menu",
        "specials": "https://yourrestaurant.com/todays-specials",
        "reservations": "https://yourrestaurant.com/book-table",
        "contact": "https://yourrestaurant.com/contact"
      },
      "destinationMessages": {
        "menu": "Loading our delicious menu...",
        "specials": "Check out today's specials...",
        "reservations": "Book your table...",
        "contact": "Get in touch with us..."
      }
    },
    "business": {
      "redirectUrl": "https://yourbusiness.com/about",
      "message": "Welcome to our business!",
      "delay": 1000,
      "destinations": {
        "about": "https://yourbusiness.com/about",
        "services": "https://yourbusiness.com/services",
        "portfolio": "https://yourbusiness.com/portfolio",
        "contact": "https://yourbusiness.com/contact"
      },
      "destinationMessages": {
        "about": "Learn about our story...",
        "services": "Discover our services...",
        "portfolio": "View our work...",
        "contact": "Get in touch..."
      }
    }
  }
}
```

**QR Codes for this setup:**

**Restaurant Profile:**
- Table tents: `https://yoursite.github.io/qr-redirect?profile=restaurant&dest=menu`
- Specials board: `https://yoursite.github.io/qr-redirect?profile=restaurant&dest=specials`
- Business cards: `https://yoursite.github.io/qr-redirect?profile=restaurant&dest=contact`

**Business Profile:**
- Portfolio flyer: `https://yoursite.github.io/qr-redirect?profile=business&dest=portfolio`
- Service brochure: `https://yoursite.github.io/qr-redirect?profile=business&dest=services`
- Networking cards: `https://yoursite.github.io/qr-redirect?profile=business&dest=contact`

## Use Cases

- **Multi-Business Management**: Different profiles for restaurant, retail, and service businesses
- **Event Management**: Separate profiles for different events (conference, wedding, concert) with unique destinations
- **Seasonal Campaigns**: Switch between profiles for different seasons/campaigns without changing QR codes
- **Department-Specific**: Different profiles for sales, support, marketing departments
- **Location-Based**: Different profiles for multiple store locations or venues
- **Client-Specific**: Separate profiles for different clients or projects
- **A/B Testing**: Test different redirect flows by switching profiles
- **Multi-Language**: Different profiles for different languages or regions

## File Structure

```
qr-redirect/
├── index.html          # Main redirect page
├── config.json         # Redirect configuration
├── style.css          # Styling
└── README.md          # This file
```

## Benefits

- ✅ **Free**: Uses GitHub Pages (free hosting)
- ✅ **No Database**: Simple JSON configuration
- ✅ **Easy Updates**: Change via GitHub web interface
- ✅ **Version Control**: Track all changes
- ✅ **No Backend**: Pure frontend solution
- ✅ **Mobile Optimized**: Works great on all devices

## Troubleshooting

### QR Code Not Redirecting
- Check that GitHub Pages is enabled and deployed
- Verify your GitHub Pages URL is correct
- Ensure `config.json` has valid JSON syntax

### Invalid Configuration
- Make sure `redirectUrl` is a valid URL (include `https://`)
- Check that JSON syntax is correct (no trailing commas)
- Verify file is saved and committed to GitHub

### Redirect Not Working
- Test the redirect URL directly in your browser
- Check browser developer tools for any errors
- Ensure the destination URL is accessible

## Advanced Usage

### Custom Domain
1. Purchase a domain and point it to GitHub Pages
2. Update your repository settings to use the custom domain
3. Generate a new QR code with your custom domain URL

### Analytics
The service includes basic view tracking in localStorage. To add more advanced analytics, you can integrate with services like Google Analytics by adding the tracking code to `index.html`.

## License

MIT License - feel free to modify and use for your projects! 