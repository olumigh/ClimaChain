# ClimaChain - Clean Energy Asset DAO Smart Contract

## Overview

This Clarity smart contract defines a decentralized platform for managing, investing in, and governing clean energy assets (solar, wind, hydro, biomass). The contract supports share-based ownership, automated revenue distribution, and governance mechanisms allowing stakeholders to propose and vote on operational decisions.

## 🚀 Features

* **Asset Registration**: Owners can register new clean energy assets with geolocation and metadata.
* **Ownership Shares**: Users can purchase shares of active assets.
* **Revenue Distribution**: Revenues from energy production are distributed proportionally to shareholders.
* **Governance System**: Shareholders can propose and vote on asset-specific decisions.
* **Metrics Tracking**: Tracks environmental and financial performance metrics for each asset.
* **Safety Checks**: Validates input data and enforces thresholds for secure operation.

---

## 📦 Contract Structure

### Constants

| Constant             | Description                                               |
| -------------------- | --------------------------------------------------------- |
| `CONTRACT-OWNER`     | The creator of the contract.                              |
| `MIN-INVESTMENT`     | Minimum investment required to register an asset (1 STX). |
| `SHARE-SCALE`        | Scaling factor for share representation (6 decimals).     |
| `VOTE-THRESHOLD`     | Default threshold (75%) for proposal acceptance.          |
| `MAINTENANCE-WINDOW` | Cooldown/maintenance period in blocks (\~24 hours).       |

---

## 📊 Data Structures

### Maps

* **`assets`**: Stores metadata and financials for each registered asset.
* **`ownership`**: Records shareholder information per asset.
* **`asset-metrics`**: Tracks environmental KPIs and performance.
* **`governance-settings`**: Customizable governance rules per asset.
* **`proposals`**: Stores active and past governance proposals.

---

## 🔧 Traits

* `asset-owner-trait`:

  * `transfer-ownership`: Allows share transfers.
  * `claim-revenue`: Allows shareholders to claim their revenue share.

---

## 📂 Key Functions

### 📌 Asset Management

#### `register-asset`

Registers a new asset with name, type, shares, price, and GPS coordinates.

#### `purchase-shares`

Allows investors to purchase shares of active assets.

---

### 💰 Revenue & Governance

#### `distribute-revenue`

Allows the contract owner to deposit revenue to an asset, updating shareholder revenue-per-share.

---

### 🛠 Internal Validators

* `is-valid-name`, `is-valid-asset-type`: Validate asset attributes.
* `calculate-voting-power`: Determines vote weight based on share ownership.

---

## ✅ Validation & Errors

The contract includes comprehensive error codes such as:

* Unauthorized actions (`ERR-NOT-AUTHORIZED`)
* Invalid names, types, amounts
* Quorum/vote failures
* Asset or proposal not found

---

## 🏗 Example Use Case Flow

1. **Register Asset**: Owner calls `register-asset`.
2. **Purchase Shares**: Investors buy shares using `purchase-shares`.
3. **Distribute Revenue**: Revenue is distributed using `distribute-revenue`.
4. **Governance Proposals**: Shareholders propose and vote on actions.

---

## 🧪 Testing Suggestions

* Attempt to register assets with invalid names/types.
* Test purchasing shares below available count.
* Test revenue distribution and confirm accuracy of `revenue-per-share`.

---

## 🔐 Security Considerations

* Prevents self-transfers and unauthorized fund movements.
* All input data is validated (string lengths, amount thresholds).
* Uses `unwrap!` and `asserts!` extensively for safe execution paths.

---

## 🪙 Tokenomics (if extended)

You could integrate a fungible token standard (e.g., SIP-010) to represent shares and streamline ownership transfer and liquidity.

---

## 🌍 Potential Extensions

* NFT representation for unique clean energy assets.
* Integration with real-time energy data oracles.
* Dynamic share pricing based on asset performance.
* Community proposal system for DAO upgrades.

---
