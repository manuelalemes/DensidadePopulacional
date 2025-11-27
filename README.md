# 🗺️ Cálculo de Densidade Populacional com Leaflet + Turf.js

Este projeto é um sistema web capaz de calcular **área geoespacial (m²)** e **densidade populacional (pessoas/m²)** a partir das coordenadas de um polígono inseridas pelo usuário.  
O sistema utiliza **Leaflet** no frontend para visualização do mapa e **Turf.js** no backend para cálculos geodésicos precisos, tudo implementado com **Node.js + TypeScript**.

<br><br>

## 🚀 Funcionalidades

- **Inserção** de número de pessoas e coordenadas  
- **Cálculo da área** em m²  
- **Cálculo da densidade** em pessoas/m²  
- **Renderização do polígono** no mapa  
- **Ajuste automático de zoom**  
- **Tipagem completa com TypeScript**  

---

## 📂 Estrutura do Projeto

src/
│

├── view.ts → Frontend (HTML, CSS, JS e Leaflet)

├── server.ts → Backend (Express + Turf.js)

└── model.ts → Interfaces da requisição e resposta

---

## ⚙️ Instalação e Execução

### 1️⃣ Inicializar o projeto
```bash
npm init -y
```

### 2️⃣ Instalar TypeScript
```bash
npm install typescript --save-dev
```

### 3️⃣ Criar tsconfig.json
```bash
npx tsc --init
```

### 4️⃣ Compilar TypeScript
```bash
npx tsc
```

### 5️⃣ Instalar tipos do Node 
```bash
npm install @types/node --save-dev
```

---

### 📦 Dependências do Backend
```bash
npm install express cors body-parser @turf/turf
npm install @types/express @types/cors @types/body-parser --save-dev
```

---

### ▶️ Executando o Projeto

Após compilar, execute:

```bash
npm run start
```
Acesse no navegador:

http://localhost:3000

---

## 🖥️ Frontend (view.ts)

O frontend é responsável por:
- Renderizar o mapa com Leaflet
- Receber inputs: número de pessoas + coordenadas
- Converter coordenadas para o formato requerido pelo backend
- Enviar tudo para a rota /density
- Receber área e densidade calculadas
- Desenhar o polígono no mapa

---

## 🔧 Backend (server.ts)

O backend:
- Recebe os dados via POST
- Usa Turf.js para criar o polígono GeoJSON e calcular a área (m²)
- Calcula a densidade:
  **densidade = pessoas ÷ área**
- Retorna JSON contendo:
   **area_m2**
   **density_p_m2**

---

## 📐 Models (model.ts)
Interfaces utilizadas:
**DensityRequest**
- people
- coordinates
**DensityResponse**
- area_m2
- density_p_m2

---

## 📊 Relação com o IBGE
O sistema utiliza a lógica oficial do IBGE:

**densidade = população / área**

Diferença:
- IBGE usa habitantes/km²
- O sistema usa pessoas/m²

Conversão:
```bash
pessoas/m² × 1.000.000 = habitantes/km²
```

---

## 🛠️ Tecnologias Utilizadas
- TypeScript
- Node.js + Express
- Leaflet.js
- Turf.js
- HTML + CSS + JavaScript
