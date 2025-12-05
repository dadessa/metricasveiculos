# Dashboard de Veículos de Comunicação - Alagoas

Dashboard interativo para análise de veículos de comunicação do estado de Alagoas, com funcionalidades de filtragem, busca e análise de desertos de mídia.

## 🚀 Funcionalidades

### 📊 **Análise Completa**
- **KPIs Dinâmicos**: Total de veículos, aprovados, reprovados e cidades
- **Gráficos Interativos**: Distribuição por status, top 10 cidades, categorias e trimestral
- **Análise de Desertos de Mídia**: Identificação de municípios sem cobertura jornalística

### 🎛️ **Filtros e Busca**
- **Filtros por Cidade**: 18 cidades com veículos cadastrados
- **Filtros por Status**: Aprovado, Aprovado Parcial, Reprovado
- **Filtros por Categoria**: 6 categorias de audiência
- **Busca por Nome**: Localização rápida de veículos específicos

### 📈 **Visualizações**
- **Distribuição por Status**: Gráfico de barras colorido
- **Top 10 Cidades**: Ranking de cidades com mais veículos
- **Top 10 Categorias**: Distribuição por faixas de audiência
- **Top 10 Trimestral**: Ranking de performance por média trimestral

### 🏜️ **Desertos de Mídia**
- **81 Desertos identificados**: Municípios sem veículos de comunicação
- **12 Cobertura Crítica**: Municípios com apenas 1 veículo
- **9 Cobertura Adequada**: Municípios com 2+ veículos
- **79,4% de Desertos**: Do total de 102 municípios alagoanos

## 🛠️ Tecnologias

- **Backend**: Flask (Python)
- **Frontend**: HTML5, CSS3, JavaScript
- **Gráficos**: Canvas API nativa
- **Dados**: Integração com Google Sheets + fallback local
- **Hospedagem**: Compatível com Render, Heroku, Vercel

## 📦 Instalação

### **Pré-requisitos**
- Python 3.8+
- pip

### **Instalação Local**
```bash
# Clone o repositório
git clone <seu-repositorio>
cd dashboard-final-deploy

# Instale as dependências
pip install -r requirements.txt

# Execute o servidor
cd src
python main.py
```

### **Acesso Local**
- URL: http://localhost:5000
- API de dados: http://localhost:5000/api/data
- API de refresh: http://localhost:5000/api/refresh

## 🌐 Deploy no Render

### **1. Configuração no Render**
1. Conecte seu repositório GitHub
2. Configure as seguintes variáveis:
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `cd src && python main.py`
   - **Environment**: Python 3

### **2. Variáveis de Ambiente**
```
FLASK_ENV=production
PORT=5000
```

### **3. Estrutura de Arquivos**
```
dashboard-final-deploy/
├── src/
│   ├── main.py              # Aplicação Flask principal
│   ├── templates/
│   │   └── index.html       # Interface do dashboard
│   └── dados_v5.json        # Dados locais (fallback)
├── requirements.txt         # Dependências Python
├── README.md               # Documentação
└── .gitignore             # Arquivos ignorados
```

## 📊 Dados

### **Fonte Principal**
- **Google Sheets**: Integração direta com planilha online
- **URL**: https://docs.google.com/spreadsheets/d/17TnGB6NpsziDec4fPH-d0TCQwk2LN0BAv6yjmIpyZnI/edit

### **Fallback Local**
- **Arquivo**: `src/dados_v5.json`
- **Registros**: 115 veículos de comunicação
- **Atualização**: Manual via upload de nova planilha

### **Estrutura dos Dados**
```json
{
  "Nome do veículo": "string",
  "Cidade": "string",
  "Status": "APROVADO|REPROVADO|APROVADO PARCIAL",
  "Categoria": "string",
  "Cookies": "string",
  "Expediente": "string",
  "Endereço": "string",
  "Média Trimestral": "number",
  "Analytics": "string"
}
```

## 🎯 Funcionalidades Técnicas

### **API Endpoints**
- `GET /`: Interface principal do dashboard
- `GET /api/data`: Retorna dados dos veículos
- `GET /api/refresh`: Atualiza dados do Google Sheets
- `GET /api/stats`: Estatísticas gerais

### **Integração Google Sheets**
- **Cache**: 5 minutos de cache automático
- **Fallback**: Arquivo local quando Google Sheets indisponível
- **Múltiplas tentativas**: 3 URLs diferentes para maior confiabilidade

### **Análise de Desertos de Mídia**
- **102 municípios**: Lista completa de Alagoas
- **Categorização automática**: Desertos, críticos, adequados
- **Percentuais dinâmicos**: Cálculo em tempo real

## 🎨 Interface

### **Design Responsivo**
- **Desktop**: Layout em grid com 4 gráficos
- **Mobile**: Layout empilhado adaptativo
- **Cores**: Verde (aprovado), vermelho (reprovado), laranja (crítico)

### **Interatividade**
- **Filtros dinâmicos**: Atualização em tempo real
- **Busca instantânea**: Resultados conforme digitação
- **Tooltips**: Informações adicionais ao passar o mouse
- **Gráficos**: Valores formatados e labels legíveis

## 📈 Métricas

### **Dados Atuais (Dezembro 2024)**
- **115 veículos** cadastrados
- **87 aprovados** (75,7%)
- **5 reprovados** (4,3%)
- **23 aprovados parciais** (20%)
- **18 cidades** com cobertura
- **81 desertos de mídia** (79,4%)

### **Performance**
- **Carregamento**: < 2 segundos
- **Responsividade**: 100% mobile-friendly
- **Compatibilidade**: Chrome, Firefox, Safari, Edge

## 🔧 Manutenção

### **Atualização de Dados**
1. **Automática**: Via botão "Atualizar Dados" (Google Sheets)
2. **Manual**: Substituir arquivo `dados_v5.json`

### **Logs e Debug**
- **Console**: Logs detalhados para debug
- **Erros**: Tratamento robusto com fallbacks
- **Status**: Indicadores visuais de fonte de dados

## 📞 Suporte

### **Problemas Conhecidos**
- **Google Sheets**: Pode ficar temporariamente indisponível
- **Cache**: Dados podem levar até 5 minutos para atualizar

### **Soluções**
- **Fallback local**: Sempre disponível
- **Refresh manual**: Botão de atualização forçada
- **Logs detalhados**: Para diagnóstico de problemas

## 📄 Licença

Este projeto foi desenvolvido para análise de veículos de comunicação do estado de Alagoas.

---

**🌐 Dashboard em Produção**: https://77h9ikcykj56.manus.space

**📊 Dados sempre atualizados com análise completa dos desertos de mídia em Alagoas!**
