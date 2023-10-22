# Estudo de plataforma embarcada - Arthur Reis

## Manual de Referência do Raspberry Pi Pico W
**Introdução**
O Raspberry Pi Pico W é uma placa de desenvolvimento baseada no microcontrolador RP2040, que inclui conectividade Wi-Fi e Bluetooth LE e muito mais. Este manual fornece informações importantes para trabalhar com o Raspberry Pi Pico W.

**Especificações**

-Microcontrolador: RP2040

-Conectividade: Wi-Fi e Bluetooth LE (exemplo)

-Tensão de Operação: 3,3 V

-Interfaces: GPIO, UART, I2C, SPI, PWM

-Dimensões: 51 X 21 mm

 **Pinout Padrão**
 
-GPIO (P0-P26)

-LED (LED_GP0 e LED_GP1)

-Boot Select (BOOTSEL)

-VCC (Alimentação) e GND (Terra)

-Antena (ANT)

-USB (USB_DM e USB_DP)

-UART (TX0 e RX0)

-I2C (SDA0 e SCL0)

-SPI (SPI0_MISO, SPI0_MOSI, SPI0_SCK e SPI0_CS)

-Wi-Fi e Bluetooth (EN_WIFI e EN_BT)

**Alimentação**

-Tensão de Alimentação: 5 V (via USB)

-Consumo de Corrente Típico: O consumo de corrente varia dependendo da carga de trabalho e do estado do dispositivo. Em operação normal, o consumo de corrente é relativamente baixo, mas pode aumentar quando recursos como Wi-Fi e Bluetooth estão ativos.

-Notas: Microcontrolador de baixo consumo de energia (já visto no tópico acima), o que o torna adequado para aplicações com restrições de energia

**Comunicação**

**UART**

-Pinos: TX, RX

-Baud Rate Suportada: 9600, 115200 e entre outros

**I2C**

-Pinos: SDA, SCL

-Velocidade Suportada: 100 kbps, 400 kbps e entre outros

**SPI**

-Pinos: SCK, MISO, MOSI, CS

-Modos Suportados: Modo 0, Modo 1, etc.

**Programação**

Linguagens Suportadas: MicroPython, C/C++

## A interface de comunicação entre componentes
Este tópico irá tratar de maneira mais específica quais são os tipos de interfaces de comunicação entre componentes, visto que elas são utilizadas para que diversos componentes se comuniquem entre si, permitindo que os dispositivos de hardware troquem informações com mais facilidade.

**UART** é uma interface serial assíncrona que permite a comunicação entre dispositivos usando sinais de dados, transmitindo e recebendo bits sequencialmente. É amplamente utilizado para a comunicação entre microcontroladores e dispositivos periféricos. **I2C** (_Inter-Integrated Circuit_) é um barramento serial de dois fios que permite que vários dispositivos se comuniquem entre si. É usado para conectar sensores, memórias, displays e outros dispositivos a um microcontrolador. **SPI** é uma interface serial síncrona que é comumente usada para transferir dados entre um microcontrolador e dispositivos como displays, memórias flash e sensores. Já a **CAN** é uma interface serial usada principalmente em sistemas automotivos e industriais para comunicação entre dispositivos em rede, como sensores e atuadores. **Ethernet** é uma interface de rede amplamente usada para comunicação em redes locais e na Internet. É comum em dispositivos como computadores, roteadores e placas de desenvolvimento. **Bluetooth** e **Wi-Fi** são interfaces sem fio usadas para comunicação em dispositivos móveis, _IoT_ e outros sistemas sem fio. _USB_ é uma interface amplamente usada para conectar dispositivos de computação, como teclados, mouses, impressoras, discos rígidos, etc. A **GPIO** é uma interface que permite que dispositivos leiam ou escrevam dados digitais em pinos de propósito geral, comuns em microcontroladores e placas de desenvolvimento. **Modbus** é um protocolo de comunicação amplamente utilizado em sistemas de automação industrial para permitir a comunicação entre controladores e dispositivos em rede.

## Prova de conceito na utilização de Bluetooth e Wi-fi com outros dispositivos
**Objetivo**: Demonstrar como o Raspberry Pi Pico W pode se comunicar com dispositivos móveis via Bluetooth e se conectar a uma rede local via Wi-Fi.

**Materiais Necessários**:

-Raspberry Pi Pico W

-Dispositivo móvel com Bluetooth (por exemplo, smartphone ou tablet)

-Acesso a uma rede Wi-Fi

**Passos**:

**1. Configuração do Bluetooth**:

a. No Raspberry Pi Pico W, precisa certificar de que o MicroPython esteja instalado. Você pode usar o MicroPython.uf2 correto e carregá-lo no dispositivo.

b. É possível criar um programa em MicroPython para ativar a funcionalidade Bluetooth. Um exemplo de código para iniciar o Bluetooth pode ser o seguinte:
```
import bluetooth
bt = bluetooth.BLE()
```
c. No dispositivo móvel,precisa ativar o Bluetooth e pesquise por dispositivos disponíveis. Você deve ver o Raspberry Pi Pico W na lista de dispositivos detectados.

d. Precisa se conectar ao Raspberry Pi Pico W a partir do dispositivo móvel e inicie a comunicação via Bluetooth.

**2. Configuração do Wi-Fi**:

a. No Raspberry Pi Pico W, precisa criar um programa em MicroPython para configurar a conexão Wi-Fi. Por exemplo:
```
import network ssid = 'RedeArthur'
password = 'Arthur123' 
wlan = network.WLAN(network.STA_IF) 
wlan.active(True) 
wlan.connect(ssid, password)
```
b. O Raspberry Pi Pico W agora deve estar conectado à rede Wi-Fi especificada.

c. Pode usar o módulo usocket para criar um servidor TCP ou HTTP que permite que outros dispositivos na rede se comuniquem com o Raspberry Pi Pico W.

**3. Comunicação em Rede**:

a. A partir de um computador ou outro dispositivo na mesma rede Wi-Fi, pode se comunicar com o Raspberry Pi Pico W usando o endereço IP atribuído a ele.

b. Pode usar protocolos como HTTP, MQTT, SSH, ou qualquer protocolo que atenda às necessidades para transmitir dados entre o Raspberry Pi Pico W e outros sistemas na rede.



