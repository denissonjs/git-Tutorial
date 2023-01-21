# git-Tutorial
Pequeno tutorial resumido de como usar o Git e seus comandos.

# Configurações iniciais do Git

- Define nome do usuário atual: `git config --global user.name "Denisson Silva"`
- Define email do usuário atual: `git config --global user.email "denissonjs@outlook.com"`
- Define/informa qual editor de codigo o usuário está utilizando: `git config --global core.editor visualStudio`
- Retorna o nome do usuário atual: `git config user.name`
- Retorna todas as informações cadastradas: `git config --list`

# Repositório:
- Repositório é o conjunto de arquivos do seu projeto.
	- Iniciar Repositório: `git init`.
	- Se a pasta estiver vazia ele cria um repositório vazio, caso contrário, ele cria um repositório com as pastas que estão ali.

# Branchs
- São as versões do sistema/programa. No primeiro commit ele cria a branch 'master', que é a primeira versão do programa.

## Trabalhando com branches
- Criando nova branch: `git branch nome_da_branch`
	- Nota: Quando criamos uma nova branch, o que tinha na versão atual é copiada para a nova, inclusive os commits. A partir daí, as alterações de uma branch, não alcançam a outra.
- Mudar de Branch: `git checkout nome_da_branch_destino`
- Listar branches, onde a branch com '*' é a atual: `git branch`

# Stage
- Stage é como se fosse um .temp que armazena somente o que é adicionado lá, somente o que está em Stage pode ser commitado, assim, modificações que você não quer commitar podem ficar de fora.
	- Adicionando modificações de um arquivo: `git add 'arquivo'`
	- Adicionando todas as modificações: `git add .`

# Commit
- O Commit salva, no seu repositorio, todas as modificações adicionadas ao stage.
	- Comando: `git commit -m 'Resumo das alterações feitas'`
	- Para adicionar ao stage e Commita todas as modificações do projeto: `git commit -am 'Resumo das alterações feitas'`

### Listar commits da branch atual: `git log`
- Retorna hash (codigo) do commit, branch do commit, quem fez o commit, quando foi feito o commit e comentário do commit.

### Revertendo commits
- Todo commit traz um hash, só os sete primeiros digitos do hash são necessários caso não queira copiar todo o hash.
	- Voltar para antes do commit (alterações pré-commit ainda ficam lá): `git reset --soft hash_do_commit_desejado`
	- Voltar para antes do add (alterações pré-add ainda ficam lá): `git reset --mixed hash do commit desejado`
	- Voltar para commit anterior deletando permanentemente o commit atual: `git reset --hard hash do commit desejado`

# Status do repositório
- Execute: `git status`
	- Retorna detalhadamente (com legenda) o status atual da branch.
- No VsCode:
	- Verde com U: Untracked - O git não sabe da existencia do arquivo, ou seja, voê criou mas não adicionou ao stage.
	- Verde com A: Added - Arquivo novo e adicionado ao stage.
	- Amarelo M: Modified - O arquivo foi modificado, mas não foi commitado.

# Status de Modificações
- Listar detalhes das alterações dos arquivos: `git diff`
- Listar nome dos arquivos que foram alterados: `git diff --name-only`
- Listar detalhes das alterações de arquivo especifico: `git diff nome_do_arquivo`
- Desfazer modificações não adicionadas em um arquivo (volta ao estado original do commit): `git checkout HEAD --nome_do_arquivo`

# Controlador de versão Remoto
- Algumns versionadores: `GitHub`, `GitLab`, `BitBucket`
- Cria repositorio no controlador remoto.
- Defina no git, onde está seu repositório remoto: `git remote add origin url_do_repo_remoto`
- Efetua o push pra o repositorio remoto: `git push origin main`

# Exceções
- fatal: not a git repository (or any of the parent directories): .git
	- Git não foi iniciado: `git init`
	
- remote: Repository not found. fatal: repository 'url_do_repo_remoto' not found
	- Causas:
		- O repositório não existe ou link errado.
		- O repositório é privado e você não tem acesso a ele.
			- Se o repositório for seu e mesmo assim retornar essa exceção, você certamente não autenticou seu terminal com sua conta git/remoteRepo. Nesse caso execute as instruções do topico `Configurações iniciais do Git` deste tutorial
	
-  ! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'url_do_repo_remoto'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
	- Foi enviada um arquivo que você também modificou foi modificado no repositório remoto.
		- Execute o pull das alterações para continuar: `git pull`
- Auto-merging server/views/index.html
CONFLICT (content): Merge conflict in server/views/index.html
Automatic merge failed; fix conflicts and then commit the result.
	- Foi enviada uma modificação no mesmo arquivo e mesma linha que você no repositório.
		- O Git marcará o arquivo indicado pela exceção da seguinte forma: `
		<<<<<<< HEAD Sua alteração ======= Alteração que estava no remoto antes do seu pull. >>>>>>>`
		- Sendo assim, é só escolher qual modificação permanece, apagar e efetuar novo commit/push.
		
# Referências
- Módulo Git e GitHub do curso fullstack da B7Web do Bonieky Lacerda: https://b7web.com.br/
- Artigo "Resolvendo conflito no Git" escrito por @ricardo pelo blog Metring: https://encurtador.com.br/tvyJ9
