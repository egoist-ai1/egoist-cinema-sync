# Egoist Cinema sync

Public storage for encrypted cross-device synchronization in Egoist Cinema.

The application writes authenticated AES-256-GCM envelopes. Profile names, viewing history, ratings and comments are never published as plaintext. GitHub write tokens and encryption keys are stored in the device's protected native storage and must never be committed here.

Shared summaries use a family key. Each profile's private library uses a separate random profile key. Viewing another profile's shared ratings or statistics does not import its private history or change personal recommendations. Devices join a family explicitly; profiles are identified by stable random IDs, never by display name.

Configure this repository in Egoist Cinema under Profile → Internet synchronization. A fine-grained GitHub token limited to this repository with Contents read/write is required for writes. Connect another device using the current profile's private connection code, or a family invitation to create an independent profile. Treat connection codes as private.

Synchronization runs on application opening and on local changes, with conditional reads, conflict retries and rate-limit backoff. GitHub is file storage, so update timing depends on the network and API limits.

This repository contains synchronization data only. No application binaries, provider credentials or movie files are hosted here.
