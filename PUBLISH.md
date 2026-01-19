# Como Publicar no PyPI

## Pré-requisitos

1. Instalar ferramentas necessárias:
```bash
pip install build twine
```

2. Criar conta no PyPI:
   - Test PyPI: https://test.pypi.org/account/register/
   - PyPI: https://pypi.org/account/register/

## Publicação

### 1. Testar no Test PyPI primeiro

```bash
# Limpar builds anteriores
rm -rf dist/ build/ *.egg-info

# Construir o pacote
python -m build

# Verificar o pacote
twine check dist/*

# Publicar no Test PyPI
twine upload --repository testpypi dist/*
```

### 2. Testar a instalação do Test PyPI

```bash
pip install --index-url https://test.pypi.org/simple/ rustpy
```

### 3. Publicar no PyPI oficial

```bash
# Construir novamente (se necessário)
python -m build

# Verificar
twine check dist/*

# Publicar no PyPI
twine upload dist/*
```

## Comandos Úteis

```bash
# Ver versão atual
python -c "import tomli; print(tomli.load(open('pyproject.toml'))['project']['version'])"

# Incrementar versão manualmente no pyproject.toml
# Editar: version = "0.1.1"

# Limpar tudo
rm -rf dist/ build/ *.egg-info
```

## Notas

- Sempre teste no Test PyPI primeiro!
- Não é possível re-upload da mesma versão no PyPI
- Para atualizar, incremente a versão no pyproject.toml
