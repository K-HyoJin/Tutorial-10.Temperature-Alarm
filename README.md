# Arduino example 10
Tutorial 10.Temperature Alarm\
온도값을 측정하고  0.05 이상이면 부저에서 소리가 출력되도록 제작

## circuit
Temperature Sensor : analog 0pin\
  buzzer : digital 8pin\
![image](https://user-images.githubusercontent.com/79436159/109286746-01f89e00-7866-11eb-9716-06ebc66f1da3.png)

## code
``` from pyfirmata import Arduino,util ```\
pyfirmata의 아두이노 모듈을 사용하기 위해 import함 

``` import time ```\
프로그램을 일정시간동안 지연시키기위해 time 모듈을 import함

``` board = Arduino('COM8')``` \
변수1 = Arduino('**포트번호**') 를 해서 보드와 연결 

```analog_input = board.get_pin('a:0:i')```\
-> 0번핀을 analog신호 입력핀으로 설정\
```buzzer = board.get_pin('d:8:o')``` \
-> 8번핀을 digital신호 출력핀으로 설정\
변수1 = 변수2.get_pin('**d or a** : **pin number** : **i or o** ') \
**d or a** : The type of the pin \
**pin number** : The number of the pin\
**i or o** : The mode of the pin

  ``` it = util.Iterator(board) ```\
보드의 입력값을 지속적으로 업데이트해주는 iterator 변수 선언

 ``` it.start()``` \
iterator 시작

``` analog_value = analog_input.read() ```\
Temperature와 연결된 0번핀의 입력을 읽어와서 변수 analog_value에 저장
```
for i in range(1):
  if analog_value is None:
    time.sleep(0.1)
    break
  if analog_value < 0.05:
    buzzer.write(0)
    time.sleep(0.1)
  if analog_value > 0.05:
    buzzer.write(1)
    buzzer.write(0)
    time.sleep(0.1)
```
analog_value값이 None이면 0.1초 지연시킨후 for문을 빠져나옴\
analog_value값이 0.05보다 작으면 buzzer의 소리를 off하도록 0을 입력으로 줌\
analog_value값이 0.05보다 크면 buzzer의 소리를 on하도록 1을 입력으로 줌
