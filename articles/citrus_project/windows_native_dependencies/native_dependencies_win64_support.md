# Native dependencies win64_support

В этом документе описаны нативные зависимости под виндовс и мас, которые были затронуты в эпике `win64_support`.

## Оглавление

- [x] [Lemon](#Lemon)
- [x] [ShaderCompiler](#ShaderCompiler)
- [x] [ShaderCompilerBinding.Win](#ShaderCompilerBinding.Win)
- [x] [OpenAL](#OpenAL)
- [x] [OpenTK](#OpenTK)
- [x] [Newtonsoft.Json](#Newtonsoft.Json)
- [x] [FbxSdk](#FbxSdk)
- [x] [FreeType](#FreeType)
- [x] [HarfBuzz](#HarfBuzz)

## Lemon

Источник: исходный код в [Citrus\Lemon](https://gitlab.game-forest.com:8888/Common/Citrus/-/tree/master/Lemon) 

Включает в себя 

- Theora https://www.theora.org/
- Vorbis and Tremor https://xiph.org/vorbis/
- yuv2rgb http://wss.co.uk/pinknoise/yuv2rgb/

Используется при взаимодействии с `.ogg` `.ogv` `.oga` `.ogx` `.spx` `.opus` `.ogm` файлами.

Список изменений: 

- Стандартная конфигурация `Lemon.vcxproj` теперь нацелена на `x64`
- Для перехода на `x64` отключены оптимизации, связанные с ассемблерными вставками
- LemonNative.dll пересобран под `x64`

## ShaderCompiler

Источник: исходный код в [Citrus\3rdParty](https://gitlab.game-forest.com:8888/Common/Citrus/-/tree/master/3rdParty)

Включает в себя: 

- glslang https://github.com/KhronosGroup/glslang
- SPIRV-Tools https://github.com/KhronosGroup/SPIRV-Tools
- spirv-headers https://github.com/KhronosGroup/SPIRV-Headers.git
- SPIRV-Cross https://github.com/KhronosGroup/SPIRV-Cross

Автор: *Костя Егоров* [kegorov](kostonke@mail.ru)

Список изменений: 

- ShaderCompiler.dll пересобран под `x64`

## ShaderCompilerBinding.Win

Источник: исходный код в [Citrus\3rdParty](https://gitlab.game-forest.com:8888/Common/Citrus/-/tree/master/3rdParty) 

Автор: *Костя Егоров* [kegorov](kostonke@mail.ru) 

Используется в процессе компиляции шейдеров. 
*(Компиляция шейдерев происходит при первом использовании материала (*`IMaterial`*))*

Список изменений: 

- Стандартная конфигурация `ShaderCompilerBinding.Win.csproj` теперь нацелена на `x64`
- ShaderCompilerBinding.Win.dll пересобран под `x64`

## OpenAL

Источник: **nuget** (утанавливается как зависимость [OpenTK](#OpenTK)) 

Используется аудиосистемой движка.

Список изменений: 

- OpenAL теперь устанавливается из **nuget**-а
- Версия изменена и зависит от OpenTK

## OpenTK

Версия: 3.1.0

Источник: **nuget** [OpenTK.GLControl](https://www.nuget.org/packages/OpenTK.GLControl/) 

По крайней мере используется в процессе рендеринга в Empty Project-е, код из OpenTK используется аудиосистемой движка. 
*(Типы данных из OpenTK используются, даже если ОpenGL не используется в качесте бэкенда. Возможно, что-то подскажет Костя Егоров* [kegorov](kostonke@mail.ru)*)*

Список изменений: 

- OpenTK теперь устанавливается из **nuget**-а
- Версия обновлена с 1.1.2 до 3.1.0
- Удалены библиотеки в `3rdParty/OpenTK/`
- Добавлены библиотеки в `3rdParty/OpenTK/Dependencies_x64`.
  (замена аналогичных библиотек в `3rdParty/OpenTK/Dependencies_x86/`)
  - d3dcompiler_47.dll
  - libEGL.dll
  - libGLESv2.dll

Примечания:

Библиотеки в `3rdParty/OpenTK/Dependencies_x64` необходимы для запуска OpenGL ES 2.0 на виндовс.
Они получены путём сборки [google/angle](https://github.com/google/angle) со следующими параметрами (OpenGL ES 2.0 эмулируется через DirectX 9):

```c
is_debug = false
angle_enable_d3d9 = true
angle_enable_d3d11 = false
angle_enable_gl = true
angle_enable_gl_desktop = false
angle_enable_metal = false
angle_enable_vulkan = false
angle_build_all = false
enable_stripping = true
build_angle_perftests = false
angle_enable_null = false
```

## Newtonsoft.Json

Версия: 12.0.3

Источник: **nuget** [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/) 

Отрабатывает отрабатывает при чтении файлов сцены, при десериализации объектов.

Список изменений: 

- Newtonsoft.Json теперь устанавливается из **nuget**-а
- Версия обновлена с 6.0.0.0 до 12.0.3

## FbxSdk

Источник: https://gitlab.game-forest.com:8888/rshutov/FbxSdk 

Отрабатывает отрабатывает при импорте 3d моделей. 

Список изменений: 

- Добавлена конфигурация для `x64`
- FbxSdk.dll пересобран под `x64`

## MFDecoder

Источник: исходный код в [Citrus\3rdParty](https://gitlab.game-forest.com:8888/Common/Citrus/-/tree/master/3rdParty) 

Написан на базе примеров в msdn: https://docs.microsoft.com/en-us/windows/win32/medfound/processing-media-data-with-the-source-reader

Используется в `VideoPlayer`.

Список изменений: 

- Добавлена конфигурация для `x64`
- MFDecoder.dll пересобран под `x64`

## FreeType

Версия: 2.10.4

Источник: наш форк https://gitlab.game-forest.com:8888/Common/3rdparty/freetype

Исходный репозиторий: https://gitlab.freedesktop.org/freetype/freetype 

Отрабатывает во время запуска движка. 

Отвечает за растеризацию глифов.

Список изменений: 

- Версия для виндовс обновлена с 2.10.1 до 2.10.4
- Версия для виндовс собрана как зависимость [HarfBuzz](#HarfBuzz)
- Добален патч, который позволяет использовать FreeType через SharpFont в приложении с архитектурой `x64` на виндовс.
  *(Этот патч не оказывает влияния на остальные платформы. Патч описан в файле* `building_FreeType.md`*.)* 
- libfreetype-6.dll пересобран под `x64`

## HarfBuzz

Версия: 2.8.1

Источник: наш форк https://gitlab.game-forest.com:8888/Common/3rdparty/harfbuzz

Исходный репозиторий: https://github.com/harfbuzz/harfbuzz

Отрабатывает во время генерации шрифтов.

Отвечает за межсимвольные интервалы.

Список изменений: 

- Версия для виндовс обновлена с 2.5.3 до 2.8.1
- Обновлена версия FreeType.
  *(Изначально при сборке HarfBuzz-а используется некоторый форк [FreeType](#FreeType)-а, но там старая версия FreeType-а.* *Оригиналый FreeType с версии 2.10.3 поддерживает систему сборки (Meson), которая используется в этом процессе.* *Теперь используется наш форк оригинального репозитория FreeType-а.)*
- В версии для виндовс отключена поддержка [cairo](https://cgit.freedesktop.org/cairo) и [fontconfig](https://www.freedesktop.org/wiki/Software/fontconfig/)
  *(cairo и fontconfig используются для тестирования HarfBuzz, но мы эти тесты не используем.)*
- В нашем GitLab созданы форки для зависимостей HarfBuzz-а.
  *(Эти форки будут использоваться для сборки HarfBuzz-а.)*
  - [HarfBuzz](https://gitlab.game-forest.com:8888/Common/3rdparty/harfbuzz) (ветка для нужд движка: 2.8.1_citrus, ссылки на зависимости заменены на наши форки)
  - [FreeType](https://gitlab.game-forest.com:8888/Common/3rdparty/freetype) (ветка для нужд движка: 2.10.4_citrus, ссылки на зависимости заменены на наши форки)
  - [Zlib](https://gitlab.game-forest.com:8888/Common/3rdparty/zlib) (ветка для нужд движка: 1.2.11_citrus, ссылки на зависимости заменены на наши форки)
  - [Glib](https://gitlab.game-forest.com:8888/Common/3rdparty/glib) (ветка для нужд движка: 2.58.1_citrus)
  - [Libpng](https://gitlab.game-forest.com:8888/Common/3rdparty/libpng) (ветка для нужд движка: master)
  - [Libffi](https://gitlab.game-forest.com:8888/Common/3rdparty/libffi) (ветка для нужд движка: citrus)
  - [ProxyLibintl](https://gitlab.game-forest.com:8888/Common/3rdparty/proxylibintl) (ветка для нужд движка: citrus)

Примечания:

Последовательность действий для сборки HarfBuzz-а подробно описана в файле `building_HarfBuzz.md`.
