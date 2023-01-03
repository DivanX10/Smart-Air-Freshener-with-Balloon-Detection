[English version](https://github.com/DivanX10/Smart-Air-Freshener-with-Balloon-Detection/blob/main/README_EN.md)

# Умный освежитель воздуха с определением наличия баллона и аромата баллона

В проекте использовался автоматический освежитель воздуха от компании Glade со сменными баллонами на 2400 распылении, который я переделал и интегрировал в Home Assistant.
![image](https://user-images.githubusercontent.com/64090632/210274020-c190c6f2-04a1-47cf-8b0d-a1e1ef07811d.png)


### Какие возможности предоставляет переделанный освежитель воздуха?
1) Распылять баллон средствами автоматизации Home Assistant
2) Распылять баллон встроенным таймером 
3) Датчик нажатия на физическую кнопку на освежителе воздуха
4) Определяет наличие баллона
5) Определяет аромат баллона
6) Можно вести учет расхода каждого баллона или только единичного
7) Написать свой код для вывода сенсоров и управления освежителем в ESPHome
8) Питание от батареек (разряжаются быстро и хватает на 1 день, но могут быть в качестве резервного питания на кратковременное обесточивание электричества)
9) Питание от сети


---

### Необходимые детали

<details>
  <summary><b>1)</b> Освежитель воздуха Glade Automatic - 1 шт.</summary>
  
![image](https://user-images.githubusercontent.com/64090632/210275338-a8fec7c1-8eed-4a49-8b24-a9cbae35a92a.png)
</details>
<details>
  <summary><b>2)</b> ESP Wemos mini - 1 шт.</summary>
  
![image](https://user-images.githubusercontent.com/64090632/210275136-fc39e573-aa01-4fbe-ae14-a6298901a5f6.png)
</details>

<details>
  <summary><b>3)</b> Понижающий преобразователь напряжения GSMIN MP1584EN DC-DC - 1 шт.</summary>
  
![image](https://user-images.githubusercontent.com/64090632/210275257-8ff22857-6f0d-442b-9d0e-46a37332211f.png)
</details>

<details>
  <summary><b>4)</b> Резисторы, любого номинала от 100 кОм до 2 Ом, можно взять набор резисторов</summary>
  
![image](https://user-images.githubusercontent.com/64090632/210275290-bc112a78-67a6-4a23-9d01-e9ef3382d7b0.png)
</details>

<details>
  <summary><b>5)</b> Разъем гнездо питания 5.5мм - 1 шт.</summary>
  
![image](https://user-images.githubusercontent.com/64090632/210274879-f41c1f5a-a022-4f81-aa65-9595111f19fa.png)
</details>

<details>
  <summary><b>6)</b> Клей токопроводящий для нитей обогрева (с никелем) NANOPROTECH - N штук на выбор</summary>
  
![image](https://user-images.githubusercontent.com/64090632/210275453-94cdc468-aa54-40ab-9ec9-fdf4335e0812.png)
</details>

<details>
  <summary><b>7)</b> Любой блок питания 9В 2А (9V/2A), штекер 5.5*2.1mm</summary>
  
![image](https://user-images.githubusercontent.com/64090632/210275605-cd81f509-ec63-4d81-9459-8ff40caa6f0b.png)
</details>

<details>
  <summary><b>8)</b> Неодимовые мощные плоские магниты прямоугольники Росмагнит 5х5х1 мм - 20шт</summary>
  
![image](https://user-images.githubusercontent.com/64090632/210276697-9c7320e6-8819-46c7-978b-151042579ff6.png)
</details>

<details>
  <summary><b>9)</b> Распечатать на 3д принтере плафторму</summary>
  
