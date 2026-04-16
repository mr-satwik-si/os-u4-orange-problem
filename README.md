# PES Version Control System (PES-VCS)

## Name: Satwik

## GitHub: mr-satwik-si

---

## 1. Introduction

This project implements a simplified version control system similar to Git.
It demonstrates how modern version control systems manage data using content-addressable storage, trees, and commits.

The system allows users to:

* Store file contents as objects
* Track changes using a staging area
* Create commits with history
* View commit logs

---

## 2. Objectives

* Implement content-addressable object storage using SHA-256
* Build tree structures to represent directories
* Implement a staging area (index)
* Create a commit system with history tracking
* Understand internal working of Git-like systems

---

## 3. System Design

The system is divided into four major components:

### 🔹 Object Storage

* Stores data as objects using SHA-256 hashing
* Supports blob, tree, and commit objects
* Ensures deduplication and integrity

### 🔹 Tree Structure

* Represents directory structure
* Maps filenames to blob/tree hashes
* Maintains sorted entries

### 🔹 Index (Staging Area)

* Tracks files staged for commit
* Stores metadata: mode, hash, size, modification time
* Saved in `.pes/index`

### 🔹 Commit System

* Stores snapshot of project
* Includes:

  * Tree hash
  * Parent commit
  * Author
  * Timestamp
  * Message
* Maintains history using linked commits

---

## 4. Phase-wise Implementation

### Phase 1: Object Storage

* Implemented `object_write` and `object_read`
* Used SHA-256 hashing
* Added deduplication
* Implemented integrity verification

---

### Phase 2: Tree

* Implemented tree serialization and parsing
* Ensured deterministic ordering of entries
* Represented directory structure

---

### Phase 3: Index

* Implemented index loading and saving
* Added support for staging files (`pes add`)
* Stored file metadata

---

### Phase 4: Commit

* Implemented commit creation
* Linked commits using parent references
* Implemented commit log traversal

---

## 5. Results

* Successfully passed all Phase 1 tests (`test_objects`)
* Successfully passed all Phase 2 tests (`test_tree`)
* Successfully implemented staging and status
* Successfully created and traversed commit history
* Passed full integration test (`test_sequence.sh`)

---

## 6. Sample Commands

```bash
./pes init
./pes add file.txt
./pes status
./pes commit -m "message"
./pes log
```

---

## 7. Repository Structure

```
.pes/
├── objects/
├── refs/heads/
├── HEAD
├── index
```

---

## 8. Conclusion

This project provided a deep understanding of how version control systems like Git work internally.
It demonstrated how data is stored efficiently using hashing, and how commits maintain history through linked structures.

---

## 9. Screenshots

All required screenshots are available in the `screenshots/` folder.

---
