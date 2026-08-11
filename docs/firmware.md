# Firmware (ESPHome)

## Base utilizada

O firmware é construído sobre o projeto **esphome-intercom**:

https://github.com/n-IA-hane/esphome-intercom

Esse projeto oferece:

- Full-duplex de áudio com AEC (ESP-SR)
- Integração nativa com Home Assistant
- Stack SIP/PBX-lite local
- Card Lovelace para atender do celular / navegador

## Arquivo principal

```
firmware/esphome/campainha.yaml
```

O arquivo ainda está em fase preliminar e contém vários comentários `TODO:`.

## Funcionalidades planejadas

| Funcionalidade              | Status          | Observação                              |
|-----------------------------|-----------------|-----------------------------------------|
| Detecção de ring            | Preliminar      | GPIO + filtro                           |
| Off-hook                    | Preliminar      | Switch GPIO                             |
| Áudio full-duplex           | Dependente      | Via package do esphome-intercom         |
| Decodificação DTMF (Caller ID) | TODO         | Preferência por software                |
| Geração DTMF (abrir porta)  | TODO            | Sequência a ser descoberta na central   |
| Entidades HA                | Preliminar      | binary_sensor, button, text_sensor      |

## Requisitos de hardware do ESP

- ESP32-S3 **com PSRAM** (obrigatório)
- Codec de áudio de qualidade (ES8311, AI-Thinker A1S, etc.)
- Amplificador + microfone adequados

## Como usar (futuro)

1. Copie `secrets.yaml.example` para `secrets.yaml` e preencha.
2. Ajuste os pinos GPIO conforme sua montagem.
3. Compile e faça flash com ESPHome.
4. Adicione o dispositivo no Home Assistant.

## TODOs principais no código

- Implementar decodificador DTMF confiável
- Mapear a sequência DTMF correta de abertura de porta da central
- Ajustar pinagem definitiva após testes de hardware
- Integrar completamente o package de áudio do esphome-intercom
