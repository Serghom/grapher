# grapher
Program for plotting graphs from files

--- 
Программа может работать как и из консоли, так и через GUI
--- 
## Консольный запуск
Запуск: 
```
grapher --source “<ключ таблицы>|<делитель>|путь к файлу данных {<указание на столбец со временем>}; <(конструкция повторяется, путь к другому файлу данных)>” --json “<путь к папке с json или путь к конкретному json файлу>”  --target “путь к папке, куда будут сохранены графики”
```

Пример: 
```
grapher --source "csv|/home/sergay/Desktop/test/souz.csv{1};sau|/home/lebedenko/Desktop/test/sau-bk_kittp.txt" --json "/home/sergay/Desktop/pythonParcer/json/typeDots" 
--target "/home/serghom/Desktop/test/reports/graph"  --jfolder
```

Описание ключей:

--source 	- является обязательным; Указываются параметры для таблицы, через делитель “|”:
		1)  Ключ таблицы, является обязательной. Ключ должен совпадать с ключем в json документе;
    		2)  Делитель, опционально. Указывается символ делителя на столбы. (default: “|”. Запрещены: «;» и «{}»);
		3) Путь к файлу, является обязательным, Указывается путь к файлу, из которого буду взяты данные;
		4) Указание на столбец со временем, опционально. Указывает на индекс столбца со временем. Пишется строго после пути к файлу, в фигурных скобках: {index} (default: 0)


--json		- является обязательным; Указывается путь к папке с json файлами (Если указан ключ --jfolder) или путь к конкретному json файлу (если ключ не указан). 

 --target	- является обязательным; Указывается  путь к папке, куда будут сохранены графики. Если конечной папки не существует, она будет создана.
 
 --- 
## Запуск GUI
Для того, чтобы запустилась GUI программа должна быть запущена без каких либо ключей.
Важно, что бы файл "settings.json" лежал в одной папке с .exe. Так же, проследите за тем, чтобы поле "embeded" в файле "settings.json" имело значение false.


--- 
## Описание JSON файлов графиков
Массив из элементов, каждый элемент содержит в себе структуру таблицы №1


#### Таблица №1
|   №|    	       Поле|              Тип|                                               Описание|
|----|---------------------|-----------------|-------------------------------------------------------|
|   1|   	      graph|     Структура[n]|  Описание структуры в таблице №2; n – кол-во элементов|
|   2|  	     vlines|     Структура[n]|  Описание структуры в таблице №4; n – кол-во элементов|
|   3|		 title_main|  	       string|  		   Подпись в шапке файла; Опционально|
|   4| 		    title_x|   	       string|   		        Подпись по оси X; Опционально|
|   5| 		    title_y|   	       string|   		        Подпись по оси Y; Опционально|
|   6| 	     second_title_y|   	       string|   		 Подпись по второй оси Y; Опционально|
|   7|   	 legend_pos|   	       string|   Определяет местоположение легенды на полотне. Список местоположений указан в списке №1; Опционально. По умолчанию «top_right»|
|   8|   	     move_x|   	        float|   Сдвигает ось X на указаное значение; Опционально. По умолчанию «0»|
|   9|   	     move_y|   	        float|   Сдвигает ось Y на указаное значение; Опционально. По умолчанию «0»|
|  10|        move_second_y|   	        float|   Сдвигает вторую ось Y на указаное значение; Опционально. По умолчанию «0»|
|  11|   	x_min_scale|   	        float|Задает границу отрисовки графика. Минимальное значение шкалы по оси X; Если min_scale > max_scale – ось перевернется; Если min_scale = max_scale – то ограничения игнорируются; Опционально. По умолчанию «0»|
|  12|   	x_max_scale|   	        float|Задает границу отрисовки графика; Максимальное значение шкалы по оси X; Если min_scale > max_scale – ось перевернется; Если min_scale = max_scale – то ограничения игнорируются; Опционально. По умолчанию «0»|
|  13|   	y_min_scale|   	        float|Задает границу отрисовки графика. Минимальное значение шкалы по оси Y; Если min_scale > max_scale – ось перевернется; Если min_scale = max_scale – то ограничения игнорируются; Опционально. По умолчанию «0»|
|  14| 	        y_max_scale|   	        float|Задает границу отрисовки графика; Максимальное значение шкалы по оси Y; Если min_scale > max_scale – ось перевернется; Если min_scale = max_scale – то ограничения игнорируются; Опционально. По умолчанию «0»|
|  15|   second_y_min_scale|   	        float|Задает границу отрисовки графика; Минимальное значение шкалы по второй оси Y; Если min_scale > max_scale – ось перевернется; Если min_scale = max_scale – то ограничения игнорируются; Опционально. По умолчанию «0»|
|  16|   second_y_max_scale|   	        float|Задает границу отрисовки графика; Максимальное значение шкалы по второй оси Y; Если min_scale > max_scale – ось перевернется; Если min_scale = max_scale – то ограничения игнорируются; Опционально. По умолчанию «0»|
|  17|		   namefile|   	       string|   		  Задает название сделаного файла|

