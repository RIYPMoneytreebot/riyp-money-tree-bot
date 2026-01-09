SECURITY.md
RIYP Money Tree Bot — Security Model & Threat Assumptions
Overview
RIYP Money Tree Bot is designed as a non-custodial, on-chain DeFi automation framework.
Security is treated as a first-class design constraint, not an afterthought.
This document outlines the security principles, threat assumptions, and mitigation strategies guiding development.
Core Security Principles
1. Non-Custodial by Design
The system never takes custody of user or DAO funds
All assets remain controlled by user-owned wallets or DAO treasury contracts
Strategy execution occurs only within user- or DAO-defined permissions
2. Explicit, Parameterized Execution
All automated actions are constrained by predefined parameters
No discretionary or arbitrary execution logic
Execution fails safely if constraints are violated
3. Minimal Trust Assumptions
No privileged admin keys controlling funds
No backdoors or emergency withdrawal authority over user assets
Governance and permissions are explicit and on-chain
Threat Model
Assumed Threats
The system is designed assuming:
Public blockchain adversaries
MEV-aware environments
Malicious external contracts
Oracle manipulation attempts
Configuration errors by users or DAOs
Out-of-Scope Threats
The following are considered out of scope:
Compromise of user private keys
Compromise of DAO governance processes
Protocol-level failures of integrated DeFi protocols
Risk Categories & Mitigations
1. Smart Contract Exploits
Risks:
Reentrancy
Integer overflow / underflow
Unauthorized execution
Mitigations:
Use of established Solidity patterns
Extensive unit and integration testing
Conservative external call handling
Planned third-party security review
2. Oracle Manipulation
Risks:
Price manipulation leading to unsafe execution
Mitigations:
Use of decentralized oracles (e.g., Chainlink)
Conservative thresholds for execution
No single-source oracle reliance
3. Execution Risk
Risks:
Slippage or adverse market movement
Partial execution failures
Mitigations:
Explicit slippage limits
Atomic transaction design
Fail-safe execution that reverts on unsafe conditions
4. Permission Misconfiguration
Risks:
Incorrect parameter settings by users or DAOs
Mitigations:
Clear documentation and examples
Sensible default parameters
Explicit permission checks in contracts
DAO Treasury Safety
For DAO use cases:
Role-based execution permissions are enforced
Execution authority can be limited to specific strategies
All actions are transparent and auditable on-chain
Upgrade & Governance Considerations
Contracts are designed to minimize upgrade requirements
If upgrades are necessary, they will be governed transparently
No unilateral upgrade authority over user or DAO funds
Audits & Reviews
Internal testing and peer review prior to mainnet usage
External audit planned before large-scale adoption
Security issues will be disclosed responsibly
Responsible Disclosure
Security issues may be reported via GitHub issues or direct contact with the maintainer.
Disclaimer
This software is experimental. Users and DAOs should understand and accept the risks associated with on-chain automation and DeFi protocol interactions.
Maintainer
Aaron C. Merlo
Founder & Lead Developer
