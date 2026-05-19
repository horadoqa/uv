# uv

O uv é uma ferramenta moderna para gerenciamento de pacotes e projetos Python, desenvolvida pela Astral e escrita em Rust. O objetivo do projeto é substituir várias ferramentas tradicionais do ecossistema Python — como `pip`, `virtualenv`, `pip-tools`, `pipx`, `poetry` e `pyenv` — por uma solução única, extremamente rápida e integrada. ([Astral Docs][1])

## Principais características

### Velocidade extrema

O uv ficou conhecido principalmente pela performance. Segundo a documentação oficial, ele pode ser entre **10x e 100x mais rápido** que o `pip`, graças a:

* paralelismo nas instalações,
* cache global compartilhado,
* resolução de dependências otimizada,
* implementação em Rust. ([Astral Docs][1])

Isso faz bastante diferença em:

* CI/CD,
* builds Docker,
* projetos grandes,
* ambientes de Machine Learning e IA.

---

## O que o uv substitui

O uv tenta centralizar várias ferramentas do ecossistema Python:

| Ferramenta tradicional | Equivalente no uv                 |
| ---------------------- | --------------------------------- |
| `pip`                  | `uv pip`                          |
| `virtualenv` / `venv`  | `uv venv`                         |
| `pip-tools`            | lockfile integrado                |
| `pipx`                 | `uv tool`                         |
| `pyenv`                | `uv python`                       |
| `poetry`               | gerenciamento completo de projeto |

([Astral Docs][1])

---

## Recursos importantes

### 1. Gerenciamento de dependências

Você pode adicionar bibliotecas diretamente ao projeto:

```bash
uv add fastapi
uv add pandas
```

O uv atualiza automaticamente:

* `pyproject.toml`
* `uv.lock`

O arquivo `uv.lock` garante builds reproduzíveis, semelhante ao `package-lock.json` do Node.js ou `Cargo.lock` do Rust. ([noze][2])

---

### 2. Ambientes virtuais automáticos

O uv cria e gerencia ambientes virtuais automaticamente:

```bash
uv sync
```

Isso reduz bastante a necessidade de comandos manuais com `venv`.

---

### 3. Gerenciamento de versões do Python

Ele também instala versões do Python:

```bash
uv python install 3.12
```

Isso elimina a dependência do `pyenv` em muitos casos. ([noze][2])

---

### 4. Execução de scripts isolados

O uv consegue executar scripts com dependências temporárias:

```bash
uv run app.py
```

Ou até usando metadados inline no próprio script.

Esse recurso é muito útil para:

* automações,
* scripts utilitários,
* protótipos rápidos,
* notebooks executáveis.

---

### 5. Compatibilidade com pip

O uv oferece comandos compatíveis com o `pip`:

```bash
uv pip install requests
```

Isso facilita a migração gradual de projetos existentes. ([Astral Docs][1])

---

## Exemplo de fluxo moderno com uv

Criar um projeto:

```bash
uv init meu-projeto
cd meu-projeto
```

Adicionar dependências:

```bash
uv add fastapi
uv add ruff --dev
```

Executar:

```bash
uv run main.py
```

Sincronizar ambiente:

```bash
uv sync
```

---

## Por que ele está ganhando tanta popularidade?

A comunidade Python frequentemente reclama da fragmentação do ecossistema de empacotamento:

* `pip`
* `venv`
* `virtualenv`
* `poetry`
* `conda`
* `pipenv`
* `pyenv`

O uv tenta oferecer uma experiência parecida com:

* `cargo` no Rust,
* `npm` no Node.js,
* `bun` no JavaScript. ([Reddit][3])

Muitos desenvolvedores consideram o uv um forte candidato a se tornar o padrão moderno de gerenciamento Python.

---

## Pontos fortes

### Vantagens

* extremamente rápido,
* instalação simples,
* menos ferramentas para configurar,
* excelente experiência para DevOps e IA,
* lockfile reproduzível,
* cache eficiente,
* ótimo para monorepos.

### Possíveis limitações

* ainda é relativamente novo,
* alguns workflows avançados do Poetry podem não estar totalmente maduros,
* empresas muito conservadoras podem preferir ferramentas tradicionais por enquanto.

---

## Instalação

Pelo instalador oficial:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Ou via pip:

```bash
pip install uv
```

Documentação oficial:

[uv Documentation](https://docs.astral.sh/uv/?utm_source=chatgpt.com)

Repositório oficial:

[uv GitHub Repository](https://github.com/astral-sh/uv?utm_source=chatgpt.com)

---

## Relação com outras ferramentas da Astral

O uv faz parte do ecossistema da Astral, junto com:

* Ruff → lint/format extremamente rápido;
* ty → type checker moderno em Rust. ([Astral Docs][4])

A ideia da Astral é construir uma stack Python moderna e altamente performática baseada em Rust.

---

Vídeos úteis para aprender:

[UV: The Fastest Python Package Manager](https://www.youtube.com/watch?v=13eNodHGRjw&utm_source=chatgpt.com)

[Python Tutorial: UV - A Faster, All-in-One Package Manager](https://www.youtube.com/watch?v=AMdG7IjgSPM&utm_source=chatgpt.com)

[1]: https://docs.astral.sh/uv/?utm_source=chatgpt.com "uv"
[2]: https://www.noze.it/en/insights/uv-package-manager/?utm_source=chatgpt.com "UV: Astral's Python package manager in Rust | noze"
[3]: https://www.reddit.com/r/Python/comments/1aroork?utm_source=chatgpt.com "Announcing uv: Python packaging in Rust"
[4]: https://docs.astral.sh/?utm_source=chatgpt.com "Astral Docs"
