# Firmware

Esta pasta contém a configuração ESPHome do projeto.

## Arquivos

- `esphome/campainha.yaml` — Configuração principal (ainda com vários TODOs)
- `esphome/secrets.yaml.example` — Modelo de secrets

## Base

O projeto utiliza o stack de áudio e intercom do repositório:

https://github.com/n-IA-hane/esphome-intercom

Consulte a documentação oficial dele para os packages mais atualizados.

## Como começar

1. Instale o ESPHome.
2. Copie `secrets.yaml.example` para `secrets.yaml` e preencha os dados.
3. Ajuste os pinos GPIO de acordo com sua montagem de hardware.
4. Compile e faça o flash.

## Status

O YAML atual é um **esqueleto preliminar**. Muitas partes ainda estão marcadas com `TODO:` e precisam de implementação/teste real.
