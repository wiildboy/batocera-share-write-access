# Abilitare la Scrittura sulla Partizione SHARE di Batocera 42 in Linux Mint  
# Enable Write Access to Batocera 42 SHARE Partition on Linux Mint

![Status](https://img.shields.io/badge/status-stable-brightgreen)
![Linux](https://img.shields.io/badge/Linux-Mint-87CF3E?logo=linuxmint&logoColor=white)
![Batocera](https://img.shields.io/badge/Batocera-42-blue)
![License](https://img.shields.io/badge/license-MIT-lightgrey)

---

# 📚 Indice / Table of Contents

- [🇮🇹 Guida Italiana](#-guida-italiana)
  - [Introduzione](#introduzione)
  - [Perché usare le ACL](#perché-usare-le-acl)
  - [1 Inserisci la chiavetta USB](#1-inserisci-la-chiavetta-usb)
  - [2 Verifica che SHARE sia montata](#2-verifica-che-share-sia-montata)
  - [3 Abilita la scrittura con ACL](#3-abilita-la-scrittura-con-acl)
  - [4 Rendi i permessi permanenti](#4-rendi-i-permessi-permanenti)
  - [5 Test rapido](#5-test-rapido)
  - [Conclusione](#conclusione)

- [🇬🇧 English Guide](#-english-guide)
  - [Introduction](#introduction)
  - [Why ACLs](#why-acls)
  - [1 Insert the USB stick](#1-insert-the-usb-stick)
  - [2 Check if SHARE is mounted](#2-check-if-share-is-mounted)
  - [3 Enable write access using ACL](#3-enable-write-access-using-acl)
  - [4 Make permissions persistent](#4-make-permissions-persistent)
  - [5 Quick test](#5-quick-test)
  - [Conclusion](#conclusion-1)

---

# 🇮🇹 Guida Italiana

## Introduzione

Se utilizzi **Batocera 42** su una chiavetta USB e lavori su **Linux Mint**, potresti vedere la partizione **SHARE** ma non riuscire a scriverci.  
Questo accade perché Batocera imposta permessi molto restrittivi.

La soluzione migliore è usare le **ACL (Access Control List)**, che permettono di aggiungere permessi senza modificare quelli originali.

---

## Perché usare le ACL

Le ACL permettono di:

- aggiungere permessi extra per il tuo utente Mint  
- non toccare i permessi originali di Batocera  
- mantenere compatibilità totale  
- funzionare anche cambiando porta USB  
- rendere i permessi persistenti per nuovi file  

---

## 1 Inserisci la chiavetta USB

Collega la chiavetta Batocera al PC.  
Linux Mint monterà automaticamente le partizioni.

---

## 2 Verifica che SHARE sia montata

```bash
mount | grep sda2

Dovresti vedere qualcosa tipo:
/dev/sda2 on /media/alex/SHARE type ext4 (...)

## 3 Abilita la scrittura con ACL

Sostituisci alex con il tuo nome utente Mint:
sudo setfacl -R -m u:alex:rwx /media/alex/SHARE

## 4 Rendi i permessi permanenti

sudo setfacl -R -m d:u:alex:rwx /media/alex/SHARE

## 5 Test rapido
touch /media/alex/SHARE/testfile

Se non ricevi errori, la scrittura è abilitata.

#Conclusione

Con due semplici comandi puoi finalmente leggere e scrivere nella partizione SHARE di Batocera 42 da Linux Mint, in modo sicuro e permanente.
Questa guida è pensata per essere semplice, chiara e adatta anche ai principianti.
