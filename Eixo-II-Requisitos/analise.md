## Requisito 1 - Correção da persistência de memória no ChromaDB

- Issue:#1031
- PR:#1081
- Link da issue: https://github.com/vanna-ai/vanna/issues/1031

### Descrição
Usuários relataram que o sistema não conseguia acessar dados previamente armazenados no ChromaDB, indicando falha na persistência da memória entre execuções.

### Código
A solução envolveu alterações na função de recuperação de coleções (_get_collection), incluindo:

- Implementação de inicialização tardia (lazy initialization) da função de embeddings
- Correção no processo de recuperação de coleções existentes
- Substituição de tratamento genérico de exceções por NotFoundError
- Adição de testes automatizados para validar persistência
- Melhoria na documentação do comportamento de persistência

A alteração remove a inicialização da função de embedding ao recuperar coleções existentes, evitando reprocessamento desnecessário e garantindo a persistência dos dados.

Além disso, houve melhoria no tratamento de exceções, tornando o sistema mais robusto.

### Processo de Discussão

A issue apresentou confirmação do problema por múltiplos usuários, indicando que se tratava de um erro recorrente no sistema.

No entanto, observa-se baixa interação técnica, sem discussões aprofundadas sobre possíveis soluções ou análise detalhada do problema.

A resolução ocorreu diretamente por meio de um Pull Request associado (#1081), sem grande debate prévio na issue.

### Análise
A issue foi rapidamente associada a um Pull Request, demonstrando boa rastreabilidade. A equipe implementou uma solução robusta, incluindo testes e documentação, o que indica maturidade no processo de desenvolvimento.

Além disso, a correção aborda diretamente a confiabilidade do sistema, um aspecto crítico em aplicações baseadas em memória de IA.

O processo evidencia uma boa capacidade de identificação e validação de problemas pela comunidade, mas demonstra fragilidade na etapa de análise e refinamento de requisitos.

A ausência de discussões estruturadas pode indicar falta de formalização no processo de engenharia de requisitos, o que pode impactar a qualidade das soluções propostas.

Observa-se ausência de práticas formais como RFCs ou discussões estruturadas, o que indica baixa maturidade no gerenciamento de requisitos.


## Requisito 2 - Suporte à integração com Gemini LLM

- Issue:#986
- Issue resolvida sem PR
- Link da Issue: https://github.com/vanna-ai/vanna/issues/986

### Processo de Discussão

A issue apresenta um processo colaborativo entre usuário e desenvolvedor. Após o relato do problema relacionado à importação do módulo GeminiLlmService, o desenvolvedor respondeu rapidamente, fornecendo orientações técnicas e sugerindo uma possível solução por meio de um commit específico.

O usuário realizou testes com a solução proposta e retornou com feedback confirmando a correção do problema, evidenciando um ciclo iterativo de validação.

### Código

A solução foi implementada por meio de um commit associado, que adicionou ou corrigiu a integração do módulo Gemini no repositório.

### Análise

O fluxo observado demonstra boa comunicação entre equipe e usuário, com resposta ágil e validação prática da solução. Esse tipo de interação evidencia um processo eficaz de gerenciamento de requisitos, mesmo sem formalização estruturada.

Entretanto, não foram identificados processos formais de documentação ou RFC, indicando uma abordagem mais informal no tratamento de requisitos.

## Requisito 3 - Correção da integração com PGVector

- Issue:#659
- PR:#660
- Link da Issue: https://github.com/vanna-ai/vanna/issues/659

### Descrição
A issue relata falhas na integração com o pgvector, incluindo erros de atributos inexistentes e problemas relacionados a execução assíncrona.

### Processo de Discussão

A issue apresentou forte interação entre desenvolvedores e usuários. O problema foi rapidamente identificado como possivelmente relacionado à falta de testes adequados e inconsistências na implementação.

Durante a discussão, foram levantadas hipóteses técnicas, como erros no uso de programação assíncrona e falhas na configuração de embeddings.

Um dos próprios contribuidores reconheceu a ausência de testes suficientes antes da integração da funcionalidade, evidenciando fragilidade no processo de validação.

Posteriormente, um Pull Request (#660) foi criado para corrigir os problemas identificados, seguido de validação e posterior lançamento de uma nova versão do sistema.

### Código

A solução foi implementada por meio do PR (#660), corrigindo a integração com pgvector e ajustando inconsistências na implementação.

O código apresenta inconsistências na implementação relacionadas ao uso de funções síncronas e assíncronas. Observa-se que métodos com a mesma finalidade foram definidos tanto com `async` quanto sem `async`, o que pode gerar conflitos durante a execução, como erros envolvendo corrotinas.

Além disso, há indícios de sobrescrita na definição da função de embeddings, onde diferentes implementações são atribuídas à mesma variável. Isso pode causar comportamento inesperado no sistema, dependendo de qual implementação for utilizada em tempo de execução.

Esses problemas indicam falta de padronização na arquitetura do código e ajudam a explicar os erros relatados na issue, especialmente aqueles relacionados a execução e integração com o PGVector.

### Análise

Este caso demonstra um processo completo de rastreabilidade, desde a identificação do problema até sua correção e validação em nova versão do sistema.

Entretanto, evidencia falhas no processo de qualidade, especialmente na ausência de testes antes da integração inicial da funcionalidade, o que resultou na introdução de erros no sistema.

Esse cenário reforça a importância de práticas de verificação e validação no desenvolvimento de software.