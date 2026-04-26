# Evidências - Eixo IV: Verificação e Validação (V&V)

Links e caminhos do repositório para os pipelines de automação e validação de código citados no documento final.

* **Mecanismos de Integração Contínua (Workflows):**
  * **Pasta de Workflows:** [https://github.com/vanna-ai/vanna/tree/main/.github/workflows](https://github.com/vanna-ai/vanna/tree/main/.github/workflows)
  * **Pipeline de Testes Principais:** Caminho `.github/workflows/tests.yml`
  * **Pipeline de Publicação:** Caminho `.github/workflows/python-publish.yaml`
  * *Referência no Doc Final:* Seção 6.1.

* **Evidências de Testes Específicos:**
  * **Retenção de Estado:** `test_agent_memory.py`
  * **Fluxos de Execução:** `test_workflow.py`
  * **Integração de APIs:** `test_azureopenai_llm.py`, `test_gemini_integration.py`
  * *Referência no Doc Final:* Seção 6.1.

* **Evidência de Benchmarking (Avaliação de Alucinações Offline):**
  * **Pasta de Avaliação:** `/src/vanna/evals` (contendo `llm_comparison.py` e a subpasta `benchmarks`).
  * *Referência no Doc Final:* Seção 6.2.