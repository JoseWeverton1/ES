# ES_2026-2_Vanna
# **Auditoria de Maturidade em Ecossistemas LLM: Projeto Vanna**

**Disciplina:** Engenharia de Software (COMP0503) | Carga Horária: 120 h

**Projeto Analisado:** [Vanna AI](https://github.com/vanna-ai/vanna)

## **Defesa Técnica (Vídeo de Auditoria)**

[**ACESSAR O VÍDEO DA AUDITORIA**](https://www.google.com/search?q=https://link-do-youtube-ou-drive)

*(Neste vídeo de XX minutos, a equipe apresenta a navegação técnica no repositório do Vanna, analisando o código-fonte, pipelines e workflows para fundamentar os achados descritos a seguir).*

## **Equipe e Atribuições**

| Nome | Eixo / Função | Atribuição Detalhada |
| :---- | :---- | :---- |
| **Diego** | Eixo I (Ágil) | Analisar Milestones, roadmap, releases e riscos de APIs. |
| **Bruno Henrique** | Eixo II (Requisitos) | Investigar RFCs e rastrear 3 requisitos (Issue \-\> PR \-\> Código). |
| **Lisboa** | Eixo III (Arquitetura) | Avaliar desacoplamento da IA e criar o Diagrama UML. |
| **Caricchio** | Eixo IV (V\&V) | Analisar workflows de CI, prevenção de alucinações e Peer Reviews. |
| **José Weverton** | Eixo V (Qualidade) | Auditar CONTRIBUTING.md, dívida técnica e ferramentas de análise. |
| **Flávio** | Plano de Melhoria | Definir 2 ações prioritárias para corrigir gaps de maturidade. |
| **Matheus** | Tech Lead | Montar o GitHub da equipe, repositório README e formatar o PDF final. |
| **Guilherme** | Direção de Vídeo | Coordenar a gravação técnica e garantir a adequação do vídeo (7 a 15 min). |

## **Síntese dos Achados da Auditoria (CMMI e MPS.BR)**

Abaixo constam os principais resultados técnicos documentados durante a inspeção do repositório oficial do Vanna. O relatório completo em formato PDF está disponível para consulta neste repositório: [A1\_Vanna\_Matheus.pdf](https://www.google.com/search?q=./A1_Vanna_Matheus.pdf).

### **Eixo I: Ciclo de Vida e Metodologias Ágeis (GPR)**

\[ Inserir síntese das análises sobre Milestones, Roadmap, Releases e Gestão de Riscos \- Responsabilidade: Diego \]

### **Eixo II: Engenharia de Requisitos (GRE)**

* **Informalidade e RFCs:** O projeto não possui processos formais de *Request for Comments* (RFC). As decisões ocorrem primordialmente em *Pull Requests* (PRs) e *Issues*.  
* **Rastreabilidade:** Foram mapeados três requisitos centrais (e.g., persistência no ChromaDB via Issue \#1031 e PR \#1081; e integração PGVector via PR \#660). A análise evidenciou a ausência de testes prévios a integrações críticas e baixa colaboração antecipada em requisitos complexos.

### **Eixo III: Arquitetura e Modelagem (PJR)**

\[ Inserir síntese sobre a arquitetura do sistema e o desacoplamento \- Responsabilidade: Lisboa \]

**Nota Técnica:** O Diagrama de Classes UML correspondente encontra-se disponível no diretório /diagramas: [Acessar diagrama da arquitetura](https://www.google.com/search?q=./diagramas/arquitetura_vanna.png).

### **Eixo IV: Verificação e Validação (V\&V)**

* **Verificação:** Constatou-se forte presença de automação de Integração Contínua (CI/CD) em .github/workflows/tests.yml, validando integrações reais com APIs por meio da ferramenta tox.  
* **Validação:** Identificou-se a ausência de mecanismos explícitos para validação semântica das respostas da IA em produção (prevenção sistemática de alucinações), com o projeto focando de forma restrita em avaliações experimentais (evals).

### **Eixo V: Qualidade de Software (GQA)**

* **Padrões:** Verificou-se aderência estrita às diretrizes do arquivo CONTRIBUTING.md, com uso das ferramentas Ruff e Mypy.  
* **Dívida Técnica:** A transição para uma arquitetura baseada em Agentes acumulou um legado considerável (observou-se mais de 25 regras de *linting* intencionalmente ignoradas para a manutenção de retrocompatibilidade).  
* **Segurança (SAST):** Constatou-se uma ausência crítica de ferramentas de análise estática de segurança (como *CodeQL* ou *Bandit*), representando alto risco em se tratando de uma biblioteca voltada à geração e execução de *queries* SQL via LLMs.

## **Plano de Melhoria de Processo (Alinhamento ao MPS.BR Nível G)**

Com o objetivo de suprir as lacunas identificadas e alinhar as práticas do projeto à certificação MPS.BR Nível G, propõem-se as seguintes ações prioritárias:

1. **Rastreabilidade Formal (GRE):** Instituição de templates estruturados para *issues*, estabelecimento de fluxos documentados de RFC e criação de um artefato próprio para matriz de rastreabilidade.  
2. **Controle de Riscos (GPR):** Adoção formal da funcionalidade de *Milestones*, definição oficial de um Roadmap e manutenção contínua de um Registro de Riscos focado em APIs de terceiros.

**Nota Operacional:** Para demonstrar a viabilidade das melhorias recomendadas, os templates propostos (*Traceability*, *Risk Register*) encontram-se estruturados e disponíveis no diretório [/plano\_de\_melhoria](https://www.google.com/search?q=./plano_de_melhoria/) deste repositório.
