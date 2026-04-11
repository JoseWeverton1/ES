## Definição

A fase da Verificação consiste em analisar e testar se o software foi implementado da maneira que foi planejado. Essa etapa tem como principal objetivo garantir que o código está correto e funcionando conforme os requisitos definidos, sendo realizada por meio de testes automatizados, integração contínua e outros mecanismos de controle, conforme estabelecido pelo processo de Verificação (VER) do MPS.BR e também pelas práticas de Verificação do CMMI, que enfatizam a análise sistemática dos produtos de trabalho ao longo do desenvolvimento,ou seja,é necessário estar sempre verificando o que está sendo desenvolvido e não apenas ao entregar o produto.

## Workflows de Integração Contínua(CI)

No projeto Vanna, foram identificados mecanismos de verificação baseados em pipelines de Integração Contínua (CI), configurados na pasta .github/workflows. Esses workflows automatizam processos essenciais sempre que há alterações no repositório, contribuindo para a validação técnica do código, em alinhamento com a recomendação do MPS.BR e do CMMI de realização contínua de atividades de verificação.
Um dos principais workflows analisados foi o arquivo tests.yml, responsável pela execução de testes automatizados. Esse processo é acionado automaticamente a cada atualização na branch principal (main), conforme demonstrado no trecho abaixo:

on:
 push:
 branches:
 - main
   
Esse comportamento garante que toda modificação relevante no código seja imediatamente verificada, o que está em conformidade com as práticas do MPS.BR e do CMMI,que enfatiza a identificação antecipada de problemas por meio de verificações sistemáticas.

O workflow realiza a configuração do ambiente, instalação de dependências e execução dos testes por meio da ferramenta tox, conforme ilustrado a seguir:

name: Install pip
 run: |
 python -m pip install --upgrade pip
 pip install tox
name: Run tests
 run: tox
 
A execução do comando tox permite a automatização dos testes em diferentes ambientes, contribuindo para uma verificação mais robusta do sistema, prática alinhada com a recomendação do MPS.BR de utilização de técnicas sistemáticas de verificação, bem como com o CMMI, que incentiva a verificação em múltiplos contextos de execução.

Além disso, o workflow utiliza variáveis de ambiente para integração com diferentes serviços externos:

env:
 OPENAI_API_KEY: ${{ secrets.OPENAI_API_KEY }}
 ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}
 
Isso indica que os testes podem envolver interações reais com APIs de modelos de linguagem, ampliando o escopo da verificação e reforçando a cobertura dos testes, o que também está alinhado às práticas do CMMI de validação técnica dos componentes integrados.

Outro workflow identificado foi o arquivo python-publish.yaml, que é executado quando uma nova versão do sistema é publicada:

on:
 release:
 types: [published]

Esse processo realiza a construção do pacote Python e sua posterior publicação:
name: Build package
 run: python -m build
name: Publish package
 uses: pypa/gh-action-pypi-publish@...
 
Embora esse workflow não execute testes diretamente, ele contribui para a verificação ao garantir que o sistema pode ser corretamente empacotado e distribuído, reduzindo riscos de falhas em ambientes de produção, o que também está alinhado com a garantia de qualidade proposta pelo MPS.BR e com o CMMI, que considera a verificação de artefatos de entrega como parte essencial do processo.

## Pasta de Testes

Também foi analisada a pasta de testes do projeto, que apresenta uma estrutura abrangente de verificação, cobrindo diferentes camadas do sistema. Essa diversidade está de acordo com a orientação do MPS.BR de realizar verificações em múltiplos produtos de trabalho, além de atender às recomendações do CMMI, que enfatiza a verificação de diferentes componentes e níveis do sistema,abaixo explícito a análise de cada arquivo de teste:

O arquivo **conftest.py** é utilizado como base de configuração dos testes, sendo responsável por definir fixtures e preparar o ambiente de execução, contribuindo para a padronização e repetibilidade dos testes, prática também incentivada pelo CMMI.

Os arquivos **test_agent_memory.py** e **test_agent_memory_sanity.py** estão relacionados à validação do mecanismo de memória dos agentes, verificando a capacidade do sistema de armazenar e recuperar informações corretamente, o que contribui para a verificação funcional do sistema conforme previsto pelo CMMI.

O arquivo **test_agents.py** realiza testes sobre o comportamento dos agentes, assegurando que a lógica central do sistema funcione conforme esperado, alinhando-se às práticas de verificação funcional.

O arquivo **test_azureopenai_llm.py** valida a integração com a API da Azure OpenAI, garantindo a correta comunicação com serviços externos, aspecto importante tanto para o MPS.BR quanto para o CMMI em termos de verificação de interfaces externas.

O arquivo **test_chromadb_persistence_fix.py** verifica a persistência de dados utilizando o banco ChromaDB.

O arquivo **test_database_sanity.py** realiza verificações básicas de integridade do banco de dados.

O arquivo **test_gemini_integration.py** testa a integração com o modelo Gemini.

O arquivo **test_legacy_adapter.py** verifica a compatibilidade com componentes legados.

O arquivo **test_llm_context_enhancer.py** valida mecanismos de enriquecimento de contexto.

O arquivo **test_memory_tools.py** testa ferramentas auxiliares relacionadas à gestão de memória.

O arquivo **test_ollama_direct.py** valida a integração com o serviço Ollama.

O arquivo **test_tool_permissions.py** realiza testes relacionados ao controle de permissões.

O arquivo **test_workflow.py** é responsável por validar o funcionamento dos fluxos de execução do sistema, garantindo que os processos definidos sejam executados corretamente e na ordem esperada. Esse tipo de teste é importante para assegurar que a orquestração das tarefas ocorra de forma consistente, estando alinhado às práticas do CMMI de verificação de fluxos e processos.

## Conclusão

Apesar da forte adoção de testes automatizados e integração contínua, não foram identificadas evidências claras de práticas formais de revisão técnica estruturada ou de rastreabilidade entre requisitos e casos de teste, aspectos também recomendados pelo MPS.BR e pelo CMMI para aumentar a maturidade do processo de verificação.
Dessa forma, conclui-se que o projeto apresenta boa aderência às práticas de verificação no que se refere à automação e execução de testes, porém ainda possui lacunas relacionadas à formalização do processo e à rastreabilidade, caracterizando uma aderência parcial ao modelo de maturidade proposto tanto pelo MPS.BR quanto pelo CMMI.

