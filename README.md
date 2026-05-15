# InnovaTech - Sistema de Gestión de Despachos 🚀

InnovaTech es una plataforma integral diseñada para la gestión de ventas y logística de despachos, construida sobre una arquitectura de **microservicios** escalable y desplegada automáticamente mediante **CI/CD**.

## 🌐 Despliegue en Vivo
El proyecto se encuentra actualmente desplegado y operativo en la siguiente dirección:
👉 **[http://18.234.35.92](http://18.234.35.92)**

---

## 🛠️ Tecnologías Utilizadas

### Frontend
* **React.js**: Interfaz de usuario moderna y reactiva.
* **Tailwind CSS**: Estilizado eficiente y responsivo.

### Backend (Microservicios)
* **Spring Boot (Java)**: Potencia los servicios de Ventas y Despachos.
* **Maven**: Gestión de dependencias y construcción.

### Infraestructura y DevOps
* **Docker & Docker Compose**: Containerización de todos los servicios.
* **AWS (EC2)**: Hosting en la nube mediante instancias Amazon Linux.
* **GitHub Actions**: Pipeline de CI/CD automatizado para construcción y despliegue.
* **MySQL**: Base de datos relacional para la persistencia de datos.

---

## 🏗️ Arquitectura del Proyecto

El sistema se divide en los siguientes servicios:
1. **Frontend**: Dashboard de administración de despachos.
2. **Backend-Ventas**: Microservicio encargado de la lógica de órdenes de compra.
3. **Backend-Despachos**: Microservicio encargado del seguimiento y logística.
4. **Database**: Instancia de MySQL 8.0 compartida para los servicios.



---

## 🚀 Pipeline de CI/CD

Este repositorio cuenta con un flujo de trabajo automatizado:
1. **Build**: Al hacer push a la rama `deploy`, GitHub Actions construye las imágenes Docker.
2. **Push**: Las imágenes se suben automáticamente a **Docker Hub**.
3. **Deploy**: GitHub Actions se conecta por SSH a la instancia **AWS EC2**, descarga las nuevas imágenes y reinicia los contenedores.

---

## 📦 Ejecución Local

Para levantar el proyecto en tu máquina local, solo necesitas tener instalado Docker y seguir estos pasos:

1. Clonar el repositorio:
   ```bash
   git clone [https://github.com/bastian-alvarez/innovatech-ep2.git](https://github.com/bastian-alvarez/innovatech-ep2.git)
   cd innovatech-ep2
