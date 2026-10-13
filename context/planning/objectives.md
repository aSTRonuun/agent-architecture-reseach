
Objetivo Geral:

Avaliar experimentalmente o trade-off entre desacoplamento e eficiência introduzido por uma camada de harness entre aplicações web e provedores de modelos de IA, confrontando o custo de substituição de provedor com o custo energético de execução, em comparação com uma integração direta sem essa camada.

Objetivos específicos:

Quantificar o custo de substituição de provedor de IA com e sem a camada, por métricas comportamentais e estruturais objetivas — casos de uso preservados após a troca, arquivos/linhas alterados, dependências diretas ao SDK, testes quebrados
Mensurar o impacto da camada sobre a eficiência energética da aplicação, comparando energia por requisição, energia por token e potência de GPU com e sem harness, sob critério de gating de corretude funcional 
Confrontar os dois resultados para caracterizar em que condições o desacoplamento obtido compensa o custo energético cobrado.

Feedback orientador
R: parece metodologia