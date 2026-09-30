---
layout: default
title: "SISTEMES D'INICI"
---
# SISTEMES D'INICI

## Índex

- [1- SystemV vs Upstart vs Systemd](#1--systemv-vs-upstart-vs-systemd)
  - [1.1- Runlevels o Targets?](#11--runlevels-o-targets)
  - [1.2- Quin és el nostre SO?](#12--quin-és-el-nostre-so)
- [2- SystemV](#2--systemv)
  - [2.1- Directoris](#21--directoris)
  - [2.2- Procés d'arrencada](#22--procés-darrencada)
- [3- Systemd](#3--systemd)
  - [3.1- Directoris](#31--directoris)
  - [3.2- systemctl](#32--systemctl)
  - [3.3- Dependències](#33--dependències)
  - [3.4- Modificar target provisional](#34--modificar-target-provisional)
  - [3.5- Modificar target definitiu](#35--modificar-target-definitiu)
  - [3.6- Afegir o treure serveis d'un target](#36--afegir-o-treure-serveis-dun-target)
  - [3.7- Creació d'un nou servei](#37--creació-dun-nou-servei)
- **[PRÀCTICA AVALUABLE](#practica-avaluable)**

---

## Conceptes fonamentals

* **Kernel (Nucli):** Component central encarregat de coordinar i assignar els recursos del sistema.
* **Aplicació:** Programa interactiu que funciona en primer pla (*foreground*) i requereix la intervenció directa de l'usuari.
* **Servei:** Programa vinculat al sistema operatiu que s'executa de manera autònoma en segon pla (*background*).
* **Procés:** Instància o funció interna en execució controlada pel sistema operatiu.

> **Nota:** Les aplicacions i els serveis generen un o més processos individualitzats, els quals el sistema operatiu s'encarrega de planificar i sincronitzar contínuament.





# 🛡️ Pràctica Systemd: SysHealth Dashboard

Aquest projecte demostra la creació i configuració d'un **target de systemd personalitzat** (`syshealth.target`) configurat com a target per defecte (*default target*). El target coordina dos serveis en segon pla executats amb permisos de superusuari (`root`):
1. **Un recolector de mètriques**: Executa un script en Bash que desa l'estat del sistema en format JSON.
2. **Un servidor web Flask**: Ofereix una interfície gràfica per visualitzar el dashboard en temps real a través del navegador.

---

## 📋 Taula d'Objectius Completats

| Requisit | Estat | Implementació |
| :--- | :---: | :--- |
| **1. Crear target propi, fer-lo default i comprovar accés** |  `syshealth.target` creat, definit com a default amb `systemctl set-default` i verificat amb `get-default`. |
| **2. Crear serveis dintre del target i comprovar inici** |  `syshealth-collector.service` i `syshealth-web.service` associats mitjançant `WantedBy=syshealth.target`. |
| **3. Executar script amb permisos de root** |  Configurat `User=root` als fitxers de servei unitats de systemd. |
| **4. Programar script i provar-lo manualment** |  Script `syshealth_collector.sh` provat manualment verificant la generació de dades. |

---

## 🚀 Guia de Desplegament Pas a Pas

### PAS 1: Preparar l'entorn i instal·lar dependències

Instal·lem Python 3 i el framework web Flask necessaris per al servidor.

```bash
sudo apt update
sudo apt install -y python3 python3-flask

<img width="690" height="212" alt="1" src="https://github.com/user-attachments/assets/72d4aad8-c97b-481d-bd74-b10b8f8cb768" />

<img width="665" height="507" alt="image" src="https://github.com/user-attachments/assets/317ae173-ec52-4fc8-afb4-e2782a23c53d" />
