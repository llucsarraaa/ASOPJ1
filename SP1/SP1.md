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
