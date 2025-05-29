# MCP Basico (Model Context Protocol) Server

## Introducción
El MCP (Model Context Protocol) es un protocolo de comunicación entre modelos de lenguaje y otros sistemas. Su objetivo es facilitar la interacción entre diferentes modelos y permitir la creación de aplicaciones más complejas y eficientes.

## Instalación
Para instalar el MCP, puedes utilizar el siguiente comando, que instalará el SDK de TypeScript:

```bash
npm install @modelcontextprotocol/sdk
```

## Agregamos zod
```bash
npm add zod
```

## Ejemplo de uso
```typescript
import { McpServer } from "@modelcontextprotocol/sdk/server/mcp.js";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";
import { z } from "zod";

// Crear servidor
const server = new McpServer({
  name: "MyServer",
  version: "1.0.0",
});

// Definir herramientas
server.tool(
  'fetch-weather', // Título de la herramienta
  'Tool to fetch weather data of a city', // Descripción de la herramienta
  {
    city: z.string().describe('City name'), // Definición de los parámetros de entrada
  },
  async ({ city }) => {
    return {
      content: [
        {
          type: 'text',
          text: `The weather in ${city} is sunny.`
        }
      ]
    };
  }
);

// Definir el transporte
const transport = new StdioServerTransport();

// Conectar el servidor al transporte
await server.connect(transport);
```

## Ejecución usando el inspector
Para ejecutar el servidor usando el inspector, puedes utilizar el siguiente comando:

```bash
npx -y @modelcontextprotocol/inspector npx -y tsx main.ts
```

## Agregar MCP a la configuración de VSCode y activar agente para utilizarlo

```json
"mcp": {
    "servers": {
      "Weather": {
        "type": "stdio",
        "command": "npx",
        "args": [
          "-y",
          "tsx",
          "/Users/juan_/OneDrive/Documentos/Mis Proyectos/MCP/01/weather.ts"
        ]
      }
    }
  }
```