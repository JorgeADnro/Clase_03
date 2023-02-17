# Autenticación con Auth0

## Instrucciones
### Ingresar a la página Auth0
1. Ingresar a la página de [Auth0](https://auth0.com/)
2. Crear una cuenta [Sign Up](https://auth0.com/signup?place=header&type=button&text=sign%20up), en caso contrario omitir el paso
3. Iniciar sesión
4. Ingresar al [Dashboard](https://manage.auth0.com/dashboard)
5. Seleccionar opción Applications|Create Apllications
![image](https://user-images.githubusercontent.com/8560750/215930625-502680e0-a889-4e88-8eee-49b643f3a242.png)

6. Ingresar un nombre o un tipo de aplicación, al finalizar dar clic en **Create**
![image](https://user-images.githubusercontent.com/8560750/215930810-08fae125-3520-46a1-97fc-dbe4aa7ca362.png)

7. Seleccionar la tecnología Angular
![image](https://user-images.githubusercontent.com/8560750/215931012-8e6d3d7c-c38f-46ec-bf9c-54d5bd01c893.png)

8.Inspeccionar el tab **Settings**, los datos a tomar en cuenta es el `Domain` y `Client ID`
![image](https://user-images.githubusercontent.com/8560750/215931174-709ccab1-1c08-478e-99e4-97de22bc8645.png)

9. Seleccionar el tab `Quick Start` y descarga la aplicación de ejemplo.

![image](https://user-images.githubusercontent.com/8560750/215931777-62c54266-42d2-421d-8c7b-cd8d957c870b.png)

10. Descomprimir el archivo `angular-01-login`.
11. Abrir consola y ubicarse en carpeta recien descomprimida.
12. Cambiarse al directorio `sample` recien creado

## Configurar aplicación de ejemplo
Para una mayor referencia [Véase](https://github.com/auth0-samples/auth0-angular-samples)

1. Abrir Visual Studio Code en la carpeta sample.
![image](https://user-images.githubusercontent.com/8560750/215932467-f58472a6-bd5d-44b7-a361-e5955133d093.png)

2. Modificar archivo `auth_config.jsn`, la ventaja de descomprimirlo es que le agrega dichos datos.
~~~
{
  "domain": "dev-tz43a35eoik3buw2.us.auth0.com",
  "clientId": "BHTtRTn7cOCnT8eI4b95pKgV9WWPSDZm",
  "authorizationParams": {
    "audience": "YOUR_API_IDENTIFIER"
  },
  "apiUri": "http://localhost:3001",
  "appUri": "http://localhost:4200",
  "errorPath": "/error"
}
~~~

3. El identificador lo copiamos la opción APIs
![image](https://user-images.githubusercontent.com/8560750/215933107-b944c3c2-4169-45d6-b429-de6a9d41dda5.png)

~~~
{
  "domain": "dev-tz43a35eoik3buw2.us.auth0.com",
  "clientId": "BHTtRTn7cOCnT8eI4b95pKgV9WWPSDZm",
  "authorizationParams": {
    "audience": "https://dev-tz43a35eoik3buw2.us.auth0.com/api/v2/"
  },
  "apiUri": "http://localhost:3001",
  "appUri": "http://localhost:4200",
  "errorPath": "/error"
}
~~~

4. Asegurarse también de que la aplicación en Auth0 esté configurada para permitir http://localhost:4200 como Callback URL, Logout URLy Allowed Web Origin.
![image](https://user-images.githubusercontent.com/8560750/215933563-475aa443-4484-4106-ade9-2bb3ef5429b6.png)

5. Instalar Auth0 Angular SDK
~~~
npm install @auth0/auth0-angular
~~~

6. Abrir archivo `app.module.ts`
- importar el `AuthModule` del paquete `@auth0/auth0-angular`
- Agregar `AuthModule` a la aplicación llamando AuthModule.forRoot y agregar a la matriz `imports` de módulo de aplicación 

~~~
  imports: [
    BrowserModule,
    AppRoutingModule,
    HttpClientModule,
    NgbModule,
    HighlightModule,
    FontAwesomeModule,
    // Import the module into the application, with configuration
    AuthModule.forRoot({
      domain: 'dev-tz43a35eoik3buw2.us.auth0.com',
      clientId: 'BHTtRTn7cOCnT8eI4b95pKgV9WWPSDZm'
      authorizationParams: {
        redirect_uri: window.location.origin
      }
    }),
    }),
  ],
~~~

Verificar que el ID Cliente corresponde con los datos de configuración de la aplicación.

6. Ejecutar aplicación
~~~
ng serve -o
~~~

![image](https://user-images.githubusercontent.com/8560750/215934263-bb0e0973-d821-4cfb-a94b-9e6c0b7da25d.png)

7. Login
![image](https://user-images.githubusercontent.com/8560750/215936769-8cd97f53-f5d2-4211-a745-43a8adda6206.png)










