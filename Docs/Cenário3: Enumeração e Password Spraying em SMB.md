🔐 Cenário 3: Enumeração e Password Spraying em SMB

Diferença Conceitual
Ao contrário da força bruta tradicional (muitas senhas para um único usuário), o Password Spraying testa poucas senhas comuns contra vários usuários. Essa abordagem reduz o ruído e evita o bloqueio automático de contas (Account Lockout).

1. Enumeração de Usuários

Para levantar os usuários válidos do sistema antes do ataque, foi utilizada a enumeração via SMB:

  Bash
  enum4linux -U 192.168.56.101

Os usuários identificados foram salvos em wordlists/PasswordSpray/sb_users.txt

  user
  msfadmin
  service

2. Execução do Password Spraying
Com a lista de usuários em mãos, testou-se à listta de senhas salvas em wordlists/PasswordSpray/senhas_spray.txt contra todas as contas utilizando o módulo smbnt:

  Bash
  medusa -h 192.168.56.101 -U sb_users.txt -P senhas_spray.txt -M smbnt -t 2 -M

  Como resultado da execução do comando anterior, foi possível identificar com sucesso o acesso válido utilizando o usuário msfadmin e a senha msfadmin.

  Validação do Acesso
  O acesso ao compartilhamento SMB com a credencial descoberta foi confirmado utilizando o smbclient:

  Bash
  smbclient -L //192.168.56.101 -U msfadmin