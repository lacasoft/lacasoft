<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:161b22,100:0066CC&height=230&section=header&text=LACA-SOFT&fontSize=72&fontColor=ffffff&animation=fadeIn&fontAlignY=34&desc=Enterprise-Grade%20Digital%20Products%20%C2%B7%20Open%20Payment%20Infrastructure&descSize=18&descAlignY=54&descColor=58a6ff"/>

<div align="center">

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&duration=3200&pause=900&color=58A6FF&center=true&vCenter=true&multiline=true&repeat=true&width=760&height=100&lines=Digital+Product+Architect+%7C+0%E2%86%921+Builder;Construyo+producto%2C+protocolo+e+infraestructura+%F0%9F%9A%80;Del+MVP+al+sistema+que+aguanta+producci%C3%B3n)](https://laca-soft.com)

[![Website](https://img.shields.io/badge/laca--soft.com-0066CC?style=for-the-badge&logo=safari&logoColor=white)](https://laca-soft.com/)
[![CoatiPay](https://img.shields.io/badge/coatipay.com-F97316?style=for-the-badge&logo=ethereum&logoColor=white)](https://coatipay.com/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/lacasoft)
[![Followers](https://img.shields.io/github/followers/lacasoft?style=for-the-badge&color=0066CC&labelColor=0d1117&logo=github&logoColor=white&label=FOLLOWERS)](https://github.com/lacasoft?tab=followers)
![Views](https://komarev.com/ghpvc/?username=lacasoft&color=0066CC&style=for-the-badge&label=PROFILE+VIEWS)

**`Shipping desde 2014`** · **`Productos en producción`** · **`Open source en USDC/Base`**

</div>

<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif" width="100%">

## <img src="https://media.giphy.com/media/WUlplcMpOCEmTGBtBW/giphy.gif" width="30"> whoami

```typescript
const laca = {
  role:     "Digital Product Architect · 0→1 Builder",
  base:     "México 🇲🇽 · remoto",
  shipping: "desde 2014",
  building: ["CoatiPay — pagos USDC sin custodia", "Evva — asistente IA con memoria real"],
  live:     ["primelane.vip", "miguardia.app", "velada.mx", "yolopicho.com"],
  stack:    ["TypeScript", "NestJS", "Angular", "Solidity", "Python", "Flutter"],
  edge:     "entiendo el negocio antes de escribir la primera línea de código",
};
```

Tomo una idea en servilleta y la convierto en un producto digital rentable con arquitectura enterprise desde el día uno. Últimamente eso incluye **protocolo propio, contratos on-chain y SDKs publicados**, no solo aplicaciones.

```
💡 Idea → 🔍 Mercado → 📐 Product Design → 🏗️ Arquitectura → 🚀 MVP → 📈 Escala → 🌐 Open Source
```

> *No solo escribo código. Diseño sistemas de negocio completos que resuelven problemas reales y generan valor.*

<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif" width="100%">

## <img src="https://media.giphy.com/media/iY8CRBdQXODJSCERIr/giphy.gif" width="30"> Now Building — CoatiPay

<div align="center">

### **Pagos en USDC sin custodia y sin gas para quien paga**

[![Protocol](https://img.shields.io/badge/Apache--2.0-protocolo_abierto-D22128?style=flat-square&logo=apache&logoColor=white)](https://github.com/lacasoft/coatipay-protocol)
[![npm](https://img.shields.io/npm/v/@lacasoft/coatipay-sdk?style=flat-square&logo=npm&logoColor=white&label=%40lacasoft%2Fcoatipay-sdk&color=CB3837)](https://www.npmjs.com/package/@lacasoft/coatipay-sdk)
![Base](https://img.shields.io/badge/Base_Sepolia-verificado_en_Basescan-0052FF?style=flat-square&logo=coinbase&logoColor=white)
![NoToken](https://img.shields.io/badge/sin_token-sin_preventa-22c55e?style=flat-square)

</div>

Una **red abierta de enrutamiento de pagos**: la DX de Stripe (`paymentIntents.create`, webhooks firmados, dashboard) sobre USDC en Base, con liquidación on-chain y **cero intermediario que custodie el dinero**.

```mermaid
flowchart LR
    A["🛒 Comercio<br/>integra el SDK"] --> B["📄 Payment Intent"]
    B --> C["✍️ Pagador firma<br/>ERC-3009"]
    C --> D["🛰️ Nodeit enruta<br/>y paga el gas"]
    D --> E["⛓️ SettlementHub<br/>en Base"]
    E --> F["💵 USDC al comercio<br/>~1% al protocolo"]
    E --> G["🔔 Webhook<br/>payment_intent.settled"]
```

<table>
<tr>
<td width="50%">

**Lo que resuelve**
- ⛽ **Gasless para el pagador** — firma una autorización ERC-3009; el nodeit pone el gas
- 🤖 **x402** — micropagos por request para agentes de IA, en montos que Stripe no puede servir
- 🧩 **DX tipo Stripe** — SDKs en JS/TS, Python y PHP
- 🌐 **Sin lock-in** — self-host o cualquier nodeit de la red

</td>
<td width="50%">

**Lo que NO es**
- ❌ Un banco — los fondos van del pagador al comercio, nunca hay custodia
- ❌ Una pasarela fiat — convive con lo que ya usas
- ❌ Un proyecto de token — no existe token; los nodeits ganan USDC
- ⚠️ **Estado:** testnet (Base Sepolia), contratos verificados, **auditoría pendiente**

</td>
</tr>
</table>

<details>
<summary><b>👀 Ver el SDK en acción</b></summary>
<br>

```typescript
import { CoatiPay } from '@lacasoft/coatipay-sdk'

const relay = new CoatiPay({ apiKey: process.env.COATIPAY_SECRET_KEY! })

// Cobrar 10 USDC — mismas primitivas que ya conoces
const intent = await relay.paymentIntents.create({
  amount: 10_000_000,          // 6 decimales → 1 USDC = 1_000_000
  currency: 'usdc',
  chain: 'base',
  metadata: { orderId: 'order_123' },
})

// Cobrar por request a un agente de IA (x402)
app.addHook('preHandler', relay.x402.middleware({ price: 300_000 }))
```

</details>

<div align="center">

[![protocol](https://img.shields.io/badge/coatipay--protocol-Solidity-363636?style=for-the-badge&logo=solidity&logoColor=white)](https://github.com/lacasoft/coatipay-protocol)
[![js](https://img.shields.io/badge/JS%2FTS_SDK-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://github.com/lacasoft/coatipay-js-sdk)
[![py](https://img.shields.io/badge/Python_SDK-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://github.com/lacasoft/coatipay-python-sdk)
[![php](https://img.shields.io/badge/PHP_SDK-777BB4?style=for-the-badge&logo=php&logoColor=white)](https://github.com/lacasoft/coatipay-php-sdk)

</div>

<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif" width="100%">

## <img src="https://media.giphy.com/media/dWesBcTLavkZuG35MI/giphy.gif" width="30"> Open Source

### ⭐ Destacados

<table width="100%">
<tr>
<td width="50%" valign="top">

#### ⛓️ [coatipay-protocol](https://github.com/lacasoft/coatipay-protocol)

Contratos y protocolo de pagos USDC: settlement, registro de nodeits, staking y disputas. Desplegado y **verificado en Basescan**.

<a href="https://github.com/lacasoft/coatipay-protocol"><img src="https://img.shields.io/github/languages/top/lacasoft/coatipay-protocol?style=flat-square&color=0066CC&labelColor=0d1117"/></a> <img src="https://img.shields.io/github/stars/lacasoft/coatipay-protocol?style=flat-square&color=58a6ff&labelColor=0d1117"/> <img src="https://img.shields.io/github/last-commit/lacasoft/coatipay-protocol?style=flat-square&color=161b22&labelColor=0d1117"/> <img src="https://img.shields.io/github/license/lacasoft/coatipay-protocol?style=flat-square&color=22c55e&labelColor=0d1117"/>

</td>
<td width="50%" valign="top">

#### 🧩 [coatipay-js-sdk](https://github.com/lacasoft/coatipay-js-sdk)

SDK JS/TS con DX de Stripe sobre USDC en Base. Gasless (ERC-3009), webhooks firmados y x402. **Publicado en npm**.

<a href="https://github.com/lacasoft/coatipay-js-sdk"><img src="https://img.shields.io/github/languages/top/lacasoft/coatipay-js-sdk?style=flat-square&color=0066CC&labelColor=0d1117"/></a> <img src="https://img.shields.io/github/stars/lacasoft/coatipay-js-sdk?style=flat-square&color=58a6ff&labelColor=0d1117"/> <img src="https://img.shields.io/github/last-commit/lacasoft/coatipay-js-sdk?style=flat-square&color=161b22&labelColor=0d1117"/> <img src="https://img.shields.io/npm/v/@lacasoft/coatipay-sdk?style=flat-square&logo=npm&logoColor=white&label=npm&color=CB3837&labelColor=0d1117"/>

</td>
</tr>
<tr>
<td width="50%" valign="top">

#### 🤖 [evva-ai](https://github.com/lacasoft/evva-ai)

Asistente personal con memoria semántica real y acciones proactivas. 28 skills, 60 tools, Telegram + WhatsApp.

<a href="https://github.com/lacasoft/evva-ai"><img src="https://img.shields.io/github/languages/top/lacasoft/evva-ai?style=flat-square&color=0066CC&labelColor=0d1117"/></a> <img src="https://img.shields.io/github/stars/lacasoft/evva-ai?style=flat-square&color=58a6ff&labelColor=0d1117"/> <img src="https://img.shields.io/github/last-commit/lacasoft/evva-ai?style=flat-square&color=161b22&labelColor=0d1117"/> <img src="https://img.shields.io/github/v/release/lacasoft/evva-ai?style=flat-square&color=8b5cf6&labelColor=0d1117&label=release"/>

</td>
<td width="50%" valign="top">

#### 🛠️ [dev-starter-kit](https://github.com/lacasoft/dev-starter-kit)

Base coherente de Claude Code para todo el equipo: 14 agentes, 15 skills y 13 stacks, con enjambre híbrido.

<a href="https://github.com/lacasoft/dev-starter-kit"><img src="https://img.shields.io/github/languages/top/lacasoft/dev-starter-kit?style=flat-square&color=0066CC&labelColor=0d1117"/></a> <img src="https://img.shields.io/github/stars/lacasoft/dev-starter-kit?style=flat-square&color=58a6ff&labelColor=0d1117"/> <img src="https://img.shields.io/github/last-commit/lacasoft/dev-starter-kit?style=flat-square&color=161b22&labelColor=0d1117"/> <img src="https://img.shields.io/github/license/lacasoft/dev-starter-kit?style=flat-square&color=22c55e&labelColor=0d1117"/>

</td>
</tr>
<tr>
<td width="50%" valign="top">

#### 🔑 [git-account-manager](https://github.com/lacasoft/git-account-manager)

Multi-cuenta de GitHub por SSH en un solo comando. Bash puro, cero dependencias, Linux y macOS.

<a href="https://github.com/lacasoft/git-account-manager"><img src="https://img.shields.io/github/languages/top/lacasoft/git-account-manager?style=flat-square&color=0066CC&labelColor=0d1117"/></a> <img src="https://img.shields.io/github/stars/lacasoft/git-account-manager?style=flat-square&color=58a6ff&labelColor=0d1117"/> <img src="https://img.shields.io/github/last-commit/lacasoft/git-account-manager?style=flat-square&color=161b22&labelColor=0d1117"/> <img src="https://img.shields.io/badge/dependencias-0-22c55e?style=flat-square&labelColor=0d1117"/>

</td>
<td width="50%" valign="top">

#### 🅰️ [angular-dashboard-template](https://github.com/lacasoft/angular-dashboard-template)

Starter Angular enterprise: standalone components, Signals y design system con dark/light.

<a href="https://github.com/lacasoft/angular-dashboard-template"><img src="https://img.shields.io/github/languages/top/lacasoft/angular-dashboard-template?style=flat-square&color=0066CC&labelColor=0d1117"/></a> <img src="https://img.shields.io/github/stars/lacasoft/angular-dashboard-template?style=flat-square&color=58a6ff&labelColor=0d1117"/> <img src="https://img.shields.io/github/last-commit/lacasoft/angular-dashboard-template?style=flat-square&color=161b22&labelColor=0d1117"/>

</td>
</tr>
</table>

### 📚 Catálogo público


| Repo | Qué es | Stack | Actividad |
|:--|:--|:--|:--|
| **[coatipay-protocol](https://github.com/lacasoft/coatipay-protocol)** | Contratos y protocolo: settlement, registro de nodeits, staking y disputas | `Solidity` `Apache-2.0` | ![](https://img.shields.io/github/last-commit/lacasoft/coatipay-protocol?style=flat-square&label=&color=0066CC) |
| **[coatipay-js-sdk](https://github.com/lacasoft/coatipay-js-sdk)** | SDK JS/TS compatible con Stripe · publicado en npm | `TypeScript` `viem` | ![](https://img.shields.io/npm/v/@lacasoft/coatipay-sdk?style=flat-square&label=&color=CB3837) |
| **[coatipay-python-sdk](https://github.com/lacasoft/coatipay-python-sdk)** | SDK async para Python 3.11+ | `Python` `httpx` `pydantic` | ![](https://img.shields.io/github/last-commit/lacasoft/coatipay-python-sdk?style=flat-square&label=&color=0066CC) |
| **[coatipay-php-sdk](https://github.com/lacasoft/coatipay-php-sdk)** | SDK para PHP 8.1+ | `PHP` `Guzzle` | ![](https://img.shields.io/github/last-commit/lacasoft/coatipay-php-sdk?style=flat-square&label=&color=0066CC) |
| **[dev-starter-kit](https://github.com/lacasoft/dev-starter-kit)** | Config `.claude` unificada: 14 agentes, 15 skills y 13 stacks (backend/frontend/mobile/blockchain) con enjambre híbrido | `Node` `Claude Code` `MIT` | ![](https://img.shields.io/github/stars/lacasoft/dev-starter-kit?style=flat-square&label=%E2%AD%90&color=0066CC) |
| **[evva-ai](https://github.com/lacasoft/evva-ai)** | Asistente personal IA con memoria semántica real y acciones proactivas · 28 skills, 60 tools, Telegram + WhatsApp | `NestJS` `pgvector` `Claude` | ![](https://img.shields.io/github/stars/lacasoft/evva-ai?style=flat-square&label=%E2%AD%90&color=0066CC) |
| **[git-account-manager](https://github.com/lacasoft/git-account-manager)** | Multi-cuenta de GitHub por SSH en un comando · bash puro, cero dependencias | `Shell` `zero-deps` | ![](https://img.shields.io/github/stars/lacasoft/git-account-manager?style=flat-square&label=%E2%AD%90&color=0066CC) |
| **[angular-dashboard-template](https://github.com/lacasoft/angular-dashboard-template)** | Starter enterprise: standalone components, Signals y design system con dark/light | `Angular` `SCSS` | ![](https://img.shields.io/github/last-commit/lacasoft/angular-dashboard-template?style=flat-square&label=&color=0066CC) |
| **[ls-nestjs-template-cli](https://github.com/lacasoft/ls-nestjs-template-cli)** | CLI para generar proyectos NestJS con templates propios | `TypeScript` `CLI` | ![](https://img.shields.io/github/last-commit/lacasoft/ls-nestjs-template-cli?style=flat-square&label=&color=0066CC) |
| **[NestJS_Bootstrap](https://github.com/lacasoft/NestJS_Bootstrap)** | Template empresarial NestJS: arquitectura modular, seguridad y buenas prácticas | `NestJS` | ![](https://img.shields.io/github/last-commit/lacasoft/NestJS_Bootstrap?style=flat-square&label=&color=0066CC) |
| **[WhatsApp-Bot](https://github.com/lacasoft/WhatsApp-Bot)** · **[n8n_ig_post](https://github.com/lacasoft/n8n_ig_post)** · **[n8n_chatbot_web](https://github.com/lacasoft/n8n_chatbot_web)** | Automatización: bots de WhatsApp y workflows de n8n para contenido y atención | `TypeScript` `n8n` | ![](https://img.shields.io/badge/automation-0066CC?style=flat-square) |

<div align="center"><sub>⭐ Si algo de aquí te sirve, una estrella ayuda a que llegue a más gente.</sub></div>

<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif" width="100%">

## <img src="https://media.giphy.com/media/iY8CRBdQXODJSCERIr/giphy.gif" width="30"> Products in Production (0→1)

<details open>
<summary><b>🎟️ PrimeLane — Event Ticketing & Access Control SaaS</b></summary>
<br>

<img src="https://img.shields.io/badge/Status-Production-success?style=flat-square"/> <img src="https://img.shields.io/badge/Type-Multi--Tenant_SaaS-blue?style=flat-square"/> <img src="https://img.shields.io/badge/Architecture-Enterprise-purple?style=flat-square"/>

**Problema identificado:** Organizadores de eventos dependientes de plataformas con comisiones abusivas y sin control sobre su marca.

**Solución diseñada:** Plataforma multi-tenant con portales white-label por organizador, venta de boletos con Stripe, validación QR en tiempo real (SSE), 5 roles de usuario y dashboard analytics completo.

**Impacto:** Democratización de la venta de boletos — desde eventos independientes hasta grandes festivales, cualquier organizador gestiona y vende de forma autónoma.

**Stack:** Angular 20 • TailwindCSS • TypeScript • Stripe • QR/zxing • SSE • PWA • i18n

🔗 [primelane.vip](https://www.primelane.vip/)

</details>

<details open>
<summary><b>🏢 MiGuardia — Enterprise Access Control Platform</b></summary>
<br>

<img src="https://img.shields.io/badge/Status-Production-success?style=flat-square"/> <img src="https://img.shields.io/badge/Type-B2B_SaaS-blue?style=flat-square"/> <img src="https://img.shields.io/badge/Architecture-Enterprise-purple?style=flat-square"/>

**Problema identificado:** Control de acceso residencial ineficiente, basado en papel, sin trazabilidad.

**Solución diseñada:** PWA empresarial con validación QR, sincronización offline-first, alertas en tiempo real y bitácora completa de incidentes.

**Impacto:** Producto SaaS en producción sirviendo múltiples complejos residenciales.

**Stack:** Angular 19 • PWA • REST APIs • OAuth 2.0 • Real-time sync • Offline-capable

🔗 [miguardia.app](https://www.miguardia.app/)

</details>

<details open>
<summary><b>🤖 Evva — AI Personal Assistant (open source)</b></summary>
<br>

<img src="https://img.shields.io/badge/Status-Live-success?style=flat-square"/> <img src="https://img.shields.io/badge/Type-AI_Agent-8b5cf6?style=flat-square"/> <img src="https://img.shields.io/badge/License-MIT-22c55e?style=flat-square"/>

**Problema identificado:** Los asistentes de IA olvidan todo entre conversaciones y solo reaccionan; nunca se adelantan.

**Solución diseñada:** Agente con **memoria semántica persistente** (PostgreSQL + pgvector), briefing proactivo diario, recordatorios programados, visión, transcripción de voz y skills que se extienden en runtime. Vive en Telegram y WhatsApp.

**Escala funcional:** 28 skills · 60 tools · 2 canales · integraciones con Calendar, Gmail, Spotify, búsqueda web y finanzas personales.

**Stack:** NestJS • TypeScript • Claude (Vercel AI SDK) • Voyage embeddings • pgvector • BullMQ + Redis • grammY • pnpm workspaces

🔗 [github.com/lacasoft/evva-ai](https://github.com/lacasoft/evva-ai) · [probar el bot](https://t.me/evva_dev_bot)

</details>

<details open>
<summary><b>🧦 VELADA — Premium DTC Brand + E-commerce</b></summary>
<br>

<img src="https://img.shields.io/badge/Status-Production-success?style=flat-square"/> <img src="https://img.shields.io/badge/Type-DTC_E--commerce-orange?style=flat-square"/> <img src="https://img.shields.io/badge/Market-Premium-gold?style=flat-square"/>

**Oportunidad detectada:** Mercado de calcetines commoditizado, sin propuesta de valor diferenciada.

**Solución diseñada:** Marca premium posicionada en "sleep technology" con producto de bambú y e-commerce optimizado para conversión.

**Impacto:** Brand positioning único en mercado mexicano, e-commerce completo con gestión de inventario.

**Stack:** React • TypeScript API • E-commerce • Gestión de inventario

🔗 [velada.mx](https://velada.mx/)

</details>

<details open>
<summary><b>🍽️ YoLoPicho — Social Impact Platform</b></summary>
<br>

<img src="https://img.shields.io/badge/Status-Production-success?style=flat-square"/> <img src="https://img.shields.io/badge/Type-Social_Impact-red?style=flat-square"/> <img src="https://img.shields.io/badge/Model-B2B2C-teal?style=flat-square"/>

**Problema identificado:** Desconexión entre la voluntad de ayudar de las personas y quienes más lo necesitan.

**Solución diseñada:** Plataforma que conecta restaurantes con clientes, transformando micro-donativos en comidas reales para personas vulnerables, con trazabilidad completa y transparencia total.

**Impacto:** Ecosistema funcional de restaurantes, donantes y beneficiarios con seguimiento fotográfico de cada donación.

**Stack:** Flutter • Dart • Sistema de reportes • Notificaciones • Trazabilidad end-to-end

🔗 [yolopicho.com](https://yolopicho.com/)

</details>

<details>
<summary><b>📝 LACA-SOFT — Tech & Innovation Knowledge Hub</b></summary>
<br>

<img src="https://img.shields.io/badge/Status-Production-success?style=flat-square"/> <img src="https://img.shields.io/badge/Type-Content_Platform-lightblue?style=flat-square"/> <img src="https://img.shields.io/badge/Focus-Thought_Leadership-black?style=flat-square"/>

**Visión:** Un espacio donde tecnología, innovación e ideas disruptivas convergen.

**Contenido:** Blog especializado en startups, seguridad, desarrollo de software, AI/LLMs, y estrategia tecnológica para founders y equipos técnicos.

🔗 [laca-soft.com](https://laca-soft.com/)

</details>

<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif" width="100%">

## <img src="https://media2.giphy.com/media/QssGEmpkyEOhBCb7e1/giphy.gif?cid=ecf05e47a0n3gi1bfqntqmob8g9aid1oyj2wr3ds3mg700bl&rid=giphy.gif" width="30"> Enterprise Tech Stack

<div align="center">

### Languages
<p><img src="https://skillicons.dev/icons?i=ts,js,python,solidity,php,java,dart,bash" /></p>

### Backend & APIs
<p><img src="https://skillicons.dev/icons?i=nestjs,nodejs,express,fastapi" /></p>

![Play Framework](https://img.shields.io/badge/Play_Framework-92D13D?style=for-the-badge&logo=play&logoColor=white)
![Slim](https://img.shields.io/badge/Slim_Framework-74A045?style=for-the-badge&logo=php&logoColor=white)
![REST](https://img.shields.io/badge/REST_%2F_Webhooks-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![SSE](https://img.shields.io/badge/SSE_%2F_Realtime-EF4444?style=for-the-badge&logo=socketdotio&logoColor=white)

### Frontend & Mobile
<p><img src="https://skillicons.dev/icons?i=angular,react,nextjs,flutter,tailwind,html,css" /></p>

![PWA](https://img.shields.io/badge/PWA_%2F_Offline--first-5A0FC8?style=for-the-badge&logo=pwa&logoColor=white)
![Signals](https://img.shields.io/badge/Angular_Signals-DD0031?style=for-the-badge&logo=angular&logoColor=white)

### AI & Agents
![Claude](https://img.shields.io/badge/Claude-D97757?style=for-the-badge&logo=anthropic&logoColor=white)
![AI SDK](https://img.shields.io/badge/Vercel_AI_SDK-000000?style=for-the-badge&logo=vercel&logoColor=white)
![pgvector](https://img.shields.io/badge/pgvector_%2F_RAG-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![Voyage](https://img.shields.io/badge/Voyage_Embeddings-6366F1?style=for-the-badge)
![Whisper](https://img.shields.io/badge/Groq_Whisper-F55036?style=for-the-badge)
![MCP](https://img.shields.io/badge/MCP_%2F_Tool_Use-8B5CF6?style=for-the-badge&logo=modelcontextprotocol&logoColor=white)
![n8n](https://img.shields.io/badge/n8n_Workflows-EA4B71?style=for-the-badge&logo=n8n&logoColor=white)

### Web3 & Payments
![Solidity](https://img.shields.io/badge/Solidity-363636?style=for-the-badge&logo=solidity&logoColor=white)
![Base](https://img.shields.io/badge/Base-0052FF?style=for-the-badge&logo=coinbase&logoColor=white)
![USDC](https://img.shields.io/badge/USDC-2775CA?style=for-the-badge&logo=circle&logoColor=white)
![viem](https://img.shields.io/badge/viem-1E1E1E?style=for-the-badge&logo=ethereum&logoColor=white)
![ERC-3009](https://img.shields.io/badge/ERC--3009_gasless-627EEA?style=for-the-badge&logo=ethereum&logoColor=white)
![x402](https://img.shields.io/badge/x402_micropagos-F97316?style=for-the-badge)
![Stripe](https://img.shields.io/badge/Stripe-635BFF?style=for-the-badge&logo=stripe&logoColor=white)

### Data & Infra
<p><img src="https://skillicons.dev/icons?i=postgres,mysql,mongodb,redis,sqlite,docker,githubactions,vercel" /></p>

![BullMQ](https://img.shields.io/badge/BullMQ-DC382D?style=for-the-badge&logo=redis&logoColor=white)
![OAuth](https://img.shields.io/badge/OAuth_2.0-4285F4?style=for-the-badge&logo=auth0&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)
![pnpm](https://img.shields.io/badge/pnpm_workspaces-F69220?style=for-the-badge&logo=pnpm&logoColor=white)

</div>

<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif" width="100%">

## <img src="https://media.giphy.com/media/LmNwrBhejkK9EFP504/giphy.gif" width="30"> GitHub Activity

<div align="center">

<img width="98%" src="https://github-profile-summary-cards.vercel.app/api/cards/profile-details?username=lacasoft&theme=github_dark"/>

<img height="200" src="https://github-profile-summary-cards.vercel.app/api/cards/repos-per-language?username=lacasoft&theme=github_dark"/>
<img height="200" src="https://github-profile-summary-cards.vercel.app/api/cards/most-commit-language?username=lacasoft&theme=github_dark"/>

<img height="200" src="https://github-profile-summary-cards.vercel.app/api/cards/stats?username=lacasoft&theme=github_dark"/>
<img height="200" src="https://github-profile-summary-cards.vercel.app/api/cards/productive-time?username=lacasoft&theme=github_dark&utcOffset=-6"/>

<img width="60%" src="https://streak-stats.demolab.com?user=lacasoft&hide_border=true&theme=github-dark&background=0d1117&ring=58a6ff&fire=0066CC&currStreakLabel=58a6ff"/>

</div>

<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif" width="100%">

## 🔥 What Sets Me Apart

<div align="center">

| | Fortaleza | En la práctica |
|:---:|:---|:---|
| 🧭 | **BUSINESS + TECH** | Entiendo el "por qué" antes del "cómo": unit economics, monetización y arquitectura en la misma conversación |
| 🏗️ | **0→1 BUILDER** | Diseño productos completos, no features sueltas — de la hipótesis al producto en producción |
| ⛓️ | **PROTOCOL-LEVEL** | Bajo hasta contratos, staking y liquidación on-chain cuando el producto lo exige |
| 🤖 | **AI-NATIVE** | Agentes con memoria, RAG y tooling propio; no wrappers de chat |
| 🧬 | **ENTERPRISE DNA** | Multi-tenant, offline-first, OAuth 2.0, testing y CI desde el día uno |
| ✅ | **TRACK RECORD** | 5 productos en producción, SDKs publicados y +25 repos públicos desde 2014 |

</div>

<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif" width="100%">

## <img src="https://media.giphy.com/media/LnQjpWaON8nhr21vNW/giphy.gif" width="30"> Let's Build Something Remarkable

<div align="center">

¿Tienes una idea que necesita convertirse en producto?
¿Buscas a alguien que entienda tanto el negocio como la tecnología?

### **Hablemos.** 🤝

[![Contacto](https://img.shields.io/badge/laca--soft.com-0066CC?style=for-the-badge&logo=safari&logoColor=white)](https://laca-soft.com/)
[![Email](https://img.shields.io/badge/laca@laca--soft.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:laca@laca-soft.com)
[![CoatiPay](https://img.shields.io/badge/coatipay.com-F97316?style=for-the-badge&logo=ethereum&logoColor=white)](https://coatipay.com/)

<br>

<sub>**LACA-SOFT** • Enterprise-Grade Digital Products • México 🇲🇽</sub>

</div>

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:161b22,100:0066CC&height=120&section=footer"/>
