# Egoist Cinema sync

Public storage for encrypted cross-device synchronization in Egoist Cinema. This repository contains no application binaries, provider credentials or media files.

The application stores authenticated AES-256-GCM envelopes. Profile names, viewing history, ratings and comments are not published as plaintext. GitHub write tokens and encryption keys must never be committed here. Credentials are protected with Windows DPAPI or Android Keystore on each connected device.

Shared summaries use a family key. Each profile's private library uses a separate random profile key and stable random ID. Multiple PCs and televisions can connect to the same profile explicitly; a family invitation creates an independent profile. Matching display names never merge identities. Other profiles' shared watched titles, ratings, comments and statistics are read-only information; they do not enter personal history or recommendation inputs.

Synchronization checks at each application startup and then once per hour while running. Conditional reads avoid downloading unchanged data. Local changes are queued for prompt upload, with durable offline retries, fresh merges after write conflicts and API rate-limit backoff. GitHub is file storage, so network conditions and API limits determine delivery time.

The initial authorized Windows installation can import the staged credential only for its original Windows user and computer. A different Windows computer joins once in Settings → Internet synchronization with its personal profile connection code and repository-only write access; login and protected configuration are remembered afterwards. An Android device can receive protected access when first paired with the authenticated home PC, and subsequently synchronize without that PC running. A personal connection code links the same profile; a family invitation creates a separate one. Treat both codes as private.

Anonymous GitHub access can read encrypted files but cannot write them or decrypt them without the appropriate keys. Writes require a fine-grained token limited to this repository with Contents read/write. Shared access is intended for trusted family devices; each profile's private key remains separate.

Only synthetic fixtures and public configuration metadata were used during release verification. Real personal libraries are uploaded by connected application devices.
