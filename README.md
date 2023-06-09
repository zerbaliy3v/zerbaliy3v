<div align="center">
  <img height="270" src="https://media.tenor.com/Vk99BwgU9BIAAAAC/tokyo-ghoul.gif"  />
</div>

###
# Visit https://github.com/lowlighter/metrics#-documentation for full reference
name: Metrics
on:
  # Schedule updates (each hour)
  schedule: [{cron: "0 * * * *"}]
  # Lines below let you run workflow manually and on each commit
  workflow_dispatch:
  push: {branches: ["master", "main"]}
jobs:
  github-metrics:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: lowlighter/metrics@latest
        with:
          # Your GitHub token
          # The following scopes are required:
          #  - public_access (default scope)
          #  - repo
          # The following additional scopes may be required:
          #  - read:org      (for organization related metrics)
          #  - read:user     (for user related data)
          #  - read:packages (for some packages related data)
          #  - repo          (optional, if you want to include private repositories)
          token: ${{ secrets.METRICS_TOKEN }}

          # Options
          user: zerbaliy3v
          template: classic
          base: header, activity, community, repositories, metadata
          config_timezone: UTC
          plugin_isocalendar: yes
          plugin_isocalendar_duration: half-year
          plugin_pagespeed: yes
          plugin_pagespeed_url: .user.website
          plugin_stargazers: yes
          plugin_stargazers_charts: yes
          plugin_stargazers_charts_type: classic
          plugin_stargazers_days: 14
          plugin_stars: yes
          plugin_stars_limit: 4
          plugin_traffic: yes
