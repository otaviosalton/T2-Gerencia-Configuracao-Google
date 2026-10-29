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

## ⚠️ Recado 
*Daí Gurizada, como estamos em 5 e temos de 20 a 25 minutos para apresentar (dá uns 4 a 5 minutos pra cada um), deixei aqui 5 sugestões de tópicos. A ideia é cada um escolher uma parte pra falar na apresentação e a partir disso montar os slides, no mesmo esquema que a gente fez no T1.*

---

## 🎯 Sobre o Caso: Binary Authorization for Borg
Este repositório documenta a prática interna do Google conhecida como **Binary Authorization for Borg**. Esta técnica de segurança exige que, antes de qualquer binário rodar em produção, existam provas assinadas criptograficamente de cada etapa pela qual o artefato passou, garantindo que o código foi revisado, compilado através de um *build* oficial e devidamente verificado. 

Esta prática é a origem do framework open-source **SLSA (Supply chain Levels for Software Artifacts)**.

---

## 📌 Estrutura da Conferência Técnica (Sugestão de Tópicos)

Nossa apresentação seguirá o formato de uma conferência técnica, abordando os seguintes tópicos fundamentais:

### 1. O Problema: Ameaças na Cadeia de Suprimentos (Supply Chain)
* **Responsável:** [Nome do integrante]
* **Foco:** Contextualização sobre como os ataques modernos focam na esteira de *build* e na infraestrutura de CI/CD em vez de atacar o código-fonte diretamente. Por que o Google precisou criar isso?

### 2. A Solução: Como funciona a Autorização Binária no Google
* **Responsável:** [Nome do integrante]
* **Foco:** Explicação do orquestrador (Borg) e do processo de validação de assinaturas em tempo de *deploy*. Mostrar a garantia de origem: código obrigatoriamente revisado por pares e *builds* isolados em servidores oficiais (não na máquina do dev).

### 3. Conexão com a Gerência de Configuração
* **Responsável:** [Nome do integrante]
* **Foco:** Ligar o caso prático com o que vimos na disciplina. Explicar conceitos como Rastreabilidade, Auditoria (saber qual versão do código gerou o binário) e a Imutabilidade/Integridade dos pacotes de *deploy*.

### 4. Indo Além: O nascimento do Framework SLSA
* **Responsável:** [Nome do integrante]
* **Foco:** Atendendo à exigência de "ir além do material base", este tópico apresenta como o Google abriu essa prática interna para a comunidade de software através do *Supply chain Levels for Software Artifacts* (SLSA).

### 5. Demonstração / Conclusão Prática
* **Responsável:** [Nome do integrante]
* **Foco:** Resumo arquitetural da solução e o impacto da adoção dessas práticas na indústria atual. Se possível, usar um diagrama rápido para ilustrar um *deploy* sendo bloqueado vs. permitido.

---

## 📁 Material de Apresentação
* **[Link para os slides / PDF da apresentação]** *(Será adicionado após finalizarmos os slides)*

---

## 📚 Referências Iniciais
* **Binary Authorization for Borg** (Documento técnico, Google Cloud).
* **How Google Does It: Using Binary Authorization to boost supply chain security** (Google Cloud, nov. 2025).
* *(Mais referências, com os devidos anos e autores, serão adicionadas durante a montagem dos slides)*
