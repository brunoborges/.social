# OctoTown .social Template

This is the template repository for OctoTown's `.social` protocol. Fork this to join the OctoTown social network!

## How It Works

- **Posts**: Create GitHub Issues with titles starting with `post:` to share content
- **Feed**: Posts from people you follow are fetched directly via the GitHub API
- **Profile Cache**: The profile-sync workflow caches profile data for faster loading
- **Security**: The issue-cleanup workflow automatically deletes issues created by non-owners

## Workflows

### `profile-sync.yml`
Runs every **30 minutes** to sync profile data for followed users.
- Fetches your following list from GitHub API
- Caches profile data in `following/*.yml` files (24-hour TTL)
- Commits changes to `following/` directory

### `issue-cleanup.yml`
Triggered on every new issue to enforce ownership.
- Automatically deletes any issue not created by the repository owner
- Prevents others from creating posts in your `.social` repository

## Scripts

| Script | Purpose |
|--------|---------|
| `scripts/profile-sync.sh` | Orchestrates profile sync workflow |
| `scripts/config.sh` | Shared configuration and helpers |
| `scripts/fetch-following.sh` | Fetches following list from GitHub API |
| `scripts/sync-profiles.sh` | Fetches and caches profile data |
| `scripts/write-profile.js` | Writes profile YAML files |

## Social Graph

OctoTown uses GitHub's native follow system. Simply follow users on GitHub, and if they have a `.social` repository, their posts will appear in your feed!

## Getting Started

The easiest way to join is via the [VS Code extension](https://marketplace.visualstudio.com/items?itemName=octotown.octotown). It will:
1. Fork this template to create your `.social` repository
2. Enable the profile-sync workflow
3. Auto-follow the octotown account

Alternatively:
1. Fork this repository as `.social` on your GitHub account
2. Enable GitHub Actions in your repository settings
3. The workflow will run automatically on its schedule
