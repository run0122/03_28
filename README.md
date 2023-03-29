# button_debounce_change_test
 
![Tinkercad Image](/LED3_Practice.png)

<hr/>

## 1. LED Turn On & Off

오늘은 pinMode() 함수를 통해서 특정한 핀을 통해서 입력과 출력을 받고, digitalWrite() 함수를 통해서 특정 핀의 상태를 변경하는 기능을 구현하였습니다.

delay()함수를 통해서 원하는 밀리초 구간동안 여러 개의 LED 중에서 내가 원하는 LED만 키고 끄는 함수를 구현하였습니다. 이 때 궁금증이 하나 생겼는데, delay()함수는 모든 LED에 영향을 주기 때문에 각각의 LED가 따로 영향받는 코드를 구현하고자 했습니다.

https://www.letsstartcoding.com/concept-alternate-blinking-leds-with-millis
위 코드를 참고하여 2개의 LED가 다른 사이클로 켜지고 꺼지는 코드를 구현할 수 있었습니다. millis()라는 함수를 이용해서 작동하는 코드였습니다. 각각의 LED에 timer변수를 줘서 LED가 켜지고 꺼지는 시간을 설정하며, 사이클이 종료될 때 현재 시간을 millis()함수를 통해 timer변수에 저장하고, 다시 사이클이 도는 형식이었습니다.

<hr/>

## 2. Push Button & Debounce

digitalRead(buttonPin) 함수를 통해서 현재 버튼 상태(buttonState)를 확인하고 buttonState가 HIGH거나 LOW일 때 변경되는 코드였습니다. buttonState가 HIGH일 때는 ledState도 HIGH, buttonState가 LOW일 때는 ledState도 LOW로 구현한 코드는 잘 작동하였습니다. 

반면에 버튼을 누를 때(buttonState == HIGH)마다 LED 상태를 변환하는 코드는 잘 작동하지 않았습니다. 한 번의 push에 여러 번 입력을 받는 것(bouncing)이 문제였습니다. 이를 해결하기 위해서 button 입력을 받고, 필요한 동작을 시행한 뒤에 delay(250)을 주는 것으로 문제를 해결하였으나 뭔가 좀 아쉬운 점이 있었습니다.

debounce 코드를 알게 되었습니다. 이 코드 또한 millis()로 구현되는 코드였습니다. 버튼이 입력되면 debounceDelay 시간 동안 버튼 상태를 유지하고 기능이 작동하는 코드였습니다. 이전의 코드를 변경하여 debounce 코드에 적용하였고 잘 작동하는 것을 확인할 수 있었습니다.

<hr/>

|함수|기능|설명|
|------|:---:|---|
|pinMode()|핀 입출력|pinMode(buttonPin, INPUT)<br>pinMode(ledPin, OUTPUT)|
|delay()|딜레이|delay(1000)|
|digitalRead()|읽기|int reading = digitalRead(buttonPin)|
|digitalWrite()|쓰기|digitalWrite(ledPin, ledState)|
|millis()|경과된 시간||
