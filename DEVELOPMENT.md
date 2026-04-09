# Development Notes

## Initial Setup

The following describes the prerequisites and one-time manual steps that were needed for setting up this repository.

### Prerequisites

- AWS Account
    - Ownership of the domain emberarchive.org

### Manual Steps

1. Enable GitHub Pages
    - In this repository, go to `Settings` -> `Pages`
    - Under `Build and Deployment` > `Source` select `GitHub Actions`
2. Verify domain in GitHub
    - In this organization, go `Settings` -> `Pages`
    - Click `Add a domain`
    - Enter the domain name `"docs.emberarchive.org"`
    - Copy the provided TXT record and token
    - Click Verify
3. Add TXT record in Route 53
    - In AWS, go to Route 53 -> Hosted Zones
    - Click `emberarchive.org`
    - Click `Create record` and enter the following:
        - Type: `TXT`
        - Name: copied TXT record name from GitHub in above step
        - Value: copied token from GitHub in above step
4. Add DNS record in Route53
    - In AWS, go to Route 53 -> Hosted Zones
    - Click `emberarchive.org`
    - Click `Create record` and enter the following:
        - Type: `CNAME`
        - Name: `"docs"`
        - Value: `"aplbrain.github.io"`
5. Set the custom domain
    - In this repository, go to `Settings` -> `Pages`
    - Under `Custom domain`, enter `"docs.emberarchive.org"`
    - Click `Save`
6. Deploy
    - Merge/Push to `main` to trigger the initial GitHub Pages deployment
7. Enable HTTPS
    - In this repository, go to `Settings` -> `Pages`
    - Check the box next to `Enforce HTTPS`
