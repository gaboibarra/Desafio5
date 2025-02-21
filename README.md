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

## 📡 3. Configurar Subredes
1. Ir al menú Subredes en la consola de VPC.
2. En ID de la VPC, seleccionar la VPC creada previamente.
3. Crear dos subredes:
  - Subred Pública (10.0.0.0/24)
  - Subred Privada (10.0.2.0/24)
4. Validar la creación de ambas subredes.

## 🔒 4. Configurar el Security Group
1. En VPC → Grupos de Seguridad, seleccionar el Security Group asociado a la VPC.
2. Ir a Reglas de entrada → Editar reglas.
3. Agregar las siguientes reglas:
  - MYSQL/Aurora - TCP 3306 - Origen: 0.0.0.0/0 (o IP específica para mayor seguridad).
  - SSH - TCP 22 - Origen: 0.0.0.0/0 (solo si accedes vía SSH).
4. Guardar los cambios.

## 📡 5. Configurar las Tablas de Enrutamiento
1. En VPC → Tablas de Enrutamiento, seleccionar la tabla de enrutamiento de la VPC.
2. Editar las rutas y agregar:
  - 0.0.0.0/0 → Internet Gateway (para permitir tráfico de internet en la subred pública).
3. Asignar la misma tabla de enrutamiento a ambas subredes.

## 🛢️ 6. Crear la Instancia de Base de Datos (RDS)
1. Acceder a AWS RDS.
2. Seleccionar Crear Base de Datos → Creación estándar.
3. Elegir:
  - Motor: MariaDB
  - Capa gratuita (para evitar costos).
  - Nombre del usuario administrador y contraseña segura.
4. En Configuración de conectividad:
  - VPC: tutorial-vpc
  - Grupo de subredes: tutorial-db-subnet-group
  - Acceso público: Sí
5. Validar la creación de la BD y guardar el endpoint.

