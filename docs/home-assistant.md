# Integração com Home Assistant e Apple Home

## Objetivo

Expor o interfone como **uma única campainha de vídeo** no Apple Home, com as seguintes características:

- Quando tocar, o Apple Home mostra a notificação de campainha
- O feed de vídeo exibido é o da câmera correspondente à porta/portão que chamou (usando Caller ID)
- Botão de abertura de porta disponível
- Voz bidirecional através do stack de intercom

## Entidades principais (ESP → HA)

| Entidade                        | Tipo            | Função                              |
|----------------------------------|-----------------|-------------------------------------|
| `binary_sensor.campainha_tocando`| binary_sensor   | Detecta o ring                      |
| `sensor.caller_id` / text_sensor | sensor          | Identifica qual porta chamou        |
| `button.abrir_porta`             | button          | Envia DTMF de abertura              |
| Entidades de áudio               | media / intercom| Voz bidirecional                    |

## Estratégia de câmera por Caller ID

1. O ESP envia o Caller ID (DTMF decodificado).
2. Uma automação ou template no Home Assistant seleciona a câmera correta.
3. Uma câmera "proxy" (ou a câmera selecionada) é vinculada à campainha via HomeKit Bridge.

### Exemplo de vinculação no HomeKit Bridge

```yaml
homekit:
  - name: "Campainha Bridge"
    port: 21064
    filter:
      include_entities:
        - binary_sensor.campainha_tocando
        - camera.interfone_atual          # câmera proxy
        - button.abrir_porta
    entity_config:
      camera.interfone_atual:
        name: "Interfone"
        linked_doorbell_sensor: binary_sensor.campainha_tocando
```

Com o `linked_doorbell_sensor`, o Apple Home trata o conjunto como uma campainha de vídeo única.

## Package de exemplo

Veja o arquivo:

```
homeassistant/packages/campainha.yaml
```

Ele contém um esqueleto de automação e entidades auxiliares.

## Observação sobre Matter

Embora o Matter 1.5+ já defina Video Doorbell, em meados de 2026 o suporte de controladores (especialmente Apple Home) ainda não é maduro o suficiente para um projeto DIY com interface analógica + switching dinâmico de câmera. Por isso a rota escolhida é **Home Assistant + HomeKit Bridge**.
