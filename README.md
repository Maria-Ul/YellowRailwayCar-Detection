# YellowRailwayCar-Detection
YOLO implementation for yellow railway car detection

Ссылка на данные: https://drive.google.com/drive/folders/1yH2gUUZAw6jHL3a_0X6u-gT1-CPLFU-f

Ссылка на веса: https://drive.google.com/file/d/1sVpZJuqk9tu97AVV37ey7m9E5flunGUg/view?usp=sharing

Ссылка на ноутбук с пайплайном: https://github.com/Maria-Ul/YellowRailwayCar-Detection/blob/main/Pipeline.ipynb

Разбиение тренировка-валидация-тест: 70-15-15 %, (571, 122, 123)


# Предсказание yolov8 с весами yolov8n.pt
В COCO, на котором училась yolo, есть машины – появилась идея не учить yolo вообще и посмотреть как она воспримет жд машину.
Пара примеров предсказаний:
![img_kjtv_0_sec](https://github.com/Maria-Ul/YellowRailwayCar-Detection/assets/58764063/9382976a-ba68-4ead-8728-69ed52311ef3)

Так как класс очень специфичный - желтая машина на темном фоне, то я решила не аугментировать данные (т.к. тест-выборку я взяла из представленных данных). 

# Обучение с yolov8n.pt 15 эпох:
Основные метрики mAP50, mAP50-95

* Тренировка
  
  mAP50 = 0.994
  
  mAP50-95 = 0.66

  Основные показатели в процессе тренировки выходят на плато:
  ![train](https://github.com/Maria-Ul/YellowRailwayCar-Detection/assets/58764063/5140e339-3873-4045-b677-14d7ffa19720)

  Метрики на валидационной выборке во время обучения: 
  ![val](https://github.com/Maria-Ul/YellowRailwayCar-Detection/assets/58764063/f64811e9-08f3-455c-9179-8d6818d74022)

  
* Валидация
  
  mAP50 = 0.992
  
  mAP50-95 =  0.66
  
  Class     Images  Instances      Box(P          R      mAP50  mAP50-95): 100%|██████████| 8/8 [00:14<00:00,  1.75s/it]
   all        122        176      0.942      0.989      0.992       0.66
  Speed: 3.0ms preprocess, 25.8ms inference, 0.0ms loss, 3.5ms postprocess per image

  Примеры работы сети на валидационной выборке:
  
  ![val_batch0_pred](https://github.com/Maria-Ul/YellowRailwayCar-Detection/assets/58764063/3937ee7f-9a71-4a20-9a4c-6a87b34f4cca)

  
* Тест
  
  Во время предсказаний добавлена Test-Time Augmentation, чтобы повысить точность определения, но, кажется. излишне.
  
  Speed: 2.6ms preprocess, 9.3ms inference, 2.0ms postprocess per image at shape (1, 3, 384, 640)

  Результаты предсказания модели: https://drive.google.com/file/d/1sVpZJuqk9tu97AVV37ey7m9E5flunGUg/view?usp=sharing

  Несколько примеров:
![img_kjtv_106_sec](https://github.com/Maria-Ul/YellowRailwayCar-Detection/assets/58764063/90df506c-8ff6-4b81-9b9a-e3a4a0d78ae6)
![img_kjtv_121_sec](https://github.com/Maria-Ul/YellowRailwayCar-Detection/assets/58764063/d9a3fd00-4820-4e42-9a10-699af55eca56)
![img_kjtv_128_sec](https://github.com/Maria-Ul/YellowRailwayCar-Detection/assets/58764063/21f90fe1-6ad8-443c-8110-a09aa11b1eff)


  


