# Lista de Materiais (BOM)

Preços aproximados em reais (Brasil — agosto 2026). Valores podem variar.

## Componentes principais

| Qtd | Componente                          | Especificação / Observação              | Onde comprar (exemplos) |
|-----|-------------------------------------|------------------------------------------|-------------------------|
| 1   | ESP32-S3 DevKit (com PSRAM)         | N16R8 ou similar                         | Mercado Livre / AliExpress |
| 1   | Placa de áudio                      | AI-Thinker ESP32-Audio-Kit V2.2 (A1S) ou módulo ES8311 | Mercado Livre / AliExpress |
| 1   | SSR                                 | AQY212EH ou equivalente                  | Mercado Livre / Mouser / DigiKey |
| 1   | Optoacoplador                       | PC817                                    | Mercado Livre / lojas de eletrônica |
| 2   | Transformador de áudio              | 600 Ω : 600 Ω (tipo telefone)           | Mercado Livre / AliExpress |
| 2   | TVS                                 | SMAJ58CA (ou similar 58 V bidirecional)  | Mercado Livre |
| 1   | PTC                                 | Resetável ~100-150 mA                    | Mercado Livre |
| 1   | Resistor de carga                   | 180–270 Ω / 2 W                         | Qualquer loja de eletrônica |
| 2–4 | Capacitores de filme                | 1–2,2 µF / 100 V                         | Mercado Livre / lojas locais |
| —   | Resistores diversos                 | 10 kΩ, 15–22 kΩ, etc.                   | — |
| 1   | Caixa / suporte                     | Isolada                                  | — |

## Estimativa de custo

| Versão                          | Faixa de preço aproximada |
|---------------------------------|---------------------------|
| Completa (A1S + SSR + bons transformadores) | R$ 280 – 380             |
| Econômica (ESP32-S3 + MAX98357 + MOSFET)    | R$ 180 – 250             |

## Links úteis (exemplos)

> Os links abaixo são apenas referências. Sempre verifique disponibilidade e preço atual.

- Mercado Livre: busque por "ESP32-S3 PSRAM", "PC817", "transformador 600 ohm", "AQY212"
- AliExpress: mesmos termos (frete para o Brasil geralmente disponível)
- Lojas nacionais: FilipeFlop, Baú da Eletrônica, Eletrogate, etc.

## Observações

- Prefira componentes com boa isolamento (SSR em vez de relé mecânico comum).
- Não economize na proteção (TVS + PTC).
- O valor final do resistor de off-hook deve ser ajustado medindo a corrente de loop na sua central.
