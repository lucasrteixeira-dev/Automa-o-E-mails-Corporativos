# 🤖 Copiloto de IA para Comunicação Corporativa
### Automação de E-mails com Make.com + Google Gemini AI

## 📌 Sobre o Projeto

Este projeto consiste em uma automação inteligente construída no **Make.com** que integra o **Gmail** ao modelo de IA generativa **Google Gemini 2.5 Flash-Lite** para processar e responder automaticamente e-mails corporativos que contenham documentos em anexo.

A solução monitora a caixa de entrada do Gmail em tempo real. Ao detectar um e-mail não lido com anexo, extrai o documento, envia para análise pelo Gemini e retorna uma resposta estruturada e profissional ao remetente — tudo de forma automática, sem intervenção humana.

---

## ⚙️ Fluxo da Automação

```
[Gmail - Novo e-mail não lido com anexo]
           ↓
[Make.com - Extrai o anexo do e-mail]
           ↓
[Google Gemini - Upload do arquivo]
           ↓
[Google Gemini 2.5 Flash-Lite - Análise com IA]
           ↓
[Gmail - Envia resposta automática estruturada]
```

### Módulos utilizados no Make.com

| Ordem | Módulo | Função |
|-------|--------|--------|
| 1 | `google-email: triggerWatchNewEmails` | Monitora a caixa de entrada e captura e-mails não lidos com anexo |
| 2 | `gemini-ai: uploadAFile` | Faz upload do anexo para a API do Google Gemini |
| 3 | `gemini-ai: createACompletionGeminiPro` | Envia o arquivo + prompt para análise pelo Gemini 2.5 Flash-Lite |
| 4 | `google-email: sendAnEmail` | Envia a resposta gerada pela IA de volta ao remetente |

---

## 🧠 Prompt Utilizado

### System Instruction
```
Analise [{{5.name}}] em anexo. Extraia todos os dados presentes no documento
e verifique se há inconsistências ou possíveis indícios de fraude. Destaque
qualquer informação ilegível, divergente ou ausente. Caso identifique riscos,
explique de forma objetiva o motivo e sugira como validar ou corrigir o problema.
```

### User Prompt
```
Analise o documento anexo: {{5.name}}
O usuário fornecerá um arquivo contendo um documento. A sua principal fonte de
informação é este arquivo, e não o prompt.

Identifique a tarefa:
O usuário poderá solicitar extração de dados, validação de informações ou
verificação de inconsistências no documento.

Realize a análise:
Examine cuidadosamente o documento e extraia todas as informações relevantes.
Além disso:
- Verifique possíveis inconsistências (ex: datas incoerentes, divergência de dados)
- Identifique sinais de possível fraude ou adulteração

Apresente a solução:
Organize a resposta de forma estruturada, separando:
  - Dados extraídos
  - Validação/consistência
  - Possíveis problemas encontrados
  - Sugestões (se aplicável)

Mantenha o tom profissional. Apresente apenas a análise, sem introduções.
```

---

## 🛠️ Como Configurar

### Pré-requisitos
- Conta no [Make.com](https://make.com) (plano gratuito é suficiente)
- Conta Google com Gmail habilitado
- Chave de API do [Google AI Studio](https://aistudio.google.com/) (Gemini)

### Passo a Passo para Importar o Blueprint

1. Acesse sua conta no **Make.com**
2. Clique em **Scenarios** → **Create a new scenario**
3. No menu inferior, clique em **Import Blueprint**
4. Faça upload do arquivo `Integration_Gmail__Google_Gemini_AI_blueprint.json`
5. O cenário será importado com todos os módulos configurados

### Configurar as Conexões

Após importar, você precisará reconectar as integrações com suas próprias credenciais:

**Módulo Gmail (Watch New Emails)**
- Clique no módulo → **Add** → Faça login com sua conta Google
- Autorize as permissões solicitadas (leitura e envio de e-mails)

**Módulos Google Gemini**
- Clique em qualquer módulo Gemini → **Add**
- Insira sua chave de API do Google AI Studio
- Nomeie a conexão (ex: "Minha conexão Gemini")

### Ativar o Cenário
- Clique em **Run once** para testar
- Envie um e-mail com um documento em anexo para sua conta Gmail
- Verifique se o fluxo executou corretamente
- Após validação, ative o agendamento clicando no toggle **ON** no canto inferior esquerdo

---

## 📂 Estrutura do Repositório

```
📁 projeto/
├── 📄 README.md                                          ← Este arquivo
├── 📄 Integration_Gmail__Google_Gemini_AI_blueprint.json ← Blueprint da automação
└── 📄 Parte_Teorica.docx                                 ← Documento acadêmico
```

---

## 🎥 Vídeo Pitch

> 🔗 **[LINK DO VÍDEO - a ser preenchido após gravação]**  
> Plataforma: YouTube / Loom / Google Drive (não listado)  
> Duração: até 4 minutos

---

## ⚠️ Considerações Éticas e de Segurança

- **LGPD:** Documentos pessoais processados pela automação estão sujeitos à Lei Geral de Proteção de Dados. Certifique-se de obter consentimento dos titulares antes de processar seus dados.
- **Privacidade:** Os arquivos são enviados à API do Google Gemini. Verifique os termos de uso e políticas de retenção de dados do Google AI.
- **Uso responsável:** A solução deve ser utilizada apenas para fins legítimos e autorizados dentro do contexto organizacional.

---

## 🔧 Tecnologias Utilizadas

| Tecnologia | Função |
|---|---|
| Make.com | Plataforma de automação low-code |
| Gmail API | Trigger (leitura) e ação (envio de e-mail) |
| Google Gemini 2.5 Flash-Lite | Modelo LLM para análise de documentos |
| Google AI Studio | Gerenciamento de chaves de API |

---

*Projeto desenvolvido para a disciplina de Fundamentos de IA com foco em IA Generativa — UniFECAF*
