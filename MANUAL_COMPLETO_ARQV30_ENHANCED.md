# MANUAL COMPLETO - ARQV30 ENHANCED
## Análise Ultra-Detalhada de Mercado com IA Avançada

---

# ÍNDICE

1. [Visão Geral](#1-visão-geral)
2. [Arquitetura do Sistema](#2-arquitetura-do-sistema)
3. [Funcionalidades Principais](#3-funcionalidades-principais)
4. [Instalação e Configuração](#4-instalação-e-configuração)
5. [Variáveis de Ambiente](#5-variáveis-de-ambiente)
6. [Como Usar o Sistema](#6-como-usar-o-sistema)
7. [APIs e Endpoints](#7-apis-e-endpoints)
8. [Integração com Serviços Externos](#8-integração-com-serviços-externos)
9. [Estrutura de Dados](#9-estrutura-de-dados)
10. [Troubleshooting](#10-troubleshooting)
11. [Desenvolvimento e Customização](#11-desenvolvimento-e-customização)
12. [Casos de Uso Práticos](#12-casos-de-uso-práticos)

---

## 1. VISÃO GERAL

### 1.1 O que é o ARQV30 Enhanced?

O **ARQV30 Enhanced** é uma plataforma avançada de análise de mercado que utiliza inteligência artificial de última geração para gerar insights ultra-detalhados sobre avatares de cliente, posicionamento de mercado, estratégias de marketing e projeções de negócio.

### 1.2 Principais Características

- **IA Avançada**: Integração com Google Gemini Pro 2.5 para análises sofisticadas
- **Pesquisa Profunda**: WebSailor e DeepSeek para coleta de dados em tempo real
- **Análise de Anexos**: Processamento inteligente de documentos e arquivos
- **Interface Moderna**: Design responsivo e intuitivo
- **Relatórios Completos**: Geração automática de PDFs profissionais
- **Banco de Dados**: Persistência com Supabase PostgreSQL

### 1.3 Tecnologias Utilizadas

- **Backend**: Python 3.11+, Flask 2.3.3
- **Frontend**: HTML5, CSS3, JavaScript ES6+
- **IA**: Google Gemini Pro 2.5, DeepSeek API
- **Banco**: Supabase (PostgreSQL)
- **Processamento**: Pandas, OpenPyXL, PyPDF2
- **Web Scraping**: WebSailor, BeautifulSoup4

---

## 2. ARQUITETURA DO SISTEMA

### 2.1 Estrutura de Diretórios

```
arqv30_enhanced/
├── src/                          # Código fonte principal
│   ├── run.py                    # Aplicação Flask principal
│   ├── main.py                   # Ponto de entrada alternativo
│   ├── database.py               # Configuração do banco
│   ├── routes/                   # Rotas da API
│   │   ├── analysis.py           # Endpoints de análise
│   │   ├── user.py              # Endpoints de usuário
│   │   └── pdf_generator.py     # Geração de PDFs
│   ├── services/                 # Serviços de negócio
│   │   ├── gemini_client.py     # Cliente Gemini Pro
│   │   ├── deep_search_service.py # Busca profunda
│   │   ├── attachment_service.py # Processamento anexos
│   │   └── websailor_integration.py # WebSailor
│   ├── models/                   # Modelos de dados
│   │   ├── analysis.py          # Modelo de análise
│   │   └── user.py              # Modelo de usuário
│   ├── static/                   # Arquivos estáticos
│   │   ├── css/                 # Estilos CSS
│   │   ├── js/                  # JavaScript
│   │   └── logo.png             # Logo da aplicação
│   └── templates/                # Templates HTML
│       └── enhanced_index.html   # Interface principal
├── supabase/                     # Migrações do banco
│   └── migrations/               # Scripts SQL
├── webagent/                     # Agente WebSailor
│   ├── tools/                   # Ferramentas do agente
│   └── websailor_react_agent.py # Agente principal
├── requirements.txt              # Dependências Python
├── .env                         # Variáveis de ambiente
├── run.bat                      # Script Windows
└── install.bat                  # Instalação Windows
```

### 2.2 Fluxo de Dados

```mermaid
graph TD
    A[Interface Web] --> B[Flask Routes]
    B --> C[Services Layer]
    C --> D[Gemini Pro 2.5]
    C --> E[WebSailor Agent]
    C --> F[DeepSeek API]
    C --> G[Attachment Service]
    C --> H[Supabase DB]
    D --> I[Análise Gerada]
    E --> I
    F --> I
    G --> I
    I --> J[PDF Report]
    I --> K[JSON Response]
```

### 2.3 Componentes Principais

#### 2.3.1 Flask Application (run.py)
- **Função**: Servidor web principal
- **Responsabilidades**: 
  - Configuração da aplicação
  - Registro de blueprints
  - Middleware CORS
  - Health checks

#### 2.3.2 Services Layer
- **GeminiClient**: Comunicação com Google Gemini Pro 2.5
- **DeepSearchService**: Pesquisa profunda na internet
- **AttachmentService**: Processamento de arquivos
- **WebSailorIntegration**: Navegação web avançada

#### 2.3.3 Database Layer
- **Supabase**: Banco PostgreSQL gerenciado
- **SQLAlchemy**: ORM para Python
- **Migrações**: Controle de versão do schema

---

## 3. FUNCIONALIDADES PRINCIPAIS

### 3.1 Análise Ultra-Detalhada de Avatar

#### 3.1.1 O que faz:
Gera um perfil completo do cliente ideal incluindo:
- **Demografia**: Idade, gênero, renda, localização
- **Psicografia**: Valores, interesses, comportamentos
- **Dores e Desejos**: Problemas e aspirações
- **Gatilhos Mentais**: Motivadores de compra

#### 3.1.2 Como funciona:
```python
# Exemplo de análise de avatar
analysis_data = {
    'segmento': 'Produtos Digitais',
    'produto': 'Curso Online',
    'publico': 'Empreendedores 25-45 anos',
    'preco': 997.00
}

# Processamento com Gemini Pro 2.5
result = gemini_client.generate_ultra_detailed_analysis(
    analysis_data,
    search_context=web_research,
    attachments_context=uploaded_files
)
```

#### 3.1.3 Resultado entregue:
```json
{
  "avatar_ultra_detalhado": {
    "perfil_demografico": {
      "idade": "28-42 anos",
      "genero": "55% homens, 45% mulheres",
      "renda": "R$ 5.000 - R$ 20.000",
      "escolaridade": "Superior completo"
    },
    "perfil_psicografico": {
      "personalidade": "Ambiciosos, orientados a resultados",
      "valores": "Liberdade financeira, crescimento pessoal",
      "interesses": "Tecnologia, negócios, inovação"
    },
    "dores_especificas": [
      "Falta de conhecimento técnico atualizado",
      "Dificuldade para escalar o negócio",
      "Concorrência acirrada no mercado"
    ]
  }
}
```

### 3.2 Pesquisa Profunda na Internet

#### 3.2.1 WebSailor Agent
Sistema avançado de navegação web que:
- Realiza buscas contextuais
- Visita páginas relevantes
- Extrai informações específicas
- Verifica fatos e dados

#### 3.2.2 DeepSeek Integration
Busca iterativa com refinamento:
- Múltiplas iterações de pesquisa
- Refinamento automático de queries
- Consolidação de resultados
- Cache inteligente

#### 3.2.3 Exemplo de uso:
```python
# Pesquisa profunda
search_query = "tendências marketing digital 2024 Brasil"
context_data = {
    'segmento': 'Marketing Digital',
    'publico': 'PMEs brasileiras'
}

results = deep_search_service.perform_deep_search(
    search_query, 
    context_data
)
```

### 3.3 Sistema de Anexos Inteligente

#### 3.3.1 Tipos de arquivos suportados:
- **PDF**: Extração com PyPDF2
- **DOC/DOCX**: Processamento com python-docx
- **Excel**: Análise com pandas/openpyxl
- **CSV**: Processamento de dados tabulares
- **TXT/JSON**: Texto e dados estruturados

#### 3.3.2 Classificação automática:
- **Drivers Mentais**: Gatilhos psicológicos
- **Provas Visuais**: Demonstrações e evidências
- **Perfis Psicológicos**: Personas e comportamentos
- **Dados de Pesquisa**: Surveys e estatísticas

#### 3.3.3 Processamento:
```python
# Upload e análise de anexo
attachment_result = attachment_service.process_attachment(
    file=uploaded_file,
    session_id=user_session
)

# Resultado
{
    'success': True,
    'content_type': 'drivers_mentais',
    'extracted_content': 'Conteúdo processado...',
    'metadata': {
        'drivers_found': ['urgência', 'escassez', 'autoridade']
    }
}
```

### 3.4 Geração de Relatórios PDF

#### 3.4.1 Características:
- **Design Profissional**: Layout corporativo
- **Conteúdo Estruturado**: Seções organizadas
- **Gráficos e Tabelas**: Visualizações de dados
- **Branding**: Logo e identidade visual

#### 3.4.2 Seções do relatório:
1. **Resumo Executivo**
2. **Perfil do Avatar**
3. **Análise de Mercado**
4. **Estratégia de Marketing**
5. **Projeções Financeiras**
6. **Plano de Ação**
7. **Insights Exclusivos**

---

## 4. INSTALAÇÃO E CONFIGURAÇÃO

### 4.1 Pré-requisitos

#### 4.1.1 Sistema Operacional:
- Windows 10/11
- macOS 10.15+
- Linux Ubuntu 18.04+

#### 4.1.2 Software necessário:
- **Python 3.11+**: [Download](https://python.org)
- **Git**: [Download](https://git-scm.com)
- **Editor de código**: VS Code recomendado

### 4.2 Instalação Passo a Passo

#### 4.2.1 Clone o repositório:
```bash
git clone https://github.com/seu-usuario/arqv30_enhanced.git
cd arqv30_enhanced
```

#### 4.2.2 Windows (Automático):
```batch
# Execute o instalador
install.bat

# Inicie a aplicação
run.bat
```

#### 4.2.3 Linux/macOS (Manual):
```bash
# Crie ambiente virtual
python -m venv venv
source venv/bin/activate  # Linux/macOS
# ou
venv\Scripts\activate     # Windows

# Instale dependências
pip install -r requirements.txt

# Configure variáveis de ambiente
cp .env.example .env
# Edite o arquivo .env com suas chaves

# Execute a aplicação
cd src
python run.py
```

### 4.3 Verificação da Instalação

#### 4.3.1 Teste básico:
```bash
# Acesse no navegador
http://localhost:5000

# Verifique status da API
curl http://localhost:5000/api/app_status
```

#### 4.3.2 Resposta esperada:
```json
{
  "app_name": "ARQV30 Enhanced",
  "version": "2.0.0",
  "status": "running",
  "services": {
    "gemini": {"available": true},
    "websailor": {"available": true},
    "deep_search": {"available": true},
    "attachments": {"available": true}
  }
}
```

---

## 5. VARIÁVEIS DE AMBIENTE

### 5.1 Arquivo .env Completo

```env
# === CONFIGURAÇÕES BÁSICAS ===
FLASK_ENV=development
SECRET_KEY="sua-chave-secreta-super-segura-aqui"
CORS_ORIGINS=*
HOST=0.0.0.0
PORT=5000

# === BANCO DE DADOS SUPABASE ===
SUPABASE_URL=https://seu-projeto.supabase.co
SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
SUPABASE_SERVICE_ROLE_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
DATABASE_URL=postgresql://postgres:senha@db.projeto.supabase.co:5432/postgres

# === INTELIGÊNCIA ARTIFICIAL ===
GEMINI_API_KEY=AIzaSyBtLYVXxG61tu0CZ4uoLcO8pTWZuGteUFc
DEEPSEEK_API_KEY=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

# === WEBSAILOR (OPCIONAL) ===
GOOGLE_SEARCH_KEY=sua-chave-google-search-api
JINA_API_KEY=sua-chave-jina-reader-api
WEBSAILOR_ENABLED=true

# === CONFIGURAÇÕES AVANÇADAS ===
MAX_LLM_CALL_PER_RUN=40
MAX_LENGTH=31744
PYTHON_VERSION=3.11.0
```

### 5.2 Como Obter as Chaves de API

#### 5.2.1 Google Gemini Pro 2.5:
1. Acesse [Google AI Studio](https://makersuite.google.com)
2. Faça login com sua conta Google
3. Clique em "Get API Key"
4. Copie a chave gerada

#### 5.2.2 Supabase:
1. Acesse [Supabase](https://supabase.com)
2. Crie um novo projeto
3. Vá em Settings > API
4. Copie as chaves:
   - `anon/public key`
   - `service_role key`
   - URL do projeto

#### 5.2.3 DeepSeek (Opcional):
1. Acesse [DeepSeek](https://platform.deepseek.com)
2. Registre-se e faça login
3. Vá em API Keys
4. Gere uma nova chave

#### 5.2.4 Google Search API (Opcional):
1. Acesse [Google Cloud Console](https://console.cloud.google.com)
2. Crie um projeto
3. Ative a Custom Search API
4. Gere credenciais de API

### 5.3 Configuração do Banco de Dados

#### 5.3.1 Setup Supabase:
```sql
-- Execute as migrações
-- Arquivo: supabase/migrations/20250702082721_twilight_violet.sql

-- Criar tabela de análises
CREATE TABLE analyses (
    id SERIAL PRIMARY KEY,
    nicho VARCHAR(255) NOT NULL,
    produto VARCHAR(255),
    descricao TEXT,
    preco DECIMAL(10,2),
    publico VARCHAR(500),
    concorrentes TEXT,
    dados_adicionais TEXT,
    objetivo_receita DECIMAL(15,2),
    orcamento_marketing DECIMAL(15,2),
    prazo_lancamento VARCHAR(100),
    avatar_data JSONB,
    positioning_data JSONB,
    competition_data JSONB,
    marketing_data JSONB,
    metrics_data JSONB,
    funnel_data JSONB,
    market_intelligence JSONB,
    action_plan JSONB,
    comprehensive_analysis JSONB,
    status VARCHAR(50) DEFAULT 'pending',
    created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
    updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);
```

---

## 6. COMO USAR O SISTEMA

### 6.1 Interface Web

#### 6.1.1 Acesso:
- URL: `http://localhost:5000`
- Interface responsiva
- Compatível com todos os navegadores modernos

#### 6.1.2 Seções principais:
1. **Header**: Status do sistema e navegação
2. **Formulário**: Entrada de dados para análise
3. **Upload**: Área para anexos
4. **Resultados**: Exibição da análise
5. **Ações**: Download PDF, nova análise

### 6.2 Preenchimento do Formulário

#### 6.2.1 Campos obrigatórios:
- **Segmento de Mercado**: Nicho principal (ex: "Produtos Digitais")

#### 6.2.2 Campos opcionais:
- **Produto/Serviço**: Nome do produto
- **Público-Alvo**: Descrição do público
- **Preço**: Valor em reais
- **Concorrentes**: Lista de competidores
- **Objetivo de Receita**: Meta financeira
- **Orçamento Marketing**: Investimento disponível
- **Prazo de Lançamento**: Timeline do projeto

#### 6.2.3 Campos avançados:
- **Pesquisa Profunda**: Query para busca na internet
- **Anexos**: Upload de arquivos relevantes
- **Dados Adicionais**: Informações complementares

### 6.3 Sistema de Anexos

#### 6.3.1 Como usar:
1. Clique na área de upload ou arraste arquivos
2. Aguarde o processamento automático
3. Visualize o status de cada arquivo
4. Remova arquivos se necessário

#### 6.3.2 Tipos recomendados:
- **Drivers Mentais**: PDFs com gatilhos psicológicos
- **Provas Visuais**: Screenshots, gráficos, cases
- **Perfis Psicológicos**: Personas, pesquisas de comportamento
- **Dados de Pesquisa**: Planilhas, surveys, estatísticas

### 6.4 Processo de Análise

#### 6.4.1 Etapas automáticas:
1. **Validação**: Verificação dos dados inseridos
2. **Processamento**: Análise dos anexos
3. **Pesquisa**: Busca profunda na internet (se configurada)
4. **IA**: Processamento com Gemini Pro 2.5
5. **Consolidação**: Geração do relatório final
6. **Persistência**: Salvamento no banco de dados

#### 6.4.2 Tempo estimado:
- **Análise básica**: 30-60 segundos
- **Com pesquisa profunda**: 2-5 minutos
- **Com anexos complexos**: 1-3 minutos adicionais

### 6.5 Interpretação dos Resultados

#### 6.5.1 Seções do relatório:
1. **Avatar Ultra-Detalhado**:
   - Perfil demográfico e psicográfico
   - Dores, desejos e gatilhos mentais
   
2. **Escopo e Posicionamento**:
   - Posicionamento no mercado
   - Proposta de valor única
   
3. **Análise de Concorrência**:
   - Concorrentes diretos e indiretos
   - Gaps de oportunidade
   
4. **Estratégia de Marketing**:
   - Palavras-chave principais
   - Canais recomendados
   
5. **Métricas de Performance**:
   - KPIs essenciais
   - Benchmarks do setor
   
6. **Projeções e Cenários**:
   - Cenários conservador, realista e otimista
   - Projeções de receita
   
7. **Plano de Ação**:
   - Fases de implementação
   - Cronograma detalhado
   
8. **Insights Exclusivos**:
   - Descobertas únicas da IA
   - Oportunidades não óbvias

---

## 7. APIs E ENDPOINTS

### 7.1 Endpoints Principais

#### 7.1.1 Análise de Mercado
```http
POST /api/analyze
Content-Type: application/json

{
  "segmento": "Produtos Digitais",
  "produto": "Curso Online",
  "publico": "Empreendedores",
  "preco": 997.00,
  "query": "tendências mercado digital 2024",
  "session_id": "session_123"
}
```

**Resposta:**
```json
{
  "avatar_ultra_detalhado": {...},
  "escopo": {...},
  "analise_concorrencia_detalhada": {...},
  "estrategia_palavras_chave": {...},
  "metricas_performance_detalhadas": {...},
  "projecoes_cenarios": {...},
  "inteligencia_mercado": {...},
  "plano_acao_detalhado": {...},
  "insights_exclusivos": [...],
  "metadata": {
    "generated_at": "2024-01-15T10:30:00Z",
    "model": "gemini-pro",
    "search_context_used": true,
    "websailor_used": true,
    "attachments_used": true
  }
}
```

#### 7.1.2 Upload de Anexos
```http
POST /api/upload_attachment
Content-Type: multipart/form-data

file: [arquivo]
session_id: session_123
```

**Resposta:**
```json
{
  "status": "success",
  "message": "Anexo processado com sucesso",
  "session_id": "session_123",
  "attachment_id": "att_456",
  "content_type": "drivers_mentais",
  "content_preview": "Conteúdo extraído..."
}
```

#### 7.1.3 Busca Profunda
```http
POST /api/deep_search
Content-Type: application/json

{
  "query": "mercado produtos digitais Brasil 2024",
  "context": {
    "segmento": "Produtos Digitais",
    "publico": "Empreendedores"
  }
}
```

#### 7.1.4 Status da Aplicação
```http
GET /api/app_status
```

**Resposta:**
```json
{
  "app_name": "ARQV30 Enhanced",
  "version": "2.0.0",
  "status": "running",
  "timestamp": "2024-01-15T10:30:00Z",
  "services": {
    "gemini": {
      "available": true,
      "description": "Google Gemini Pro 2.5 para análise"
    },
    "websailor": {
      "available": true,
      "status": {...},
      "description": "WebSailor para navegação web avançada"
    },
    "deep_search": {
      "available": true,
      "description": "DeepSeek para busca profunda na internet"
    },
    "attachments": {
      "available": true,
      "stats": {...},
      "description": "Processamento de anexos"
    }
  }
}
```

### 7.2 Endpoints de Gerenciamento

#### 7.2.1 Listar Análises
```http
GET /api/analyses?limit=10&segmento=Produtos%20Digitais
```

#### 7.2.2 Obter Análise Específica
```http
GET /api/analyses/123
```

#### 7.2.3 Gerar PDF
```http
POST /api/generate_pdf
Content-Type: application/json

{
  "report_content": {...}
}
```

#### 7.2.4 Análise em Lote
```http
POST /api/analyze_batch
Content-Type: application/json

[
  {
    "segmento": "E-commerce",
    "produto": "Loja Virtual",
    "query": "tendências e-commerce 2024"
  },
  {
    "segmento": "SaaS",
    "produto": "Software B2B",
    "query": "mercado SaaS Brasil"
  }
]
```

### 7.3 Códigos de Resposta

| Código | Significado | Descrição |
|--------|-------------|-----------|
| 200 | OK | Requisição processada com sucesso |
| 201 | Created | Recurso criado com sucesso |
| 400 | Bad Request | Dados inválidos ou ausentes |
| 404 | Not Found | Recurso não encontrado |
| 413 | Payload Too Large | Arquivo muito grande (>10MB) |
| 500 | Internal Server Error | Erro interno do servidor |
| 503 | Service Unavailable | Serviço temporariamente indisponível |

---

## 8. INTEGRAÇÃO COM SERVIÇOS EXTERNOS

### 8.1 Google Gemini Pro 2.5

#### 8.1.1 Configuração:
```python
import google.generativeai as genai

genai.configure(api_key=os.getenv('GEMINI_API_KEY'))

model = genai.GenerativeModel(
    model_name="gemini-2.5-pro",
    generation_config={
        "temperature": 0.7,
        "top_p": 0.8,
        "top_k": 40,
        "max_output_tokens": 8192,
    }
)
```

#### 8.1.2 Uso:
- **Análise de texto**: Processamento de dados de entrada
- **Geração de insights**: Criação de análises detalhadas
- **Estruturação de dados**: Formatação em JSON
- **Contextualização**: Incorporação de pesquisas e anexos

#### 8.1.3 Limites:
- **Tokens por minuto**: 1,000,000
- **Requisições por minuto**: 1,000
- **Tokens por requisição**: 8,192 (output)

### 8.2 Supabase Database

#### 8.2.1 Configuração:
```python
from supabase import create_client, Client

supabase: Client = create_client(
    os.getenv('SUPABASE_URL'),
    os.getenv('SUPABASE_SERVICE_ROLE_KEY')
)
```

#### 8.2.2 Operações:
```python
# Inserir análise
result = supabase.table('analyses').insert({
    'nicho': 'Produtos Digitais',
    'produto': 'Curso Online',
    'avatar_data': {...},
    'status': 'completed'
}).execute()

# Buscar análises
analyses = supabase.table('analyses')\
    .select('*')\
    .eq('nicho', 'Produtos Digitais')\
    .order('created_at', desc=True)\
    .limit(10)\
    .execute()
```

#### 8.2.3 Recursos utilizados:
- **Row Level Security**: Controle de acesso
- **Real-time**: Atualizações em tempo real
- **Storage**: Armazenamento de arquivos
- **Edge Functions**: Processamento serverless

### 8.3 DeepSeek API

#### 8.3.1 Configuração:
```python
import requests

headers = {
    'Authorization': f'Bearer {os.getenv("DEEPSEEK_API_KEY")}',
    'Content-Type': 'application/json'
}

payload = {
    'model': 'deepseek-chat',
    'messages': [...],
    'max_tokens': 2000,
    'temperature': 0.3
}
```

#### 8.3.2 Funcionalidades:
- **Pesquisa iterativa**: Múltiplas consultas refinadas
- **Análise de tendências**: Identificação de padrões
- **Consolidação de dados**: Síntese de informações
- **Cache inteligente**: Otimização de performance

### 8.4 WebSailor Agent

#### 8.4.1 Componentes:
- **Search Tool**: Busca no Google
- **Visit Tool**: Extração de conteúdo web
- **React Agent**: Raciocínio multi-step
- **LLM Integration**: Processamento com IA

#### 8.4.2 Fluxo de trabalho:
1. **Planejamento**: Definição da estratégia de busca
2. **Execução**: Busca e navegação web
3. **Extração**: Coleta de informações relevantes
4. **Síntese**: Consolidação dos resultados
5. **Verificação**: Validação dos dados coletados

---

## 9. ESTRUTURA DE DADOS

### 9.1 Modelo de Análise

#### 9.1.1 Tabela `analyses`:
```sql
CREATE TABLE analyses (
    id SERIAL PRIMARY KEY,
    
    -- Dados básicos
    nicho VARCHAR(255) NOT NULL,
    produto VARCHAR(255),
    descricao TEXT,
    preco DECIMAL(10,2),
    publico VARCHAR(500),
    concorrentes TEXT,
    dados_adicionais TEXT,
    
    -- Dados financeiros
    objetivo_receita DECIMAL(15,2),
    orcamento_marketing DECIMAL(15,2),
    prazo_lancamento VARCHAR(100),
    
    -- Resultados da análise (JSONB)
    avatar_data JSONB,
    positioning_data JSONB,
    competition_data JSONB,
    marketing_data JSONB,
    metrics_data JSONB,
    funnel_data JSONB,
    market_intelligence JSONB,
    action_plan JSONB,
    comprehensive_analysis JSONB,
    
    -- Metadados
    status VARCHAR(50) DEFAULT 'pending',
    created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
    updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);
```

#### 9.1.2 Estrutura JSON do Avatar:
```json
{
  "avatar_ultra_detalhado": {
    "perfil_demografico": {
      "idade": "28-42 anos",
      "genero": "55% homens, 45% mulheres",
      "renda": "R$ 5.000 - R$ 20.000",
      "escolaridade": "Superior completo",
      "localizacao": "Grandes centros urbanos",
      "profissao": "Empreendedores, profissionais liberais"
    },
    "perfil_psicografico": {
      "personalidade": "Ambiciosos, orientados a resultados",
      "valores": "Liberdade financeira, crescimento pessoal",
      "interesses": "Tecnologia, negócios, inovação",
      "estilo_vida": "Dinâmico, conectado digitalmente",
      "comportamento_compra": "Pesquisa antes de comprar, valoriza qualidade"
    },
    "dores_especificas": [
      "Falta de conhecimento técnico atualizado",
      "Dificuldade para escalar o negócio",
      "Concorrência acirrada no mercado"
    ],
    "desejos_profundos": [
      "Alcançar liberdade financeira",
      "Ser reconhecido como especialista",
      "Ter mais tempo para família"
    ],
    "gatilhos_mentais": [
      "Urgência: Oportunidades limitadas",
      "Autoridade: Especialistas reconhecidos",
      "Prova social: Cases de sucesso"
    ]
  }
}
```

### 9.2 Estrutura de Anexos

#### 9.2.1 Sessão de anexos:
```python
session_storage = {
    'session_123': {
        'created_at': datetime.utcnow(),
        'attachments': [
            {
                'attachment_id': 'att_456',
                'original_filename': 'drivers_mentais.pdf',
                'file_path': '/tmp/session_123/att_456_drivers_mentais.pdf',
                'file_size': 1024000,
                'mime_type': 'application/pdf',
                'content_type': 'drivers_mentais',
                'extracted_content': 'Conteúdo extraído...',
                'metadata': {
                    'drivers_found': ['urgência', 'escassez', 'autoridade'],
                    'content_length': 5000,
                    'word_count': 800
                },
                'uploaded_at': '2024-01-15T10:30:00Z'
            }
        ]
    }
}
```

### 9.3 Cache de Pesquisas

#### 9.3.1 DeepSearch Cache:
```python
search_cache = {
    'query_hash_123': {
        'query': 'mercado produtos digitais Brasil 2024',
        'context_hash': 'ctx_456',
        'results': 'Resultados consolidados...',
        'timestamp': '2024-01-15T10:30:00Z',
        'iterations': 3
    }
}
```

---

## 10. TROUBLESHOOTING

### 10.1 Problemas Comuns

#### 10.1.1 Erro de Encoding Unicode
**Sintoma**: `UnicodeEncodeError: 'charmap' codec can't encode character`

**Solução**:
```python
# Já corrigido no código
def safe_print(text):
    try:
        print(text)
    except UnicodeEncodeError:
        import re
        clean_text = re.sub(r'[^\x00-\x7F]+', '', str(text))
        print(clean_text)
```

#### 10.1.2 Módulo WebSailor não encontrado
**Sintoma**: `ModuleNotFoundError: No module named 'services.websailor_react_agent'`

**Solução**: Arquivo já criado na correção. Verifique se existe:
```bash
ls src/services/websailor_react_agent.py
```

#### 10.1.3 CSS não encontrado
**Sintoma**: `GET /static/css/enhanced-styles.css HTTP/1.1" 404`

**Solução**: Arquivo CSS criado em `src/static/css/enhanced-styles.css`

#### 10.1.4 Erro de conexão com Supabase
**Sintoma**: `Connection timeout` ou `Authentication failed`

**Solução**:
1. Verifique as variáveis de ambiente
2. Teste a conexão:
```python
from supabase import create_client
client = create_client(SUPABASE_URL, SUPABASE_KEY)
result = client.table('analyses').select('count').execute()
```

#### 10.1.5 API Gemini não responde
**Sintoma**: `API key invalid` ou `Quota exceeded`

**Solução**:
1. Verifique a chave da API
2. Confirme os limites de uso
3. Teste a conexão:
```python
import google.generativeai as genai
genai.configure(api_key=API_KEY)
model = genai.GenerativeModel('gemini-pro')
response = model.generate_content('Teste')
```

### 10.2 Logs e Debugging

#### 10.2.1 Ativar logs detalhados:
```python
import logging
logging.basicConfig(level=logging.DEBUG)
```

#### 10.2.2 Arquivo de log:
```bash
tail -f src/arqv30_enhanced.log
```

#### 10.2.3 Debug do Flask:
```python
app.run(debug=True)
```

### 10.3 Performance

#### 10.3.1 Otimizações:
- **Cache**: Ativar cache de pesquisas
- **Conexões**: Pool de conexões do banco
- **Timeouts**: Configurar timeouts adequados
- **Compressão**: Ativar gzip no Flask

#### 10.3.2 Monitoramento:
```python
# Métricas de performance
import time
start_time = time.time()
# ... processamento ...
duration = time.time() - start_time
logger.info(f"Análise concluída em {duration:.2f}s")
```

---

## 11. DESENVOLVIMENTO E CUSTOMIZAÇÃO

### 11.1 Estrutura do Código

#### 11.1.1 Padrões utilizados:
- **MVC**: Model-View-Controller
- **Service Layer**: Lógica de negócio separada
- **Repository Pattern**: Acesso a dados
- **Dependency Injection**: Injeção de dependências

#### 11.1.2 Convenções:
- **Nomes**: snake_case para Python, camelCase para JavaScript
- **Imports**: Organizados por categoria
- **Docstrings**: Documentação em português
- **Type Hints**: Tipagem estática quando possível

### 11.2 Adicionando Novos Serviços

#### 11.2.1 Criar novo serviço:
```python
# src/services/novo_servico.py
import logging
from typing import Dict, Optional

logger = logging.getLogger(__name__)

class NovoServico:
    def __init__(self):
        self.api_key = os.getenv('NOVO_SERVICO_API_KEY')
    
    def is_configured(self) -> bool:
        return bool(self.api_key)
    
    def processar(self, dados: Dict) -> Optional[str]:
        try:
            # Lógica do serviço
            resultado = self._fazer_processamento(dados)
            logger.info("Processamento concluído com sucesso")
            return resultado
        except Exception as e:
            logger.error(f"Erro no processamento: {e}")
            return None
```

#### 11.2.2 Integrar no sistema:
```python
# src/routes/analysis.py
from services.novo_servico import NovoServico

novo_servico = NovoServico()

@analysis_bp.route('/novo_endpoint', methods=['POST'])
def novo_endpoint():
    data = request.get_json()
    resultado = novo_servico.processar(data)
    return jsonify({'resultado': resultado})
```

### 11.3 Customizando a Interface

#### 11.3.1 Modificar CSS:
```css
/* src/static/css/enhanced-styles.css */
:root {
    --primary-color: #sua-cor-primaria;
    --secondary-color: #sua-cor-secundaria;
}

.custom-component {
    background: var(--primary-color);
    border-radius: 10px;
    padding: 1rem;
}
```

#### 11.3.2 Adicionar JavaScript:
```javascript
// src/static/js/enhanced-analysis.js
function novaFuncionalidade() {
    // Sua lógica aqui
    console.log('Nova funcionalidade executada');
}

// Adicionar ao evento de inicialização
document.addEventListener('DOMContentLoaded', function() {
    novaFuncionalidade();
});
```

### 11.4 Testes

#### 11.4.1 Estrutura de testes:
```python
# tests/test_services.py
import unittest
from src.services.gemini_client import GeminiClient

class TestGeminiClient(unittest.TestCase):
    def setUp(self):
        self.client = GeminiClient()
    
    def test_connection(self):
        result = self.client.test_connection()
        self.assertTrue(result)
    
    def test_analysis(self):
        data = {'segmento': 'Teste'}
        result = self.client.generate_ultra_detailed_analysis(data)
        self.assertIsNotNone(result)

if __name__ == '__main__':
    unittest.main()
```

#### 11.4.2 Executar testes:
```bash
python -m pytest tests/
```

---

## 12. CASOS DE USO PRÁTICOS

### 12.1 Caso 1: Lançamento de Produto Digital

#### 12.1.1 Cenário:
Empreendedor quer lançar um curso online sobre marketing digital para pequenas empresas.

#### 12.1.2 Dados de entrada:
```json
{
  "segmento": "Marketing Digital",
  "produto": "Curso Marketing para PMEs",
  "publico": "Donos de pequenas empresas, 30-50 anos",
  "preco": 497.00,
  "objetivo_receita": 50000.00,
  "orcamento_marketing": 15000.00,
  "prazo_lancamento": "3 meses",
  "query": "tendências marketing digital PMEs Brasil 2024",
  "concorrentes": "Hotmart, Udemy, Coursera"
}
```

#### 12.1.3 Anexos recomendados:
- PDF com pesquisa sobre dores das PMEs
- Planilha com dados do mercado
- Screenshots de concorrentes
- Personas já desenvolvidas

#### 12.1.4 Resultado esperado:
- Avatar detalhado do dono de PME
- Estratégia de posicionamento
- Palavras-chave para SEO/SEM
- Funil de vendas otimizado
- Projeções financeiras realistas
- Plano de lançamento em 90 dias

### 12.2 Caso 2: Análise de Concorrência

#### 12.2.1 Cenário:
Empresa de SaaS quer entender melhor seus concorrentes e identificar oportunidades.

#### 12.2.2 Dados de entrada:
```json
{
  "segmento": "SaaS B2B",
  "produto": "Software de Gestão",
  "publico": "Gestores de empresas médias",
  "preco": 299.00,
  "query": "análise concorrentes SaaS gestão empresarial Brasil",
  "concorrentes": "Conta Azul, Omie, Bling, Tiny"
}
```

#### 12.2.3 Resultado esperado:
- Mapeamento completo da concorrência
- Análise de preços e posicionamento
- Gaps de mercado identificados
- Estratégias de diferenciação
- Oportunidades de nicho

### 12.3 Caso 3: Expansão de Mercado

#### 12.3.1 Cenário:
Empresa de fitness quer expandir para o mercado online.

#### 12.3.2 Dados de entrada:
```json
{
  "segmento": "Fitness Online",
  "produto": "Plataforma de Treinos",
  "publico": "Pessoas que treinam em casa, 25-45 anos",
  "preco": 97.00,
  "query": "mercado fitness online Brasil tendências 2024"
}
```

#### 12.3.3 Anexos úteis:
- Pesquisa com clientes atuais
- Dados de performance da academia física
- Análise de apps concorrentes

#### 12.3.4 Resultado esperado:
- Avatar do cliente online vs. presencial
- Estratégia de migração digital
- Pricing para mercado online
- Canais de aquisição digital
- Métricas de sucesso específicas

### 12.4 Caso 4: Validação de Ideia

#### 12.4.1 Cenário:
Profissional quer validar ideia de consultoria em neuroeducação.

#### 12.4.2 Dados de entrada:
```json
{
  "segmento": "Neuroeducação",
  "produto": "Consultoria para Pais",
  "publico": "Pais preocupados com educação dos filhos",
  "preco": 1997.00,
  "query": "mercado neuroeducação Brasil demanda pais"
}
```

#### 12.4.3 Resultado esperado:
- Validação do tamanho de mercado
- Perfil detalhado dos pais interessados
- Precificação adequada
- Canais de comunicação eficazes
- Estratégia de autoridade no nicho

---

## CONCLUSÃO

O **ARQV30 Enhanced** é uma ferramenta poderosa que combina inteligência artificial avançada, pesquisa profunda na internet e análise inteligente de dados para gerar insights ultra-detalhados sobre mercados e avatares de cliente.

### Principais Benefícios:

1. **Economia de Tempo**: Análises que levariam semanas são feitas em minutos
2. **Precisão**: IA de última geração garante insights precisos
3. **Completude**: Análise 360° do mercado e cliente
4. **Acionabilidade**: Resultados práticos e implementáveis
5. **Escalabilidade**: Processa múltiplas análises simultaneamente

### Próximos Passos:

1. **Instale** o sistema seguindo o guia de instalação
2. **Configure** as variáveis de ambiente com suas chaves
3. **Teste** com um caso simples primeiro
4. **Explore** todas as funcionalidades gradualmente
5. **Customize** conforme suas necessidades específicas

### Suporte:

Para dúvidas, problemas ou sugestões:
- **Documentação**: Este manual completo
- **Logs**: Arquivo `arqv30_enhanced.log`
- **Debug**: Mode debug do Flask
- **Comunidade**: Issues no repositório GitHub

---

**ARQV30 Enhanced v2.0** - Transformando dados em insights acionáveis com o poder da IA.