![image](https://user-images.githubusercontent.com/64090632/210276971-7149593f-cffe-45b2-ae90-71349b066ec9.png)

</details>

---

### Заливка на ESP Wemos mini прошивку для управления освежителем воздуха
В ESPHome создаем проект для управления освежителем воздуха, [**копируем код**](https://github.com/DivanX10/Smart-Air-Freshener-with-Balloon-Detection/blob/main/air-freshener-glade.yaml) и заливаем на плату

---

### Сборка

Извлекаем родную плату и делаем как на схеме
![image](https://user-images.githubusercontent.com/64090632/210275692-ac4eafeb-6fe4-436b-8851-254242e53015.png)

Увеличенный размер родной платы для понимания.
1) Желтый провод припаиваем ко второй ножке справа к микросхеме. Этот провод припаиваем к плате esp, к контактам D8 GPIO15 
2) Припаиваем резистор на 1кОм, а к нему зеленый провод. Далее припаиваем провод от резистора к плате esp, к контактам D7 GPIO13
3) Оранжевый провод это +3.3V и припаиваем к плате esp, к контактам +3.3V
4) Синий провод припаиваем к плате esp, к контактам GND
5) Перерезаем контакт на дорожке текстолита идущий от желтого провода. Это нужно для того, чтобы мы могли управлять диспенсером при выключенном таймере

![image](https://user-images.githubusercontent.com/64090632/210275721-a08a3a74-0b19-419d-b336-99912dc7a1f0.png)

6) Разрезаем пружинку с контактом + для батарейного отсека и припаиваем диод (выделил красным маркером). Зачем это нужно? Это нужно для защиты платы esp от выхода ииз строя по той причиине, что если в освежителе воздуха будут стоять батарейки и мы еще подключим в сеть, то чип отвечающий за преобразование напряжения не будет пытаться зарядить батарейку и не будет сильно нагреваться, что может выйти из строя. Диод препятствует течи тока в обратную сторону к батарейке 

![image](https://user-images.githubusercontent.com/64090632/210277101-1be5b60b-3c46-44ad-9fe9-774a9652f727.png)

7) На esp припаиваем провода и резистор на 5.1 кОм (есть в комплекте резисторов) или 5.6 кОм. Резистор припаиваем к контактам A0 и GND. Припаиваем два провода от контактам A0(на фото провод коричневого цвета) и к +3.3V(на фото провод черного цвета) и протягиваем в самый низ корпуса баллона

![image](https://user-images.githubusercontent.com/64090632/210277241-fe4dfb8f-bc95-4cc8-bb74-df4d2110848c.png)

8) Устанавливаем в отверстие корпуса разъем гнездо питания 5.5мм, припаиваем от разъема провода к понижайке преобразователя напряжения GSMIN MP1584EN DC-DC, а от понижайки к esp. На понижайке выставляем напряжение 2.2-3.3в и проверяем силу мотора. Если Рычаг сильно вдавливается в ограничитель и начинает трещать, то понижайте напряжение до 2.2в и должно быть так, чтобы рычаг упирался в огрничитель и в тоже время у мотора не хватало сил на продавливание рычага и не мог сточить шестеренки

![image](https://user-images.githubusercontent.com/64090632/210278174-10582517-9206-448b-834d-a3b9750d9eb2.png)

10) Протягиваем два провода от контактов A0 и +3.3V и наносим термоклей так, чтобы в центре был круг, а сзади была дуга. Провода я залил токопроводящим клеем - паять не нужно. 
> Важно! Токопроводящий клей плохо ложится на гладкую поверхность пластик, он начинает вспучиваться и отлипать. Обязательно гладкую поверхност зашкурить или процарапать хорошенько, тогда токопроводящий клей ляжет отлично

![image](https://user-images.githubusercontent.com/64090632/210277467-12c2e240-952f-4ab6-b7bf-b121e80a0ca5.png)
![image](https://user-images.githubusercontent.com/64090632/210277657-3d1cc3c7-f971-48de-bc78-308dd1ec1f5b.png)

10) Распечатываем платформу на 3д принтере, устанавливаем 2 магнитика для усиления примагничивания, устанавлдиваем в отверстие резистор и замазываем токопроводящим клеем. Расход токопроводящего клея может быть разным, поэтому, если будет несколько платформ, то желательно взять несколько штук. Я взял 5 пачек. Модель STL можно скачать [отсюда](https://www.thingiverse.com/thing:5762367)

![image](https://user-images.githubusercontent.com/64090632/210278033-ac35a90f-8700-4062-8e59-537360ee1ea5.png)





