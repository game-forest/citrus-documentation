# ParticleEmitter

ParticleEmitter - контейнер для системы частиц

Свойства **ParticleEmitter**:

* Является [виджетом](../widget.md)
* **EmissionMethod** - способ генерации частиц, а именно:
    * **NumberPerSecond** - генерация N частиц в секунду (старый метод)
    * **ConstantNumber** - генерация N частиц за один вызов, которые никогда не исчезнут. ImmortalParticles для них всегда включен, хоть и скрыт из интерфейса.
    * **NumberPerBurst** - генерация N частиц каждый раз, когда вызвано определенное действие. Анимируется свойство Action, на данный момент доступен только Burst.
* **Shape** - форма контейнера для частиц (Custom активируется автоматически при использовании EmitterShapePoint)
* **EmissionType** - тип излучения частиц (от центра/к центру)
* **ParticlesLinkage** - указать, куда привязывать контейнер частиц (root-сцена/текущий контейнер/другое)
* **Number** - количество частиц, используемых в генерации различными методами
* **TimeShift** - временной сдвиг (в секундах)
* **Speed** - скорость движения частиц
* **AlongPathOrientation** - включить ориентирование партиклей вдоль трека (сплайна/кривой)
* **WindDirection** - направление ветра в градусах (0 - дует слева, 90 - дует сверху)
* **WindAmount** - сила ветра
* **GravityDirection** - направление гравитации (0 - тянет направо, 90 - тянет вниз)
* **GravityAmount** - сила гравитации
* **MagnetAmount** - сила влияния магнитов на эмиттер
* **Orientation** - угол поворота созданных частиц
* **Direction** - угол поворота эмиттера (контейнера) частиц
* **Lifetime** - время жизни частиц в секундах
* **Zoom** - зум для созданных частиц
* **AspectRatio** - соотношение сторон для созданных частиц
* **Velocity** - угловая скорость частиц
* **Spin** - задать частицам угол вращения (в градусах)
* **AngularVelocity** - угловая скорость контейнера частиц (в градусах)
* **RandomMotionRadius** - радиус рандомного движения частиц
* **RandomMotionSpeed** - скорость рандомного движения частиц
* **RandomMotionAspectRatio** - соотношение сторон зоны движения частиц
* **RandomMotionRotation** - вращение рандомного движения частиц
* **Action** - триггер для NumberPerBurst, на данный момент доступен только Burst