
### O que é ?

É um software open source que possui diversas utilizações como: Webserver, proxy reverso, caching, load balancer, media streaming, além de proxy para serviços de e-mail.

### Principais características

- Um dos servidores web mais potentes do mercado
- Performa mais que o apache
- consegue suportar alto volume de conexões simultaneas
- Utiliza baixa memória e suporta alta concorrência
- Normalmente é mais utilizado como webserver e proxy reverso
- Mais de 50% dos sites mais acessados do mundo utilizam nginx 
- Possui suporte aos recursos web mais modernos como Websockets, HTTP2, streaming de vídeos, etc. 

### Como funciona ?


NGINX MASTER PROCESS ->  (VAI ALOCAR SEU ESPAÇO NA MEMÓRIA)
Diferente do Apache que gera um processo para cada conexão, o NGINX gera apenas um processo principal que trabalha com diversos Workers

Workers -> Quem vai processar as requisições
Para cada core da máquina o nginx gerará um worker

- Assíncrona 
- Event Driven -> Abre um canal de comunicação e fica escutando um evento
- Não bloqueante
- 1 Worker por core
- Multiplexing ->  Um único processo, você consegue abrir mais de um canal. 



### Proxy Reverso

Proxy reverso é um serviço intermediário que recebe as requisições de diversos clients, as processa e as encaminha para o serviço correspondete. 


### Load Balancing 
HealthCheck -> 
-  Passivo -> Caso servidor A falhe, o nginx redirecionará a requisição para o servidor B e etc
- Ativo -> De tempos em tempos (configurado pelo usuário) o nginx verifica a saúde dos servidores, e caso um destes esteja com problemas, imediamente altera o servidor ( apenas nginx plus)

### configuraçoes de upstream

##### least_conn; 
- Com o método least connections, o load balancer compara o atual número ativos de conexões em cada servidor e envia a requisição para o que tem menos. 
##### weight;
- Método para configurar qual servidor no upstream tem mais peso

`e.g upstream example {
  server example:80 weight=2;
  server example2:80;
}`

