# 🚀 Desafío 5 - **Configuración de AWS con EC2, VPC y RDS**

Este documento detalla los pasos para crear un entorno de desarrollo en AWS con EC2, VPC, y RDS, incluyendo configuración de seguridad, subredes y conectividad.

**📌 Requisitos**
Antes de comenzar, asegúrate de tener acceso a una cuenta de AWS con permisos suficientes para administrar recursos como ***IAM, VPC, EC2 y RDS***.

## 🔐 **1. Crear un Usuario IAM con Permisos de Administrador**

1. Acceder a la consola de AWS IAM.
2. Ir a Personas y seleccionar Crear Persona.
3. Marcar la opción Proporcionar acceso de usuario a la consola de administración de AWS.
4. Elegir contraseña generada automáticamente.
5. En establecer permisos, seleccionar Adjuntar políticas directamente.
6. Elegir la política AdministratorAccess.
7. Revisar los detalles y confirmar la creación.
8. Guardar las credenciales en un lugar seguro.

## 🌐 2. Crear una VPC
1. Acceder a la consola de AWS VPC.
2. Seleccionar VPC y más e ingresar los datos de la VPC:
  - IPv4 CIDR block: 10.0.0.0/16
  - IPv6 CIDR block: No IPv6
  - Nombre de la VPC: tutorial-vpc
  - Subred pública IPv4 CIDR: 10.0.0.0/24
Hacer clic en Crear VPC y validar los componentes creados.







