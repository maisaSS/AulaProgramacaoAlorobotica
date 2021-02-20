
/*
  Ping))) Sensor

  Este esboço lê um PING))) telêmetro ultrassônico e retorna a distância
  para o objeto mais próximo do alcance. Para fazer isso, ele envia um pulso ao sensor para
  iniciar uma leitura e ouvir um pulso retornar. O comprimento do
  o pulso de retorno é proporcional à distância do objeto ao sensor.

  criado em 3 de novembro de 2008
  por David A. Mellis
  modificado em 30 de agosto de 2011
  por Tom Igoe

  Este código de exemplo está no domínio público.

  http://www.arduino.cc/en/Tutorial/Ping
*/


// esse valor não muda, declaramos as portas dos equipamentos:
const int pingPin = 7;
const int motorD = 2; 
const int motorE = 8;
const int LedVerde = 13;
const int LedVermelha = 11;


void setup(){
  
  //definimos a "função" da porta;
  pinMode(motorE, OUTPUT);
  pinMode(motorD, OUTPUT);
  pinMode(LedVermelha, OUTPUT);
  pinMode(LedVerde, OUTPUT);
 
  
  // inicializando a comunicação serial;
  Serial.begin(9600);
}



void loop(){
  long duration, DistanciaCM;
  
  // Calibragem do sensor e calculando a distância
  pinMode(pingPin, OUTPUT);
  digitalWrite(pingPin, LOW);
  delayMicroseconds(2);
  digitalWrite(pingPin, HIGH);
  delayMicroseconds(5);
  digitalWrite(pingPin, LOW);
  pinMode(pingPin, INPUT);
  duration = pulseIn(pingPin, HIGH);


  // convertendo tempo em distância
  // A velocidade do som é de 340 m / s ou 29 microssegundos por centímetro.
  // O ping viaja para trás e para trás, para encontrar a distância do objeto que
  // tire metade da distância percorrida.
  DistanciaCM = duration/ 29 / 2;

  //imprimindo no monitor serial:
  Serial.print(DistanciaCM);
  Serial.print("cm");
  Serial.println();
  
  
  //definindo a condição inicial do nosso rob:
  digitalWrite(LedVermelha, LOW);//deslogando o led
  digitalWrite(LedVerde, LOW); //desligando o led



  //criando a condição " SE o valor da distancia(distanciaCM) for maior que 20 cm então ACENDA O LED VERDE e LIGUE O MOTOR."
  if (DistanciaCM > 20) {
    digitalWrite(motorE, HIGH);
    digitalWrite(motorD, HIGH);
    digitalWrite(LedVerde, HIGH);
    Serial.println("verde aceso");
    Serial.println("motor girando");
    delay(500);
    }
    //Se não for, ou seja, se o valor da distancia(distanciaCM) não for maior do que 20cm então ACENDA O LED VERMELHO e DESLIGUE O MOTOR.
  else{
   Serial.println("Vermelho aceso");
   Serial.println("Motor desligado");
   digitalWrite(LedVermelha, HIGH);
   digitalWrite(motorE, LOW);
   digitalWrite(motorD, LOW);
    delay(500);
  }
  }
