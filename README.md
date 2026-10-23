# Klipora Downloader MVP

A local-first starter project for authorized social-video downloads and legally distributable torrent downloads.

## Requirements

- macOS on Apple Silicon or Intel
- Node.js 20+
- `yt-dlp` installed and available on PATH for social-video downloads
- Internet connection for downloading dependencies and content

## Run locally

```bash
npm install
```

Install yt-dlp using Homebrew if you have Homebrew:

```bash
brew install yt-dlp
```

Start the app:

```bash
npm start
```

Open http://127.0.0.1:3000

The server binds to `127.0.0.1` by default and is intended for local development only.

## Current features

- Responsive video/torrent interface
- Video metadata inspection through yt-dlp
- Format selection and video download jobs
- Magnet-link torrent jobs using WebTorrent
- Job status polling and temporary download storage
- Download size limit and basic URL validation
- Local-only server binding by default

## Current MVP limitations

- Torrent `.torrent` file upload is not implemented yet; magnet links only.
- Download jobs are stored in memory and disappear after a server restart.
- Torrent downloads are stopped only when the torrent client/server exits; production cancellation needs a dedicated job manager.
- Format IDs may refer to video-only formats. For the most reliable output, start with “Best available quality.”
- Platform support changes over time; update yt-dlp regularly.
- Basic URL validation is not a complete SSRF defense. Do not expose this app publicly.
- This starter has no user accounts, authentication, persistent queue, remote object storage, or production worker isolation.
- The torrent backend is not suitable for public deployment without strict isolation, abuse prevention, network egress controls, and storage quotas.

## Safety

Only download content you own, have permission to download, or that is legally distributable. Do not use this app to bypass DRM, access controls, or platform restrictions. A clean watermark-free version is available only when an authorized source provides one.

## Free hosting reality

A static frontend can be deployed on a free static host, but video extraction and torrent downloading require a backend with outbound network access, disk space, and long-running process support. Many free serverless hosts do not permit these workloads. Keep the worker local for development until a suitable backend is chosen.
