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
  "delay": 2000
}
```

### Configuration Options

- **`redirectUrl`**: The destination URL (required)
- **`message`**: Custom message shown during redirect (optional)
- **`delay`**: Redirect delay in milliseconds (optional, default: 2000)

## Examples

### Redirect to Your Portfolio
```json
{
  "redirectUrl": "https://yourportfolio.com",
  "message": "Welcome! Taking you to my portfolio...",
  "delay": 1500
}
```

### Redirect to a Specific Campaign
```json
{
  "redirectUrl": "https://yourstore.com/special-offer",
  "message": "Special offer loading...",
  "delay": 1000
}
```

## Use Cases

- **Event Links**: Update QR codes on printed materials to point to different event pages
- **Menu QR Codes**: Restaurant menus that can be updated seasonally
- **Business Cards**: Point to different landing pages for different campaigns
- **Conference Materials**: Update session links without reprinting materials
- **Marketing Campaigns**: A/B test different landing pages with the same QR code

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