package controller;

import java.util.Random;
import java.util.Scanner;

public class ExercicioMatrizes {

	static final byte[][] REGRAS_DO_JOGO = {

			{ 0, -1, 1, 1, -1 }, 
			{ 1, 0, -1, -1, 1 }, 
			{ -1, 1, 0, 1, -1 }, 
			{ -1, 1, -1, 0, 1 }, 
			{ 1, -1, 1, -1, 0 } 
			
	};

	static final String[] opcoes = { "Pedra", "Papel", "Tesoura", "Lagarto", "Spock" };

	static final byte GANHOU = 1;
	static final byte EMPATOU = 0;
	static final byte PERDEU = -1;

	static Random random = new Random();
	static Scanner scanner = new Scanner(System.in);

	static int opcaoComputador() {

		return random.nextInt(REGRAS_DO_JOGO.length);
	}

	static int opcaoJogador() {

		System.out.println("\nEscolha sua jogada: ");
		System.out.println("\n[0] Pedra");
		System.out.println("[1] Papel");
		System.out.println("[2] Tesoura");
		System.out.println("[3] Lagarto");
		System.out.println("[4] Spock");
		System.out.print("\n Qual sua jogada desejada? ");
		byte jogada = scanner.nextByte();

		return jogada;
	}

	static void jogar() {

		int jogadaPlayer = opcaoJogador();
		int jogadaComputador = opcaoComputador();

		System.out.println("\nJogador 1 escolheu: " + opcoes[jogadaPlayer]);
		System.out.println("Computador escolheu: " + opcoes[jogadaComputador]);
		System.out.println("");

		if (REGRAS_DO_JOGO[jogadaPlayer][jogadaComputador] == GANHOU) {

			System.out.println("Parabéns, você venceu!");

		} else if(REGRAS_DO_JOGO[jogadaPlayer][jogadaComputador] == EMPATOU) {
			
			System.out.println("Houve um empate!");

		} else {
						
			System.out.println("O computador venceu!");
			
		}

	}

	static void menu() {

		System.out.println("");
		System.out.println("---MENU---");
		System.out.println("Jogo: Pedra, Papel, Tesoura, Lagarto e Spock");
		System.out.println("");

		System.out.println("[0] Sair");
		System.out.println("[1] Jogar");
		System.out.println("");
		System.out.print("Selecione a opção desejada: ");
		System.out.print("");
		int opcao = scanner.nextInt();

		switch (opcao) {

		case 0:
			System.exit(0);
			break;

		case 1:
			jogar();
			menu();
			break;

		default:
			System.err.println("Opção inválida, tente novamente!");
			System.out.println("");
			menu();
			break;

		}

	}

	public static void main(String[] args) {

		menu();

	}

}
