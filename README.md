# Instituto Tecnológico de Costa Rica

## Escuela de Computación

### IC8057 - Introducción al Desarrollo de Páginas Web

**Laboratorio 1 – Tecnologías Web Modernas**

**Estudiante**: Elder Leon Perez

**Carnet**: 2023166120

**Curso**: IC-8057 – Introducción al Desarrollo de Páginas Web

---

## 1. Frameworks de desarrollo web

### a. ¿Qué es un framework y qué problema resuelve?

Segun AWS se define como el conjunto de conceptos practicas o criterios entandarizados que se enfocan en resolver una problematica, por ejemplo evitar escribir codigo repetitivo ademas de implementar buenas practicas como sistemas MVC facilitando el orden del proyecto, de igual forma permite a los desarrolladores trabajar mas rapido debido a que el uso de dichas herramientas disminuyen grandes bloques de codigo en sentencias mas pequeñas.

**Ejemplo:** React native es un framework de proramacion de aplicaciones nativas multiplataforma basado en JavaScript y ReactJS, los cuales cuentan con "VirtualDom" en e cual se encuentra JSX en el que se definen documentos HTML y mediante JavaScript se tranforman en componentes en la vista.

### b. Arquitectura general y enfoque (MVC, SPA, SSR, etc.).

Segun React Native Docs se utiliza un sistema parecido al SPA que se basa en actualiazar la pagina dinamicamente sin nesecidad de recargar todas la pagina mediante puentes asincronicos, es posible implementarlo de forma adaptada a modelos MVC sin necesidad del SSR de forma interna implementa el uso de Bridge o JSI en la nueva arquitectura, la cual conecta el codigo con los componentes permitiendo el desarrollo de aplicaciones.

### c. Ejemplo práctico documentado (estructura de proyecto, fragmento de código comentado).

_Estructura general de un proyecto_

    mi-proyecto/
    ├── public/
    ├── src/
    │   ├── components/
    │   │   ├── ComponenteA/
    │   │   │   ├── ComponenteA.jsx
    │   │   │   ├── ComponenteA.css
    │   │   │   └── ComponenteA.test.js
    │   │   └── ComponenteB/
    │   │       ├── ComponenteB.jsx
    │   │       ├── ComponenteB.css
    │   │       └── ComponenteB.test.js
    │   ├── pages/
    │   │   ├── PaginaPrincipal/
    │   │   │   ├── PaginaPrincipal.jsx
    │   │   │   ├── PaginaPrincipal.css
    │   │   │   └── PaginaPrincipal.test.js
    │   │   └── PaginaContacto/
    │   │       ├── PaginaContacto.jsx
    │   │       ├── PaginaContacto.css
    │   │       └── PaginaContacto.test.js
    │   ├── styles/
    │   │   ├── global.css
    │   │   └── variables.css
    │   ├── assets/
    │   │   ├── images/
    │   │   │   └── logo.png
    │   │   └── fonts/
    │   │       └── fuente.woff2
    │   ├── hooks/
    │   │   └── useMiHook.js
    │   ├── App.jsx
    │   └── index.jsx
    ├── package.json
    ├── .gitignore
    └── README.md

_fragmento de código comentado_
// Importa react y componentes basicos
import React, { useState } from 'react';
import { View, Text, TextInput, TouchableOpacity, StyleSheet, Alert } from 'react-native';

// Pantalla de inicio de login
export default function LoginScreen() {

    // Estados para informacion basica de un login

        const [email, setEmail] = useState('');

        const [password, setPassword] = useState('');

    // Funcion que se ejecuta al presionar el boton, solo imprime exito o error podria redireccionar a pantalla Home.
        const handleLogin = () => {
            // Validación simple de ejemplo
            if (email === 'usuario@correo.com' && password === '123456') {
                Alert.alert('Éxito', '¡Bienvenido!');
            } else {
                Alert.alert('Error', 'Correo o contraseña incorrectos');
            }
        };
        //retorna la estructura basica de la vista
    return (
        // Contenedor principal que centra el contenido
            <View style={styles.container}>
            {/* Título principal */}
            <Text style={styles.title}>Iniciar Sesión</Text>

            {/* Input para correo electrónico */}
            <TextInput
                style={styles.input}
                placeholder="Correo electrónico"
                value={email}
                onChangeText={setEmail}
                keyboardType="email-address"

            />

            {/* Input para contraseña */}
            <TextInput
                style={styles.input}
                placeholder="Contraseña"
                value={password}
                onChangeText={setPassword}
                secureTextEntry
            />

            {/* Botón de login */}
            <TouchableOpacity style={styles.button} onPress={handleLogin}>
                <Text style={styles.buttonText}>Login</Text>
            </TouchableOpacity>
            </View>
        );
    }

