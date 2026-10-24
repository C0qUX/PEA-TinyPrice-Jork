# TinyPrice

Aplicacion Android desarrollada con Kotlin y Jetpack Compose a partir del codelab TinyPrice. La app permite buscar ofertas, revisar resultados y abrir la fuente original. La clave privada de TinyFish no se almacena en el APK: una Edge Function de Supabase actua como intermediaria.

## Funcionalidades

- Interfaz Compose con inicio, carga, resultados, error y detalle.
- Estado unidireccional con ViewModel y StateFlow.
- Repositorio local para demostracion y repositorio remoto con Retrofit.
- Edge Function `search-products` escrita en TypeScript.
- Pruebas unitarias del ViewModel y prueba instrumentada de Compose.
- Tema claro y oscuro.

## Ejecucion local

1. Abre el proyecto en Android Studio.
2. Sincroniza Gradle y selecciona un emulador o dispositivo con API 23 o superior.
3. Ejecuta la configuracion `app`. Por defecto se utilizan datos de demostracion.

Para usar la funcion alojada, configura estas propiedades fuera del repositorio, por ejemplo en `~/.gradle/gradle.properties`:

```properties
edgeRuntimeBaseUrl=https://YOUR_PROJECT_REF.supabase.co/functions/v1
useRemoteDeals=true
```

## Verificacion

```bash
./gradlew :app:testDebugUnitTest :app:assembleDebug :app:lintDebug
```

La variable `TINYFISH_API_KEY` debe configurarse exclusivamente como secreto de Supabase. Nunca debe añadirse a Kotlin, Gradle, GitHub ni capturas.

## Fuente

- Codelab: https://epanchanaf.github.io/tinyprice-codelab/
