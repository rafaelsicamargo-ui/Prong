# 🧪 ContentLab - CRM de Validação & Inteligência WGSN com Gemini

O **ContentLab** é um MVP completo de CRM para criadores, gestores de social media e agências testarem hipóteses orgânicas, validarem ganchos e transformarem conteúdos em pipeline de vendas com inteligência preditiva via **API do Google Gemini**.

Projetado com estética **Whimsical**, experiência de colunas estilo **Trello (Drag and Drop nativo)** e arquitetura 100% estática pronta para deploy imediato no **Netlify** ou **GitHub Pages**.

---

## 🎨 As 4 Camadas da Aplicação

### 1. UI/UX e Design System (Inspiração: Whimsical & Trello)
- **Visual Whimsical**: Minimalista, cantos arredondados suaves (`rounded-3xl`), paleta pastel de alto contraste, amplo uso de white-space e alternância fluida entre **Light Mode** e **Dark Mode**.
- **Sidebar de Navegação**: Acesso direto entre:
  - 📊 **Visão Geral**: Dashboard com KPIs de validação, taxa de conversão em DMs e funil.
  - 📋 **Kanban de Testes**: Quadro com Drag & Drop suave e tags de identificação visual.
  - 🏆 **Biblioteca de Validados**: Mostruário automático dos posts de alta performance.
  - 🔮 **WGSN / Tendências**: Motor preditivo acionado pelo Gemini.
- **Kanban Estilo Trello**:
  - Colunas: **Backlog**, **Em Teste**, **Validado (Ouro)** e **Descartado**.
  - **Drag and Drop nativo e suave**: Arraste os cards entre as colunas.
  - Tags coloridas automáticas:
    - *Pilar do Funil*: Atração, Conexão, Conversão.
    - *Categoria do Gancho*: Dor, Desejo, Objeção.
    - *Formato*: Reels, Carrossel, Stories, Foto Única.

### 2. O Coração do CRM (Lógica de Validação & LocalStorage)
- Cada post é modelado como um objeto completo persistido no `localStorage`:
  - `id`, `titulo`, `formato`, `etapa_funil`, `categoria_gancho`, `gancho_texto`, `cta_utilizado`, `metricas` (`views`, `salvamentos`, `respostas_direct`), `status` e `created_at`.
- **Coleta Reativa Automática**: Qualquer card movido para a coluna **"Validado"** é instantaneamente sincronizado e exibido na aba **"Biblioteca de Validados"**.

### 3. O Motor Analítico (O Efeito WGSN via Gemini API)
- Localizado na aba **"WGSN / Gerador de Tendências"**.
- Botão **"Analisar Padrões e Gerar Calendário"**:
  - Coleta em tempo real o JSON dos posts validados.
  - Envia via `fetch` assíncrono para a API do Gemini com failover inteligente (`gemini-1.5-flash` / `gemini-3.8-flash`).
  - A IA atua como uma analista de tendências WGSN:
    1. Identifica o formato e gancho que mais converteram em leads.
    2. Emite um diagnóstico sintético do comportamento do público.
    3. Gera um cronograma estruturado de **4 semanas** replicando esses padrões.
- Botão **"➕ Importar Tudo para o Kanban"**: Carrega todos os novos posts gerados diretamente para a coluna Backlog do Kanban com 1 clique!

### 4. System Prompt Estrito (Regras de Negócio Inegociáveis)
- **Mentalidade SDR & Webhook Trigger**:
  - Toda CTA gerada força a interação do lead via comentário com palavra-chave ou direct (ex: *"Comente FUNIL"*, *"Mande DIRECT na DM"*), servindo de gatilho para automações de triagem em webhooks (ex: n8n, Manychat) antes de passar a oportunidade ao closer.
- **Oferta Transparente (Anti-Fake Anchoring)**:
  - Estritamente proibido criar copys com falsas ancoragens de preço (ex: *"De R$ 5.000 por R$ 97"*) ou escassez inventada. A comunicação é reta, limpa e focada no custo-benefício prático e ROI tangível.

---

## 🚀 Como Hospedar no Netlify ou GitHub Pages

Como a aplicação é construída em **HTML5, Tailwind CSS CDN e Vanilla JS puro**, ela não possui build step nem dependências de servidor:

### Opção 1: Netlify Drop (30 Segundos)
1. Acesse [app.netlify.com/drop](https://app.netlify.com/drop).
2. Arraste a pasta inteira deste projeto para a tela.
3. Seu SaaS estará online imediatamente com link SSL gratuito!

### Opção 2: GitHub Pages
1. Crie um repositório no GitHub e envie os arquivos (`git push`).
2. Acesse **Settings -> Pages**.
3. Selecione o branch `main` e a pasta `/ (root)`.
4. Clique em **Save**. Em segundos a URL pública estará ativa!

### Opção 3: Executar Localmente
- Dê um duplo clique no arquivo `run.bat` no Windows, ou
- Execute no terminal: `python start_server.py`.
- Acesse `http://localhost:3000`.
