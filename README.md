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
Daí Gurizada, como estamos em 5 e temos de 20 a 25 minutos para apresentar (dá uns 4 a 5 minutos pra cada um), deixei aqui 5 sugestões de tópicos. A ideia é cada um escolher uma parte pra falar na apresentação e a partir disso montar os slides, no mesmo esquema que a gente fez no T1.

---

## 🎯 Sobre o Caso: Binary Authorization for Borg
Este repositório documenta a prática interna do Google conhecida como **Binary Authorization for Borg**. Esta técnica de segurança exige que, antes de qualquer binário rodar em produção, existam provas assinadas criptograficamente de cada etapa pela qual o artefato passou, garantindo que o código foi revisado, compilado através de um build oficial e devidamente verificado.

Esta prática é a origem do framework open-source **SLSA (Supply chain Levels for Software Artifacts)**.

---

## 📌 Estrutura da Conferência Técnica (Sugestão de Tópicos)

Nossa apresentação seguirá o formato de uma conferência técnica, abordando os seguintes tópicos fundamentais:

### 1. O Problema: Ameaças na Cadeia de Suprimentos (Supply Chain)
* **Responsável:** Otávio Cabalheiro Salton

Historicamente, a segurança em Engenharia de Software focava em proteger o repositório de código-fonte ou blindar o servidor em produção. No entanto, o vetor de ataque mudou: as ameaças mais críticas hoje miram a **cadeia de suprimentos (Supply Chain)** e a infraestrutura de CI/CD (Integração e Entrega Contínuas).

Em vez de tentar invadir um sistema rodando, os atacantes buscam comprometer as ferramentas de *build* ou adulterar dependências durante a compilação. O perigo crítico dessa abordagem é que o artefato malicioso acaba recebendo a "assinatura de confiança" oficial da empresa, pois saiu de dentro da própria esteira de produção (como visto no ataque à SolarWinds).

Para o Google — que opera um monorepo massivo e realiza milhares de *deploys* diários —, garantir apenas que o código foi bem escrito e revisado deixou de ser suficiente. Tornou-se imperativo garantir, de ponta a ponta, que a própria esteira de *build* é inviolável e que o artefato final não sofreu nenhuma adulteração antes de chegar à produção.

### 2. A Solução: Como funciona a Autorização Binária no Google
* **Responsável:** Lucas Didoné de Oliveira
* **Foco:** Explicação do orquestrador (Borg) e do processo de validação de assinaturas em tempo de deploy. Mostrar a garantia de origem: código obrigatoriamente revisado por pares e builds isolados em servidores oficiais (não na máquina do dev).

### 3. Conexão com a Gerência de Configuração
* **Responsável:** Miguel Angelo Moreschi Tome
* **Foco:** Ligar o caso prático com o que vimos na disciplina. Explicar conceitos como Rastreabilidade, Auditoria (saber qual versão do código gerou o binário) e a Imutabilidade/Integridade dos pacotes de deploy.

### 4. Indo Além: O nascimento do Framework SLSA
* **Responsável:** Pedro Carlesso
* **Foco:** Atendendo à exigência de "ir além do material base", este tópico apresenta como o Google abriu essa prática interna para a comunidade de software através do Supply chain Levels for Software Artifacts (SLSA).

### 5. Demonstração / Conclusão Prática
* **Responsável:** Leonardo dos Anjos
* **Foco:** Resumo arquitetural da solução e o impacto da adoção dessas práticas na indústria atual. Se possível, usar um diagrama rápido para ilustrar um deploy sendo bloqueado vs. permitido.

---

## 📁 Material de Apresentação
* **[Link para os slides / PDF da apresentação]** *(Será adicionado após finalizarmos os slides)*

---

## 📚 Referências Iniciais
* **Binary Authorization for Borg** (Documento técnico, Google Cloud).
* **How Google Does It: Using Binary Authorization to boost supply chain security** (Google Cloud, nov. 2025).
* *(Mais referências, com os devidos anos e autores, serão adicionadas durante a montagem dos slides)*
