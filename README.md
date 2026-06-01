# Projet-CAN-embarqu-STM32F4-Arduino
# CAN Bus Communication System – STM32F4 / Arduino

Communication CAN temps réel à 500 kbps entre un Arduino UNO (+ shield MCP2515)
et un STM32F407 Discovery, avec monitoring des trames via UART sur PC.

Projet académique – Informatique Industrielle & Systèmes Embarqués  
Université d'Évry Paris-Saclay | 2025-2026

---

## Architecture du système

Arduino UNO + CAN Shield → (CAN 500 kbps) → STM32F407 → (UART 115200 bps) → PC Terminal

---

## Matériel utilisé

| Composant | Modèle |
|---|---|
| Microcontrôleur | STM32F407VGT6 (Discovery) |
| Nœud CAN | Arduino UNO + MCP2515 |
| Transceiver CAN | MCP2551 |
| Interface PC | FT232RL (FTDI USB-UART) |
| Terminaison bus | Résistances 120Ω |

---

## Configuration technique

- **Fréquence CAN** : 500 kbps (APB1 42 MHz, Prescaler=6, BS1=11TQ, BS2=2TQ)
- **UART** : USART2, 115200 bps, 8N1, pins PA2/PA3
- **CAN** : pins PA11 (RX) / PA12 (TX), AF9
- **Horloge système** : HSI 16 MHz → PLL → SYSCLK 84 MHz

---

## Fonctionnement

1. L'Arduino génère des trames CAN et les envoie sur le bus
2. Le STM32 reçoit les trames via interruption FIFO0
3. Chaque trame est formatée (`ID / DLC / Data en hex`)
4. Les données sont transmises au PC via UART pour monitoring temps réel

---

## Outils

- STM32CubeIDE / STM32CubeMX
- Keil MDK-ARM
- Terminal série (ex: PuTTY, CoolTerm)

---

## Rapport complet

Voir `rapport.pdf` pour la documentation complète :
architecture, registres configurés, flowchart, code source commenté.
Voir `rapport.pdf` pour la documentation complète : architecture, registres configurés, flowchart, code source commenté.
