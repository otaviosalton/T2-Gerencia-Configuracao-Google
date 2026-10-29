# T2-Gerencia-Configuracao-Google

# Trabalho Avaliativo 2 (T2) — Gerência de Configuração (ENS4000)
**Área de Ciências Exatas e Engenharias — Universidade de Caxias do Sul (UCS)**  
**Grupo B:** Google — *Binary Authorization for Borg*

---

## 👥 Integrantes do Grupo
* Lucas Didoné de Oliveira
* Leonardo Ronsani dos Anjos
* Pedro Henrique Carlesso
* Otávio Cabalheiro Salton
* Miguel Angelo Moreschi Tome

---

## 🎯 Sobre o Caso: Binary Authorization for Borg
Este repositório documenta a prática interna do Google conhecida como **Binary Authorization for Borg**. Esta técnica de segurança exige que, antes de qualquer binário rodar em produção, existam provas assinadas criptograficamente de cada etapa pela qual o artefato passou, garantindo que o código foi revisado, compilado através de um *build* oficial e devidamente verificado[cite: 3]. 

Esta prática é a origem do framework open-source **SLSA (Supply chain Levels for Software Artifacts)**[cite: 3].

---

## 📌 Estrutura da Conferência Técnica

A nossa apresentação está estruturada no formato de conferência técnica, abordando os seguintes tópicos fundamentais:

### 1. O Problema: Ameaças na Cadeia de Suprimentos (Supply Chain)
* *Responsável: [Nome do integrante]*
* Contextualização sobre como ataques modernos focam na esteira de *build* e infraestrutura de CI/CD em vez de atacar o código-fonte diretamente.

### 2. A Solução: Como funciona a Autorização Binária no Google
* *Responsável: [Nome do integrante]*
* Explicação do orquestrador (Borg) e do processo de validação de assinaturas em tempo de *deploy*.
* Garantia de origem: Código revisado por pares e *builds* isolados e oficiais.

### 3. Conexão com a Gerência de Configuração
* *Responsável: [Nome do integrante]*
* **Rastreabilidade e Auditoria:** Como saber exatamente qual versão do código gerou um binário específico.
* **Integridade de Artefatos:** Garantia de que a configuração e o pacote de *deploy* são imutáveis e confiáveis.

### 4. Indo Além: O nascimento do Framework SLSA
* *Responsável: [Nome do integrante]*
* Apresentação de como o Google abriu essa prática para a comunidade através do *Supply chain Levels for Software Artifacts* (SLSA).

### 5. Demonstração / Conclusão Prática
* *Responsável: [Nome do integrante]*
* Resumo arquitetural e impacto da adoção destas práticas na indústria de software atual.

---

## 📁 Material de Apresentação
* **[Link para os slides / PDF da apresentação]** *(Adicionar após a finalização)*

---

## 📚 Referências Iniciais
* **Binary Authorization for Borg** (Documento técnico, Google Cloud)[cite: 3].
* **How Google Does It: Using Binary Authorization to boost supply chain security** (Google Cloud, nov. 2025)[cite: 3].
* *[Mais referências serão adicionadas durante o desenvolvimento da pesquisa]*
