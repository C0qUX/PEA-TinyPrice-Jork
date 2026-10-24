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
3. Ejecuta la configuracion `app`. La configuracion incluida consulta la Edge Function alojada de TinyPrice.

La URL publica del proyecto esta configurada en `gradle.properties`:

```properties
edgeRuntimeBaseUrl=https://lqritfdfipwyqspssari.supabase.co/functions/v1
useRemoteDeals=true
```

Para ejecutar la app temporalmente con los datos locales de demostracion:

```bash
./gradlew :app:assembleDebug -PuseRemoteDeals=false
```

## Verificacion

```bash
./gradlew :app:testDebugUnitTest :app:assembleDebug :app:lintDebug :app:connectedDebugAndroidTest
```

La variable `TINYFISH_API_KEY` debe configurarse exclusivamente como secreto de Supabase. Nunca debe añadirse a Kotlin, Gradle, GitHub ni capturas.

La funcion publicada responde en:

```text
https://lqritfdfipwyqspssari.supabase.co/functions/v1/search-products
```

## Fuente

- Codelab: https://epanchanaf.github.io/tinyprice-codelab/
