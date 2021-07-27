# Projeto de uma Fonte de Tensão ajustável entre 3V a 12V com capacidade de 100mA
Projeto de uma Fonte de Tensão ajustável entre 3V a 12V com capacidade de 100mA. A fonte possui uma Tensão RMS de 127V, com pico aproximado para 180V (arredondamos de um pico de 179.6V para um valor inteiro de 180V).


## Alunos:
Bruno Mitsuo Homma [github: brunohomma](https://github.com/brunohomma)

Rodrigo Valim Maciel [github: rvalimaciel](https://github.com/rvalimaciel)

Vitor Laperriere de Faria [github: vitorlape](https://github.com/vitorlape)

## Instruções:

## Escolha dos componentes:
| Quantidade | Componentes                 | Valor R$ |
|------------|-----------------------------|----------|
| 1          | Transformador 24v 200mA     | [R$27,99](https://tinyurl.com/transformador24v) |
| 4          | Diodo 1N4148                | [R$0,10 x 4 = R$0,40](https://tinyurl.com/vd29hv2v) |
| 3          | Resistores (1k, 1k, 2.2k)| [R$0,14 x 3 = R$0,42](https://tinyurl.com/resistor1k) |
| 1          | Capacitor Eletrolítico 470uF| [R$0,25](https://tinyurl.com/xkf6jmpc) |
| 1          | Potenciômetro 5k            | [R$2,70](https://tinyurl.com/25ct25jr) |
| 1          | Diodo Zenner                | [R$0,19](https://tinyurl.com/diodozener13v) |
| 1          | LED                         | [R$0,23](https://tinyurl.com/ledazul5mm) |
| 1          | Transistor bc337            | [R$0,20](https://tinyurl.com/transistorbc337) |
| 1          | Fusível 0.2A                | [R$0,60](https://tinyurl.com/65jvr5db) |
| **Total**  |                             |  R$32,98    |

## Os componentes

* **Transformador**: Esse componente tem a funcionalidade de converter os 180V de pico para 24V de pico por meio da relação e proporção de espiras em cada um dos dois lados.

* **Ponte de diodo**: Esse arranjo de diodos tem a funcionalidade de remover a parte negativa da senoide fornecida na entrada do circuito, assim o sentido da corrente fica apenas em uma direção.

* **Resistores**: Os resistores têm a função de limitar a corrente no circuito.

* **Capacitor**: O capacitor tem a função de suprir a corrente no circuito quando a mesma estiver descendente. Assim a corrente fica mais contínua e estável.

* **Potenciômetro**: O Potenciômetro é um resistor variável que controla a tensão na base do transistor.

* **Diodo Zener**: O diodo zener limita o valor máximo de tensão para a base do transistor. No caso, a tensão máxima escolhida é de 13V, pois o transistor tem um consumo de tensão de 0.7V, e para conseguirmos atingir o limite superior de 12V de tensão na saída da fonte, é necessário escolher um valor superior a 12 + 0,7.

* **LED**: O diodo emissor de luz (LED) informa que está tendo fluxo de corrente e assim o a fonte está ligada.

* **Transistor**: O transistor nesse circuito funciona como um regulador de tensão. Para que o transistor esteja ligado, é necessário que tenha uma diferença de potencial de 0,7V  entre a base e o emissor. Dessa maneira a tensão na base serve de referência para controlar a tensão máxima no emissor, que é a saída do circuito

* **Fusível**: O fusível é usado para proteger o circuito de picos de corrente, caso ultrapasse a corrente predeterminada, um filamento interno se rompe.

## Imagem do circuito
<img src="./Imagens/circuito falstad.png">

## Link do circuito no Falstad:
<a href="https://tinyurl.com/ygy8f4wm" target="_blank">Clique aqui</a> para acessar o nosso circuito construido no Falstad.

## Fórmulas utilizadas

### Cálculo da relação de transformação
<img src="https://render.githubusercontent.com/render/math?math=r_{t} = \frac{V_{s}}{V_{p}}"> (razão da transformação)

Precisamos converter de 180V para 24V, então a razão deve ser:

<img src="https://render.githubusercontent.com/render/math?math=V_{p} = 180V">
<img src="https://render.githubusercontent.com/render/math?math=V_{s} = 24V">

<img src="https://render.githubusercontent.com/render/math?math=\frac{24}{180} = 0.133...">

### Cálculo da Tensão (Antes/Depois) da Ponte de Diodo

Utilizando um diodo feito de sílicio (a mais utilizado comercialmente), a tensão seria consumida em 0.7V. A corrente transita por dois diodos, então a fórmula para calcular a tensão depois da ponte será:

<img src="https://render.githubusercontent.com/render/math?math=V_{depois} = V_{antes} - 2V_{d}">

A tensão será, portanto:

<img src="https://render.githubusercontent.com/render/math?math=24 - 2 \cdot 0.7 = 22.6V">

### Cálculo do Capacitor

Vamos utilizar o ripple de 10%, desta maneira podemos utilizar a fórmula simplificada de Calcular o Ripple de até 20%. Segue a fórmula:

<img src="https://render.githubusercontent.com/render/math?math=V_{ripple} = \frac{V_{s}}{2f \cdot C \cdot R_{eq}}">

Sabemos que a corrente do circuito pode ser definida por:

<img src="https://render.githubusercontent.com/render/math?math=i = \frac{V_{s}}{R_{eq}}">

Então, o Ripple pode ser escrito como:

<img src="https://render.githubusercontent.com/render/math?math=V_{ripple} = \frac{i}{2f \cdot C}">

E a corrente total pode ser calculada por:

<img src="https://render.githubusercontent.com/render/math?math=i = i_{carga} %2b i_{RZener} %2b i_{LED}">

Para calcular cada corrente individualmente:

<img src="https://render.githubusercontent.com/render/math?math=i_{carga} = \frac{V_{zener} - V_{be}}{120}">
<img src="https://render.githubusercontent.com/render/math?math=i_{RZener} = \frac{V_{medio} - V_{zener}}{1000}">
<img src="https://render.githubusercontent.com/render/math?math=i_{LED} = \frac{V_{medio}-1.8}{1000}">

A corrente do resistor do zener é equivalente a soma das correntes do potenciômetro, da base do transistor e do zener em si:

<img src="https://render.githubusercontent.com/render/math?math=i_{RZener} = i_{pot} %2b i_{B} %2b i_{zener}">

Podemos encontrar o ripple de 10% fazendo o seguinte cálculo:

<img src="https://render.githubusercontent.com/render/math?math=V_{ripple} = 0.1 \cdot V_{s}">

Logo, a Capacitância pode ser calculada por:

<img src="https://render.githubusercontent.com/render/math?math=C = \frac{i}{2f \cdot V_{ripple}}">

Fazendo os cálculos:

<img src="https://render.githubusercontent.com/render/math?math=V_{ripple} = 0.1 \cdot 22.6 = 2.26">
<img src="https://render.githubusercontent.com/render/math?math=V_{media} = V_{s} - \frac{2.26}{2}">
<img src="https://render.githubusercontent.com/render/math?math=i_{carga} = \frac{13 - 0.7}{120} = 0.1025">
<img src="https://render.githubusercontent.com/render/math?math=i_{Rzener} = \frac{21.47 - 13}{1000} \approx 0.0085">
<img src="https://render.githubusercontent.com/render/math?math=i_{LED} = \frac{21.47 - 1.8}{1000} \approx 0.0197">
<img src="https://render.githubusercontent.com/render/math?math=i = 0.1025 %2b 0.0085 %2b 0.0197 \approx 0.1307">
<img src="https://render.githubusercontent.com/render/math?math=C = \frac{0.1307}{2 \cdot 60 \cdot 2.26} \cdot 10^{6} \approx 481.93">

## Imagem esquemático da PCB
<img src="./Imagens/esquematico pcb.jpg">

## Imagem PCB no programa Proteus
<img src="./Imagens/esquematico proteus.jpg">

## Modelagem 3D da Fonte Ajustável 12V

<img src="./Imagens/placa proteus.jpg">

![modelagem-3d-fonte-ajustavel](./Videos/placa3d.gif)

## Vídeo de Explicação da Fonte
Vídeo disponível no [Drive do Bruno Homma](https://drive.google.com/file/d/1EmnFBPCx9rpqXM2GddKcgBpviJb3DgZ1/view?usp=sharing).

