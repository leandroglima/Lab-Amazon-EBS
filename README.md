# 📦 Lab Amazon EBS — Criação, Snapshot e Restauração

Este laboratório demonstra o processo de **criação de um volume EBS**, **escrita de dados**, **criação de snapshots**, **exclusão de dados** e **restauração a partir de snapshots** usando uma instância Amazon EC2.

---

## 🗂 Visão Geral do Processo


<img width="902" height="470" alt="Imagem colada" src="https://github.com/user-attachments/assets/baa2edb6-4dcf-46d2-9707-f75b7a8ba9df" />


---

## 1️⃣ Criação e Configuração do Volume EBS

1. **Criar o volume no EBS**
   - Criar um novo volume no Amazon EBS e associá-lo à instância EC2 previamente configurada.
   - Para confirmar o vínculo, acesse **Storage** no console da EC2.

2. **Conectar na instância EC2**
   ```bash
   # Usar o Instance Connect no console AWS
Verificar volumes existentes

bash
Copiar código
df -h
Criar sistema de arquivos

bash
Copiar código
sudo mkfs -t ext3 /dev/sdb
Criar ponto de montagem

bash
Copiar código
sudo mkdir /mnt/data-store
Montar volume e configurar montagem automática

bash
Copiar código
sudo mount /dev/sdb /mnt/data-store
echo "/dev/sdb /mnt/data-store ext3 defaults,noatime 1 2" | sudo tee -a /etc/fstab
2️⃣ Escrita e Verificação de Arquivo
Escrever texto no volume

bash
Copiar código
sudo sh -c "echo some text has been written > /mnt/data-store/file.txt"
Verificar conteúdo

bash
Copiar código
cat /mnt/data-store/file.txt
3️⃣ Criação do Snapshot e Exclusão de Arquivo
Criar um snapshot do volume /dev/sdb no console AWS.

Excluir arquivo

bash
Copiar código
sudo rm /mnt/data-store/file.txt
Confirmar exclusão

bash
Copiar código
ls /mnt/data-store/file.txt
4️⃣ Restauração do Volume a partir do Snapshot
Restaurar o volume usando o snapshot criado.

Associar o volume restaurado à instância EC2.

5️⃣ Montagem e Verificação do Volume Restaurado
Criar novo ponto de montagem

bash
Copiar código
sudo mkdir /mnt/data-store2
Montar volume restaurado (exemplo: /dev/sdc)

bash
Copiar código
sudo mount /dev/sdc /mnt/data-store2
Listar arquivo recuperado

bash
Copiar código
ls /mnt/data-store2/file.txt
Verificar volumes montados

bash
Copiar código
df -h