### d. Comparación breve entre al menos dos frameworks (según lenguaje o enfoque).

| Criterio         | React Native                                              | Flutter                                         |
| ---------------- | --------------------------------------------------------- | ----------------------------------------------- |
| **Lenguaje**     | JavaScript / TypeScript                                   | Dart                                            |
| **Enfoque**      | Basado en **componentes**, reutiliza UI nativa            | Basado en **widgets**, renderiza su propia UI   |
| **Rendimiento**  | Bueno, depende del **Bridge/JSI**                         | Muy alto, compila a código nativo directamente  |
| **Arquitectura** | Basada en componentes + Bridge / JSI (nueva arquitectura) | Basada en widgets + motor de renderizado propio |

## 2. Control de versiones y trabajo colaborativo

### a. ¿Qué es el control de versiones y por qué es esencial?

Se define comom la practica de rastrear y gestionar los cambios en un proyecto de software, se implementea mediante software que ayudan a los esquipos de trabajo a gestionar los cambios en el codigo fuente a lo largo del ciclo de vida del software.
El sistema de control de versiones hace un seguimiento de todas modificaciones que se realizan en el codigo y en caso de comenterse un error permite a los desarrolladores ir hacia atras y recuperar la ultima version estable del programa sin perder la totalidad de la prodiccion.

### b. Conceptos clave: repositorio, commit, branch, merge, pull request.

_Repositorio:_ Es el conjunto de confirmaciones, ramas y etiquetas para indentificar las confirmaciones ademas de ser el lugar local o en nube donde se almacena el proyecto.<br>
_Commit:_ Es el registro de cambios que se hacen en el repositorio incluye informacion como quien modifico el proyecto, quien lo hace y cuando.<br>
_Branch:_ Es una linea independiente de desarrollo dentro de un repositorio, permite crear un entorno de ensayo separado donde se pueden hacer cambios sin afectar la rama principal.<br>
_Merge:_ Es la accion de unir los cambios de una rama en otra agregandolas al proyecto principal.<br>
_Pull request:_ Es la solicitud para revisar e integrar cambios de una rama en otra, permite que los desarrolladores revisen el codigo antes de integrarlo es muy comun en repositorios de codigo abierto.

### c. Flujos de trabajo comunes (Git Flow, trunk-based, feature branches).

_Git flow:_ Optimiza el flujo de trabajo mediante el uso de ramas aisladas para el desarrollo de funciones, la preparacion, publicacion y el mantenimiento.Su estricto modelo de ramificación también aporta una estructura muy necesaria para los proyectos más grandes.<br>
_trunk-based:_ Trabaja principalmente en una rama principal integra facilmente en la rama principal mediante commits frecuentes, requiere mucha disiplina y pruebas automaticas robustas para no romper la rama principal.<br>

- feature branches:\* Cada nueva funcionalidad se desarrolla en una rama independiente llamada feature branch una vez finalizada se hace un merge o pull request hacia la rama principal.

### d. Ejemplo de cómo usar Git en un proyecto (inicialización, commits, ramas).

_Inicializacion:_ git init "se utiliza para crear el repositorio"<br>

_Commits:_ git add => git commit -m "Mensaje descriptivo " " Se implementa para guardar los cambios realizados"<br>

_Ramas:_ git branch nombre => git checkout nombre "implementado para crear ramas y no poner en peligro el proyecto principal" <br>

### e. Herramientas recomendadas (GitHub, GitLab, Bitbucket).

| Herramienta   | Descripción resumida                                                                                 |
| ------------- | ---------------------------------------------------------------------------------------------------- |
| **GitHub**    | Plataforma basada en la nube para almacenar, compartir y colaborar en código.                        |
| **GitLab**    | Gestor de repositorios Git que permite colaboración en código; escrito en Ruby y Go, creado en 2011. |
| **Bitbucket** | Herramienta de alojamiento de código basada en Git, integrada con Jira y Trello.                     |

---

## 3. Autenticación y seguridad moderna

### a. Conceptos: autenticación, autorización, tokens, JWT, OAuth.

_Autenticacion:_ Segun Microsoft confirma que el usuario que inicia sesión es quien dice ser.<br>
_Autorizacion:_ Confirma que el usuario tiene los permisos adecuados para acceder a la informacion o pagina que busca ingresar.<br>
_Tokens:_ clave generada representa la indetificacion y permiso de un usuario para el inicio de sesion.<br>
_JWT:_ Formato estándar que se utiliza para transmitir información de forma segura entre dos partes (por ejemplo, entre un cliente y un servidor).<br>
_OAuth:_ Protocolo estándar de la industria para la autorizació se centra en la simplicidad del desarrollador cliente al tiempo que proporciona flujos de autorización específicos para aplicaciones web, aplicaciones de escritorio, teléfonos móviles y dispositivos de sala de estar.<br>

