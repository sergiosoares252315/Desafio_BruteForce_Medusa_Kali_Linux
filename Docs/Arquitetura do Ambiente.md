## 🖥️ Arquitetura do Ambiente

O laboratório foi configurado no **Oracle VirtualBox** utilizando uma rede **Host-Only (Rede Exclusiva de Hospedeiro)**, garantindo o isolamento total do tráfego em relação à rede externa.

| Papel | Sistema Operacional | IP no Laboratório | Principais Serviços / Ferramentas |
| :--- | :--- | :--- | :--- |
| **Atacante** | Kali Linux | `192.168.56.102`  | `medusa`, `nmap`, `enum4linux` / `smbclient` |
| **Alvo** | Metasploitable 2 | `192.168.56.101`  | vsftpd (FTP), Apache/DVWA (HTTP), Samba (SMB) |

### Verificação de Conectividade
Antes dos testes, foi validada a comunicação entre as máquinas virtuais:
```bash
ping -c 4 192.168.56.101