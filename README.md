#include <bits/stdc++.h>
using namespace std;

int main() {

/*EXPLICAÇÃO DAS VARIAVEIS

Declaramos elas como tipo int (inteiro), para que a operação utilizando mod (%) ou o resto da divisão, fosse possivel.
Colocamos os nomes das variaveis da seguinte maneira:

cpf = valor que será inserido pelo usuário;
cpfd10 = é atribuida o valor da variavel cpf, onde utilizamos para fazer o calculo de descobrir o primeiro digito verificador
e também é utilizada para que o valor original do cpf não seja alterado/perdido;
d1 à d11 = digitos que seriam equivalente a posiçao do numero digitado, exemplo: 987654321-98, o d1 seria equivalente ao numero que esta na primeira
posiçao da esquerda para a direita, ou seja d1 = 9, d2 = 8, e assim sucessivamente;
d10am = para descobrirmos o segundo digito verificador do cpf, atribuimos o valor de d10 para a variavel d10am = d10 ArMazenado.
*/

	int cpf, cpfd10, d1, d2, d3, d4, d5, d6, d7, d8, d9, d10, d11, d10am;
	
    cout << "Descubra os dois digitos verificadores(dois ultimos digitos do CPF)! \nColoque os primeiros 9 digitos do CPF: ";
	cin >> cpf;

	cpfd10 = cpf; // Aqui é a atribuição do valor da variavel cpf para a cpfd10.

	if(cpfd10 >= 1 && cpfd10 < 1000000000) { // Aqui é uma verificção para saber se o numero digitado é permitido ou seja, maior que 1 e, menor que 1 bilhão.

//DESCOBRINDO O PRIMEIRO DIGITO.

		d9 = cpfd10 % 10 * 2;           // Se passar pela verificação, o numero digitado pelo o usuario, começara a ser dividido por digitos;
		cpfd10 = cpfd10 / 10;           // Neste caso, a variavel d9, está sendo atrbuida pelo valor do cpfd10 % 10 * 2;
                                        // Exemplo : cpfd10 = 123456789; o d9 é igual à: 123456789 % 10 = 9; e o * 2 é atribuida ao valor para que conseguimos
		d8 = cpfd10 % 10 * 3;           // fazer a conta da descoberta dos ultimos digitos, este valor é retirado e uma tabela, cada posição tem que ser
		cpfd10 = cpfd10 / 10;           // multiplicada por um valor especifico, mas o processo é o mesmo.
                                        // Depois deste processo, o valor da variavel é atualizada, ou seja, agora ela vale 12345678.
		d7 = cpfd10 % 10 * 4;           // Este processo acontece até chegar no primeiro digíto da esquerda para direita ou o d1;
		cpfd10 = cpfd10 / 10;

		d6 = cpfd10 % 10 * 5;
		cpfd10 = cpfd10 / 10;

		d5 = cpfd10 % 10 * 6;
		cpfd10 = cpfd10 / 10;

		d4 = cpfd10 % 10 * 7;
		cpfd10 = cpfd10 / 10;

		d3 = cpfd10 % 10 * 8;
		cpfd10 = cpfd10 / 10;

		d2 = cpfd10 % 10 * 9;
		cpfd10 = cpfd10 / 10;

		d1 = cpfd10 % 10 * 10;
		cpfd10 = cpfd10 / 10;
		
		// Nesta etapa, o valor do d10 vai ser igual a soma de todos os digitos, % 11, mas NÃO é o valor final;
		d10 = (d1 + d2 + d3 + d4 + d5 + d6 + d7 + d8 + d9) % 11; 

		if(d10 < 2) { // Aqui é passada uma verifição para ver se o d10 ele é menor que 2, se caso for, o d10 passará a valer 0.
	
			d10 = 0;

		} else { // Caso contrário o d10 = 11 - d10.

			d10 = 11 - d10;

		}

		d10am = d10; // Aqui o valor de d10 esta sendo armazenado para o d10am.

//DESCOBRINDO O SEGUNDO DIGITO

		d10am = d10am * 2; // E aqui acontece o mesmo processo para descobrir o d10, porém, agora para descobrir o d11, utilizando o valor do d10 no calcúlo.

		d9 = (d9 / 2) * 3;

		d8 = (d8 / 3) * 4;

		d7 = (d7 / 4) * 5;

		d6 = (d6 / 5) * 6;

		d5 = (d5 / 6) * 7;

		d4 = (d4 / 7) * 8;

		d3 = (d3 / 8) * 9;

		d2 = (d2 / 9) * 10;

		d1 = (d1 / 10) * 11;

		d11 = (d1 + d2 + d3 + d4 + d5 + d6 + d7 + d8 + d9 + d10am) % 11; // Então o valor de d11 é igual a soma de todos os digitos % 11.

		if(d11 < 2) { // Se o valor de d11 for menor que 2, ele começa a valer 0.

			d11 = 0;

		} else { // Caso contrário, d11 = 11 - d11.

			d11 = 11 - d11;

		}

// CÓDIGO CASO NÃO POSSUIR 9 DIGITOS MAIOR QUE 0


// Aqui é passado uma verificação para saber se o numero possui apenas 8 digitos, se caso sim, ele imprime o numero de cpf, pórem, com 1 zero na frente.
// E isso acontece nos demais casos, se possuir 7 digitos, dois zeros; 6 digitos, 3 zeros, e assim vai sucessivamente até ser apenas 1 digito = 8 zeros;
		if(cpf < 100000000 && cpf > 9999999) {
			
			cout << "\nOs digítos verificadores foram encontrados!\nO CPF é: 0" << cpf << "-" << d10 << d11;    
			
		} else if(cpf < 10000000 && cpf > 999999) {

			cout << "\nOs digítos verificadores foram encontrados!\nO CPF é: 00" << cpf << "-" << d10 << d11;

		} else if(cpf < 1000000 && cpf > 99999) {

			cout << "\nOs digítos verificadores foram encontrados!\nO CPF é: 000" << cpf << "-" << d10 << d11;

		} else if(cpf < 100000 && cpf > 9999) {

			cout << "\nOs digítos verificadores foram encontrados!\nO CPF é: 0000" << cpf << "-" << d10 << d11;

		} else if(cpf < 10000 && cpf > 999) {

			cout << "\nOs digítos verificadores foram encontrados!\nO CPF é: 00000" << cpf << "-" << d10 << d11;

		} else if(cpf < 1000 && cpf > 99) {

			cout << "\nOs digítos verificadores foram encontrados!\nO CPF é: 000000" << cpf << "-" << d10 << d11;

		} else if(cpf < 100 && cpf > 9) {

			cout << "\nOs digítos verificadores foram encontrados!\nO CPF é: 0000000" << cpf << "-" << d10 << d11;

		} else if(cpf < 10) {

			cout << "\nOs digítos verificadores foram encontrados!\nO CPF é: 00000000" << cpf << "-" << d10 << d11;

		} else {    // Se possuir 9 digítos, ele irá imprimir normal, com os dois digitos verificadores

			cout <<"\nOs digítos verificadores foram encontrados!\nO CPF é: "<< cpf << "-" << d10 << d11;

		}


	} else { // Caso o numero enviado pelo usuario não cumprir as exigencias, o cpf é invalido.

		cout << "CPF INVÁLIDO";

	}

}
