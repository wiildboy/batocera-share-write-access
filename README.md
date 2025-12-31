# **Abilitare la Scrittura sulla Partizione SHARE di Batocera 42 in Linux Mint**  
# **Enable Write Access to Batocera 42 SHARE Partition on Linux Mint**

![Status](https://img.shields.io/badge/status-stable-brightgreen)  
![Linux](https://img.shields.io/badge/Linux-Mint-87CF3E?logo=linuxmint&logoColor=white)  
![Batocera](https://img.shields.io/badge/Batocera-42-blue)  
![License](https://img.shields.io/badge/license-MIT-lightgrey)

---

# **📚 Indice / Table of Contents**

- [🇮🇹 Guida Italiana](#-guida-italiana)
  - **1. Introduzione**
  - **2. Perché usare le ACL**
  - **3. Inserisci la chiavetta USB**
  - **4. Verifica che SHARE sia montata**
  - **5. Abilita la scrittura con ACL**
  - **6. Rendi i permessi permanenti**
  - **7. Test rapido**
  - **8. Conclusione**
- [🇬🇧 English Guide](#-english-guide)
  - **1. Introduction**
  - **2. Why ACLs**
  - **3. Insert the USB stick**
  - **4. Check if SHARE is mounted**
  - **5. Enable write access using ACL**
  - **6. Make permissions persistent**
  - **7. Quick test**
  - **8. Conclusion**

---

# 🇮🇹 **Guida Italiana**

## **1. Introduzione**

Se utilizzi **Batocera 42** su una chiavetta USB e lavori su **Linux Mint**, potresti vedere la partizione **SHARE** ma non riuscire a scriverci.  
Questo accade perché Batocera imposta permessi molto restrittivi.

La soluzione migliore è usare le **ACL (Access Control List)**, che permettono di aggiungere permessi senza modificare quelli originali.

---

## **2. Perché usare le ACL**

Le ACL permettono di:

- aggiungere permessi extra per il tuo utente Mint  
- non toccare i permessi originali di Batocera  
- mantenere compatibilità totale  
- funzionare anche cambiando porta USB  
- rendere i permessi persistenti per nuovi file  

---

## **3. Inserisci la chiavetta USB**

Collega la chiavetta Batocera al PC.  
Linux Mint monterà automaticamente le partizioni.

---

## **4. Verifica che SHARE sia montata**

bash
mount | grep sda2

Dovresti vedere qualcosa tipo:

bash
/dev/sda2 on /media/alex/SHARE type ext4 (...)

## 5. Abilita la scrittura con ACL

Sostituisci alex con il tuo nome utente Mint:

bash
sudo setfacl -R -m u:alex:rwx /media/alex/SHARE

## 6. Rendi i permessi permanenti

bash
sudo setfacl -R -m d:u:alex:rwx /media/alex/SHARE

## 7. Test rapido

bash
touch /media/alex/SHARE/testfile

Se non ricevi errori, la scrittura è abilitata.

Con due semplici comandi puoi finalmente leggere e scrivere nella partizione SHARE di Batocera 42 da Linux Mint, in modo sicuro e permanente.
Questa guida è pensata per essere semplice, chiara e adatta anche ai principianti.

## English Guide

## 1 Introduction

If you use Batocera 42 on a USB stick and manage your files from Linux Mint, you may see the SHARE partition but be unable to write to it.
This happens because Batocera applies strict permissions.

The best solution is to use ACLs (Access Control Lists), which allow adding permissions without modifying the original ones.

## 2 Why ACLs

ACLs allow you to:

    grant extra permissions to your Mint user
    avoid modifying Batocera’s original permissions
    maintain full compatibility
    work even if you change USB ports
    make permissions persistent for new files

## 3 Insert the USB stick

Plug the Batocera USB stick into your computer.
Linux Mint will automatically mount the partitions.

## 4 Check if SHARE is mounted

mount | grep sda2
Expected output:
/dev/sda2 on /media/alex/SHARE type ext4 (...)

## 5 Enable write access using ACL

Replace alex with your Mint username:
sudo setfacl -R -m u:alex:rwx /media/alex/SHARE

## 6 Make permissions persistent

sudo setfacl -R -m d:u:alex:rwx /media/alex/SHARE

## 7 Quick test

touch /media/alex/SHARE/testfile

If no errors appear, write access is enabled.

## 8. Conclusion

With just two commands, you can safely and permanently enable write access to the Batocera 42 SHARE partition from Linux Mint.
This guide is designed to be simple, clear, and beginner-friendly.
