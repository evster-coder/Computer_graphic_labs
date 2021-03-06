Укажите ваши файлы моделей <b>(!!!)</b>

Используются glfw, GLAD. Устанавливаются в соответствии с инструкцией по ссылке: https://ravesli.com/urok-2-podgotovka-k-pervomu-proektu-opengl-nastrojka-glfw-cmake-i-glad/ <br>
Инструкция с сайта:
<ul>
  <li>
1. Скачать glfw: https://www.glfw.org/download.html
  </li>
  <li>
2. Вы можете создать новую папку, которая будет содержать все заголовочные файлы и файлы из сторонних библиотек, на которую вы впоследствии сможете ссылаться из своей IDE или компилятора. Например, можно создать папку, в которой будут находиться папки Lib и Include. В них мы будем хранить все наши библиотечные и подключаемые файлы, которые собираемся использовать для наших OpenGL-проектов. Получается, что все сторонние библиотеки будут организованы в одном месте (и их можно будет совместно использовать на нескольких компьютерах).
  </li>
  <li>
3. Для начала давайте откроем Visual Studio и создадим новый проект. Для этого нужно выбрать тип проекта "C++", а далее — "Пустой проект". <br>
   Для того, чтобы наш проект мог использовать GLFW, нам нужно связать с ним полученную библиотеку. Это можно сделать, указав в настройках линкера, что мы хотим использовать библиотеку glfw3.lib, но проект пока не знает где её искать, т.к. все подобные файлы мы переместили в другую папку. Таким образом, сначала мы должны добавить эту папку в наш проект.<br>

Для этого нажмите правой кнопкой мышки на имя проекта в "Обозреватель Решений" > "Свойства". В появившемся окне выберите "Каталоги VC++" > "Каталоги библиотек"
Здесь вы можете добавить свои собственные каталоги, чтобы проект знал, где искать необходимые файлы. Это можно сделать, вставив вручную путь до каталога или щелкнув по соответствующей строке и выбрав пункт <Изменить…><br>
Здесь вы можете добавить столько дополнительных каталогов, сколько захотите, и с этого момента IDE при поиске файлов библиотек также будет просматривать и эти директории. Поэтому, как только вы подключите папку Lib из проекта GLFW, вы сможете использовать все файлы библиотек из этой папки. Аналогично обстоят дела и с добавлением папки Include для заголовочных файлов.
<br>Поскольку для VS были указаны все необходимые файлы, то мы, наконец, можем связать GLFW с нашим проектом, перейдя в раздел "Компоновщик" > "Ввод"<br>
Чтобы связать библиотеку нам нужно указать для компоновщика её имя. Так как библиотека называется glfw3.lib, то мы добавляем название этого файла в раздел "Дополнительные зависимости" (вручную или же через пункт <Изменить…>) и с этого момента при запуске процесса компиляции GLFW будет связан с нашим проектом. В дополнение к GLFW мы также должны добавить ссылки на библиотеку OpenGL, но данные действия будут отличаться в зависимости от (вашей) используемой операционной системы:

<br>Библиотека OpenGL в Windows. Если вы используете операционную систему Windows, то необходимый нам файл библиотеки opengl32.lib, входящий в пакет Microsoft SDK, уже есть вместе с Visual Studio и не требует отдельной установки. Поскольку мы используем компилятор VS и работаем под операционной системой Windows, то всё, что вам нужно сделать — это добавить название файла opengl32.lib к общему списку параметров компоновщика.
<br>
На этом установка и настройка GLFW завершена.
  </li>
  <li>
  4. GLAD — это библиотека с открытым исходным кодом, которая управляет всей той громоздкой работой, о которой мы говорили выше. GLAD имеет несколько иную настройку конфигурации, чем большинство распространенных библиотек с открытым исходным кодом.

Перейдите в веб-сервис GLAD, в поле «Profile» установлено "Core". Также параметр "Generate a loader" должен быть отмечен галочкой. Пункт «Extensions» мы пока пропустим, остается нажать кнопку "Generate", чтобы создать нужные нам файлы библиотеки <br>
<br>
К этому моменту GLAD предоставит вам возможность скачать zip-архив, содержащий в себе две подключаемые папки и файл glad.c. Вам нужно скопировать обе эти папки (glad и KHR) в свою папку с подключаемыми файлами (или добавьте дополнительный элемент, указывающий на эти папки в свойствах проекта), а также добавить файл glad.c в свой проект.
  </li>
</ul>