--- 
#### Таблица №2
|   №|    	       Поле|              Тип|                                               Описание|
|----|---------------------|-----------------|-------------------------------------------------------|
|   1|			KEY|     Структура[n]|Описание структуры в таблице №3; n – кол-во элементов; Имя самого поля является ключем, должно совпадать с ключем указанном в ключе —source|

--- 
#### Таблица №3
|   №|    	       Поле|              Тип|                                               Описание|
|----|---------------------|-----------------|-------------------------------------------------------|
|   1|   	      param|  	       string|Название параметра по которому будет строиться график; (Не указывать если, указаны param_x и param_y)|
|   2|  	    param_x|  	       string|Название параметра для оси X; (Нельзя указывать без param_y)|
|   3|		    param_y|  	       string|Название параметра для оси Y; (Нельзя указывать без param_x)|
|   4| 		       name|   	       string|   		        Имя в легенде|
|   5| 		      width|   	          int|Определяет толщину линии в пикселях. Если указано значение меньше нуля, то линия не будет отоброжаться|
|   6| 	     	       dash|   	       string|Определяет тип линии. Список типов указан в списке №2; Опционально. По умолчанию «SolidLine»|
|   7| 	     	      color|   	       string|Определяет цвет линии. Можно указывать как HEX значение так и названия цветов, список названий указан в списке №3; Опционально. По умолчанию «blue»|
|   8| 	    	       dots|   	       	 bool|Определяет, будут ли отрисованые маркеры на точках; Опционально. По умолчанию «false»|
|   9| 	     	  dots_size|   	          int|Размер маркеров; В случае, если dots == false – не указывается|
|  10| 	     	 dots_style|   	       string|Стиль маркеров, список маркеров указан в списке №4; В случае, если dots == false – не указывается; Опционально. По умолчанию «Diamond»|
|  11| 	     	   second_y|   	       	 bool|Определяет, что данный параметр будет строиться по второй оси Y; Опционально. По умолчанию «false»|


--- 
#### Таблица №4
|   №|    	       Поле|              Тип|                                               Описание|
|----|---------------------|-----------------|-------------------------------------------------------|
|   1|   	       text|  	       string|  		       Текст, который будет отображен|
|   2| 	     text_font_size|     	  int|						Размер шрифта|
|   3|		 text_coord|  	    Структура|Описание структуры в таблице №5; Опционально. По умолчанию «{.x=0.0, .y=0.0}»|
|   4|     text_orientation|   	       string|Указывает оринтацию текста. Список указан в списке №5; Опционально. По умолчанию «Horizontal»|
|   5| 		      color|   	       string|Определяет цвет линии. Можно указывать как HEX значение так и названия цветов, список названий указан в списке №3; Опционально. По умаолчанию «blue»|
|   6| 	    	       dash|   	       string|Определяет тип линии. Список типов указан в списке №2; Опционально. По умолчанию «SolidLine»|
|   7| 	     	      width|   	          int|Определяет толщину линии. Если указано значение меньше нуля, то линия не будет отоброжаться|
|   8| 	     	    point_x|   	        float|Указывает точку на оси X, на которой будет нарисована вертикальная линия|
|   9| 	    	      y_max|   	        float|Указывает максимальное значение; вертикальной линии; Если y_max && y_min == 0, то, y_max  = y_max_scale ∙ 0,8 && y_min = y_min_scale ∙ 0,8 (Максимальное значение шкалы по оси Y = 300, минимальное значение шкалы по оси Y = -50; следовательно значения y_max = 240, y_min = -40)|
|  10| 	    	      y_min|   	        float|Указывает минимальное значение; вертикальной линии; Если y_max && y_min == 0, то, y_max  = y_max_scale ∙ 0,8 && y_min = y_min_scale ∙ 0,8 (Максимальное значение шкалы по оси Y = 300, минимальное значение шкалы по оси Y = -50; следовательно значения y_max = 240, y_min = -40)|
