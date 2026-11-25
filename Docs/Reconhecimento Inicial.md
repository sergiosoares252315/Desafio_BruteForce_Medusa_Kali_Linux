🔍 Reconhecimento Inicial
Para confirmar os serviços ativos e as respectivas portas no alvo, foi executada uma varredura com o Nmap:

  Bash
  nmap -sV -p 21,80,139,445 192.168.56.101

Principais portas identificadas:

  21/tcp — FTP (vsftpd 2.3.4)

  80/tcp — HTTP (Apache httpd hospedando o DVWA)

  139/tcp e 445/tcp — NetBIOS / SMB (Samba smbd)