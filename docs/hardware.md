# Hardware

## Visão Geral

O adaptador se conecta à porta RJ11 existente do terminal de interfone analógico e realiza:

- Detecção de ring (toque)
- Controle de off-hook (atendimento)
- Acoplamento de áudio bidirecional (2 fios → TX/RX)
- Geração e decodificação de DTMF (Caller ID + abertura de porta)

### Diagrama de blocos

```
RJ11 (Tip / Ring)
        │
   [Proteção primária]  ← TVS + PTC + Fusível
        │
   ┌────────────┐     ┌────────────┐
   │  Ring Detect  │     │  Off-hook    │
   │  (Opto)       │     │  (SSR + R)   │
   └────────────┘     └────────────┘
        │                    │
        │         ┌─────────┐
        │         │ Hybrid  │
        │         │ Áudio   │
        │         └─────────┘
        │              │
        └───────────────┬──────────┐
                     │ ESP32-S3 +│
                     │ Codec    │
                     └───────────┘
```

## Componentes principais

| Função              | Componente recomendado              | Observação                              |
|---------------------|-------------------------------------|-----------------------------------------|
| Proteção            | TVS SMAJ58CA + PTC                  | Obrigatório (ring alto)                 |
| Ring Detect         | PC817 + RC                          | Isolação ótica                         |
| Off-hook            | SSR AQY212EH + resistor 180–270 Ω  | Preferir SSR por isolamento             |
| Hybrid de áudio     | 2× transformador 600:600 Ω + caps   | Crítico para qualidade de voz           |
| MCU + Áudio         | ESP32-S3 (PSRAM) + ES8311 / A1S     | PSRAM obrigatória para o stack de áudio |

## Valores sugeridos (ponto de partida)

- Resistor de carga off-hook: comece com **220 Ω / 2 W** e ajuste medindo a corrente de loop.
- Resistor série do opto de ring: 15–22 kΩ.
- Capacitores de bloqueio DC no hybrid: 1–2,2 µF / 100 V (filme).

## Avisos importantes

- A linha possui tensão perigosa. Sempre desconecte antes de soldar.
- Mantenha isolamento galvânico entre a linha e o ESP32 sempre que possível.
- Teste cada bloco separadamente (ring → off-hook → áudio).

## Próximos passos de hardware

- [ ] Desenhar esquema completo em KiCad
- [ ] Validar valores finais do resistor de off-hook na central real
- [ ] Testar qualidade do hybrid com o stack de AEC
- [ ] Criar PCB (opcional)
