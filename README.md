# GitHubActions для сборки проектов под Windows через cmake

 Сборка tdlib для Windows через GitHub Actions
 
##  Workflow для сборки TDLib (Telegram Database Library) под Windows с Java-биндингами

GitHub Actions для автоматической сборки [tdlib](https://github.com/tdlib/td) — официальной библиотеки Telegram — под Windows в варианте для Java (через JNI).
 
## Как это работает
 
При каждом `git push` в ветку `main` GitHub автоматически запускает виртуальную машину Windows и выполняет следующие шаги:
 
1. Клонирует исходный код tdlib с официального репозитория
2. Устанавливает Java JDK 17 (Eclipse Temurin)
3. Устанавливает вспомогательные инструменты: `gperf`, `php`
4. Устанавливает C++ зависимости через vcpkg: `OpenSSL`, `zlib`
5. Конфигурирует сборку через CMake с флагом `-DTD_ENABLE_JNI=ON`
6. Компилирует библиотеку
7. Сохраняет результат как артефакт (`.dll` файлы)
## Результат сборки
 
После успешного выполнения workflow в разделе **Actions → Artifacts** доступен архив `tdlib-windows-java` с готовыми файлами библиотеки, включая `tdjni.dll`.
 
## Инструменты
 
| Инструмент | Назначение |
|---|---|
| GitHub Actions | CI/CD платформа для автоматической сборки |
| CMake | Система сборки C++ проектов |
| vcpkg | Менеджер C++ зависимостей |
| Java JDK 17 | Среда выполнения для JNI-варианта библиотеки |
| Chocolatey | Менеджер пакетов Windows |
