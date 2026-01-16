# Arco_N8N_Manuais
## 🧠 RAG: Manuais AVAC + Segurança 🔒

Este fluxo gere a leitura de manuais técnicos e permite consultas exclusivas para a equipa via WhatsApp.

### 📂 Parte 1: Ingestão Automática (Cima)
1. **Drive Trigger:** Monitoriza a pasta de manuais no Google Drive.
2. **Gestão de Loja:** Verifica na `Data Table` se a loja "doc_store" já existe.
   - **Se sim:** Usa o ID existente.
   - **Se não:** Cria uma nova loja no Google Gemini e guarda o ID.
3. **Indexação:** Envia o PDF para a Google Cloud para leitura futura.

### 💬 Parte 2: Chat Seguro (Baixo)
4. **WhatsApp Trigger:** Recebe a mensagem.
5. **⛔ Segurança (Portaria):** O nó `Verificar Permissão` valida se o número de telefone pertence à lista de técnicos autorizados. Se não pertencer, o fluxo para.
6. **Contexto:** O nó `Get Store Name` recupera o ID da loja atualizado da tabela.
7. **Agente RAG:**
   - Modelo: **Gemini Flash**.
   - Ferramenta: `search_documents` (lê o conteúdo técnico).
   - Responde apenas com base nos manuais.

---
**Custo:** Gerido via Google Cloud (Pay-as-you-go).
