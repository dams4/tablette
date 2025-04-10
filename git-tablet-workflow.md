# 🌐 Fluxo Git com Termux no Tablet + GitHub

Este arquivo resume o processo completo que segui para configurar o Termux no Android como ambiente de desenvolvimento Git integrado com GitHub, com autenticação SSH segura. Inclui também comandos essenciais aprendidos no processo.

---

## 📦 Pré-requisitos

- Ter o Termux instalado e atualizado no Android
- Ter um repositório Git no GitHub
- Ter um projeto local no PC (VSCode, por exemplo)

---

## 🔧 Configuração do Git no Termux

```bash
pkg install git -y
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"
```

Verifique:

```bash
git config --list
```

---

## 🔐 Configuração de Chave SSH no Termux

### Gerar a chave:

```bash
ssh-keygen -t ed25519 -C "seu@email.com"
```

Pressione Enter em tudo.

### Ver a chave pública:

```bash
cat ~/.ssh/id_ed25519.pub
```

### Adicionar no GitHub:
- Acesse: https://github.com/settings/keys
- Clique em **New SSH key**
- Cole o conteúdo copiado
- Tipo: `Authentication Key`

---

## 🔁 Clonar o repositório com SSH

```bash
git clone git@github.com:seu-usuario/seu-repo.git
cd seu-repo
```

---

## 📝 Fazendo alterações e enviando para o GitHub

```bash
# Edita um arquivo
micro novo_arquivo.py

# Adiciona e faz commit
git add novo_arquivo.py
git commit -m "Adição via tablet"

# Envia para o GitHub
git push
```

---

## 📥 Receber alterações do GitHub no PC

```bash
git pull
```

Se houver conflitos:

```bash
# Resolver os conflitos manualmente, depois:
git add nome_do_arquivo
git rebase --continue
```

---

## 🔄 Atualizar seu repositório local com o GitHub (forçar sync)

```bash
git fetch origin
git reset --hard origin/main
```

---

## 🚮 Remover um arquivo do projeto via Git no terminal

```bash
git rm nome_do_arquivo.py
git commit -m "Remoção do arquivo nome_do_arquivo.py"
git push
```

Se o arquivo já foi removido manualmente com `rm`:

```bash
git add -u
git commit -m "Remoção via rm e Git"
git push
```

---

## 🛠️ Configurar o repositório remoto com SSH (caso tenha clonado via HTTPS)

```bash
git remote set-url origin git@github.com:seu-usuario/seu-repo.git
```

---

## 🧪 Testar conexão SSH com GitHub

```bash
ssh -T git@github.com
```

Se tudo estiver certo, deve aparecer:

```
Hi seu-usuario! You've successfully authenticated, but GitHub does not provide shell access.
```

---

## ✅ Fluxo completo Git: PC ↔️ GitHub ↔️ Tablet (Termux)

1. Criar/modificar no PC → `git push`
2. No tablet → `git pull`, modifica, `git add`, `commit`, `push`
3. De volta ao PC → `git pull`

---

## 🔥 Observações

- Use `git status` com frequência para ver o que mudou
- Sempre faça `git pull --rebase` antes de `git push`, se houver alterações remotas
- Prefira SSH para evitar digitar token ou senha
- Use `git log --oneline` para ver o histórico resumido

---

Feito por Danilo com Termux, suor e persistência. 💪📲💻


---

## 🆕 Adicionando um novo arquivo ao repositório (passo a passo profissional)

Este é o procedimento padrão que um programador deve seguir para adicionar qualquer novo arquivo (incluindo `.py`, `.cpp`, `.md`, etc.) ao repositório com clareza e boas práticas.

### 1. Criar o novo arquivo:

```bash
micro nome_do_arquivo.extensao
```

Ou:

```bash
touch nome_do_arquivo.extensao
```

### 2. Verificar o que mudou:

```bash
git status
```

### 3. Adicionar o arquivo ao Git:

```bash
git add nome_do_arquivo.extensao
```

### 4. Fazer o commit com mensagem clara:

```bash
git commit -m "Adição de nome_do_arquivo.extensao com funcionalidades XYZ"
```

### 5. Enviar para o GitHub:

```bash
git push
```

✔️ **Essa regra vale para QUALQUER tipo de arquivo**, incluindo `.md` (Markdown), `.txt`, `.py`, `.html`, etc.

💡 Mantenha as mensagens de commit informativas e frequentes, sempre que adicionar ou modificar funcionalidades ou arquivos no projeto.

