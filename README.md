# Python Floripa — Radiografia da Comunidade

Dashboard interativo e dinâmico com a análise analítica contínua dos meetups da **Python Floripa**: funil de conversão, retenção histórica, perfil de engajamento, categorização de palestras e canais de aquisição.

🔗 **Acesse o Dashboard ao vivo:** [https://labarboza14.github.io/python-floripa-dashboard/](https://labarboza14.github.io/python-floripa-dashboard/)

---

## 📌 Visão Geral

O projeto consolida os dados de inscrições e check-ins dos meetups presenciais da comunidade, integrando a esteira analítica desde a coleta bruta até a visualização pública. 

A arquitetura opera de forma **reativa e desacoplada**: a interface web consome dinamicamente o arquivo estruturado `dados.json`, refletindo automaticamente métricas acumuladas, evolução temporal e rankings sem necessidade de alterações manuais no código-fonte da aplicação.

---

## 📊 Dimensões e Indicadores

| Dimensão | Indicadores | Objetivo |
| :--- | :--- | :--- |
| **Funil por Evento** | Inscrições, check-ins válidos e taxa de presença (%) | Acompanhar a conversão real e a perda entre inscrição e presença. |
| **Retenção Histórica** | Retorno imediato (próximo evento), curto prazo (2–3 edições) e longo prazo | Medir a capacidade de retenção contínua da comunidade ao longo do tempo. |
| **Perfil da Comunidade** | Distribuição: *Evento Único*, *Recorrente*, *Frequente*, *Alta Recorrência* e *Core Community* | Monitorar a maturidade da base e o crescimento de membros ativos. |
| **Grade de Conteúdo** | Volume de palestras por categoria temática | Identificar tendências técnicas e diversidade dos temas abordados. |
| **Fidelidade & Assiduidade** | Ranking dos participantes mais frequentes e distribuição por local | Reconhecer membros assíduos com proteção de privacidade. |

---

## 🏗️ Arquitetura da Solução

```mermaid
flowchart LR
    A[Relatórios Sympla .xlsx] --> B[(Google Drive /eventos)]
    C[Planilha de Controle /Temas] --> D[Pipeline Google Apps Script]
    B --> D
    D -->|Commit Automático API REST| E[(GitHub Repo /dados.json)]
    E -->|Deploy Contínuo| F[GitHub Pages /index.html]
Ingestão: Os relatórios de participantes (inscrições e check-ins) são armazenados em pasta dedicada no Google Drive.

Processamento & Governança: O pipeline desenvolvido em Google Apps Script cruza as participações com a base de temas, normaliza registros, calcula indicadores de assiduidade e aplica tratamento de anonimização.

Deploy Automatizado: O script compila os dados consolidados e executa commits automatizados do arquivo dados.json via GitHub REST API.

Camada de Apresentação: O frontend consome o JSON atualizado e renderiza os gráficos e tabelas de forma reativa.

🗂️ Estrutura do Repositório
Plaintext
python-floripa-dashboard/
├── index.html          # Aplicação web estática (Dashboard interativo com Chart.js)
├── dados.json          # Base agregada e anonimizada gerada pelo pipeline
└── README.md           # Documentação técnica e operacional do projeto
🔄 Fluxo de Atualização Operacional
Para registrar uma nova edição realizada da comunidade:

Salvar o arquivo de inscrições e presenças na pasta do Google Drive (/eventos).

Cadastrar as palestras do encontro na aba Temas da planilha de controle.

Acionar o menu 🚀 Python Floripa > Atualizar Dashboard no GitHub (ou botão de controle direto na planilha).

O pipeline recalcula as métricas históricas, atualiza os registros de auditoria e comita o dados.json. O GitHub Pages publica a nova versão em poucos segundos.

🔒 Privacidade e Governança de Dados (LGPD)
Em conformidade com as boas práticas de proteção de dados (Lei 13.709/2018):

Mascaramento de Identificadores: E-mails têm o nome de usuário parcialmente ofuscado (ex.: car***@dominio.com).

Anonimização no Ranking: Nomes de participantes são exibidos estritamente no formato Primeiro Nome + Inicial do Sobrenome (ex.: Mariana S.).

Campos Críticos: Telefones, documentos e e-mails integrais são estritamente restritos à base operacional interna e nunca exportados para a camada pública.

Agregação: Dados demográficos e de aquisição são expostos exclusivamente em formato estatístico consolidado.

🛠️ Tecnologias Utilizadas
Frontend: HTML5, CSS3, JavaScript (ES6+), Chart.js

Tipografia: Google Fonts (Fredoka, IBM Plex Sans, IBM Plex Mono)

Automação & Integração: Google Apps Script, Google Drive API, GitHub REST API

Hospedagem & CI/CD: GitHub Pages

🤝 Contribuições e Suporte
Projeto mantido pela comunidade Python Floripa.

Sugestões de novas análises, melhorias de interface ou relatos de inconsistências podem ser enviados através das Issues deste repositório.
