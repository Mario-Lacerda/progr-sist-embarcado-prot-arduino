# DESAFIO Dio - **Programando Sistemas Embarcados com a Placa de Prototipação Arduino** 



## PROJETO 1

### **Projeto: Protótipo de Termômetro Digital**

Este projeto visa criar um protótipo de termômetro digital usando a placa de prototipação Arduino. O termômetro será capaz de medir a temperatura ambiente e exibir o resultado no display LCD.

**Requisitos:**

- Placa Arduino Uno
- Módulo LCD 16x2
- Sensor de temperatura DS18B20
- Cabos de conexão

**Código-Fonte:**

```plaintext
#include <LiquidCrystal.h>
#include <OneWire.h>

// Define os pinos do LCD
const int rs = 12;
const int en = 11;
const int d4 = 5;
const int d5 = 4;
const int d6 = 3;
const int d7 = 2;

// Define o pino do sensor de temperatura
const int ds18b20Pin = 8;

// Inicializa o display LCD
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);

// Inicializa o sensor de temperatura
OneWire ds18b20(ds18b20Pin);

void setup() {
  // Inicializa o LCD
  lcd.begin(16, 2);

  // Configura o sensor de temperatura
  ds18b20.begin();
}

void loop() {
  // Lê a temperatura do sensor
  float temperature = readTemperature();

  // Exibe a temperatura no display LCD
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("Temperatura:");
  lcd.setCursor(0, 1);
  lcd.print(temperature);
  lcd.print(" °C");

  // Aguarda 1 segundo
  delay(1000);
}

float readTemperature() {
  // Cria um ponteiro para o primeiro sensor de temperatura
  OneWire::DeviceAddress tempDeviceAddress;

  // Procura por sensores de temperatura
  if (ds18b20.search(tempDeviceAddress)) {
    // Converte a temperatura para o formato float
    float temperature = ds18b20.readTemperature(tempDeviceAddress);

    // Retorna o valor da temperatura
    return temperature;
  } else {
    // Retorna o valor 0 se não encontrar nenhum sensor
    return 0;
  }
}
```

**Montagem do Circuito:**

1. Conecte o pino VCC do sensor de temperatura ao pino 5V da Arduino.
2. Conecte o pino GND do sensor de temperatura ao pino GND da Arduino.
3. Conecte o pino SCL do sensor de temperatura ao pino A5 da Arduino.
4. Conecte o pino SDA do sensor de temperatura ao pino A4 da Arduino.
5. Conecte o pino RS do LCD ao pino 12 da Arduino.
6. Conecte o pino EN do LCD ao pino 11 da Arduino.
7. Conecte o pino D4 do LCD ao pino 5 da Arduino.
8. Conecte o pino D5 do LCD ao pino 4 da Arduino.
9. Conecte o pino D6 do LCD ao pino 3 da Arduino.
10. Conecte o pino D7 do LCD ao pino 2 da Arduino.

**Compilação e Upload:**

1. Abra o software Arduino IDE.
2. Selecione a placa Arduino Uno.
3. Carregue o código-fonte no Arduino.

**Execução do Programa:**

1. Conecte o Arduino a uma fonte de alimentação.
2. Ligue o Arduino.
3. O termômetro começará a medir a temperatura ambiente e a exibir o resultado no display LCD.



## PROJETO2

**Projeto: Programando Sistemas Embarcados com a Placa de Prototipação Arduino**

Este projeto visa fornecer uma introdução prática à programação de sistemas embarcados usando a popular placa de prototipação Arduino. Os sistemas embarcados são dispositivos eletrônicos que são projetados para executar tarefas específicas dentro de um sistema maior.



**Requisitos:**

- Placa Arduino (por exemplo, Arduino Uno, Nano ou Mega)
- Cabo USB
- LEDs
- Resistores

**Código-Fonte:**

```plaintext
// Piscar um LED conectado ao pino digital 13
void setup() {
  // Define o pino 13 como saída
  pinMode(13, OUTPUT);
}

void loop() {
  // Acende o LED
  digitalWrite(13, HIGH);
  // Aguarda 1 segundo
  delay(1000);
  // Apaga o LED
  digitalWrite(13, LOW);
  // Aguarda 1 segundo
  delay(1000);
}
```

**Explicação Técnica:**

