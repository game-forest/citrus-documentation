# Frame

Frame (группа)  - используется как контейнер для других виджетов.

Свойства **Frame**:

* Является [виджетом](widget.md)
* **ClipChildren** - как поступать с контентом за пределами фрейма (обрезать/игнорировать)

Допустимые значения:
    - **None** doesn't clip children
    - **ScissorTest** clips by frame rectangle, doesn't support rotation but faster
    - **StensilTest** clips by frame rectangle, supports rotation but slower
    - **NoRender** skips children rendering.

* **RenderTarget** - рендерит фрейм в текстуру, согласно выбранному размеру. Затем эту текстуру можно использовать в полях *Texture*
