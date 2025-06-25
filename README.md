ALUNOS: Luan SIlva e Danilo Cazuzzi
TURMA: Manhã


let prompt = require('prompt-sync')();

//Pedir a senha (máximo 3 tentativas)
let senhaCorreta = "SENAI123";
let tentativas = 0;
let senha;

while (tentativas < 3) {
    senha = prompt("Digite a senha: ");
    if (senha === senhaCorreta) {
        console.log("Senha correta! Acesso liberado.\n");
        break;
    } else {
        tentativas++;
        console.log("Senha errada. Você ainda tem " + (3 - tentativas) + " tentativa(s).");
    }
}

if (tentativas === 3) {
    console.log("Você errou 3 vezes. Acesso negado.");
    process.exit(); //Encerra o programa
}

//Mostrar o menu até o usuário escolher sair
let opcao;

do {
    console.log("=== MENU ===");
    console.log("1 - Tabuada de Soma");
    console.log("2 - Tabuada de Subtração");
    console.log("3 - Tabuada de Multiplicação");
    console.log("4 - Tabuada de Divisão");
    console.log("5 - Fatorial");
    console.log("6 - Sair");
    opcao = prompt("Escolha uma opção (1 a 6): ");

    if (opcao === '6') {
        console.log("Programa encerrado");
        break;
    }

    let numero = prompt("Digite um número: ");
    while (isNaN(numero)) {
        console.log("Digite apenas números!");
        numero = prompt("Digite um número: ");
    }
    numero = parseInt(numero);

    console.log("Resultado:");

    //Executa a opção escolhida
    if (opcao === '1') {
        for (let i = 0; i <= 10; i++) {
            console.log(numero + " + " + i + " = " + (numero + i));
        }
    } else if (opcao === '2') {
        for (let i = 0; i <= 10; i++) {
            console.log(numero + " - " + i + " = " + (numero - i));
        }
    } else if (opcao === '3') {
        for (let i = 0; i <= 10; i++) {
            console.log(numero + " x " + i + " = " + (numero * i));
        }
    } else if (opcao === '4') {
        for (let i = 1; i <= 10; i++) {
            console.log(numero + " ÷ " + i + " = " + (numero / i).toFixed(2));
        }
    } else if (opcao === '5') {
        let fatorial = 1;
        for (let i = 1; i <= numero; i++) {
            fatorial = fatorial * i;
        }
        console.log(numero + "! = " + fatorial);
    } else {
        console.log("Opção inválida. Tente de novo.");
    }

    console.log(""); // finaliza o programa 

} while (opcao !== '6');
