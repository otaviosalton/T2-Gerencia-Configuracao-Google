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

O Binary Authorization for Borg, conhecido como BAB, é um mecanismo interno de segurança desenvolvido pelo Google para garantir que somente softwares confiáveis sejam executados em seus ambientes de produção[cite: 1]. Seu principal objetivo é impedir que aplicações sem as devidas aprovações ou produzidas fora dos ambientes oficiais sejam executadas na infraestrutura da empresa[cite: 1].

Essa solução está relacionada ao conceito de Zero Trust, ou Confiança Zero, que estabelece que nenhum usuário ou sistema deve receber confiança automaticamente[cite: 1]. Na prática, isso significa que não basta um desenvolvedor ter autorização para acessar a infraestrutura: o software também precisa comprovar que passou pelos processos de segurança exigidos antes de chegar à produção[cite: 1].

Para entender a importância dessa solução, imagine um desenvolvedor que compila um programa diretamente em seu próprio computador e envia o executável para os servidores da empresa[cite: 1]. Se essa máquina estiver comprometida, o arquivo poderá conter alterações maliciosas ou códigos não autorizados[cite: 1]. Para evitar esse risco, o Google estabeleceu um processo que controla desde a aprovação do código até a execução do programa[cite: 1].

Esse processo funciona com base em três etapas principais[cite: 1]:

**A primeira etapa é a revisão obrigatória por pares, conhecida como Two-Party Review.**[cite: 1]
Isso significa que uma alteração no código não pode ser aprovada exclusivamente pelo próprio desenvolvedor que a realizou[cite: 1]. Antes de ser incorporada ao projeto, ela precisa ser analisada e aprovada por outro profissional qualificado[cite: 1]. Essa etapa ajuda a identificar erros, vulnerabilidades e alterações suspeitas, garantindo que o código passe por uma avaliação antes de seguir para a compilação[cite: 1].

**A segunda etapa são os builds isolados, realizados em servidores oficiais do Google.**[cite: 1]
Depois de aprovado, o código é encaminhado para um ambiente de compilação controlado[cite: 1]. Isso significa que o executável não deve ser produzido diretamente no computador pessoal do desenvolvedor para depois ser enviado à produção[cite: 1]. A compilação acontece em servidores oficiais, com processos e dependências controlados[cite: 1]. Ao final, são produzidas atestações criptográficas, que funcionam como evidências técnicas de que aquele binário foi gerado por um processo autorizado[cite: 1].

Essas atestações permitem verificar informações importantes, como a origem do código e as condições utilizadas durante a compilação[cite: 1]. Dessa forma, o sistema consegue diferenciar um software produzido pelo processo oficial de um arquivo cuja procedência não pode ser comprovada[cite: 1, 2].

**A terceira etapa é a validação durante o deploy, realizada pela integração entre o BAB e o Borg.**[cite: 2]
O Borg é o sistema de gerenciamento de clusters do Google, responsável por organizar os recursos computacionais e controlar a execução das aplicações em seus servidores[cite: 2]. Antes de permitir que um programa seja executado, o Borg utiliza o BAB para verificar se o binário apresenta as assinaturas e as atestações exigidas pelas políticas de segurança[cite: 2].

Se as evidências estiverem ausentes, forem inválidas ou não atenderem aos requisitos estabelecidos, a execução será bloqueada[cite: 2]. Por outro lado, se o software cumprir todas as condições exigidas, ele poderá ser executado no ambiente de produção[cite: 2].

Na prática, podemos comparar esse funcionamento a um controle de segurança: não basta o programa chegar ao servidor, ele precisa comprovar que foi produzido e aprovado de acordo com as regras estabelecidas pelo Google[cite: 2].

Portanto, o Binary Authorization for Borg demonstra como o Google utiliza processos de revisão, ambientes de compilação controlados e verificações criptográficas para proteger sua infraestrutura[cite: 2]. O grande diferencial da solução é que a segurança não depende apenas da confiança nas pessoas, mas também de evidências técnicas verificadas automaticamente antes da execução do software[cite: 2].

