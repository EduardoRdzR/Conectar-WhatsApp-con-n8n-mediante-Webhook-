# Guía Completa: Conectar WhatsApp a n8n con Webhook
En esta guía te enseñaré paso a paso a poder conectar tu flujo de n8n con WhatsApp en un servidor local, desde cero.

## Tabla de Contenidos 

- [Introducción](#introducción)
- [Instalar Docker](#instalar-docker)
---

## Introducción

Existen diferentes maneras de poder alojar un flujo de n8n y de conectarlo con WhatsApp, pero en esta ocasión lo haremos en un servidor local mediante Docker y usaremos un Webhook para comunicarnos con WhatsApp Cloud API.

---

## Instalar Docker

## Configurar Docker

## Entrar a n8n 

Con esto ya podríamos empezar a trabajar un flujo de n8n, pero como nosotros utilizaremos Webhook tendremos que hacer unos pasos adicionales para poder acceder desde internet a nuestro n8n local mediante un túnel (ngrok).
## Modificar el Entorno para poder Utilizar Webhook
## ngrok
### 1. Instalar ngrok
  - Entra a https://ngrok.com
  - Crea una cuenta
  - Descarga ngrok, puede ser desde la Microsoft Store

### 2. Configurar ngrok
  - Abre ngrok
  - Conéctalo con tu token
  ```
  ngrok config add-authtoken TU_TOKEN
  ```
  TU_TOKEN debe ser remplazado por el token que te da ngrok en el apartado "Your Authtoken", en la parte superior de la página.
  - Como n8n corre en http://localhost:5678
  - Entonces ejecuta:
  ```
  ngrok http 5678
  ```
  - Te aparecerá algo así:
  ```
  Forwarding    https://a1b2c3d4.ngrok-free.app -> http://localhost:5678
  ```
  Esa es tu URL pública, tenla a la mano ya que se necesitará para conectar con WhatsApp.

### 3. Configurar Docker 
  - Ve al documento docker-compose.yml y AGREGA las siguientes tres lineas en el apartado enviroment:
  ```
  environment:
    - WEBHOOK_URL=https://a1b2c3d4.ngrok-free.app/
    - N8N_EDITOR_BASE_URL=https://a1b2c3d4.ngrok-free.app
    - N8N_PROXY_HOPS=1
 ```
 Modificas las URLs a como te lo haya dado ngrok

     
