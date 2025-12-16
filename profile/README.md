<div align="center">
  <pre>
  ██████╗ ███████╗ ██████╗  ██████╗ ████████╗ ██████╗██╗  ██╗██╗
  ██╔══██╗██╔════╝██╔════╝ ██╔═══██╗╚══██╔══╝██╔════╝██║  ██║██║
  ██║  ██║█████╗  ██║  ███╗██║   ██║   ██║   ██║     ███████║██║
  ██║  ██║██╔══╝  ██║   ██║██║   ██║   ██║   ██║     ██╔══██║██║
  ██████╔╝███████╗╚██████╔╝╚██████╔╝   ██║   ╚██████╗██║  ██║██║
  ╚═════╝ ╚══════╝ ╚═════╝  ╚═════╝    ╚═╝    ╚═════╝╚═╝  ╚═╝╚═╝
  </pre>

  <h3>👾 The Sentient Asset Agent on Solana 👾</h3>

  <p>
    <strong>Feed it SOL. Watch it trade. Pray it doesn't get Rekt.</strong>
  </p>

  <p>
    <a href="https://twitter.com/XXXXXX">
      <img src="https://img.shields.io/twitter/follow/Degotchi?style=social&label=Follow%20the%20Cult" alt="Twitter" />
    </a>
    <a href="https://discord.gg/XXXXXX">
      <img src="https://img.shields.io/discord/123456789?color=5865F2&label=Discord&logo=discord&logoColor=white" alt="Discord" />
    </a>
    <img src="https://img.shields.io/badge/Solana-Mainnet-14F195?logo=solana&logoColor=white" alt="Solana" />
  </p>
</div>

---
## Degotchi

**Degotchi** is a crypto-native virtual pet system inspired by *Degen culture* and *Tamagotchi*.

A Degotchi is an **on-chain pet with an independent personality**.
It forms opinions, proposes actions, and expresses outcomes — but **never executes financial actions without explicit human approval**.

This project explores **human-in-the-loop AI decision systems** in a Web3 context.

---

### Core Philosophy

* 🧠 **AI suggests, humans decide**
* 🐾 **Pets are first-class on-chain entities**
* 🔐 **No private keys are ever handled by AI**
* 🎮 **Finance as interaction, not automation**

Degotchi is **not** an auto-trading bot.
It is a *personality-driven decision companion*.

---

### System Architecture

The project is organized as a modular full-stack system:

#### 🧠 Brain (Python)

AI decision engine and state orchestration:

* Market signal ingestion
* Personality-driven decision modeling
* Action proposal generation
* Time-based state evolution (hunger, mood, cooldowns)

> Brain can propose actions, but cannot execute them.

---

#### 🧍 Body (Web / React)

User-facing web interface:

* Pet status visualization
* Proposal review
* Interaction history

---

#### 🪢 Leash (Mobile / React Native)

User control and security layer:

* Wallet connection
* Biometric authentication
* Explicit approval or rejection of proposals

> Leash is the only component that can authorize real-world effects.

---

#### 🔗 On-chain Programs (Rust / Solana)

Smart contracts defining:

* Degotchi pet identity (NFT)
* Pet ↔ User binding ("Leash")
* Permission and allowance constraints
* Immutable on-chain ownership logic

---

### Key Concepts

* **Pet-first design**
  Pets exist independently on-chain. Users adopt and bind to them.

* **Human-in-the-loop execution**
  All sensitive actions require explicit user approval.

* **Personality-driven behavior**
  Actions are influenced by pet traits, mood, and experience.

* **Social expression with consent**
  Degotchi can express decisions publicly (e.g. Twitter) only with user authorization.

## Complete data sequenceDiagram
---
```mermaid
sequenceDiagram
    autonumber
    participant S as Scheduler
    participant B as Brain Service
    participant A as API Layer
    participant U as User (Leash/Web)
    participant E as Execution Layer
    participant D as Database

    S->>B: Periodic Tick
    activate B
    B->>B: Load Pet State & Build Context
    
    rect rgb(240, 240, 240)
        Note right of B: Orchestrator Agents
        B->>B: Hunger / Mood / Investment
    end

    B->>D: Persist Proposal
    B->>A: Forward Proposal
    deactivate B

    A->>U: Notify User
    
    U->>E: Approve / Reject
    
    activate E
    E->>E: On-chain / Social Side Effects
    E->>B: Report Execution Result
    deactivate E

    activate B
    B->>D: Update & Save Pet State
    deactivate B
```

## System brain logics

```mermaid
sequenceDiagram
    autonumber
    participant S as Scheduler
    participant B as Brain
    participant O as Orchestrator
    
    S->>B: tick()
    activate B
    
    Note right of B: Data Loading
    B->>B: load_pet / user / market
    B->>B: Create DecisionContext
    
    B->>O: select_agent()
    activate O
    
    par Run Agents
        O->>O: HungerAgent.propose()
        and
        O->>O: MoodAgent.propose()
        and
        O->>O: InvestmentAgent.propose()
    end
    
    O-->>B: Return Selected Proposal
    deactivate O

    B->>B: save_proposal()
    deactivate B
```

## User concept decisions 
```mermaid
sequenceDiagram
    autonumber
    participant App as User App (Leash)
    participant API as API Layer
    participant Exec as Execution Layer
    participant Brain as Brain Service
    participant DB as Database

    App->>API: approve(proposal_id)
    activate API
    
    API->>API: validate_proposal()
    API->>API: check_pet_binding()
    API->>API: check_allowance()

    API->>Exec: Execute Payload
    deactivate API
    activate Exec

    alt On-Chain
        Exec->>Exec: Broadcast Tx
    else Social
        Exec->>Exec: Post Content
    else Internal
        Exec->>Exec: State Action
    end

    Exec->>Brain: Sync Result
    deactivate Exec
    
    activate Brain
    Brain->>DB: Update Pet State
    deactivate Brain
```
### Technology Stack

* **Blockchain**: Solana
* **Smart Contracts**: Rust
* **Backend / AI**: Python
* **Database**: Supabase (PostgreSQL)
* **Web**: React
* **Mobile**: React Native
* **Infrastructure**: Docker, Nginx, VPS
* **RPC**: Helius

---

### Disclaimer

Degotchi is an experimental project for educational and exploratory purposes.
It does not provide financial advice and does not perform autonomous trading.

---
## 🤝 Contributing

We are building in public. We welcome **Rustaceans**, **Pythonistas**, and **Flutter Devs**.

Please read our [CONTRIBUTING.md](https://github.com/Degotchi/.github/blob/main/CONTRIBUTING.md) before submitting a PR.
*Note: If you rug, I will find you.*

## 📄 License

Code is open-sourced under **MIT License** (Contracts) and **AGPL-3.0** (AI Core). See individual repos for details.

---

<div align="center">
  <p>
    <i>Built with ☕, 😭, and ⚡ on Solana.</i><br>
    <b>NOT FINANCIAL ADVICE. THE PET MIGHT LOSE YOUR MONEY.</b>
  </p>
</div>
