# 🇪🇸 Android Template (Kotlin + Jetpack Compose)

🚀 **Repositorio:** `https://github.com/MarioMDev/android-template`

Plantilla opinada para crear apps **nativas Android** modernas usando:

* 🧱 **Kotlin 2.2.x**
* 🖌️ **Jetpack Compose (Material 3, Navigation)**
* 🧬 **Hilt (DI)**
* 📦 **Modularización (core / feature / sample)**
* 🌐 **Retrofit 3 + Chucker (debug)**
* 💾 **Room 2.8.x + Flow**
* 🧪 **Tests básicos + GitHub Actions**

Pensada para que **no vuelvas a empezar un proyecto desde cero** y para que puedas añadir/quitar módulos según el caso.

---

## 🗂️ Estructura del proyecto

```text
android-template/
├─ app/                     ← entrypoint, NavHost, theme app
├─ core/
│  ├─ common/               ← Result, error mapper, dispatchers
│  ├─ designsystem/         ← colores, tipografías, componentes base
│  ├─ domain/               ← modelos y casos de uso
│  └─ data/                 ← contratos de repositorio + DI
├─ sample/
│  ├─ remote/               ← Retrofit 3 + Chucker + API pública
│  └─ local/                ← Room + DataStore + Flow
└─ feature/
   ├─ home/                 ← ejemplo MVVM
   └─ dashboard/            ← ejemplo MVI (state + event + effect)
```

---

## 🏁 Cómo iniciar un proyecto nuevo desde este template

1. **Clona el repo** ⤵️

   ```bash
   git clone https://github.com/MarioMDev/android-template.git mi-nueva-app
   cd mi-nueva-app
   ```

2. **Renombra el paquete / appId** (opcional pero recomendable) 🏷️

    * Busca `com.mario.template`
    * Cambia por `com.tuempresa.tuapp`

3. **Decide el perfil** 🔧

    * ✅ **Rápido** → borra `sample/` si no quieres ejemplos

      ```bash
      rm -rf sample
      ```
    * ✅ **Completo** → déjalo todo tal cual

4. **Lanza el proyecto** ▶️

   ```bash
   ./gradlew :app:assembleDebug
   ```

   o desde Android Studio: **Run > app**

5. **Crea tu primera feature** 🧩

    * Copia `feature/home` → renómbrala
    * Regístrala en el `NavHost` de `app`

6. **Sube a tu repo** ☁️

   ```bash
   git remote set-url origin <tu-repo>
   git push -u origin main
   ```

---

## 🧭 Navegación

El `app` ya trae un `NavHost` así:

```kotlin
NavHost(
    navController = navController,
    startDestination = "home",
) {
    homeNavGraph(navController)
    dashboardNavGraph(navController)
}
```

Para añadir una pantalla nueva 👉 creas tu `feature:<nombre>` y añades su `...NavGraph(...)` aquí.

---

## 🧠 Arquitectura propuesta

* **Capa UI (Compose)** → `feature/*`
* **Capa dominio** → `core/domain` (use cases, models)
* **Capa datos** → `core/data` + `sample/*`
* **Inyección** → Hilt en `app` y módulos en `core/*`

Puedes usar **MVVM** (home) o **MVI** (dashboard) según la pantalla.

---

## 🧪 CI / CD

El repo incluye un workflow de GitHub Actions:

```text
.github/workflows/android-ci.yml
```

Ejecuta en cada push / PR:

* `./gradlew :app:assembleDebug`
* `./gradlew :app:testDebugUnitTest`

Así sabes si el template sigue compilando ✅

---

## 🔁 Actualizar versiones (muy importante en 2025)

Todas las versiones viven en **`gradle/libs.versions.toml`**.
Cuando Google saque:

* nuevo **Compose BOM** (ej. `2025.11.00`)
* nuevo **AGP** (ej. `8.14.0`)
* nuevo **Kotlin** (ej. `2.3.x`)

👉 solo actualizas ese archivo.

---

## ✅ Qué incluye

* ✅ Compose + Material 3 + Tooling
* ✅ Hilt + hilt-navigation-compose
* ✅ Navigation Compose
* ✅ Retrofit 3 + OkHttp + Chucker (debug)
* ✅ Room + DataStore
* ✅ Ejemplo MVVM
* ✅ Ejemplo MVI
* ✅ Modularización
* ✅ GitHub Actions

## ❌ Qué NO incluye (a propósito)

* ❌ Firebase
* ❌ Navigation legacy
* ❌ Multimódulo exagerado
* ❌ Cosas muy de un producto concreto

---

## 📁 Convención de módulos

* **`core:*`** → compartido, sin UI
* **`feature:*`** → UI + lógica de pantalla
* **`sample:*`** → ejemplos que puedes borrar sin romper el resto