### b. Diagrama de flujo explicativo del proceso de autenticación con JWT.

    flowchart TD
        A[Inicio del proceso] --> B[Genera JWT firmado]
        B --> C[Envía JWT al endpoint de tokens]
        C --> D[Salesforce recibe el JWT]
        D --> E[Valida firma y parámetros]
        E --> F{¿JWT válido y aplicación autorizada?}
        F -- Sí --> G[Emite Access Token]
        G --> H[Accede a recursos protegidos]
        F -- No --> I[Solicitud rechazada]

### c. Buenas prácticas en seguridad web.

    1. Implementar politicas estrictas de seguridad de contenidos(CSP)
    2. Activar HTTP Strict Transport Security (HSTS)
    3. Auditorías de seguridad y pruebas de penetración periódicas
    4. Utilizar la Integridad de Subrecursos (SRI) para guiones externos

### d. Aplicaciones reales en plataformas modernas.

Existen diversas plataformas o servicios que implementan como Auth0 y Firebase Authentication que implementan tokens firmados ara la autenticacion.

## 4. Gestores de contenido desacoplados (Headless CMS)

### a. Definición de Headless CMS vs CMS tradicional.

    _Headless CMS:_ Es un repositotio en que el contenido se entrega a partir de API, desacoplando la capa de presentacion fronted del backend por esta razon se le llama sin cabeza ya que el fronted se acopla por separado.
    _CMS tradicional:_ En el sistema tradicional es un todo en uno ya que el fronted y backend estan acoplados dentro de la misma plataforma.

### b. Arquitectura basada en APIs.

Es un modelo donde la aplicaciones se construyen idependientemente y se cumunica a traves de APIs, en este enfoque el backend contiene la logica y el acceso a datos mediante (API REST o GraphQL) y la vista consume las APIs para mostrar la informacion.Este tipo de arquitectura permite a los desarrolladores desacoplar las interfaces facilitando aspectos como mantenimiento y reutilizacion de codigo.

### c. Ventajas, limitaciones y casos de uso comunes.

| Categoría                | Descripción                                                                                                                                                                                |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Ventajas**             | • La edición de contenido se independiza del diseño<br>• Mayor flexibilidad para elegir tecnologías de presentación<br>• Actualización rápida del contenido en múltiples canales           |
| **Desventajas**          | • Se debe construir un frontend de forma individual<br>• Algunos procesos no se pueden realizar sin manipulación de código<br>• Riesgos de seguridad si la API no se protege adecuadamente |
| **Casos de uso comunes** | • Uso de banners <br>• Sitios con diferentes interfaces segun el dispositivo<br>                                                                                                           |

### d. Ejemplo de cómo se conecta el frontend a un CMS headless.

Con react es posible hacer la solicitud con una peticion HTTP montando el componente y una peticion fectch que recibe la informacion en Json y luego se renderiza la inforamacion

---

## 5. Pasarelas de pago en aplicaciones web

### a. ¿Qué es una pasarela de pago? ¿Qué rol cumple en una aplicación moderna?

Se define como el proceso tecnologico que permite aceptar pagos con diferentes targetas bancarias actuando como puente entre el comercio y el cliente garantizando el pago exitoso.

### b. Requisitos comunes: cuenta de comercio, seguridad, integración técnica.

cuenta de comercio: Cuenta que permite aceptar transacciones con tarjetas de credito o debito.<br>
seguridad: Es importante cumplir con estadares como (PCI-DSS) ademas de incluir certificados como SSL/TLS<br>
integración técnica: Es el proceco que implica la conexion entre las tiendas con sistemas ERP ademas de gestion de inventario y el software de gestion de relacion con el cliente (CRM)<br>

### c. Ventajas y limitaciones de integrar pagos en línea.

| Categoría   | Descripción                                                                      |
| ----------- | -------------------------------------------------------------------------------- |
| ventajas    | •Facilidad de uso<br>•Reduccion de costos <br> • Simplificacion de transacciones |
| Desventajas | •Aumento de fraude y ciberdelincuencia <br>• Desafios de integracion             |

### d. Comparación entre al menos dos pasarelas (ej. Stripe, TiloPay, Bancos, etc.)

