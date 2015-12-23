# Hackathon

## Возможное решение задачи

Исходя из условий задачи мы имеем направленный граф со взвешенными ребрами. Так как число вершин(V) в графе составляет около 1.2 миллионов и число ребер(E) около 5.6 миллионов, то анализировать отсутствующие связи во всем графе будет достаточно ресурсозатратно. Поэтому вместо анализа графа целиком нужно анализировать подграфы этого графа. В качестве характеристик для машинного обучения классификатора будем использовать сходство(similarity) между двумя вершинами a и b, посчитанные на графе G = Г_a&cup;Г_b, где Г_a и Г_b - соседи вершин a и b соответвенно. В качестве меры схожести будем использовать:
* Jaccard’s Coefficient,
* Adamic/Adar(Frequency-Weighted Common Neighbors),
* Preferential Attachment,
* Rooted Page Rank,
* Cosine similarity.
Данный список можно дополнить еще несколькими метриками схожести.

Для подсчета схожести будем пользоваться формулой: SCORE_ab = 1/|Г_a| * &Sigma; SCORE_vb, где v &isin; Г_a

После извлечения характеристик необходимо разбить полученный набор данных на обучающую выборку и тестовую и подать на вход бинарному классификатору.

### Это возможное решение задачи и для его реализции придется распараллеливать процесс извлечения характеристик и обучения классификатора. К сожаления по ряду обстоятельств не успел реализовать данный вариант решения в отведенное время, в baseline.ipynb находится код для получения submission.csv, который был в итоге загружен. В файле solution.ipynb находится код для извлечения характеристик для классификатора(код не оптимизирован, не учтены веса ребер между вершинами)