- **Configuração (setup):** A função `setup()` é executada uma vez quando a placa Arduino é ligada. Ela define o pino digital 13 como saída, o que significa que podemos controlar seu estado (ligado ou desligado).
- **Loop Principal (loop):** A função `loop()` é executada repetidamente após a `setup()`. Ela alterna o estado do pino digital 13, acendendo e apagando o LED conectado a ele. A função `delay()` é usada para controlar o tempo que o LED permanece ligado ou desligado.

**Montagem do Circuito:**

1. Conecte um resistor de 220 ohms em série com um LED.
2. Conecte o terminal positivo do LED ao pino digital 13 do Arduino.
3. Conecte o terminal negativo do LED ao terra (GND) do Arduino.

**Compilação e Upload:**

1. Abra o software Arduino IDE.
2. Selecione a placa Arduino que você está usando.
3. Copie e cole o código-fonte na janela do editor.
4. Clique no botão "Verificar" para verificar se há erros de sintaxe.
5. Clique no botão "Upload" para enviar o código para a placa Arduino.

**Conclusão:**

Este projeto fornece uma base para explorar o mundo dos sistemas embarcados usando a placa Arduino. Ele demonstra como controlar dispositivos externos (neste caso, um LED) por meio de programação. Com mais conhecimento e prática, você pode desenvolver sistemas embarcados mais complexos para uma ampla gama de aplicações.







## APLICAÇÃO PRÁTICA



## **Protótipo: Termômetro digital**

