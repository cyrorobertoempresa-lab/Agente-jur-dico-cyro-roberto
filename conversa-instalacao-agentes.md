# Instalação dos agentes jurídicos no Claude (Code e Cowork)

Registro da conversa com o Claude Code em que os 57 agentes de advocacia foram instalados e publicados como plugin.

- **Repositório de origem:** https://github.com/asv-digital/agents-advogados
- **Repositório de destino:** https://github.com/cyrorobertoempresa-lab/Agente-jur-dico-cyro-roberto

---

## 1. Instalar os agentes

**Usuário:**
> https://github.com/asv-digital/agents-advogados instale todas as skill e agentes que tem nesse

**Claude:**
Instalei os 57 agentes do repositório em `~/.claude/agents/`, que é a pasta global. Skills não havia nenhuma: o repositório só tem a pasta `agents/` e o README.

- Os agentes cobrem cível, trabalhista, família e sucessões, criminal, tributário, empresarial, consumidor, imobiliário, previdenciário, execução e consultivo (parecer, contratos, LGPD).
- Todos usam `model: sonnet` e as ferramentas `Read, Grep, Bash, Edit, Write`.
- Li todos os arquivos antes de instalar e não achei comandos estranhos nem links suspeitos. O único link é o do índice IPCA do TJ-SP.
- Os agentes só aparecem numa sessão nova. Depois, confirme com `/agents`.
- Esta sessão roda num contêiner na nuvem que é descartado depois, então a instalação é temporária. Para manter os agentes, instale no seu computador ou coloque-os num repositório seu.

---

## 2. Rodar os comandos de instalação

**Usuário:**
```bash
git clone https://github.com/asv-digital/agents-advogados.git
cp agents-advogados/agents/*.md ~/.claude/agents/
```

**Claude:**
Rodei os dois comandos e eles funcionaram: os 57 agentes estão em `~/.claude/agents/` e já estão ativos nesta sessão. Isso vale só para este contêiner na nuvem; no seu computador, rode os mesmos comandos no seu terminal.

---

## 3. Salvar no seu repositório

**Usuário:**
> https://github.com/cyrorobertoempresa-lab/Agente-jur-dico-cyro-roberto.git salva nesse repositório

**Claude:**
Coloquei os 57 agentes em `.claude/agents/`, criei um `README.md` e fiz o commit `d4bc16d` na branch `main`. O envio foi **recusado** (erro 403): o Claude não tinha permissão para gravar no repositório.

Para liberar:
1. Abra https://claude.ai/connect-github e conecte (ou reconecte) sua conta do GitHub.
2. Instale o app do Claude no GitHub para a conta `cyrorobertoempresa-lab`, pela mesma página, e dê acesso a esse repositório.

**Usuário:**
> ja

**Claude:**
Agora deu certo: enviei o commit para a branch `main`.

---

## 4. Clonar o repositório

**Usuário:**
> voce ja clonou?

**Claude:**
Sim, o repositório já estava clonado nesta sessão, em `/home/user/agente-jur-dico-cyro-roberto`. Para usar no seu computador, rode lá:
```bash
git clone https://github.com/cyrorobertoempresa-lab/Agente-jur-dico-cyro-roberto.git
```

**Usuário:**
```bash
git clone https://github.com/cyrorobertoempresa-lab/Agente-jur-dico-cyro-roberto.git
```

**Claude:**
Não clonei de novo porque o repositório já estava aqui; só atualizei a cópia, que já estava em dia. Esse comando é para rodar no **seu computador**. Depois, dentro da pasta, rode `claude` e confira com `/agents`.

---

## 5. Usar no Cowork

**Usuário:**
> da pra usar tambem no chat cowork

**Claude:**
Dá. O Cowork só instala agentes que venham dentro de um **plugin**, então reorganizei o repositório nesse formato (que também funciona no Claude Code). Enviei como commit `73e444b`, e o validador de plugins do Claude Code aprovou.

Nova estrutura:
```
.claude-plugin/marketplace.json
plugins/advocacia/.claude-plugin/plugin.json
plugins/advocacia/agents/*.md   (57 agentes)
README.md
```

Plugins funcionam no **Cowork** e no **Claude Code**, mas não no chat comum do Claude.

Fontes:
- [Cowork — Install plugins](https://claude.com/docs/cowork/guide/plugins.md)
- [Extending Claude Cowork with plugins](https://claude.com/resources/guides/claude-cowork-product-guide/extending-claude-cowork-with-plugins)

---

## 6. Passo a passo para instalar em outra conta

**Usuário:**
> me dê o passo a passo do que foi feito aqui pra que eu possa instalar em outra conta

**Claude:**

### Parte 1: o que foi feito
1. Baixei os agentes originais de `asv-digital/agents-advogados`: 57 arquivos `.md`, um por agente.
2. Copiei os agentes para o repositório `cyrorobertoempresa-lab/Agente-jur-dico-cyro-roberto`.
3. Organizei tudo como plugin (a estrutura da seção 5).
4. Conectei o GitHub ao Claude em https://claude.ai/connect-github e instalei o app do Claude no repositório.
5. Enviei para a branch `main`.

### Parte 2: instalar em outra conta

**1. Dê à outra conta acesso ao repositório.** Só é preciso se o repositório for privado.
- No GitHub, abra o repositório → **Settings** → **Collaborators** → **Add people** e adicione o usuário do GitHub da outra pessoa.
- Na outra conta do Claude, conecte esse GitHub em https://claude.ai/connect-github.

**2. No Cowork (app Claude)**
1. Entre com a outra conta.
2. Abra **Customize** → **Plugins** → **Add marketplace**.
3. Digite: `cyrorobertoempresa-lab/Agente-jur-dico-cyro-roberto`
4. Encontre o plugin **advocacia** e clique em **Install**.
5. Abra o plugin e confira na aba **Agents** se os 57 agentes aparecem.
6. Opcional: ative **Sync automatically** para receber as atualizações do repositório.

**3. No Claude Code (opcional)**
```
/plugin marketplace add cyrorobertoempresa-lab/Agente-jur-dico-cyro-roberto
/plugin install advocacia@agente-juridico-cyro-roberto
```
Feche e abra o Claude Code de novo, e confira com `/agents`.

**Se não quiser dar acesso ao GitHub:** no GitHub, clique em **Code** → **Download ZIP**. Depois, em **Customize** → **Plugins**, use a opção de **upload** e envie esse arquivo. Pode ser preciso compactar só a pasta `plugins/advocacia`. Esse caminho não foi testado.
