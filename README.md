# YellowRailwayCar-Detection
YOLO implementation for yellow railway car detection

Ссылка на данные: https://drive.google.com/drive/folders/1yH2gUUZAw6jHL3a_0X6u-gT1-CPLFU-f

Разбиение тренировка-валидация-тест: 70-15-15 %, (571, 122, 123)


# Предсказание yolov8 с весами yolov8n.pt
(т.к. в COCO, на котором училась yolo есть машины, появилась идея не учить yolo вообще и посмотреть как она воспримет жд машину)
Пара примеров предсказаний:
![img_kjtv_0_sec](https://github.com/Maria-Ul/YellowRailwayCar-Detection/assets/58764063/9382976a-ba68-4ead-8728-69ed52311ef3)

Так как класс очень специфичный - желтая машина на темном фоне, то я решила не аугментировать данные (т.к. тест-выборку я взяла из представленных данных). 

# Обучение с yolov8n.pt 15 эпох:
Основные метрики mAP50, mAP50-95

* Тренировка
  mAP50 = 0.994
  mAP50-95 = 0.66

  Основные показатели в процессе тренировки выхоядт на плато:
  
  ![train](https://github.com/Maria-Ul/YellowRailwayCar-Detection/assets/58764063/5140e339-3873-4045-b677-14d7ffa19720)

  Метрики на валидационной выборки : 
  
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

  ![Uploading img_kjtv_66_sec.jp![img_kjtv_98_sec](https://github.com/Maria-Ul/YellowRailwayCar-Detection/assets/58764063/3ce96742-67fd-4d38-a778-1f3b5f3fc781)
![img_kjtv_94_sec](https://github.com/Maria-Ul/YellowRailwayCar-Detection/assets/58764063/23f7d00d-0f7e-4817-8b0a-d6706274fcda)
g…]()![img_kjtv_106_sec](https://github.com/Maria-Ul/YellowRailwayCar-Detection/assets/58764063/506fc8f3-ff09-4edf-8542-9681e0b47625)


