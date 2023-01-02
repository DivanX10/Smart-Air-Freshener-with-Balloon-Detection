# Умный освежитель воздуха с определением наличия баллона и аромата баллона

В проекте использовался автоматический освежитель воздуха от компании Glade со сменными баллонами на 2400 распылении, который я переделал и интегрировал в Home Assistant
![image](https://user-images.githubusercontent.com/64090632/210274020-c190c6f2-04a1-47cf-8b0d-a1e1ef07811d.png)


### Какие возомжности предоставляет переделанный освежитель воздуха?
1) Распылять баллон средствами автоматизации Home Assistant
2) Распылять баллон встроенным таймером 
3) Датчик нажатия на физическую кнопку на освежителе воздуха
4) Определяет наличие баллона
5) Определяет аромат баллона
6) Можнос вести учет расхода каждого баллона или только единичного
7) Написать свой код для вывода сенсоров и управления освежителем в ESPHome
8) Питание от батареек
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
  <summary><b>5)</b> Разъем гнездо питания 5.5мм</summary>
  
![image](https://user-images.githubusercontent.com/64090632/210274879-f41c1f5a-a022-4f81-aa65-9595111f19fa.png)
</details>