Vamos utilizar um projeto de um **termômetro digital** para demonstrar como embarcar um projeto com Arduino. Este termômetro utiliza um sensor [LM35 ](https://www.makerhero.com/produto/sensor-de-temperatura-lm35dz/)para ler a temperatura e exibir o valor em um LCD.

O [LM35](https://www.makerhero.com/produto/sensor-de-temperatura-lm35dz/) é um sensor de precisão, que produz uma saída de 10 mV por grau Celsius, tem uma precisão de 0.5 °C e trabalha de 0°C a 100°C. Quando comparado a outros sensores, como termistores, é mais caro, porém seu uso é muito mais simples e mais preciso, sem necessidade de processamento ou hardware extras para melhorar a precisão.

##### **Materiais Necessários**

- [1 x Arduino UNO](https://www.makerhero.com/produto/placa-uno-r3-cabo-usb-para-arduino/)
- [1 x Sensor de temperatura LM35](https://www.makerhero.com/produto/sensor-de-temperatura-lm35dz/)
- [1 x Trimpot](https://www.makerhero.com/produto/potenciometro-trimpot-100k-3362/)
- [1 x Display LCD](https://www.makerhero.com/produto/display-lcd-16x2-backlight-verde/)
- [1 x Protoboard](https://www.makerhero.com/produto/protoboard-830-pontos/)
- [1 x Resistor 220 Ω](https://www.makerhero.com/produto/resistor-220ω-14w-x20-unidades/)
- [Jumpers diversos](https://www.makerhero.com/produto/kit-jumpers-10cm-x120-unidades/)

##### **Circuito**

O circuito do projeto termômetro digital, utilizando o Arduino, esta representado abaixo.

![Termômetro digital com Arduino UNO](https://www.makerhero.com/wp-content/uploads/2020/06/Termometro-digital-circuito.jpg)

##### **Código**

O código do projeto está descrito abaixo. Utilizamos a biblioteca LiquidCrystal (nativa da arduino IDE) para a comunicação com o LCD. A função setup é responsável por inicializar o LCD e escrever Temperatura na primeira linha do display e o símbolo de grau Celsius ao final da segunda linha (estas duas strings permanecem constantes durante todo o funcionamento do termômetro)..

Na função loop, chamamos a função read_temp que lê o sensor através do conversor AD e realiza a conversão de tensão para temperatura, o valor é escrito no LCD na segunda linha, alinhado à direita, logo antes do símbolo “°C”, com precisão de uma casa decimal (um número após a vírgula).

```

```

##### **Protótipo em Funcionamento**

O funcionamento do protótipo é demonstrado na imagem abaixo, o Arduino lê o sensor de temperatura (componente preto à direita) e escreve o valor, em graus Celsius, no display LCD. A temperatura mostrada corresponde ao valor informado pelo site [weather](https://weather.com/), com uma margem de erro de 2 ºC.

![img](https://www.makerhero.com/wp-content/uploads/2020/06/Termometro-digital-completo-e1591974540653.jpg)

## **Desenvolvimento do produto final**

Para saber quais componentes do Arduino Uno são necessários no nosso projeto podemos dar uma olhada no [esquemático do Arduino Uno Rev3](https://www.arduino.cc/en/uploads/Main/Arduino_Uno_Rev3-schematic.pdf).

Pode parecer um pouco confuso, mas se separarmos o circuito pela sua função, podemos dividir o Arduino em três partes:

- **Controle de alimentação:** Responsável por garantir o correto nível de tensão necessário pelos componentes;
- **Comunicação:** Realiza a ponte entre o USB do PC e a porta serial do microcontrolador principal;
- **Microcontrolador principal:** Pode ser considerado o “coração” do Arduino Uno, é responsável por executar todas as funções que programamos.

Um **microcontrolador** é um pequeno computador cujos componentes (processador, memória RAM, memória ROM, …) e alguns periféricos (conversor A/D, GPIOs, gerador de PWM, ..) estão encapsulados em um único chip. No caso do Arduino Uno, o microcontrolador utilizado é o **ATMEGA328P-PU**. Quando programamos o Arduino, estamos na verdade, programando este microcontrolador.

No caso deste projeto, onde não há necessidade de comunicação com o PC, necessitamos apenas do microcontrolador e alguns poucos componentes que o chip necessita para funcionar.

Vale ressaltar que o **ATMEGA328P-PU** não possui uma porta USB nativa. Só somos capazes de comunicar o PC com o Arduino devido ao módulo de comunicação, que converte a saída serial do chip para a porta USB do PC. Se seu projeto requer comunicação com PC é recomendado utilizar outro microcontrolador. O microcontrolador do Arduino Leonardo, por exemplo, possui porta USB nativa, no entanto o processo de comunicação USB com o sistema operacional do PC pode ser uma tarefa complicada sem os drivers adequados.

##### **Materiais Necessários**

- [1 x Atmega328P-PU](https://www.makerhero.com/produto/mini-kit-arduino-atmega328p-bootloader/)
- [1 x Cristal oscilador de quartzo 16 MHz](https://www.makerhero.com/produto/mini-kit-arduino-atmega328p-bootloader/)
- [2 x Capacitores 22 pF](https://www.makerhero.com/produto/mini-kit-arduino-atmega328p-bootloader/)
- [1 x Sensor de temperatura LM35](https://www.makerhero.com/produto/sensor-de-temperatura-lm35dz/)
- [1 x Trimpot](https://www.makerhero.com/produto/potenciometro-trimpot-100k-3362/)
- [1 x Display LCD](https://www.makerhero.com/produto/display-lcd-16x2-backlight-verde/)
- [1 x Protoboard](https://www.makerhero.com/produto/protoboard-830-pontos/)
- [Jumpers diversos](https://www.makerhero.com/produto/kit-jumpers-rigidos-x140-unidades/)

##### **Circuito**

O circuito equivalente ao projeto, utilizando o microcontrolador ao invés do Arduino, esta representado abaixo.

![img](https://www.makerhero.com/wp-content/uploads/2020/06/Termometro-sem-o-Arduino.jpg)

Repare que além do microcontrolador estamos utilizando um **cristal de quartzo** e **alguns capacitores**. O cristal de quartzo, junto com os capacitores cerâmicos, formam o circuito oscilador, que produz sinal de clock utilizado pelo processador do ATMEGA.

Como desejamos utilizar o mesmo código escrito para o Arduino, que utiliza funções dependentes de tempo (comunicação com LCD e delay), precisamos garantir que a base de tempo (o clock) é a mesma. Utilizamos um cristal de 16 MHz e dois capacitores de 22 pF pois estes são os valores utilizados no Arduino Uno.

No [datasheet ](http://ww1.microchip.com/downloads/en/DeviceDoc/Atmel-42735-8-bit-AVR-Microcontroller-ATmega328-328P_Datasheet.pdf)do ATMEGA é possível encontrar os valores de cristal suportados e os capacitores que devem ser utilizados. Apesar de haver um oscilador RC interno no microcontrolador, utilizamos um oscilador à cristal externo pois este é muito mais preciso.

