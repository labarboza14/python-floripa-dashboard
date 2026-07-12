Python Floripa — Radiografia da Comunidade

Dashboard interativo com a análise consolidada dos meetups da Python Floripa: funil de inscrições, retenção, perfil de engajamento e canais de aquisição — construído a partir dos dados brutos de inscrição e check-in de 13 eventos (mar/2025 – mai/2026).

🔗 Ver o dashboard ao vivo: https://labarboza14.github.io/python-floripa-dashboard/


📊 O que tem aqui

SeçãoO que mostraFunil por eventoInscrições vs. check-ins vs. taxa de presença, evento a eventoRetenção% de participantes que voltaram em algum evento futuroPerfil da comunidadeDistribuição de 1.256 participantes por nível de engajamento (nunca compareceu → core community)Qualidade do retornoQuando as pessoas voltam: no próximo evento, em 2–3 eventos, ou nuncaProgramaçãoTemas mais frequentes nas palestras (14 categorias, 38 talks)Perfil & aquisiçãoDe onde vêm os participantes: cidade, faixa etária, canal (Instagram, Google, site próprio etc.) e qual canal converte melhorFidelidade individual & localRanking dos 20 participantes mais assíduos + comparação de presença por local de evento


🧠 Glossário rápido (pra quem não viu a base de dados)
Pensado pra quem só vai olhar o dashboard, sem contexto prévio.

Taxa de presença: % de inscritos que efetivamente fizeram check-in no evento.
Taxa de retenção: de quem foi a um evento, quantos % voltaram em qualquer evento futuro.
Retorno imediato / curto / longo prazo: se a pessoa voltou logo no próximo evento, em 2–3 eventos depois, ou só bem mais tarde.
Perfil da comunidade: classificação por frequência acumulada —
Nunca compareceu → Evento único → Recorrente → Frequente → Alta recorrência → Core community.
Perfil do evento: Aquisição (maioria de gente nova) vs. Equilibrado (mix de novos e recorrentes).
Canal de origem: por onde a pessoa chegou até a inscrição (Instagram, Google, link direto do site, etc.).


🗂️ Estrutura do projeto

python-floripa-dashboard/
├── index.html          # dashboard completo (HTML + CSS + JS, tudo em 1 arquivo)


O dashboard é um único arquivo autocontido: HTML, estilos e a biblioteca de gráficos (Chart.js) estão embutidos nele. Não depende de internet, CDN ou build step — abre em qualquer navegador, mesmo offline.


🔄 Como atualizar quando sair um novo evento
Os números do dashboard não são ao vivo — são um retrato gerado a partir da base de dados em um momento específico. Fluxo de atualização:


Rode novamente o notebook de análise (Colab) da comunidade, incluindo os dados do novo evento. Ele reprocessa as tabelas de apoio no Google Drive (analise_eventos, evolucao, retencao_eventos, perfil_comunidade, etc.).
Gere uma nova versão do index.html a partir dessas tabelas atualizadas.
Substitua o index.html no repositório (upload manual ou git push) — o GitHub Pages atualiza automaticamente.


🔒 Privacidade e dados

Este projeto não expõe dados sensíveis no sentido legal do termo (LGPD, Art. 5º, XIII) — não há informações de saúde, biometria, religião, orientação sexual, opinião política ou dado similar.

Ainda assim, há dados pessoais envolvidos, tratados com os seguintes cuidados:

E-mails: mascarados em qualquer lugar do dashboard (ex.: fe***@gmail.com).
Nomes no ranking de participação: reduzidos a primeiro nome + inicial do sobrenome (ex.: "Felipe A."), para diminuir a identificabilidade mantendo o reconhecimento dentro da comunidade.
Telefones, e-mails completos e demais campos de contato da base bruta: nunca entram neste dashboard público — ficam apenas na planilha original de uso interno da organização.
Dados agregados (cidade, faixa etária, canal de origem etc.): apresentados apenas em totais e percentuais, sem vínculo a indivíduos.

Se em algum momento a comunidade decidir que mesmo "primeiro nome + inicial" é identificável demais (grupos pequenos, nomes incomuns), o caminho mais seguro é substituir por posição no ranking sem nome (#1, #2...) ou por apelido escolhido pela própria pessoa.


🛠️ Stack

HTML + CSS puro
Chart.js v4 (embutido no arquivo, sem CDN)
Fontes: IBM Plex Sans / IBM Plex Mono / Fredoka (Google Fonts)
Dados processados via notebook Python (Google Colab) a partir dos exports brutos de inscrição/check-in

🤝 Sobre

Projeto mantido pela comunidade Python Floripa — meetups gratuitos de Python em Florianópolis e região. Dúvidas ou sugestões sobre os dados, abra uma issue neste repositório.
