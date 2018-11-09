1. Considere um MSP430 sendo usado para leituras analógicas. O Raspberry Pi está conectado a ele via UART. O MSP430 foi programado para converter e enviar dados de 10 bits a cada 10 ms. Escreva o código para o Raspberry Pi receber estes dados, e cada 1 segundo apresentar no terminal a média das últimas 100 amostras.

2. Considere um MSP430 sendo usado para leituras analógicas. O Raspberry Pi está conectado a ele via SPI, e é o mestre. O MSP430 foi programado para funcionar da seguinte forma:

- O MSP430 recebe o byte `0x55` e envia o byte `0xAA`, o que indica o começo de conversão. 
- 100us depois, o MSP430 recebe os bytes `0x01` e `0x02`, e envia o byte menos significativo e o mais significativo da conversão de 10 bits, nesta ordem.
 
Escreva o código para o Raspberry Pi executar este protocolo, de forma a obter conversões a cada 10 ms. A cada 1 segundo ele deve apresentar no terminal a média das últimas 100 amostras.

cahr d[2];
while(1){
  soma = 0;
    for(i=0; i<100;i++){
      d[0] = 0x55;
      write(12cfd, d, 1);  
      uleep(100);
      read(12cfd, d, d);
      soma += d[0] + (d[1]<<8);
      usleep(10000);
}
soma +=50;
soma /= 100;
printf(" media = %d /n, soma);


i2c = HalfDuplex
