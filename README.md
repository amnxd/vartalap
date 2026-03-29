# Vartalap

Vartalap is a modern, real-time chat application built with Flutter and a Rust backend.
It is designed for smooth conversations, fast rendering, and a polished dark UI with practical collaboration features.

Website : https://chat.malevolent.in 
Mobile Application : https://github.com/amnxd/vartalap/releases/tag/v0.2.2

## Product Overview

Vartalap focuses on a clean messaging experience with responsive interaction design.
The app combines real-time delivery with a local-first cache, so conversations feel immediate and remain usable even when network quality changes.

Core design goals:
- Fast message flow with low-friction interaction
- Professional, neutral dark visual language
- Scalable chat history performance
- Reliable delivery and recovery behavior

## UX and Interface Highlights

- Neutral dark default background
  - Primary default theme uses a gray-dark palette inspired by productivity tools (Excalidraw and n8n style direction), not a saturated blue or purple base.

- Unread-first open behavior
  - Chat opens at the first unread message when available.
  - If everything is read, chat opens at the latest message (bottom), matching expected behavior from major chat apps.

- Smooth history rendering
  - Lazy message windowing keeps rendering lightweight for long conversations.
  - Older messages load incrementally with top-edge paging and near-top prefetch.
  - Viewport is preserved while older history loads to avoid jumpy scroll behavior.

- Conversation clarity
  - Grouped message spacing and compact chronological flow
  - Readable typography tuned for chat density
  - Subtle unread divider and clean message threading cues

- Message interaction set
  - Reply to message
  - Edit and delete
  - Reactions
  - Mentions and typing indicators
  - Read and delivered receipts (context-aware)

## Feature Set

- Authentication and account management
- Real-time chat via WebSocket
- Direct messaging flows
- Global chat support
- Optional E2EE support for eligible chat contexts
- Stickers and emoji reaction workflows
- Local message persistence for fast reopen and resilience
- Backup and restore options, including encrypted backup flows
- Runtime appearance customization (theme, background, composer, spacing)

## Performance and Architecture

- Frontend
  - Flutter UI with optimized list rendering
  - Incremental history paging with prefetch
  - Optimistic message insertion and retry handling

- Backend
  - Rust service with Postgres
  - Paginated server-side history endpoint
  - WebSocket event delivery for real-time updates

- Data strategy
  - Local cache for speed and continuity
  - Server pagination for scalable history retrieval

## Tech Stack

- Frontend: Flutter, Dart
- Backend: Rust, Actix Web
- Database: PostgreSQL
- Realtime: WebSocket

## Quick Start

1. Install Flutter and Android toolchain.
2. From repository root:

flutter pub get
flutter run

## Backend Configuration

The app uses a compiled backend base URL from Dart defines.

Common define:
- AETHER_BASE_URL

Example run:

flutter run --dart-define=AETHER_BASE_URL=https://YOUR_BACKEND_HOST

Example release build:

flutter build apk --release --dart-define=AETHER_BASE_URL=https://YOUR_BACKEND_HOST

## Android Release Build

Current app version:
- 0.2.2+22

Release build command:

flutter build apk --release

Default output:
- build/app/outputs/flutter-apk/app-release.apk

## Web Build

Build command:

flutter build web --release --dart-define=AETHER_BASE_URL=https://YOUR_BACKEND_HOST

Deploy static artifacts from:
- build/web/

## Firebase and Google Sign-In Notes

For Android Google Sign-In and cloud-backed features:
- Ensure Android package name and signing certificates match Firebase configuration.
- Keep android/app/google-services.json aligned with the active package and key fingerprints.

## Backend API Notes

Chat history endpoint supports pagination:
- GET /chats/:id/messages?limit=100&before_time=<RFC3339>&before_id=<id>

Response includes:
- messages
- hasMore
- nextCursor

This enables true incremental history loading for large chat timelines.

## Development Utilities

- Docker compose support for local backend stack
- Database reset utility scripts for local development
- Release notes and versioned release documentation in the release folder

## Project Structure

- lib/ : Flutter app source
- backend_rust/ : Rust API and realtime server
- android/, ios/, web/, windows/, macos/, linux/ : platform targets
- tool/ : helper scripts

## Vision

Vartalap is built to feel production-grade from day one: clean, performant, reliable, and visually intentional.
The roadmap continues in the same direction with deeper collaboration workflows, stronger reliability tooling, and further UI refinement.
