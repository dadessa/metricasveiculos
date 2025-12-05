# 🚀 Guia de Deploy - Dashboard de Veículos de Comunicação

Este guia contém instruções detalhadas para implantar o dashboard em diferentes plataformas.

## 📦 Arquivos Incluídos

```
dashboard-final-deploy/
├── src/
│   ├── main.py                 # Aplicação Flask principal
│   ├── templates/
│   │   └── index.html         # Interface completa do dashboard
│   └── dados_v5.json          # Dados locais (115 registros)
├── requirements.txt           # Dependências Python
├── README.md                 # Documentação completa
├── .gitignore               # Arquivos ignorados pelo Git
├── render.yaml              # Configuração para Render
├── Procfile                 # Configuração para Heroku
├── vercel.json              # Configuração para Vercel
└── DEPLOY.md                # Este guia de deploy
```

## 🌐 Deploy no Render (Recomendado)

### **1. Preparação**
```bash
# 1. Faça upload dos arquivos para seu repositório GitHub
git init
git add .
git commit -m "Dashboard de Veículos de Comunicação - Alagoas"
git branch -M main
git remote add origin https://github.com/seu-usuario/dashboard-veiculos-alagoas.git
git push -u origin main
```

### **2. Configuração no Render**
1. Acesse [render.com](https://render.com)
2. Conecte sua conta GitHub
3. Clique em "New Web Service"
4. Selecione seu repositório
5. Configure:
   - **Name**: `dashboard-veiculos-alagoas`
   - **Environment**: `Python 3`
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `cd src && python main.py`
   - **Auto-Deploy**: `Yes`

### **3. Variáveis de Ambiente**
```
FLASK_ENV=production
PORT=5000
```

### **4. Deploy Automático**
- O arquivo `render.yaml` já está configurado
- Deploy automático a cada push no GitHub
- URL gerada automaticamente pelo Render

## 🔥 Deploy no Heroku

### **1. Instalação do Heroku CLI**
```bash
# Instale o Heroku CLI
# https://devcenter.heroku.com/articles/heroku-cli
```

### **2. Deploy**
```bash
# 1. Login no Heroku
heroku login

# 2. Criar aplicação
heroku create dashboard-veiculos-alagoas

# 3. Deploy
git push heroku main

# 4. Abrir aplicação
heroku open
```

### **3. Configuração**
- O `Procfile` já está configurado
- Variáveis de ambiente via Heroku Dashboard
- Logs: `heroku logs --tail`

## ⚡ Deploy no Vercel

### **1. Instalação do Vercel CLI**
```bash
npm i -g vercel
```

### **2. Deploy**
```bash
# 1. Login no Vercel
vercel login

# 2. Deploy
vercel

# 3. Seguir instruções interativas
```

### **3. Configuração**
- O `vercel.json` já está configurado
- Deploy automático via GitHub
- Domínio personalizado disponível

## 🐳 Deploy com Docker

### **1. Criar Dockerfile**
```dockerfile
FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

EXPOSE 5000

CMD ["python", "src/main.py"]
```

### **2. Build e Run**
```bash
# Build
docker build -t dashboard-veiculos .

# Run
docker run -p 5000:5000 dashboard-veiculos
```

## 🔧 Configurações Importantes

### **Variáveis de Ambiente**
```bash
# Produção
FLASK_ENV=production
PORT=5000

# Desenvolvimento
FLASK_ENV=development
FLASK_DEBUG=True
```

### **URLs de Teste**
Após o deploy, teste estas URLs:
- `/` - Interface principal
- `/api/data` - Dados JSON
- `/api/refresh` - Atualizar dados
- `/api/stats` - Estatísticas

### **Monitoramento**
- **Logs**: Verifique logs da aplicação
- **Status**: Monitore uptime
- **Performance**: Tempo de resposta < 2s

## 📊 Dados e Integração

### **Google Sheets**
- **URL**: https://docs.google.com/spreadsheets/d/17TnGB6NpsziDec4fPH-d0TCQwk2LN0BAv6yjmIpyZnI/edit
- **Cache**: 5 minutos automático
- **Fallback**: Arquivo local `dados_v5.json`

### **Atualização de Dados**
1. **Automática**: Via Google Sheets (botão "Atualizar Dados")
2. **Manual**: Substituir `src/dados_v5.json`

## 🚨 Troubleshooting

### **Problemas Comuns**
1. **Erro 500**: Verificar logs da aplicação
2. **Dados não carregam**: Verificar Google Sheets
3. **Gráficos não aparecem**: Verificar JavaScript no console

### **Soluções**
1. **Logs detalhados**: Console do navegador
2. **Fallback local**: Sempre disponível
3. **Refresh manual**: Botão de atualização

## ✅ Checklist de Deploy

### **Antes do Deploy**
- [ ] Arquivos organizados
- [ ] Requirements.txt atualizado
- [ ] Dados locais incluídos
- [ ] Configurações de produção

### **Após o Deploy**
- [ ] URL funcionando
- [ ] Dados carregando
- [ ] Gráficos renderizando
- [ ] Filtros funcionando
- [ ] Busca operacional
- [ ] Análise de desertos ativa
- [ ] Responsividade mobile

### **Testes Finais**
- [ ] Botão "Atualizar Dados"
- [ ] Filtros sem duplicação
- [ ] Gráfico Top 10 Trimestral legível
- [ ] Tabela detalhada carregando
- [ ] KPIs de desertos de mídia

## 🎯 Resultado Esperado

### **Funcionalidades Ativas**
- ✅ **115 veículos** de comunicação
- ✅ **18 cidades** com cobertura
- ✅ **81 desertos de mídia** identificados
- ✅ **4 gráficos interativos**
- ✅ **Filtros sem duplicação**
- ✅ **Busca por nome**
- ✅ **Interface responsiva**

### **Performance**
- ✅ **Carregamento**: < 2 segundos
- ✅ **Uptime**: 99.9%
- ✅ **Mobile**: 100% compatível

---

**🚀 Dashboard pronto para produção com análise completa dos desertos de mídia em Alagoas!**
