# git-Tutorial
Pequeno tutorial resumido de como usar o Git e seus comandos.

# Configurações iniciais do Git

- Define nome do usuário atual: `git config --global user.name "Denisson Silva"`
- Define email do usuário atual: `config --global user.email "denissonjs@outlook.com"`
- Define/informa qual editor de codigo o usuário está utilizando: `git config --global core.editor visualStudio`
- Retorna o nome do usuário atual: `git config user.name`
- Retorna todas as informações cadastradas: `git config --list`

# Iniciando um novo repositório: `git init`

- Se a pasta estiver vazia ele cria um repositório vazio, caso contrário, ele cria um repositório com as pastas que estão ali.

# Branch: São as versões do sistema/programa. No primeiro commit ele cria a branch 'master', que é a primeira versão do programa.

## Trabalhando com branches
- Criando nova branch: `git branch nome_da_branch`
	- Nota: Quando criamos uma nova branch, o que tinha na versão atual é copiada para a nova, inclusive os commits. A partir daí, as alterações de uma branch, não alcançam a outra.
- Mudar de Branch: `git checkout nome_da_branch_destino`
- Listar branches, onde a branch com '*' é a atual: `git branch`

# Adicionando modificações ao stage (stage é como se fosse um arq. temp que armazena somente o que é adicionado lá)
- Adicionando modificações de um arquivo: `git add 'arquivo'`
- Adicionando todas as modificações: `git add .`

# Verificar Status do projeto: `git status`

# Verificando Modificações nos arquivos
- Listar detalhes das alterações dos arquivos: `git diff`
- Listar nome dos arquivos que foram alterados: `git diff --name-only`
- Listar detalhes das alterações de arquivo especifico: `git diff nome_do_arquivo`
- Desfazer modificações não adicionadas em um arquivo (volta ao estado original do commit): `git checkout HEAD --nome_do_arquivo`

# Commit efetiva as modificações no repositório ao git
- Commit das modificações adicionadas na área de stage (no git add) `git commit -m 'mensagem'`
- Adicionar ao stage e Commita todas as modificações do projeto: `git commit -am 'mensagem'`

# Listar commits da branch atual: `git log`
- Retorna hash do commit, branch do commit, quem fez o commit, quando foi feito o commit e comentário do commit.

# Revertendo commits
- Todo commit traz um hash, só os sete primeiros digitos do hash são necessários caso não queira copiar todo o hash.

- Voltar para antes do commit (alterações pré-commit ainda ficam lá): `git reset --soft hash_do_commit_desejado`
- Voltar para antes do add (alterações pré-add ainda ficam lá): `git reset --mixed hash do commit desejado`
- Voltar para commit anterior deletando permanentemente o commit atual: `git reset --hard hash do commit desejado`

# Subindo Repositório para um controlador de versão remoto (GitHub, GitLab, BitBucket)
- Cria repositorio no controlador remoto.
- Setando o repositório remoto: `git remote add origin url_do_repo_remoto`
- Efetua o push pra o repositorio remoto: `git push origin main`

