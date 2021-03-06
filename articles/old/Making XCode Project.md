1.) Открыть файл *.citproj проекта и прописать в нём информацию, необходимую для сбора ресурсов XCode-проекта.
	Блок информации	выглядит следующим образом (на примере проекта Game):

	XCodeProject: {
		DoSvnUpdate: false,
		DoSvnCommit: false,
		Resources: '*.dll *.exe *.png Game Data.iOS .monotouch-32 .monotouch-64',
		DataFolder: 'Game_XCode_Project_Data',
		Version: '6.55'
	}

	Следует обратить особое внимание на поля "Resources" и "DataFolder". В поле "Resources" указываются
	через пробел маски файлов и папок, которые на следующем шаге будут автоматически скопированы в папку
	проекта XCode. В примере, приведённом выше, маску "Game" нужно заменить на соответствующую названию
	проекта. Все остальные маски нужно оставить как есть, при необходимости можно добавить другие маски в
	целях копирования в XCode-проект других файлов.

	В поле "DataFolder" указывается каталог, в котором у нас будет создан XCode-проект. Этот каталог лучше
	создать в каталоге iOS-проекта игры.

2.) Запускаем Orange на Mac. Загружаем citproj-файл проекта в Citrus Project. Выбираем в Target platform
	режим iPhone/iPad. Внизу в выпадающем списке слева от кнопки "Go" выбираем пункт "Update XCode Project".
	Нажимаем кнопку "Go". Набираемся терпения и ждём. Убеждаемся по логу в консоли, что всё прошло нормально
	и все необходимые файлы успешно скопированы. В конце лога мы должны увидеть надпись "Elapsed Time ..."

3.) Открываем XCode. Заходим последовательно через меню в File --> New --> Project.
	Выбираем iOS -> Application -> Single View Application. В "Product Name" пишем название нашего проекта.
	Выбираем папку, куда будет сохранён наш XCode-проект. В качестве этой папки выбираем ранее созданную на
	первом шаге папку, находящуюся в папке iOS-проекта нашей игры. Нажимаем кнопку "Create".

	В дереве файлов созданного XCode-проекта удаляем всё лишнее, кроме файлов "Info.plist" и "*.app"
	(* - название проекта). Каталоги, в которых лежат эти ("Info.plist" и "*.app") файлы, соответственно
	тоже не удаляем.

4.) Теперь нам осталось добавить в наш XCode-проект файлы нашей игры, которые подготовил Orange на втором
	шаге. Но здесь есть один важный момент. Библиотеки *.dll для нашей игры положились в папки ".monotouch-32" и
	".monotouch-64". А для Мака папки, имя которых начинается с точки, считаются скрытыми и более того,
	оболочка XCode не разрешит в дерева проекта создавать папки с использованием символа точки в имени.
	Поэтому, нужно во-первых, сделать, чтобы Mac в Finder'е показывал скрытые файлы и папки. Для этого нужно
	выполнить следующие команды в консоли:

	defaults write com.apple.finder AppleShowAllFiles -bool YES
	killall Finder

	Перезапускаем Finder, заходим в каталог XCode-проекта и убеждаемся, что папки ".monotouch-32" и
	".monotouch-64" стали видны. Далее, убираем точку в имени с обеих папок.

	Теперь в дереве файлов проекта в XCode вверху на названии проекта делаем правый клик и выбираем
	"Add files to...". Открываем в появившемя окошке папку с проектом XCode, выбираем все файлы
	и папки "monotouch-32" и "monotouch-64" (без точек, т.к. мы их переименовали), скопированные
	Orange на втором шаге и добавляем их в проект.

	Теперь сохраняем проект, закрываем XCode, идём в папку проекта, ставим обратно точки вначале имён папок
	"monotouch-32" и "monotouch-64". А теперь эти точки нужно также поставить в файле проекта XCode. Поскольку
	оболочка XCode не позволяет использовать точки в именах папок, то делать это прийдётся вручную и с помощью
	хорошего текстового редактора (стандартный TextEdit не пойдёт, он нарушает кодировку; нужен, например,
	Sublime Text). Скачиваем и устанавливаем Sublime Text, открываем xcodeproj путём правого клика и выбора
	пункта "Show Package Contents". Открываем через Sublime Text файл "project.pbxproj", ищем при помощи поиска
	ссылки на папки "monotouch-32" и "monotouch-64", ставим там точки в начале их имени. Сохраняем файл, выходим.

	Снова открываем проект в XCode. Запускаем. Всё.
