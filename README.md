# Infraestructura como código (IaC): Laboratorio de seguridad RedHat/AlmaLinux

Este repositorio contiene la arquitectura de automatización para el despliegue y aseguramiento de un entorno de red empresarial basado en **Redhat/AlmaLinux (RHEL Binary Compatible)** utilizando **Ansible**.

## Propósito del Proyecto
El objetivo es demostrar la capacidad de orquestar múltiples nodos de servidor, garantizando la **Idempotencia**, la consistencia de la configuración y la aplicación de políticas de seguridad (**Hardening**) de forma masiva y eficiente.

## Arquitectura del Laboratorio
* **Control Node:** Estación de gestión con Ansible Core.
* **Managed Nodes:** 03 servidores Redhat/AlmaLinux (Minimal Install).
* **Protocolo:** Comunicación cifrada vía SSH (ED25519).

## Stack Tecnológico
* **Orquestación:** Ansible.
* **Sistema Operativo:** AlmaLinux 10.
* **Seguridad:** Firewalld, OpenSSH Hardening, GRC (Governance, Risk, and Compliance).

---

## Descripción de Playbooks

### 1. Actualización y Preparación (`01_system_update.yml`)
Garantiza que todos los nodos operen con los últimos parches de seguridad y dependencias base instaladas.

### 2. Gestión de Identidad (`02_user_management.yml`)
Automatiza la creación de usuarios administrativos, gestión de privilegios `sudo` y despliegue de llaves públicas SSH, eliminando la dependencia de contraseñas inseguras.

### 3. Fortalecimiento de Infraestructura (`03_security_hardening.yml`)
Aplica capas de seguridad defensiva:
* Configuración estricta de **Firewalld**.
* Hardening de **OpenSSH** (Desactivación de Root Login y Password Auth).
* Implementación de **Banner Legal** de advertencia de acceso.

---

## Instrucciones de Configuración
Para utilizar este laboratorio, siga estos pasos:

1. **Renombrar archivos de ejemplo:**
   ```bash
   cp inventory.example.ini inventory.ini
   cp ansible.cfg.example ansible.cfg
   cp 01_system_update.yml.example 01_system_update.yml
   cp 02_user_management.yml.example 02_user_management.yml
   cp 03_security_hardening.yml.example 03_security_hardening.yml
