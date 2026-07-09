# Laboratorio 01 - AWS IAM (Identity and Access Management)

## Objetivo

Aprender a administrar el acceso a los recursos de AWS mediante la creación de usuarios, grupos y políticas de IAM, aplicando el principio de mínimo privilegio y habilitando mecanismos de autenticación segura.

---

## Servicios utilizados

- AWS IAM
- AWS Management Console

---

## Actividades realizadas

- Creación de un usuario IAM para administración.
- Creación del grupo **Administrators**.
- Asociación de la política administrada **AdministratorAccess** al grupo.
- Asignación del usuario al grupo.
- Configuración de una contraseña para acceso a la consola.
- Habilitación de autenticación multifactor (MFA).
- Inicio de sesión utilizando el usuario IAM en lugar del usuario raíz.

---

## Arquitectura

```text
Usuario Root
      │
      ▼
Administrators (Grupo IAM)
      │
      ▼
AdministratorAccess (Política AWS)
      │
      ▼
Usuario IAM
```

---

## Evidencias

| Evidencia | Descripción |
|-----------|-------------|
| 01-iam-dashboard.png | Consola principal de IAM |
| 02-iam-user.png | Usuario IAM creado |
| 03-group.png | Grupo Administrators |
| 04-policy.png | Política AdministratorAccess asignada |
| 05-mfa.png | MFA habilitado |
| 06-login-iam-user.png | Inicio de sesión con usuario IAM |

---

## Buenas prácticas aplicadas

- No utilizar el usuario Root para tareas diarias.
- Agrupar permisos mediante grupos IAM.
- Habilitar MFA para aumentar la seguridad.
- Aplicar el principio de menor privilegio.

---

## Lecciones aprendidas

- Diferencia entre usuario Root e IAM.
- Importancia del MFA.
- Uso de grupos para simplificar la administración de permisos.
- Las políticas administradas permiten asignar permisos de forma rápida.

---

## Próximos pasos

En el siguiente laboratorio se implementará una instancia Amazon EC2 y se utilizará el usuario IAM para administrarla.
