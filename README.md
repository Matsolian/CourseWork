# Курсовая №17 — генерация изображений диффузионной моделью

Рабочая папка проекта. На этом этапе выполняется EDA трёх наборов; модель ещё не обучалась. `../example/` — справочные материалы.

## Как запустить EDA в Miniconda DS

В Jupyter выберите ядро **DS**. Установите зависимости в этом ядре (`%pip install -r requirements-eda.txt` из `CourseWork` или `%pip install -r ../requirements-eda.txt` из `CourseWork/notebooks`). При необходимости проверьте путь Python: `import sys; print(sys.executable)`. Затем запускайте по порядку:

1. `notebooks/01_EDA.ipynb` — CIFAR-10, источник [University of Toronto](https://www.cs.toronto.edu/~kriz/cifar.html).
2. `notebooks/02_EDA_fashion.ipynb` — Fashion-MNIST, источник [Zalando Research](https://github.com/zalandoresearch/fashion-mnist).
3. `notebooks/03_EDA_flowers.ipynb` — Oxford Flowers 102, источник [University of Oxford](https://www.robots.ox.ac.uk/~vgg/data/flowers/102/).
4. `notebooks/04_EDA_comparison.ipynb` — сравнение **фактических результатов** трёх EDA и выбор датасета для последующего обучения.

**Весь исполняемый код EDA, числа, графики и выводы находятся в четырёх notebook.** Отдельные отчёты, JSON и PNG не создаются. Данные уже скачаны в `data/`; если их нет, возьмите CIFAR-10 Python version, четыре IDX `.gz` из репозитория Fashion-MNIST и три файла Oxford Flowers 102 по ссылкам выше. Тетради читают исходные файлы и выводят результаты под соответствующими ячейками. Четвёртая считывает метки CIFAR-10 и Fashion-MNIST, а для Flowers использует проверенные в третьей тетради размеры официальных выборок и число объектов на класс (без зависимости от SciPy). Данные в `data/` не включайте в репозиторий. У Oxford Flowers архив ~345 МБ, `scipy` требуется для чтения официальных `.mat`-файлов. У CIFAR-10 полный архив имеет размер 170 498 071 байт и MD5 `c58f30108f718f92721af3b95e74349a`.

Статистики пикселей вычисляются на train; отложенный test не участвует в выборе параметров модели. Разбиения CIFAR-10 и Fashion-MNIST повторяются при `seed=42`, Flowers использует официальное `data/flowers102/setid.mat`.
