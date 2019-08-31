<h1> PARSEC 3.0 - Swaptions </h1>

Aplicação desenvolvida pela Universidade de Princenton que calcula o preço de um portfólio de Swaptions. Para mais informações, é possível consultar artigos como:\
    
- https://parsec.cs.princeton.edu/download/tutorial/3.0/parsec-tutorial.pdf
- http://arco.e.ac.upc.edu/wiki/images/8/8a/Seminar_Parsec3.pdf

<h2> Perfilamento do Código </h2>
No projeto_1, foi analisado o perfilamento dessa aplicação utilizando o Gprof. Assim, foi modificado o Makefile do projeto adicionando a diretiva *-pg*. Também, para a execução dos arquivos, foi chamado a entrada *native* disponível no próprio projeto.

Para executar o projeto, basta executar o comando *make* no diretório *src*. Após isso, pode-se chamar o *./swaption* passando os parâmetros necessários. Os parâmetros são:

- **ns:**​ referente ao número de swaptions que o algoritmo irá gerar aleatoriamente.
- **sm:**​ número de simulações que serão executados para cada swaption gerado.
- **nt:**​ número de threads que serão usados. Esse parâmetro é opcional e por padrão é usado apenas 1 thread.
- **sd:** semente de geração de números aleatórios usados. Caso não seja informado, o Swaptions pega um número padrão dele.

Para rodar o perfilamento segue a sequência de comandos:

    # Permite a compilação habilitando a paralelização usando pthreads.
    make version=pthreads 

    # Chamada para 10 swaptions, 10000 simulações e 1 thread.
    ./swaptions -ns 10 -sm 10000 -nt 1

    # Gprof
    gprof swaptions gmon.out > resultado.txt
    cat resultado.txt
