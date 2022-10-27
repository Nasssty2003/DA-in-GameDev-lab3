# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #3 выполнил(а):
- Нестерова Анастасия Андреевна
- РИ210947
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.
- ✨Magic ✨

## Цель работы
Познакомиться с программными средствами для создания системы машинного обучения и её интеграции в Unity.

## Задание 1
### Реализовать систему машинного обучения в связке Pythin - Google-Sheets - Unity. При выполнении задания можно использовать видео-материалы и исходные данные, предоставленные преподавателями курса.
Ход работы:
1) Создаём новый пустой 3D проект на Unity
![Снимок экрана 2022-10-27 в 00 37 18](https://user-images.githubusercontent.com/43472988/198121087-b791ffda-fced-4f72-a9fe-533aa19ffe9f.png)
2) В созданный проект добавляем ML Agent
![Снимок экрана 2022-10-27 в 00 37 12](https://user-images.githubusercontent.com/43472988/198120917-8d42db49-c0a3-4b8b-8d9f-72d01326348a.png)
3) Во вкладке с компонентами (Components) внутри Unity видим строку ML Agent
![Снимок экрана 2022-10-27 в 01 00 34](https://user-images.githubusercontent.com/43472988/198125425-9b28f150-e92a-415c-a8e2-313af76fa6e5.png)
4) Пишем серию команд для создания и активации нового ML-агента, а также для скачивания необходимых библиотек как показано на рисунках в методических указаниях
5) Возвращаемся в Unity, запускаем сцену и проверяем работу ML-Agent'а (на скрине создан один объект для проверки работы) 
![197032998-ce8d361c-3581-413f-b3e3-394c30039b9f](https://user-images.githubusercontent.com/43472988/198136774-5a7114ff-c05d-4af1-abe7-6998cfd73caa.png)
6) Делаем 3, 9 и 27 копий модели "Плоскость-Сфера-Куб" и запускаем симуляцию сцены
![taufz5dj1p4](https://user-images.githubusercontent.com/43472988/198138898-03e4f218-b39e-4a0a-af8a-48700c226123.jpg)
![vIvkZQkTNwQ](https://user-images.githubusercontent.com/43472988/198139220-5bad018b-710e-4b1c-a195-e3321d9e5112.jpg)
![0-b3ghqWCeo](https://user-images.githubusercontent.com/43472988/198139228-bc1f8844-8156-4db2-a7bf-858cd7d73e61.jpg)
![HIUB37YiYQk](https://user-images.githubusercontent.com/43472988/198139282-8f1a898b-33e5-4fc6-949d-ab79cd19c7a3.jpg)
7) После завершения обучения проверяем работу модели
![Dsae8W4WAdo](https://user-images.githubusercontent.com/43472988/198139967-4d896757-3c1b-41e0-a690-828546470efb.jpg)
![riOnjX7GtgM](https://user-images.githubusercontent.com/43472988/198140053-58d88d66-b05d-4ea5-aa4e-02691b0af4b6.jpg)
8) Делаем выводы (рассматриваем изменение переменных): чем больше объектов, тем больше количество шагов, кроме того увеличивается Mean Reward и уменьшается Std of Reward.

## Задание 2
### Подробно описать каждую строку файла конфигурации нейронной сети, доступного в папке с файлами проекта. Самостоятельно найти информацию о компонентах Decision Requester, Behavior Parameters, добавленных на сфере.
```
behaviors: #behaviors отвечает за поведение объекта.
  RollerBall: # Описывается объект RollerBall
    trainer_type: ppo # Выбираем тип обучения с поощрением
    hyperparameters: # Перечисляем гиперпараметры этого объекта
      batch_size: 10 # batch_size - переменная количества опытов на каждой итерации градиентного спуска
      buffer_size: 100 # buffer_size - переменная общего количества опыта
      learning_rate: 3.0e-4 # learning_rate - переменная начальной скорости обучения объекта
      beta: 5.0e-4 # Переменная беты объекта
      epsilon: 0.2 # Переменная эпсилон
      lambd: 0.99 # Переменная лямбда
      num_epoch: 3 # num_epoch - переменная количества проходов, которые необходимо выполнить при выполнении оптимизации градиентного спуска
      learning_rate_schedule: linear # earning_rate_schedule определяет, каким образом скорость обучения изменяется
    network_settings: # Создаются сетевые настройки
      normalize: false # normalize показывает применяется ли нормализация к входным данным векторного наблюдения
      hidden_units: 128 # hidden_units - переменная количества единиц в скрытых слоях нейронной сети
      num_layers: 2 # num_layers - переменная количества скрытых слоев в нейронной сети
    reward_signals: # Создаётся сигналы вознаграждения
      extrinsic: # В extrinsic задаются внешние свойства сигналов
        gamma: 0.99 # Переменная гаммы 
        strength: 1.0 # Переменная силы
    max_steps: 500000 # max_steps - Переменная максимального количества допустимых шагов
    time_horizon: 64 # time_horizon - Переменная временного горизонта
    summary_freq: 10000 # Переменная для суммарной частоты
    
```

Decision Requester: запрос на принятие решения вызывает CollectObservation, а затем получает последнее действие в OnActionReceived, основанное на этом новом собранном наблюдении. С действиями из TakeActionBetweenDecisions он снова вызывает OnActionReceived без сбора новых наблюдений и выводит последнее действие, которое получил от NN.

Behavior Parameters: Параметры поведения, которые есть у каждого Агента. Поведение определяет, как Агент принимает решения. Например, максимальный шаг определяет, сколько шагов моделирования может произойти до окончания эпизода Агента.

## Задание 3 
### Доработать сцену и обучить ML-Agent таким образом, чтобы шар перемещался между двумя кубами разного цвета. Кубы должны, как и в первом задании, случайно изменять координаты на плоскости.
Для того, чтобы шар перемещался между двумя кубами разного цвета я написала код в Visual Studio по шаблону того, что было показано в видео в материалах для лабораторной работы.
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Unity.MLAgents;
using Unity.MLAgents.Sensors;
using Unity.MLAgents.Actuators;

public class RollerAgent : Agent
{
    Rigidbody rBody;
    // Start is called before the first frame update
    void Start()
    {
        
        rBody = GetComponent<Rigidbody>();
    }

    public Transform Target1;
    public Transform Target2;
    private float speedMove;
    private bool isTrue = true;
    public override void OnEpisodeBegin()
    {
        if (this.transform.localPosition.y < 0)
        {
            this.rBody.angularVelocity = Vector3.zero;
            this.rBody.velocity = Vector3.zero;
            this.transform.localPosition = new Vector3(0, 0.5f, 0);
        }
        Target1.localPosition = new Vector3(Random.value * 8-4, 0.5f, Random.value * 8-4);
        Target2.localPosition = new Vector3(Random.value * 8-4, 0.5f, Random.value * 8-4);   
    }
    public override void CollectObservations(VectorSensor sensor)
    {       
        sensor.AddObservation(Target1.localPosition);
        sensor.AddObservation(this.transform.localPosition);
        sensor.AddObservation(rBody.velocity.x);
        sensor.AddObservation(rBody.velocity.z);
    }
    public float forceMultiplier = 10;
    public override void OnActionReceived(ActionBuffers actionBuffers)
    {
        speedMove = Mathf.Clamp(actionBuffers.ContinuousActions[0], 1f, 10f);
        Vector3 controlSignal = Vector3.zero;
        controlSignal.x = actionBuffers.ContinuousActions[0];
        controlSignal.z = actionBuffers.ContinuousActions[1];
        rBody.AddForce(controlSignal * forceMultiplier);
        if (transform.position != Target1.transform.position & isTrue == true)
        {
            transform.position = Vector3.MoveTowards(transform.position, Target1.transform.position, Time.deltaTime * speedMove);
        }

        if (transform.position == Target1.transform.position & isTrue == true)
        {
            isTrue = false;
        }

        if (transform.position != Target2.transform.position & isTrue == false)
        {
            transform.position = Vector3.MoveTowards(transform.position, Target2.transform.position, Time.deltaTime * speedMove);
        }

        if (transform.position == Target2.transform.position & isTrue == false)
        {
            isTrue = true;
        }

        if (this.transform.localPosition.y < 0)
        {
            EndEpisode();
        }
    }
}
```
Скрин со сценой и шаром, перемещающимся между кубами:
![oaFy-DFMIL0](https://user-images.githubusercontent.com/43472988/198216274-ea52d9b3-279b-497d-b530-7ebd18becf6d.jpg)

## Выводы
В данной лабораторной работе я научилась подгружать в Unity дополнительные пакеты и работать с ними. Кроме того, из лекции я узнала о важности внутриигрового баланса. Он необходим, как минимум для создания более понятной и интересной для пользователя игры. И продумывать этот баланс нужно как в многопользовательских играх, так и в однопользовательских. Сделать это можно несколькими способами: от образа или от характеристик. 
.
| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