| Característica                  | Stripe                                 | PayPal                       | Tilopay                                        | Bancos                  |
| ------------------------------- | -------------------------------------- | ---------------------------- | ---------------------------------------------- | ----------------------- |
| Disponibilidad en Centroamérica | Limitada (solo algunos países)         | Ampliamente disponible       | Diseñado para la región                        | Parcialmente disponible |
| Soporte en español              | Limitado                               | Parcial                      | 100% en español y local                        | Sí                      |
| Integración con métodos locales | Baja                                   | Baja                         | Alta                                           | Sí                      |
| Transferencia bancaria          | Requiere cuenta en EE. UU. u otro país | Requiere banco intermediario | Depósito directo en banco local                | Sí                      |
| Checkout / experiencia usuario  | Requiere programación                  | Redirección fuera del sitio  | Visual adaptable sin código, links/QR/WhatsApp | Sí                      |

## 6. Automatización del despliegue y hosting moderno

### a. ¿Qué es CI/CD y por qué se usa en desarrollo web?

CI/CD significa Continuous Integration y Continuous Delivery implementados en el
desarrollo web se utilizan para automatizar todo el proceso de construcción, pruebas y publicación de una aplicación.

### b. Hosting estático vs dinámico.

| Aspecto       | Hosting Estático          | Hosting Dinámico                    |
| ------------- | ------------------------- | ----------------------------------- |
| Contenido     | Fijo / pre-generado       | Generado al momento                 |
| Velocidad     | Muy rápido                | Más lento (depende del servidor)    |
| Flexibilidad  | Limitada                  | Alta                                |
| Escalabilidad | Muy fácil                 | Requiere más recursos               |
| Ejemplos      | GitHub Pages, Netlify, S3 | Heroku, AWS EC2, servidores propios |

### c. Flujo de despliegue automatizado.

Es un proceso donde el codigo de un poyecto pasa de desarrollo a produccion de forma automatica implentando CI/CD principalmente se hace algun commit de algun cambio mendiante la integracion continua se ejecutan pruebas automaticas y compila para detectar errores antes de ir a produccion mendiante CD si las pruebas son exitosas prepara el paquete para despliegue se publica el cambio en el servidor y por ultimo se verifica que todo funcione correctamente.

### d. Documentar el proceso seguido para desplegar la parte 2 del laboratorio.

## 6.Bibliografia

About the New Architecture · React Native. (2025, 15 agosto). https://reactnative.dev/architecture/landing-page<br>
What is a Framework? - Framework in Programming and Engineering Explained - AWS. (s. f.). Amazon Web Services, Inc. https://aws.amazon.com/what-is/framework/<br>
Learn flutter. (s. f.). Flutter. https://docs.flutter.dev/get-started/learn-flutter <br>
DataScientest. (2023b, octubre 30). GitLab: Saber todo sobre el repositorio Git para DevOps. https://datascientest.com/es/gitlab-todo-lo-que-hay-que-saber#:~:text=%C2%BFQu%C3%A9%20es%20GitLab%3F,plataforma%20completamente%20de%20c%C3%B3digo%20abierto
<br>Atlassian. (s. f.). Resumen de Bitbucket | Bitbucket. Bitbucket. https://bitbucket.org/product/es/guides/getting-started/overview#a-brief-overview-of-bitbucket
<br>¿Qué es la autenticación? Definición y métodos | Seguridad de Microsoft. (s. f.). https://www.microsoft.com/es-es/security/business/security-101/what-is-authentication#:~:text=La%20autenticaci%C3%B3n%20confirma%20que%20el,a%20la%20informaci%C3%B3n%20que%20busca.
<br>OAuth 2.0 — OAuth. (s. f.). https://oauth.net/2/
<br>Rudra, A. (2023, 29 noviembre ). ¿Qué es la seguridad web? Buenas prácticas de seguridad de sitios web. PowerDMARC. https://powerdmarc.com/es/web-security-website-security-explained/
<br>Khan, F. (2024, 27 febrero). Mastering API Architecture: A Comprehensive Guide | Astera. Astera. https://www.astera.com/es/type/blog/api-architecture/

Lahuerta, C. (2025, 5 marzo). CMS: características, ventajas y desventajas. Idital. https://idital.com/cms-caracteristicas-ventajas-desventajas/
<br>Qué es una pasarela de pago? | Checkout.com. (s. f.). https://www.checkout.com/es-es/blog/que-es-pasarela-pago
<br>Xicara, E. (2025, 20 junio). Stripe o PayPal: Desventajas de usarlos en la región. Qué considerar antes de elegir una pasarela de pagos. Tilopay Connect. https://connect.tilopay.com/es-cr/stripe-o-paypal/
<br>Atlassian. (s. f.-a). Continuous integration vs. delivery vs. deployment | Atlassian. https://www.atlassian.com/continuous-delivery/principles/continuous-integration-vs-delivery-vs-deployment
