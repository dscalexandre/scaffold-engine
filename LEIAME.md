# Scaffold Engine — Setup Inicial

CLI for generating projects from templates, focusing on standardization, environment isolation, and reproducibility.

## 🧹 0. LIMPEZA TOTAL

rm -rf .venv
rm -rf engine/
rm -f poetry.lock

```bash

# 🧱 1. ESTRUTURA DO PROJETO

mkdir -p ~/workspace/platform/scaffold-engine && cd $_

mkdir -p engine assets .github

touch engine/__init__.py \
      engine/cli.py \
      README.md \
      LICENSE \
      .gitignore \
      pyproject.toml \
      .editorconfig \
      .github/pull_request_template.md


# 🧹 2. CONFIGURAÇÃO DO .gitignore

__pycache__/
*.py[cod]
*$py.class

# Virtual environments
venv/
.venv/

# Testing
.pytest_cache/

# Environment variables
.env
.env.local

# IDEs
.vscode/

# Build artifacts
build/
dist/
*.egg-info/
.eggs/
*.whl

# Keep this file versioned
LEIAME.md

# Windows
Thumbs.db
Thumbs.db:encryptable
ehthumbs.db
Desktop.ini

# macOS
.DS_Store
.AppleDouble
.LSOverride

# Linux
*~
.fuse_hidden*
.directory
.Trash-*


# 🧾 2.1 .editorconfig

root = true

[*]
indent_style = space
indent_size = 4
end_of_line = lf
charset = utf-8
insert_final_newline = true


# ⚙️ 3. CONFIGURAÇÃO DO pyproject.toml

[tool.poetry]
name = "scaffold-engine"
version = "0.1.0"
description = "Python CLI for standardized and reproducible project scaffolding with Cookiecutter and Cruft"
authors = ["Alexandre Rodrigues"]
license = "MIT"
readme = "README.md"
packages = [{ include = "engine" }]

[tool.poetry.dependencies]
python = "^3.10"
typer = "^0.9.0"

[tool.poetry.scripts]
scaffold = "engine.cli:app"

[build-system]
requires = ["poetry-core>=2.0.0,<3.0.0"]
build-backend = "poetry.core.masonry.api"


# 📄 4. README.md
# (Adicionar conteúdo manualmente)

# 🗂️ 5. ASSETS
# (Adicionar assets/logo.png manualmente)

# ⚖️ 6. LICENSE

MIT License

Copyright (c) 2026 Alexandre Rodrigues

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.


# 📄 7. TEMPLATE DE PULL REQUEST (.github/pull_request_template.md)

## Description
Describe what was implemented and why.

## Type of Change
- [ ] feat
- [ ] fix
- [ ] chore
- [ ] docs
- [ ] refactor

## How to Test
Steps to validate:
- poetry run scaffold hello

## Checklist
- [ ] Code follows project standards
- [ ] Tested locally
- [ ] No errors observed
- [ ] Documentation updated (if needed)

## Related Issues
Closes #1

XXXXXXXXXXXXXXXXXXXXXXXXX
# OBSERVAÇÃO
Na reinicialização do projeto, os únicos diretórios/arquivos que precisam ser excluidos é o 'dir engine', git e o repositório no GitHub.
XXXXXXXXXXXXXXXXXXXXXXXXX

# 🔧 8. INICIALIZAÇÃO DO GIT

git init
git branch -M main

git add .
git commit -m "chore: initial project structure"


# ☁️ 9. REPOSITÓRIO REMOTO

gh repo create scaffold-engine \
  --public \
  --description "Python CLI for standardized and reproducible project scaffolding with template lifecycle management using Cookiecutter and Cruft." \
  --source . \
  --remote origin \
  --push

gh repo edit \
  --add-topic cookiecutter \
  --add-topic scaffolding \
  --add-topic python \
  --add-topic cli \
  --add-topic mlops \
  --add-topic data-engineering \
  --add-topic cruft


# 🌿 10. FEATURE: DEPENDÊNCIAS

# Issue
gh issue create --title "Setup dependencies" --body "Configure Poetry, dependency management and ensure reproducible environment."

# Branch
git checkout -b feat/1-setup-dependencies

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
PAREI AQUI........................PAREI AQUI...................
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx


# 📦 11. INSTALAÇÃO

poetry install


# 🔍 12. TESTES

poetry run scaffold --help


# 💾 13. COMMIT

git add poetry.lock
git commit -m "chore(deps): add poetry.lock for reproducible dependencies"

git push origin feat/1-setup-dependencies


# Issue comment (implementação inicial)
gh issue comment 1 --body "Dependencies installed and poetry.lock generated."


# 🔀 14. PULL REQUEST

gh pr create \
  --title "chore(deps): setup dependencies" \
  --body "
## Description
Adds poetry.lock to ensure reproducible dependency management.

## Type of Change
- [x] chore

## How to Test
Steps to validate:
- poetry install
- poetry run scaffold --help

## Checklist
- [x] Code follows project standards
- [x] Tested locally
- [x] No errors observed

## Related Issues
Closes #1
"

# Issue comment (PR vinculado)

gh issue comment 1 --body "PR opened for dependency setup."


gh pr merge --merge --delete-branch

git checkout main
git pull --rebase origin main


# 🌿 15. FEATURE: CLI BASE

# Issue
gh issue create --title "CLI base" --body "Implement initial CLI structure using Typer CLI framework."

# Branch
git checkout -b feat/2-cli-base


# 🧠 16. IMPLEMENTAÇÃO (engine/cli.py)

import typer

app = typer.Typer(help="Scaffold Engine CLI")

@app.callback()
def main():
    pass

@app.command()
def hello():
    typer.echo("Hello from Scaffold Engine")

if __name__ == "__main__":
    app()


# 🔍 17. TESTES

poetry run scaffold --help
poetry run scaffold hello


# 💾 18. COMMIT

git add engine/cli.py
git commit -m "feat(cli): add initial Typer CLI with hello command"

git push origin feat/2-cli-base


# Issue comment (implementação inicial)
gh issue comment 2 --body "Initial CLI structure created using Typer. Hello command implemented."


# 🔀 19. PULL REQUEST

gh pr create \
  --title "feat(cli): initial CLI implementation" \
  --body "
## Description
Adds initial CLI structure using Typer with a basic hello command.

## Type of Change
- [x] feat

## How to Test
Steps to validate:
- poetry run scaffold hello

## Checklist
- [x] Code follows project standards
- [x] Tested locally
- [x] No errors observed

## Related Issues
Closes #2
"

# Issue comment (PR vinculado)

gh issue comment 2 --body "PR opened for CLI implementation."


gh pr merge --merge --delete-branch

git checkout main
git pull --rebase origin main


# 🏷️ 20. TAG

git tag -a v0.1.0 -m "Initial CLI version"
git push origin v0.1.0


# 🔍 21. VALIDAÇÃO FINAL

git log --oneline --graph --decorate
git status
git branch -a


# 🏁 FINALIZADO
```

###############################################################################
###############################################################################

# USAR QUANDO FOR CONSTRUIR O TEMPLATE:

1. Ponto MUITO importante (que define se isso funciona bem)

Para garantir que o .venv fique dentro do projeto:

👉 no template você deve ter:

poetry config virtualenvs.in-project true
✔ Ideal no seu hook
run("poetry config virtualenvs.in-project true")
run("poetry install")

---

# FUTURAMENTE QUANDO FOR CRIAR O TEMPLATE:

1. Revisar seu template agora para garantir que:

👉 o .venv está sendo criado corretamente
👉 hooks estão perfeitos
👉 integração com engine está 100%
