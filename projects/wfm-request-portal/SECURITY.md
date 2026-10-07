# Security

## Public repository policy

Never commit:

- passwords
- API keys
- access tokens
- connection secrets
- private SharePoint URLs
- employee personal data
- production exports
- corporate configuration

## Environment configuration

Environment-dependent values should be supplied through configuration rather than hard-coded in source.

For a Power Platform implementation, prefer:

- Environment Variables
- Connection References
- deployment-time configuration
- separate DEV / TEST / PROD environments

## Data protection

Sample data in this repository must be synthetic.

No production or personally identifiable information should be required to run the portfolio implementation.
