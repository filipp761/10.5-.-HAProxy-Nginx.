# 10.5-HAProxy-Nginx.
# Задание 1.
Что такое балансировка нагрузки и зачем она нужна?
Балансировка – это процесс распределения нагрузки на различные устройства, на несколько серверов, коммутаторов и т.п.
Балансировщик нужен для:
* отказоустойчивость (если один сервер откажет, балансировщик распределит трафик между остальными элементами инфраструктуры);
* балансировщик позволяет оптимально использовать ресурсы и быстрее обслуживать запросы;
* балансировщик обеспечит более плавное масштабирование инфраструктуры;
* защита от DDoS-атак
________________________________________
#Задание 2.
Чем отличаются между собой алгоритмы балансировки round robin и weighted round robin? В каких случаях каждый из них лучше применять?

**Алгоритм балансировки round robin**: алгоритм кругового обслуживания представляет собой перебор по круговому циклу: первый запрос передается одному серверу, затем следующий зарос передается другому и так до последнего сервера, а затем все начинается сначала.

**Алгоритм балансировки weighted round robin**: усовершенствованная версия алгоритма robin round. Суть усовершенствований заключается в следующем: каждому серверу присваивается свой весовой коэффициент в соответствии с его производительностью и мощностью. Это помогает распределять нагрузку более гибко: серверы с большим весом обрабатывают больше запросов. 

Применение:

**round robin** лучше применять, когда у нас все сервера однотипные по производительности, и нам нет необходимости учитывать загруженность того или сервера в составе кластера. Подходить для балансировки нагрузки вычислительных сетей (DNS)

**weighted round robin** лучше применять, когда сервера имеют различную производительность. Чем мощнее машина, тем больше запросов она обрабатывает. Это удобно применять, когда есть основной мощный сервер, а второй резервный, который включается в работу при скачке нагрузки.
