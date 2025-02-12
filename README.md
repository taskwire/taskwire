# TaskWire

TaskWire est un framework permettant de gérer des jobs asynchrones avec WebSockets et BullMQ. Il permet au frontend d'envoyer des tâches sans passer par des requêtes HTTP classiques, et de suivre leur exécution en temps réel.

## 🚀 Fonctionnalités

  - 📡 Communication en WebSockets : Pas besoin de polling, le serveur push les mises à jour.

  - 🔄 Gestion de queue avec BullMQ : Puissant et scalable.

  - 🛠 Client facile à utiliser : API simple pour envoyer des jobs et suivre leur état.

  - 📊 Traçabilité complète : Chaque job a un identifiant unique et un suivi détaillé.

  - ⚡ Middleware Express : Intégration simple avec les applications Express.

## ❓ Pourquoi TaskWire ?

Les architectures classiques basées sur HTTP nécessitent souvent de nombreux appels réseau synchrones, ce qui peut entraîner une latence accrue et une surcharge du serveur. 

TaskWire résout ce problème en :

  - Utilisant WebSockets pour une communication bidirectionnelle en temps réel.

  - Permettant un suivi transparent des jobs avec un système de queue robuste.

  - Réduisant la charge serveur grâce à une gestion asynchrone des tâches.

  - Offrant une intégration fluide avec Express et d'autres frameworks.

## 📦 Installation

Installez les différents packages selon vos besoins :

```shell
npm install @taskwire/server @taskwire/express-middleware @taskwire/client
```

Ou avec yarn :

```shell
yarn add @taskwire/server @taskwire/express-middleware @taskwire/client
```

## 🏗️ Utilisation

### 1️⃣ Backend (Node.js, BullMQ, WebSockets)

```typescript
import { TaskWireServer } from "@taskwire/server";

const server = new TaskWireServer({ port: 4000 });
server.start();
```

### 2️⃣ Middleware Express (optionnel)

```typescript
import express from "express";
import { taskWireMiddleware } from "@taskwire/express-middleware";

const app = express();
app.use(taskWireMiddleware());
app.listen(3000, () => console.log("Serveur Express démarré sur le port 3000"));
```

### 3️⃣ Frontend (WebSocket Client)

```typescript
import { TaskWireClient } from "@taskwire/client";

const client = new TaskWireClient("ws://localhost:4000");

(async () => {
  const result = await client.execute("DB_USER_CREATE_ONE", { name: "Alice" });
  console.log("Résultat du job :", result);
})();
```

## 🛠 Roadmap
  - 


## 📄 Licence

MIT License
