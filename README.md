# Arduino example 10
Tutorial 10.Temperature Alarm\
출력되는 온도값이 0.05 이상이면 부저에서 소리가 출력되도록 제작

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
