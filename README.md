# 📦 Lab Amazon EBS — Criação, Snapshot e Restauração

Este laboratório demonstra o processo de **criação de um volume EBS**, **escrita de dados**, **criação de snapshots**, **exclusão de dados** e **restauração a partir de snapshots** usando uma instância Amazon EC2.

## 1️⃣ Criação e Configuração do Volume EBS

1. **Criar o volume no EBS**
   - Criar um novo volume no Amazon EBS e associá-lo à instância EC2 previamente configurada.
   - Para confirmar o vínculo, acesse **Storage** no console da EC2.

2. **Conectar na instância EC2**

   # Usar o Instance Connect no console AWS
Verificar volumes existentes
df -h

Criar sistema de arquivos
sudo mkfs -t ext3 /dev/sdb
Criar ponto de montagem

sudo mkdir /mnt/data-store
Montar volume e configurar montagem automática

sudo mount /dev/sdb /mnt/data-store
echo "/dev/sdb /mnt/data-store ext3 defaults,noatime 1 2" | sudo tee -a /etc/fstab

2️⃣ Escrita e Verificação de Arquivo
Escrever texto no volume

sudo sh -c "echo some text has been written > /mnt/data-store/file.txt"
Verificar conteúdo

cat /mnt/data-store/file.txt

3️⃣ Criação do Snapshot e Exclusão de Arquivo
Criar um snapshot do volume /dev/sdb no console AWS.

Excluir arquivo

sudo rm /mnt/data-store/file.txt
Confirmar exclusão

ls /mnt/data-store/file.txt


4️⃣ Restauração do Volume a partir do Snapshot
Restaurar o volume usando o snapshot criado.

Associar o volume restaurado à instância EC2.

5️⃣ Montagem e Verificação do Volume Restaurado

Criar novo ponto de montagem

sudo mkdir /mnt/data-store2
Montar volume restaurado (exemplo: /dev/sdc)


sudo mount /dev/sdc /mnt/data-store2

Listar arquivo recuperado

ls /mnt/data-store2/file.txt

Verificar volumes montados

df -h

---

## 🗂 Visão Geral do Processo


<img width="902" height="470" alt="Imagem colada" src="https://github.com/user-attachments/assets/baa2edb6-4dcf-46d2-9707-f75b7a8ba9df" />

<img width="1838" height="1004" alt="Imagem colada (6)" src="https://github.com/user-attachments/assets/6822c14a-d521-47b7-aadd-05d1b18fd1ae" />

<img width="1854" height="1051" alt="Imagem colada (4)" src="https://github.com/user-attachments/assets/c9f80069-1dc7-4db3-a08e-7b1fc5fead4c" />

<img width="1854" height="1051" alt="Imagem colada (2)" src="https://github.com/user-attachments/assets/15301b5c-e674-4f84-a734-5de03fbfbe29" />


<img width="1854" height="1051" alt="Imagem colada (3)" src="https://github.com/user-attachments/assets/552e1c99-b5a6-477e-8ab1-46446d64f6e8" />

<img width="1838" height="1004" alt="Imagem colada (7)" src="https://github.com/user-attachments/assets/36950b35-46a2-415a-b227-33f170739da2" />

<img width="1838" height="642" alt="Imagem colada (5)" src="https://github.com/user-attachments/assets/eff19544-20af-4e7d-a1f6-87b49f14489a" />

---

