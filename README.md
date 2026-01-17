# **Abilitare la Scrittura sulla Partizione SHARE di Batocera 42 in Linux Mint**  
# **Enable Write Access to Batocera 42 SHARE Partition on Linux Mint**

![Status](https://img.shields.io/badge/Status-Stable-brightgreen)
![Linux Mint](https://img.shields.io/badge/Linux-Mint-87CF3E?logo=linuxmint&logoColor=white)
![Batocera 42](https://img.shields.io/badge/Batocera-42-blue)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

![Markdown](https://img.shields.io/badge/Made%20with-Markdown-000000?logo=markdown)
![Platform Linux](https://img.shields.io/badge/Platform-Linux-1793D1?logo=linux&logoColor=white)
![Shell Bash](https://img.shields.io/badge/Shell-Bash-4EAA25?logo=gnubash&logoColor=white)

![Retro Gaming](https://img.shields.io/badge/Retro-Gaming-orange)
![Batocera Compatible](https://img.shields.io/badge/Batocera-Compatible-blue)

![Maintained](https://img.shields.io/badge/Maintained-yes-brightgreen)
![Contributions Welcome](https://img.shields.io/badge/Contributions-welcome-blue)
![Docs Included](https://img.shields.io/badge/Docs-Included-success)

![Languages](https://img.shields.io/badge/Languages-IT%20%7C%20EN-blue)
![Author WiildBoy](https://img.shields.io/badge/Author-WiildBoy-red)

![Stars](https://img.shields.io/github/stars/WiildBoy/batocera-share-write-access?style=flat&color=yellow)
![Forks](https://img.shields.io/github/forks/WiildBoy/batocera-share-write-access?style=flat&color=lightblue)
![Visitors](https://visitor-badge.laobi.icu/badge?page_id=WiildBoy.batocera-share-write-access)
![Last Commit](https://img.shields.io/github/last-commit/WiildBoy/batocera-share-write-access)
![Repo Size](https://img.shields.io/github/repo-size/WiildBoy/batocera-share-write-access)
![Commit Activity](https://img.shields.io/github/commit-activity/m/WiildBoy/batocera-share-write-access)


---

# **📚 Indice / Table of Contents**

- [🇮🇹 Guida Italiana](#guida-italiana)
  - **1. Introduzione**
  - **2. Perché usare le ACL**
  - **3. Inserisci la chiavetta USB**
  - **4. Verifica che SHARE sia montata**
  - **5. Abilita la scrittura con ACL**
  - **6. Rendi i permessi permanenti**
  - **7. Test rapido**
  - **8. Conclusione**
- [🇬🇧 English Guide](#english-guide)
  - **1. Introduction**
  - **2. Why ACLs**
  - **3. Insert the USB stick**
  - **4. Check if SHARE is mounted**
  - **5. Enable write access using ACL**
  - **6. Make permissions persistent**
  - **7. Quick test**
  - **8. Conclusion**

---
<a id="guida-italiana"></a>
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

`mount | grep SHARE`

Dovresti vedere qualcosa tipo:

/dev/sda2 on /media/alex/SHARE type ext4 (...)

Nota: Il dispositivo potrebbe essere diverso da sda2 (ad esempio sdb2, sdc2, ecc.) 
a seconda di quanti dischi/USB hai collegato. L'importante è che vedi "SHARE" nel risultato.

Se non vedi nulla, verifica quale dispositivo corrisponde alla partizione SHARE con:

`lsblk -o NAME,LABEL,SIZE,FSTYPE,MOUNTPOINT`

Cerca la riga con LABEL "SHARE" e annota il dispositivo (es. sdb2).

## 5. Abilita la scrittura con ACL

Sostituisci alex con il tuo nome utente Mint:

`sudo setfacl -R -m u:alex:rwx /media/alex/SHARE`

## 6. Rendi i permessi permanenti

`sudo setfacl -R -m d:u:alex:rwx /media/alex/SHARE`

## 7. Test rapido

`touch /media/alex/SHARE/testfile`

Se non ricevi errori, la scrittura è abilitata.

Con due semplici comandi puoi finalmente leggere e scrivere nella partizione SHARE di Batocera 42 da Linux Mint, in modo sicuro e permanente.
Questa guida è pensata per essere semplice, chiara e adatta anche ai principianti.

---

<a id="english-guide"></a>
## 🇬🇧 English Guide

## 1 Introduction

If you use Batocera 42 on a USB stick and manage your files from Linux Mint, you may see the SHARE partition but be unable to write to it.
This happens because Batocera applies strict permissions.

The best solution is to use ACLs (Access Control Lists), which allow adding permissions without modifying the original ones.

## 2 Why ACLs

ACLs allow you to:

- grant extra permissions to your Mint user
- avoid modifying Batocera’s original permissions
- maintain full compatibility
- work even if you change USB ports
- make permissions persistent for new files

## 3 Insert the USB stick
Plug the Batocera USB stick into your computer.
Linux Mint will automatically mount the partitions.

## 4 Check if SHARE is mounted

`mount | grep SHARE`

You should see something like:

/dev/sda2 on /media/alex/SHARE type ext4 (...)

Note: The device might be different from sda2 (e.g., sdb2, sdc2, etc.) 
depending on how many disks/USB drives you have connected. The important thing is that you see "SHARE" in the output.

If you don't see anything, check which device corresponds to the SHARE partition with:

`lsblk -o NAME,LABEL,SIZE,FSTYPE,MOUNTPOINT`

Look for the row with LABEL "SHARE" and note the device (e.g., sdb2).


## 5 Enable write access using ACL

Replace alex with your Mint username:

`sudo setfacl -R -m u:alex:rwx /media/alex/SHARE`

## 6 Make permissions persistent

`sudo setfacl -R -m d:u:alex:rwx /media/alex/SHARE`

## 7 Quick test

`touch /media/alex/SHARE/testfile`

If no errors appear, write access is enabled.

## 8. Conclusion

With just two commands, you can safely and permanently enable write access to the Batocera 42 SHARE partition from Linux Mint.
This guide is designed to be simple, clear, and beginner-friendly.
