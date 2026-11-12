# Player de Músicas com Arduino

Projeto por:

- Bruno Vieira Silva Golçalvez
- Fernando Risseto de Amorim
- Raphael Rodrigues de Oliveira

Ideia do projeto 

A ideia do projeto foi montar um pequeno "player" de músicas usando um Arduino UNO. As músicas são tocadas em um buzzer e o nome da música atual aparece em um display LCD 16x2. Com os botões, o usuário navega entre as músicas e escolhe qual quer ouvir.

Objetivos:

- Tocar 5 músicas conhecidas (Pantera cor de rosa, Pac-Man, Subway Surf, Tokyo drift e Tetris) usando apenas um buzzer;
- Mostrar no LCD qual música está selecionada (Musica 4/5 > Pac-Man);
- Permitir a troca de músicas pelos botões;
- Indicar o estado do player com LEDs.

Metodologia
Materiais utilizados

- 1x Arduino UNO
- 1x Protoboard
- 1x Display LCD 16x2 (no físico, com módulo I2C)
- 1x Buzzer 
- 3x Botões 
- 1x LED vermelho
- 1x LED verde
- 1x Potenciômetro
- Resistores
- Jumpers

Passo a passo

1. Simulação no Tinkercad: primeiro montamos todo o circuito no Tinkercad para testar as ligações antes de mexer no físico. Essa parte foi relativamente fácil.
2. Músicas: usamos as melodias do repositório [robsoncouto/arduino-songs](https://github.com/robsoncouto/arduino-songs), que já traz o código pronto (notas e durações) de várias músicas.
3. Programação: juntamos as músicas em um único código e implementamos a lógica dos botões, LEDs e do display.
4. Montagem física: na simulação usamos o LCD 16x2 comum (ligado em vários pinos), mas no projeto físico usamos um LCD com módulo I2C, que usa só dois fios de dados (SDA e SCL) e deixa a montagem bem mais simples.


[Circuito montado no Tinkercad:](https://www.tinkercad.com/things/4BOl5XSJOVI-reprodutordemusicaprojetofei)

Circuito no Tinkercad ( imagem e video em suas respectivas pastas )

Projeto físico montado:

<img src="img/WhatsApp%20Image%202026-11-11%20at%2023.48.25.jpeg" width="300">

Experimentos

Sequência do projeto em funcionamento:

1. Ligando o LCD I2C: o display é conectado à protoboard com apenas 4 fios (VCC, GND, SDA e SCL) e o código é enviado pela Arduino IDE.

   <img src="img/WhatsApp%20Image%202026-11-11%20at%2023.48.26.jpeg" width="300">

2. Selecionando a música: com os botões, o usuário navega pela lista e o LCD mostra o número e o nome da música atual (na foto, Musica 3/5 > Subway Surf).

   <img src="img/WhatsApp%20Image%202026-11-11%20at%2023.49.10.jpeg" width="300">

3. Tocando a música: o buzzer toca a melodia selecionada e os LEDs indicam o estado do player.

Vídeos do projeto funcionando:

- [Vídeo 1](videos/WhatsApp%20Video%202026-11-11%20at%2023.49.25.mp4)
- [Vídeo 2](videos/WhatsApp%20Video%202026-11-11%20at%2023.49.41.mp4)

## Tecnologias utilizadas

- Arduino UNO
- Linguagem C (Arduino IDE)
- Tinkercad (simulação do circuito)
- Biblioteca LiquidCrystal (LCD na simulação)
- Biblioteca LiquidCrystal_I2C (LCD com módulo I2C no físico)
- Função tone() para gerar as notas no buzzer
- GitHub (código e documentação)

## Conclusão

Conseguimos montar um player de músicas funcional com Arduino, que toca as melodias no buzzer e mostra a música atual no LCD.

Para resolver o problema, primeiro validamos o circuito no Tinkercad, depois reaproveitamos as melodias prontas do repositório arduino-songs e focamos na lógica do nosso código. As partes mais trabalhosas foram:

- O LCD: controlar quando limpar a tela (clear()), posicionar o cursor e escrever de novo (setCursor(), print()) sem a tela piscar ou ficar com texto sobrando. Além disso, tivemos que adaptar o código ao passar do LCD comum (simulação) para o LCD com I2C (físico).
- Os loops: fazer a música tocar nota por nota e, ao mesmo tempo, conseguir ler os botões para trocar de música foi a parte mais complicada da lógica.

No fim, o projeto ajudou a entender melhor a comunicação com displays, o uso do I2C e a organização de loops no Arduino.
