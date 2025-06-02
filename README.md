# Домашнее задание к занятию "`Хранение в K8s. Часть 2`" - `Маркин Алексей`

### Цель задания

В тестовой среде Kubernetes нужно создать PV и продемострировать запись и хранение файлов.

### Задание 1

**Что нужно сделать**

Создать Deployment приложения, использующего локальный PV, созданный вручную.

1. Создать [Deployment](https://github.com/Markin-AI/kub-7/blob/main/deploy-bm-pvc.yaml) приложения, состоящего из контейнеров busybox и multitool.
2. Создать [PV](https://github.com/Markin-AI/kub-7/blob/main/bm-pv.yaml) и [PVC](https://github.com/Markin-AI/kub-7/blob/main/deploy-bm-pvc.yaml) для подключения папки на локальной ноде, которая будет использована в поде.
3. Продемонстрировать, что multitool может читать файл, в который busybox пишет каждые пять секунд в общей директории.

![1](https://github.com/Markin-AI/kub-7/blob/main/img/1.png)
 
4. Удалить Deployment и PVC. Продемонстрировать, что после этого произошло с PV. Пояснить, почему.

![2](https://github.com/Markin-AI/kub-7/blob/main/img/2.png)

После удаления PVC, PV сменил статус с Bound на Released, так как больше не свзан с PVC.

5. Продемонстрировать, что файл сохранился на локальном диске ноды. Удалить PV.  Продемонстрировать что произошло с файлом после удаления PV. Пояснить, почему.


![3](https://github.com/Markin-AI/kub-7/blob/main/img/3.png)

Политика Reclaim Policy: Retain сохраняет файлы даже после удаления PV.

5. Предоставить манифесты, а также скриншоты или вывод необходимых команд.

[Deployment + PVC](https://github.com/Markin-AI/kub-7/blob/main/deploy-bm-pvc.yaml)

[PV](https://github.com/Markin-AI/kub-7/blob/main/bm-pv.yaml)

------

### Задание 2

**Что нужно сделать**

Создать Deployment приложения, которое может хранить файлы на NFS с динамическим созданием PV.

1. Включить и настроить NFS-сервер на MicroK8S.
2. Создать [Deployment](https://github.com/Markin-AI/kub-7/blob/main/deploy-m-pvc.yaml) приложения состоящего из multitool, и подключить к нему [PV](https://github.com/Markin-AI/kub-7/blob/main/pv-nfs.yaml), созданный автоматически на сервере NFS.
3. Продемонстрировать возможность чтения и записи файла изнутри пода. 
4. Предоставить манифесты, а также скриншоты или вывод необходимых команд.

![4](https://github.com/Markin-AI/kub-7/blob/main/img/4.png)

![5](https://github.com/Markin-AI/kub-7/blob/main/img/5.png)

[Deployment + PVC](https://github.com/Markin-AI/kub-7/blob/main/deploy-m-pvc.yaml)

[PV](https://github.com/Markin-AI/kub-7/blob/main/pv-nfs.yaml)

------

### Правила приёма работы

1. Домашняя работа оформляется в своём Git-репозитории в файле README.md. Выполненное задание пришлите ссылкой на .md-файл в вашем репозитории.
2. Файл README.md должен содержать скриншоты вывода необходимых команд `kubectl`, а также скриншоты результатов.
3. Репозиторий должен содержать тексты манифестов или ссылки на них в файле README.md.