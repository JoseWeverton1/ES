## Definição

A fase da Validação consiste em analisar se o software atende as necessidades e expectativas de quem o utiliza, conforme definido pelo processo de Validação (VAL) do MPS.BR e também pelo CMMI, que busca assegurar que o produto seja adequado ao uso pretendido.

## Pull Requests e Peer Review

Observa-se que o projeto Vanna adota práticas estruturadas tanto em nível de desenvolvimento quanto de colaboração entre os membros da equipe.
O projeto utiliza ativamente o mecanismo de Pull Requests no GitHub, evidenciado pela existência de 64 Pull Requests abertos e 273 Pull Requests concluídos, o que demonstra um fluxo contínuo de contribuições e revisões. Esse processo permite que alterações sejam analisadas antes de sua integração ao código principal, caracterizando a prática de peer review. A análise dos Pull Requests indica que o projeto promove a validação das implementações por meio da revisão colaborativa, possibilitando a identificação de inconsistências, melhorias e possíveis falhas antes da incorporação definitiva no sistema, prática alinhada às recomendações do CMMI para validação colaborativa dos produtos de trabalho.

## Análise breve da Arquitetura

A análise da estrutura interna do sistema, localizada no diretório src/vanna, evidencia uma arquitetura modular composta por diversos componentes, como agentes, ferramentas, integrações com modelos de linguagem e mecanismos de execução de tarefas. Essa organização demonstra uma separação clara de responsabilidades, com módulos específicos para interação com LLMs (core e integrations), execução de ferramentas (tools) e gerenciamento de capacidades do sistema (capabilities), o que também favorece práticas de validação incremental conforme sugerido pelo CMMI.

## Módulo de Avaliação

Adicionalmente, foi identificado um módulo de avaliação (evals) no diretório src, contendo arquivos como llm_comparison.py e basic.yaml, além de subpastas como benchmarks e datasets/sql_generation. Esses componentes indicam que o projeto realiza testes comparativos entre modelos de linguagem e utiliza conjuntos de dados específicos para avaliar a capacidade da IA na geração de consultas SQL, permitindo a medição de desempenho em cenários controlados.

Esses mecanismos demonstram uma preocupação com a qualidade e o desempenho dos modelos de linguagem, contribuindo para a evolução técnica do sistema. Entretanto, tais práticas estão mais associadas à avaliação experimental (evaluation) e benchmarking do que a um processo formal de validação em ambiente de produção, não garantindo plenamente os critérios de validação definidos tanto pelo MPS.BR quanto pelo CMMI.

## Conclusão

Apesar dessa estrutura robusta, não foram identificados componentes explícitos responsáveis pela validação das respostas geradas pelos modelos de linguagem. Em particular, não há evidências de mecanismos dedicados à verificação da qualidade semântica das saídas, como validação de respostas, filtragem de resultados ou tratamento sistemático de alucinações, o que representa uma lacuna importante frente às recomendações do CMMI para validação do comportamento do sistema.

Nesse sentido, observa-se que o projeto apresenta uma validação parcial, com forte foco em aspectos técnicos e de implementação, mas com limitações na validação do comportamento final percebido pelo usuário, situação também identificada como uma lacuna frente às práticas do CMMI, carecendo de mecanismos mais robustos para validação das saídas da IA, o que representa uma lacuna relevante considerando a natureza do sistema.