---

## 🐛 ¿Problemas comunes?

* Si te falla Hilt → revisa que **todos** los módulos tengan KSP + el plugin aplicado.
* Si no te reconoce una ruta de navegación → que el `NavHost` del `app` tenga incluida tu feature.
* Si fail en CI → ejecuta local:

  ```bash
  ./gradlew clean :app:assembleDebug :app:testDebugUnitTest
  ```

---

---

# 🇬🇧 Android Template (Kotlin + Jetpack Compose)

🚀 **Repo:** `https://github.com/MarioMDev/android-template`

Opinionated template to create **modern native Android apps** using:

* 🧱 **Kotlin 2.2.x**
* 🖌️ **Jetpack Compose (Material 3, Navigation)**
* 🧬 **Hilt (DI)**
* 📦 **Modularization (core / feature / sample)**
* 🌐 **Retrofit 3 + Chucker (debug)**
* 💾 **Room 2.8.x + Flow**
* 🧪 **Basic tests + GitHub Actions**

Goal: **never start from scratch again**.

---

## 🗂️ Project structure

```text
android-template/
├─ app/                     ← entrypoint, NavHost, app theme
├─ core/
│  ├─ common/               ← Result, error mapper, dispatchers
│  ├─ designsystem/         ← colors, typography, base components
│  ├─ domain/               ← models and use cases
│  └─ data/                 ← repository contracts + DI
├─ sample/
│  ├─ remote/               ← Retrofit 3 + Chucker + public API
│  └─ local/                ← Room + DataStore + Flow
└─ feature/
   ├─ home/                 ← MVVM sample
   └─ dashboard/            ← MVI sample (state + event + effect)
```

---

## 🏁 How to start a new project from this template

1. **Clone the repo** ⤵️

   ```bash
   git clone https://github.com/MarioMDev/android-template.git my-new-app
   cd my-new-app
   ```

2. **Rename package / appId** (optional but recommended) 🏷️

    * find `com.mario.template`
    * replace with `com.yourcompany.yourapp`

3. **Choose your profile** 🔧

    * ✅ **Fast** → delete `sample/` if you don’t need examples

      ```bash
      rm -rf sample
      ```
    * ✅ **Full** → keep everything

4. **Run the project** ▶️

   ```bash
   ./gradlew :app:assembleDebug
   ```

   or from Android Studio: **Run > app**

5. **Create your first feature** 🧩

    * copy `feature/home` → rename
    * register it in `AppNavHost`

6. **Push to your own repo** ☁️

   ```bash
   git remote set-url origin <your-repo>
   git push -u origin main
   ```

---

## 🧭 Navigation

`app` already ships with a `NavHost`:

```kotlin
NavHost(
    navController = navController,
    startDestination = "home",
) {
    homeNavGraph(navController)
    dashboardNavGraph(navController)
}
```

To add a new screen 👉 create your `feature:<name>` and add its `...NavGraph(...)` there.

---

## 🧠 Recommended architecture

* **UI layer (Compose)** → `feature/*`
* **Domain layer** → `core/domain`
* **Data layer** → `core/data` + `sample/*`
* **DI** → Hilt in `app` + modules in `core/*`

You can use **MVVM** (home) or **MVI** (dashboard).

---

## 🧪 CI / CD

GitHub Actions workflow:

```text
.github/workflows/android-ci.yml
```

Runs on every push / PR:

* `./gradlew :app:assembleDebug`
* `./gradlew :app:testDebugUnitTest`

So you always know the template still builds ✅

---

## 🔁 Updating versions (critical in 2025)

All versions are in **`gradle/libs.versions.toml`**.
When Google releases:

* new **Compose BOM** (e.g. `2025.11.00`)
* new **AGP** (e.g. `8.14.0`)
* new **Kotlin** (e.g. `2.3.x`)

👉 just update that file.

---

## ✅ Includes

* ✅ Compose + Material 3 + Tooling
* ✅ Hilt + hilt-navigation-compose
* ✅ Navigation Compose
* ✅ Retrofit 3 + OkHttp + Chucker (debug)
* ✅ Room + DataStore
* ✅ MVVM sample
* ✅ MVI sample
* ✅ Modularization
* ✅ GitHub Actions

## ❌ Not included (by design)

* ❌ Firebase
* ❌ Legacy navigation
* ❌ Over-modularized setup
* ❌ Product-specific stuff

---

## 🐛 Common issues

* Hilt errors → check **all modules** apply KSP + Hilt plugin
* Navigation errors → check your feature is registered in `AppNavHost`
* CI fails → run locally:

  ```bash
  ./gradlew clean :app:assembleDebug :app:testDebugUnitTest
  ```