# Oscilia

Prototype de système embarqué d'acquisition de mouvements :
accéléromètre (STM32F4 Discovery) → UART → NUCLEO-WB55RG → BLE → téléphone / Raspberry Pi 4.

> Prototype technique, pas un dispositif médical validé.

## Architecture

```
STM32F4 Discovery          NUCLEO-WB55RG              Client BLE
(acquisition 100 Hz,  ──►  (validation paquets,  ──►  (LightBlue, puis
 double buffer RAM,  UART   service GATT Notify) BLE   Raspberry Pi + Python)
 paquets binaires+CRC)
```

## Organisation du dépôt (prévue)

| Dossier | Contenu |
|---|---|
| `firmware/f4-acquisition/` | Projet STM32CubeIDE du STM32F4 Discovery |
| `firmware/wb55-ble/` | Projet STM32CubeIDE du NUCLEO-WB55RG |
| `raspberry-pi/` | Client BLE Python (Bleak), affichage, export CSV |
| `docs/` | Format des paquets, CRC, brochage, notes de test |

## Étapes

1. [ ] Identifier et lire l'accéléromètre du STM32F4
2. [ ] Buffer RAM 100 Hz + double buffering
3. [ ] Liaison UART F4 → WB55 (paquets, CRC, séquence)
4. [ ] BLE seul sur le WB55 (test LightBlue)
5. [ ] Intégration UART + BLE
6. [ ] Client Raspberry Pi
7. [ ] Améliorations (pertes, latence, détection de mouvements, LoRa)
