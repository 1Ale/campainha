# Campainha

Adaptador de interfone analógico (compatível com sistemas tipo TDMI / Comunic) para **Home Assistant** e **Apple Home**.

O objetivo é transformar um terminal de interfone analógico existente em uma campainha inteligente com:

- Voz bidirecional (full-duplex)
- Detecção de toque (ring)
- Identificação da origem da chamada (Caller ID via DTMF)
- Botão de abertura de porta/portão
- Integração nativa com Home Assistant
- Exposição limpa para o Apple Home (via HomeKit Bridge) como uma única campainha de vídeo

> **Status atual:** Projeto em fase inicial (documentação + firmware preliminar + lista de hardware).

---

## Aviso de Segurança

A linha de interfone analógico opera com tensão contínua (tipicamente 22–60 V DC) e tensão de ring elevada (pode chegar a 150 Vrms).  
**Trabalhe sempre com a linha desconectada** durante a montagem e testes iniciais. Use proteções adequadas (TVS, PTC, isolamento).

---

## Estrutura do Repositório

```
campainha/
├── docs/                  # Documentação detalhada
├── hardware/              # BOM + esquemas (futuro)
├── firmware/              # Configuração ESPHome
├── homeassistant/         # Packages e exemplos de automação
├── LICENSE
└── README.md
```

---

## Documentação

- [Hardware](docs/hardware.md) — Esquema elétrico, proteções e considerações
- [Firmware](docs/firmware.md) — Visão geral do ESPHome + stack de áudio
- [Home Assistant](docs/home-assistant.md) — Integração, Caller ID → câmera e HomeKit Bridge
- [Roadmap](docs/roadmap.md) — Próximos passos

---

## Hardware

Lista completa de componentes e links de compra no Brasil:

→ [hardware/bom.md](hardware/bom.md)

---

## Firmware (ESPHome)

O firmware é baseado no projeto [esphome-intercom](https://github.com/n-IA-hane/esphome-intercom) (stack VoIP/full-duplex maduro).

Arquivo principal:

```
firmware/esphome/campainha.yaml
```

Ainda contém vários `TODO:` — está em fase preliminar.

---

## Licença

Este projeto está sob a licença **MIT**.

Veja o arquivo [LICENSE](LICENSE) para o texto completo.

---

## Contribuições

Pull requests são bem-vindos. Por enquanto o projeto ainda está em estágio inicial de documentação e protótipo.
