# Estrategia de Despliegue: Blue/Green Deployment

## 1. Introducción
Para el proyecto **Sistema de Inventario**, se ha seleccionado la estrategia de despliegue **Blue/Green Deployment**. Esta estrategia permite minimizar el tiempo de inactividad (zero-downtime) y reducir los riesgos al lanzar nuevas versiones del sistema.

## 2. Descripción de Entornos
- **Entorno Blue (Producción Activa):** Es la versión que actualmente está en línea recibiendo el tráfico real de los usuarios.
- **Entorno Green (Staging / Pre-producción):** Es el entorno idéntico a producción donde se despliega la nueva versión para realizar pruebas finales.

## 3. Flujo de Trabajo
1. Los cambios validados en la rama `develop` se despliegan en el entorno **Green**.
2. Se realizan pruebas funcionales e integrales sin afectar a los usuarios en vivo.
3. Una vez aprobada la versión, el enrutador/balanceador de carga redirige el tráfico del entorno **Blue** al entorno **Green**.
4. El entorno **Green** pasa a ser el nuevo **Blue**. En caso de encontrar un fallo crítico, se puede realizar un **rollback** inmediato volviendo a dirigir el tráfico al entorno anterior.