### 3. Conexão com a Gerência de Configuração
* **Responsável:** Miguel Angelo Moreschi Tome
* **Foco:** Ligar o caso prático com o que vimos na disciplina. Explicar conceitos como Rastreabilidade, Auditoria (saber qual versão do código gerou o binário) e a Imutabilidade/Integridade dos pacotes de deploy.

### 4. Indo Além: O nascimento do Framework SLSA
* **Responsável:** Pedro Henrique Carlesso

Com o aumento alarmante de ataques à integridade de pacotes de software (como os casos da SolarWinds e Codecov), a indústria carecia de um framework completo para proteger toda a cadeia de suprimentos de ponta a ponta. 

Como o Google já utilizava o BAB internamente com sucesso por mais de oito anos, a empresa decidiu abrir esse conhecimento para o mercado. Em 2021, o Google apresentou o **SLSA (Supply chain Levels for Software Artifacts)** — um projeto diretamente inspirado no BAB — e o doou para a fundação OpenSSF.

O conceito central do SLSA é a **Proveniência**: um registro que descreve exatamente qual entidade construiu o artefato, por qual processo e a partir de quais entradas. O framework é adotável de forma incremental através de "trilhas", começando pela trilha de *build*, dividida em níveis:
* **Nível 1:** A proveniência mostra de forma clara como o pacote foi construído.
* **Nível 2:** A proveniência é assinada criptograficamente e gerada por uma plataforma de build hospedada, protegendo contra adulterações *após* a compilação.
* **Nível 3:** A própria plataforma de build é blindada e reforçada, protegendo o código contra adulterações *durante* a compilação.

**Diferença fundamental (BAB vs. SLSA):**
Enquanto o **BAB** é o mecanismo interno de execução do Google (integrado ao orquestrador Borg para barrar ativamente os *deploys* que não possuem assinaturas), o **SLSA** é uma especificação aberta e padronizada. Ele define os níveis e formatos recomendados de atestação de segurança para que qualquer organização no mundo decida como aplicá-los à sua própria infraestrutura.

### 5. Demonstração Interativa / Conclusão Prática
* **Responsável:** Leonardo Ronsani dos Anjos

Para ilustrar na prática como uma política de autorização atua na barreira de *deploy*, desenvolvemos um **Simulador Interativo do Binary Authorization for Borg** (`simulador-bab.html`)[cite: 3, 6].

A ferramenta permite simular o fluxo de decisão do orquestrador diante de três cenários reais[cite: 3]:
* **Cenário A (Versão Aprovada):** Código revisado, *build* oficial, atestação válida e integridade verificada — resultando em **Deploy Autorizado (`ALLOW`)**[cite: 3].
* **Cenário B (Build Não Confiável):** Artefato compilado fora do ambiente oficial — resultando em **Deploy Bloqueado (`DENY`)**[cite: 3].
* **Cenário C (Arquivo Adulterado):** Pacote modificado após a emissão da evidência (detectado via divergência real de *hash* SHA-256) — resultando em **Deploy Bloqueado (`DENY`)**[cite: 3].

Além dos cenários pré-definidos, o simulador conta com um modo interativo para alterar regras de revisão, *build*, atestação e conteúdo do artefato em tempo real, demonstrando o impacto prático do controle de procedência e integridade na proteção de ambientes de produção[cite: 3].

---

## 📁 Material de Apresentação e Demonstração
* **[Acessar Simulador Interativo BAB (Ao Vivo)](https://otaviosalton.github.io/T2-Gerencia-Configuracao-Google/simulador-bab.html)** — Demonstração prática interativa rodando via GitHub Pages (código-fonte em [`simulador-bab.html`](./simulador-bab.html))
* **[Link para os slides / PDF da apresentação]** *(Será adicionado após finalizarmos os slides)*

---

## 📚 Referências Iniciais
* **Binary Authorization for Borg** (Documento técnico, Google Cloud).
* **How Google Does It: Using Binary Authorization to boost supply chain security** (Google Cloud, nov. 2025).
* *(Mais referências, com os devidos anos e autores, serão adicionadas durante a montagem dos slides)*
