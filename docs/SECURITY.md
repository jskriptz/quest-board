# Security Policy

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| Latest  | :white_check_mark: |

## Reporting a Vulnerability

If you discover a security vulnerability, please:

1. **Do not** open a public issue
2. Email the maintainers directly or use GitHub's private vulnerability reporting
3. Include:
   - Description of the vulnerability
   - Steps to reproduce
   - Potential impact
   - Suggested fix (if any)

## Security Considerations

### API Key Handling

Quest Board uses a **Bring Your Own Key (BYOK)** model for AI features:

- **No embedded keys:** The repository contains no API keys
- **User-provided keys:** Each user enters their own Anthropic API key
- **Local storage only:** Keys are stored in the user's browser localStorage
- **Never transmitted:** Keys are sent only to Anthropic's API, never to any other server
- **Optional feature:** The app works without AI — quests simply use plain text

**For deployers:**
- Do NOT embed API keys in the code
- Do NOT create backend proxies that use your keys
- Let users provide their own keys (they control their own costs)

**For users:**
- Your API key is stored only in YOUR browser
- Clear localStorage to remove your key
- Get your own key at https://console.anthropic.com

### Client-Side Security

- All data is stored in browser localStorage
- No server-side components exist
- XSS prevention through proper DOM manipulation
- Input sanitization for user-entered quest text

### Third-Party Dependencies

Quest Board intentionally has **zero external dependencies** to minimize supply chain risk.

## Security Best Practices for Users

1. Use the app from trusted sources (official GitHub Pages or your own deployment)
2. Do not enter sensitive information in quest descriptions
3. Clear localStorage if using a shared computer
4. Keep your browser updated

## Acknowledgments

We appreciate responsible disclosure of security issues.
