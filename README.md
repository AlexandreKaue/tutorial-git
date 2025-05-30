# Tutorial Git com Autenticação SSH

Este tutorial descreve como configurar um repositório Git no GitHub com autenticação SSH.

## Passos para configuração

### 1. Configuração Inicial do Git

Para começar, configure o Git com seus dados:

```bash
git config --global user.name "SeuNomeDeUsuário"
git config --global user.email "seu.email@exemplo.com"
```

### 2. Gerar Chave SSH

Gere uma chave SSH para autenticação segura:

```bash
ssh-keygen -t ed25519 -C "seu.email@exemplo.com"
```

Isso vai gerar uma chave pública e privada para autenticação SSH.

### 3. Adicionar Chave SSH ao GitHub

1. Copie a chave pública gerada:

```bash
cat ~/.ssh/id_ed25519.pub
```

2. Adicione a chave pública em [GitHub SSH Keys](https://github.com/settings/keys)

### 4. Testar Conexão SSH com GitHub

Teste a conexão com o GitHub:

```bash
ssh -T git@github.com
```

Se a configuração estiver correta, você verá uma mensagem como:
```
Hi SeuNomeDeUsuário! You've successfully authenticated, but GitHub does not provide shell access.
```

### 5. Inicializar Repositório Git Localmente

No diretório do projeto, inicialize o repositório Git:

```bash
git init
```

### 6. Fazer o Primeiro Commit

Crie um arquivo README.md e faça o commit:

```bash
echo "# nome-do-repositorio" >> README.md
git add README.md
git commit -m "primeiro commit"
```

### 7. Configurar o Branch Principal

Renomeie o branch principal para `main`:

```bash
git branch -M main
```

### 8. Adicionar o Repositório Remoto

Adicione o repositório remoto ao GitHub:

```bash
git remote add origin https://github.com/SeuUsuario/nome-do-repositorio.git
```

**Nota:** Se já existir um repositório remoto, o comando resultará no erro: `error: remote origin already exists.`

### 9. Alterar URL do Repositório para SSH

Como a autenticação por senha foi descontinuada, altere a URL do repositório para usar SSH:

```bash
git remote set-url origin git@github.com:SeuUsuario/nome-do-repositorio.git
```

### 10. Enviar para o GitHub

Finalmente, faça o push para o repositório no GitHub:

```bash
git push -u origin main
```

---

## Comandos Git Úteis

- Verificar status do repositório: `git status`
- Visualizar histórico de commits: `git log`
- Criar novo branch: `git checkout -b nome-do-branch`
- Mudar para outro branch: `git checkout nome-do-branch`
- Atualizar repositório local: `git pull origin main`

