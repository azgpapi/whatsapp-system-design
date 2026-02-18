# WhatsApp System Design (Scale: 1B Users)

A professional blueprint for a global, popular, real-time messaging system.

## 📌 Project Overview
- **Goal:** High-availability, low-latency messaging.
- **Key Features:** 1-on-1 Chat, Presence (Online/Offline), Read Receipts.

## 🏗️ Architecture Documentation
1. [High-Level Design (HLD)](./docs/high-level-design.md) - System-wide view.
2. [Low-Level Design (LLD)](./docs/low-level-design.md) - API & Class Design.
3. [Database Schema](./docs/database-design.md) - Storage strategy & Trade-offs.

## 🧠 Architectural Decisions (ADR)
- [ADR 001: Choosing WebSockets over HTTP](./ADR/001-websockets.md)