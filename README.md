# guiaLinux

Guia de comandos para administração de servidores Linux

## Índice

### 📁 [Comandos de Arquivos e Diretórios](#arquivos-e-diretórios)
1. [ls](#ls) - Listar arquivos e diretórios
2. [cd](#cd) - Navegar entre diretórios
3. [pwd](#pwd) - Mostrar diretório atual
4. [mkdir](#mkdir) - Criar diretórios
5. [rmdir](#rmdir) - Remover diretórios vazios
6. [rm](#rm) - Remover arquivos e diretórios
7. [cp](#cp) - Copiar arquivos e diretórios
8. [mv](#mv) - Mover/renomear arquivos
9. [find](#find) - Encontrar arquivos e diretórios
10. [locate](#locate) - Localizar arquivos rapidamente
11. [which](#which) - Localizar executáveis
12. [whereis](#whereis) - Localizar binários, código fonte e manuais
13. [file](#file) - Determinar tipo de arquivo
14. [stat](#stat) - Exibir informações detalhadas do arquivo
15. [touch](#touch) - Criar arquivos vazios ou atualizar timestamps
16. [chmod](#chmod) - Alterar permissões de arquivo
17. [chown](#chown) - Alterar proprietário do arquivo
18. [chgrp](#chgrp) - Alterar grupo do arquivo
19. [umask](#umask) - Definir permissões padrão
20. [ln](#ln) - Criar links

### 🔄 [Comandos de Processos](#processos)
21. [ps](#ps) - Listar processos em execução
22. [top](#top) - Monitor de processos em tempo real
23. [htop](#htop) - Monitor de processos interativo
24. [pgrep](#pgrep) - Encontrar processos por nome
25. [pkill](#pkill) - Terminar processos por nome
26. [kill](#kill) - Terminar processo por PID
27. [killall](#killall) - Terminar todos os processos com nome específico
28. [jobs](#jobs) - Listar jobs ativos
29. [bg](#bg) - Colocar job em background
30. [fg](#fg) - Trazer job para foreground
31. [nohup](#nohup) - Executar comando imune a hangups
32. [screen](#screen) - Multiplexador de terminal
33. [tmux](#tmux) - Terminal multiplexer
34. [at](#at) - Agendar execução de comandos
35. [cron](#cron) - Agendador de tarefas
36. [systemctl](#systemctl) - Controlar serviços systemd

### 🌐 [Comandos de Rede](#rede)
37. [ping](#ping) - Testar conectividade de rede
38. [wget](#wget) - Baixar arquivos da internet
39. [curl](#curl) - Transferir dados de/para servidores
40. [ssh](#ssh) - Conexão segura remota
41. [scp](#scp) - Cópia segura de arquivos via rede
42. [rsync](#rsync) - Sincronização de arquivos
43. [netstat](#netstat) - Estatísticas de rede
44. [ss](#ss) - Informações de socket
45. [iptables](#iptables) - Configuração de firewall
46. [ufw](#ufw) - Firewall simplificado
47. [ifconfig](#ifconfig) - Configuração de interface de rede
48. [ip](#ip) - Configuração avançada de rede
49. [route](#route) - Tabela de roteamento
50. [traceroute](#traceroute) - Rastrear rota de pacotes

---

## Arquivos e Diretórios

### ls
Lista arquivos e diretórios do diretório atual ou especificado.

```bash
ls                    # Lista arquivos do diretório atual
ls -l                 # Lista detalhada (permissões, proprietário, tamanho, data)
ls -la                # Lista detalhada incluindo arquivos ocultos
ls -lh                # Lista detalhada com tamanhos em formato legível
ls -ltr               # Lista por data de modificação (mais recente por último)
ls /path/to/directory # Lista conteúdo de diretório específico
```

### cd
Navega entre diretórios.

```bash
cd /path/to/directory # Navega para diretório específico
cd ~                  # Navega para diretório home
cd ..                 # Navega para diretório pai
cd -                  # Navega para diretório anterior
cd                    # Navega para diretório home (sem argumentos)
```

### pwd
Mostra o caminho completo do diretório atual.

```bash
pwd                   # Exibe diretório atual
pwd -P                # Exibe caminho físico (resolve links simbólicos)
```

### mkdir
Cria diretórios.

```bash
mkdir directory_name              # Cria um diretório
mkdir -p path/to/nested/directory # Cria diretórios aninhados
mkdir -m 755 directory_name       # Cria diretório com permissões específicas
mkdir dir1 dir2 dir3             # Cria múltiplos diretórios
```

### rmdir
Remove diretórios vazios.

```bash
rmdir directory_name    # Remove diretório vazio
rmdir -p path/to/dir   # Remove diretórios vazios hierarquicamente
```

### rm
Remove arquivos e diretórios.

```bash
rm file.txt           # Remove arquivo
rm -f file.txt        # Força remoção sem confirmação
rm -r directory       # Remove diretório e seu conteúdo recursivamente
rm -rf directory      # Força remoção recursiva sem confirmação
rm *.txt              # Remove todos os arquivos .txt
```

### cp
Copia arquivos e diretórios.

```bash
cp source.txt dest.txt          # Copia arquivo
cp -r source_dir dest_dir       # Copia diretório recursivamente
cp -p file.txt backup.txt       # Preserva atributos (permissões, timestamps)
cp *.txt /backup/               # Copia todos arquivos .txt para /backup/
cp -u source.txt dest.txt       # Copia apenas se source for mais novo
```

### mv
Move ou renomeia arquivos e diretórios.

```bash
mv old_name.txt new_name.txt    # Renomeia arquivo
mv file.txt /path/to/directory/ # Move arquivo para outro diretório
mv dir1 dir2                    # Renomeia diretório
mv *.txt /backup/               # Move todos arquivos .txt
```

### find
Encontra arquivos e diretórios baseado em critérios.

```bash
find /path -name "*.txt"        # Encontra arquivos .txt
find . -type f                  # Encontra apenas arquivos
find . -type d                  # Encontra apenas diretórios
find . -size +100M              # Encontra arquivos maiores que 100MB
find . -mtime -7                # Arquivos modificados nos últimos 7 dias
find . -name "*.log" -delete    # Encontra e deleta arquivos .log
```

### locate
Localiza arquivos usando banco de dados indexado.

```bash
locate filename         # Localiza arquivo por nome
locate "*.conf"         # Localiza arquivos de configuração
locate -i filename      # Busca case-insensitive
updatedb               # Atualiza banco de dados do locate (como root)
```

### which
Localiza executáveis no PATH.

```bash
which command_name      # Mostra caminho do executável
which -a python         # Mostra todos os caminhos encontrados
```

### whereis
Localiza binários, código fonte e páginas de manual.

```bash
whereis command_name    # Localiza binário, source e manual
whereis -b command      # Apenas binário
whereis -m command      # Apenas manual
whereis -s command      # Apenas source
```

### file
Determina o tipo de arquivo.

```bash
file filename           # Mostra tipo do arquivo
file *                  # Mostra tipo de todos os arquivos
file -b filename        # Mostra apenas a descrição do tipo
```

### stat
Exibe informações detalhadas sobre arquivo ou sistema de arquivos.

```bash
stat filename           # Informações detalhadas do arquivo
stat -f /               # Informações do sistema de arquivos
stat -c '%n %s' file    # Formato customizado (nome e tamanho)
```

### touch
Cria arquivos vazios ou atualiza timestamps.

```bash
touch filename          # Cria arquivo vazio ou atualiza timestamp
touch -c filename       # Não cria arquivo se não existir
touch -t 202301011200 file # Define timestamp específico
touch file1 file2 file3 # Cria múltiplos arquivos
```

### chmod
Altera permissões de arquivos e diretórios.

```bash
chmod 755 filename      # rwxr-xr-x
chmod +x script.sh      # Adiciona permissão de execução
chmod -w filename       # Remove permissão de escrita
chmod u+x,g-w filename  # Adiciona exec para user, remove write para group
chmod -R 644 directory  # Aplica recursivamente
```

### chown
Altera proprietário de arquivos e diretórios.

```bash
chown user filename             # Altera proprietário
chown user:group filename       # Altera proprietário e grupo
chown -R user:group directory   # Aplica recursivamente
chown :group filename           # Altera apenas o grupo
```

### chgrp
Altera grupo de arquivos e diretórios.

```bash
chgrp group filename            # Altera grupo
chgrp -R group directory        # Aplica recursivamente
```

### umask
Define permissões padrão para novos arquivos.

```bash
umask                   # Mostra umask atual
umask 022               # Define umask (arquivos 644, diretórios 755)
umask -S                # Mostra em formato simbólico
```

### ln
Cria links entre arquivos.

```bash
ln target link_name             # Cria hard link
ln -s target symbolic_link      # Cria link simbólico
ln -sf target existing_link     # Força criação de link simbólico
```

---

## Processos

### ps
Lista processos em execução.

```bash
ps                      # Processos do usuário atual
ps aux                  # Todos os processos com detalhes
ps -ef                  # Formato completo
ps -u username          # Processos de usuário específico
ps -C process_name      # Processos por nome
ps --forest            # Árvore de processos
```

### top
Monitor de processos em tempo real.

```bash
top                     # Monitor básico
top -u username         # Processos de usuário específico
top -p PID             # Monitorar processo específico
# Teclas durante execução:
# q - sair
# k - matar processo
# r - alterar prioridade (renice)
# M - ordenar por uso de memória
# P - ordenar por uso de CPU
```

### htop
Monitor de processos interativo (se instalado).

```bash
htop                    # Interface melhorada do top
htop -u username        # Processos de usuário específico
# F1-F10 para funções específicas
# Setas para navegar, Space para marcar
```

### pgrep
Encontra processos por nome ou outros critérios.

```bash
pgrep process_name      # PIDs de processos por nome
pgrep -u username       # PIDs de processos do usuário
pgrep -f pattern        # Busca no comando completo
pgrep -l pattern        # Mostra PID e nome
```

### pkill
Termina processos por nome ou critérios.

```bash
pkill process_name      # Mata processos por nome
pkill -u username       # Mata processos do usuário
pkill -f pattern        # Mata por padrão no comando
pkill -9 process_name   # Mata com SIGKILL (força)
```

### kill
Termina processo por PID.

```bash
kill PID                # Termina processo (SIGTERM)
kill -9 PID             # Força terminação (SIGKILL)
kill -l                 # Lista sinais disponíveis
kill -HUP PID           # Envia sinal SIGHUP
kill -STOP PID          # Para processo
kill -CONT PID          # Continua processo parado
```

### killall
Termina todos os processos com nome específico.

```bash
killall process_name    # Mata todos os processos
killall -9 process_name # Força terminação
killall -u username     # Mata processos do usuário
killall -i process_name # Modo interativo (confirma)
```

### jobs
Lista jobs ativos na sessão atual.

```bash
jobs                    # Lista jobs
jobs -l                 # Com PIDs
jobs -r                 # Apenas jobs rodando
jobs -s                 # Apenas jobs parados
```

### bg
Coloca job em background.

```bash
bg                      # Último job para background
bg %1                   # Job número 1 para background
bg %?string             # Job que contém string
```

### fg
Traz job para foreground.

```bash
fg                      # Último job para foreground
fg %1                   # Job número 1 para foreground
fg %?string             # Job que contém string
```

### nohup
Executa comando imune a hangups.

```bash
nohup command &         # Executa em background imune a hangup
nohup command > log.txt 2>&1 & # Redireciona saída para arquivo
```

### screen
Multiplexador de terminal.

```bash
screen                  # Inicia nova sessão
screen -S session_name  # Sessão com nome
screen -ls              # Lista sessões
screen -r               # Reconecta à última sessão
screen -r session_name  # Reconecta à sessão específica
screen -d session_name  # Desconecta sessão
# Ctrl+A, D - desconectar
# Ctrl+A, C - nova janela
# Ctrl+A, N - próxima janela
```

### tmux
Terminal multiplexer moderno.

```bash
tmux                    # Nova sessão
tmux new -s session_name # Sessão com nome
tmux ls                 # Lista sessões
tmux attach -t session  # Anexa à sessão
tmux kill-session -t session # Mata sessão
# Ctrl+B, D - desconectar
# Ctrl+B, C - nova janela
# Ctrl+B, N - próxima janela
```

### at
Agenda execução de comandos.

```bash
echo "command" | at now + 1 hour    # Executa em 1 hora
at 14:30                           # Executa às 14:30
at midnight                        # Executa à meia-noite
atq                               # Lista jobs agendados
atrm job_id                       # Remove job agendado
```

### cron
Agendador de tarefas.

```bash
crontab -e              # Edita crontab do usuário
crontab -l              # Lista crontab atual
crontab -r              # Remove crontab
crontab -u user -e      # Edita crontab de outro usuário
# Formato: min hora dia mês dia_semana comando
# 0 2 * * * /backup.sh  # Todo dia às 2:00
```

### systemctl
Controla serviços systemd.

```bash
systemctl status service_name    # Status do serviço
systemctl start service_name     # Inicia serviço
systemctl stop service_name      # Para serviço
systemctl restart service_name   # Reinicia serviço
systemctl enable service_name    # Habilita na inicialização
systemctl disable service_name   # Desabilita na inicialização
systemctl list-units --type=service # Lista todos os serviços
```

---

## Rede

### ping
Testa conectividade de rede.

```bash
ping hostname           # Ping contínuo
ping -c 4 hostname      # Ping com 4 pacotes
ping -i 2 hostname      # Intervalo de 2 segundos
ping -s 1000 hostname   # Pacotes de 1000 bytes
ping6 hostname          # Ping IPv6
```

### wget
Baixa arquivos da internet.

```bash
wget http://example.com/file.zip    # Download simples
wget -O output.zip http://url       # Salva com nome específico
wget -c http://url                  # Continua download interrompido
wget -r http://site.com             # Download recursivo
wget --limit-rate=200k http://url   # Limita velocidade
wget -b http://url                  # Download em background
```

### curl
Transfere dados de/para servidores.

```bash
curl http://example.com             # GET request
curl -o file.html http://url        # Salva em arquivo
curl -O http://url/file.zip         # Usa nome original
curl -I http://url                  # Apenas headers
curl -X POST -d "data" http://url   # POST request
curl -u user:pass http://url        # Autenticação básica
curl -L http://url                  # Segue redirects
```

### ssh
Conexão segura remota.

```bash
ssh user@hostname               # Conexão básica
ssh -p 2222 user@hostname       # Porta específica
ssh -i keyfile user@hostname    # Chave privada específica
ssh -L 8080:localhost:80 user@host # Port forwarding local
ssh -R 8080:localhost:80 user@host # Port forwarding remoto
ssh -X user@hostname            # X11 forwarding
```

### scp
Cópia segura de arquivos via rede.

```bash
scp file.txt user@host:/path/       # Copia arquivo para remoto
scp user@host:/path/file.txt .      # Copia arquivo do remoto
scp -r directory user@host:/path/   # Copia diretório recursivamente
scp -P 2222 file.txt user@host:     # Porta específica
scp -i keyfile file.txt user@host:  # Chave específica
```

### rsync
Sincronização eficiente de arquivos.

```bash
rsync -av source/ dest/             # Sincronização local
rsync -av source/ user@host:dest/   # Sincronização remota
rsync -avz source/ user@host:dest/  # Com compressão
rsync -av --delete src/ dest/       # Deleta arquivos extras no destino
rsync -av --exclude='*.tmp' src/ dest/ # Exclui arquivos .tmp
rsync -avP source/ dest/            # Com progresso
```

### netstat
Estatísticas de rede e conexões.

```bash
netstat -tulpn          # Todas as portas TCP/UDP
netstat -an             # Todas as conexões
netstat -rn             # Tabela de roteamento
netstat -i              # Interfaces de rede
netstat -s              # Estatísticas por protocolo
```

### ss
Informações modernas de socket.

```bash
ss -tulpn               # Substituto moderno do netstat
ss -4                   # Apenas IPv4
ss -6                   # Apenas IPv6
ss state established    # Apenas conexões estabelecidas
ss sport = :80          # Porta origem 80
ss dport = :443         # Porta destino 443
```

### iptables
Configuração de firewall.

```bash
iptables -L                         # Lista regras
iptables -A INPUT -p tcp --dport 22 -j ACCEPT  # Permite SSH
iptables -A INPUT -p tcp --dport 80 -j ACCEPT  # Permite HTTP
iptables -A INPUT -j DROP           # Bloqueia resto
iptables -D INPUT 1                 # Deleta regra 1
iptables -F                         # Limpa todas as regras
iptables-save > backup.rules        # Backup das regras
```

### ufw
Firewall simplificado.

```bash
ufw enable              # Habilita firewall
ufw disable             # Desabilita firewall
ufw allow ssh           # Permite SSH
ufw allow 80            # Permite porta 80
ufw deny 23             # Bloqueia porta 23
ufw status              # Status e regras
ufw reset               # Reseta configuração
```

### ifconfig
Configuração de interface de rede (comando clássico).

```bash
ifconfig                # Mostra todas as interfaces
ifconfig eth0           # Mostra interface específica
ifconfig eth0 up        # Ativa interface
ifconfig eth0 down      # Desativa interface
ifconfig eth0 192.168.1.100 netmask 255.255.255.0 # Define IP
```

### ip
Configuração avançada de rede (comando moderno).

```bash
ip addr show            # Mostra endereços IP
ip link show            # Mostra interfaces de rede
ip route show           # Mostra rotas
ip addr add 192.168.1.100/24 dev eth0  # Adiciona IP
ip link set eth0 up     # Ativa interface
ip route add default via 192.168.1.1   # Define gateway padrão
```

### route
Configuração da tabela de roteamento.

```bash
route -n                # Mostra tabela de roteamento
route add default gw 192.168.1.1   # Adiciona rota padrão
route add -net 192.168.2.0/24 gw 192.168.1.1  # Adiciona rota específica
route del default       # Remove rota padrão
```

### traceroute
Rastreia rota de pacotes até o destino.

```bash
traceroute hostname     # Traça rota até hostname
traceroute -n hostname  # Sem resolução DNS
traceroute -p 80 hostname # Porta específica
traceroute6 hostname    # IPv6
mtr hostname           # Traceroute contínuo (se instalado)
```

---

## Contribuição

Veja [CONTRIBUTING.md](CONTRIBUTING.md) para diretrizes de contribuição.

## Licença

Este projeto está licenciado sob a [Creative Commons Attribution-ShareAlike 4.0 International License](LICENSE).
