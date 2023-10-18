![img_kjtv_0_sec](https://github.com/Maria-Ul/YellowRailwayCar-Detection/assets/58764063/9f811e37-ca63-4c4d-ad25-a4bde1492c0e)# YellowRailwayCar-Detection
YOLO implementation for yellow railway car detection

Ссылка на данные: https://drive.google.com/drive/folders/1yH2gUUZAw6jHL3a_0X6u-gT1-CPLFU-f

Разбиение тренировка-валидация-тест: 70-15-15 %, (571, 122, 123)


Предсказание yolov8 с весами yolov8n.pt
(т.к. в COCO, на котором училась yolo есть машины, появилась идея не учить yolo вообще и посмотреть как она воспримет жд машину)
Пара примеров предсказаний:
![img_kjtv_0_sec](https://github.com/Maria-Ul/YellowRailwayCar-Detection/assets/58764063/9382976a-ba68-4ead-8728-69ed52311ef3)

Так как класс очень специфичный - желтая машина на темном фоне, то я решила не аугментировать данные (т.к. тест-выборку я взяла из представленных данных). 

Обучение с yolov8n.pt 15 эпох:
