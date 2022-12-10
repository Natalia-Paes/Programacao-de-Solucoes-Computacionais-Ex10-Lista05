# Programacao-de-Solucoes-Computacionais-Ex10-Lista05
Jogo de Craps. Faça um programa de implemente um jogo de Craps.
import java.util.ArrayList;
import java.util.Scanner;

public class Ex10 {
    public static void main(String[] args) throws Exception {
        Scanner sc = new Scanner(System.in);
        ArrayList<Integer> historicoPontos = new ArrayList<Integer>();

        int rodadas = 1;

        while (true) {
            System.out.println("------------------------");
            System.out.println("Rodada " + rodadas);
            System.out.println("------------------------");
            System.out.println("Girando dados...");
            int pontos = giraDados();

            if ((rodadas == 1) && (pontos == 7 || pontos == 11)) {
                System.out.println("Voçê ganhou, parabéns!!!");
                break;
            } else if ((rodadas == 1) && (pontos == 2 || pontos == 3 || pontos == 12)) {
                System.out.println("CRAPS!!!!");
                System.out.println("Voçê perdeu!!");
                break;
            }

            historicoPontos.add(pontos);

            if ((rodadas != 1) && (pontos == historicoPontos.get(0))) {
                System.out.println("Voçê ganhou, tirou " + pontos + " pontos" + " 2x");
                break;
            }

            if ((rodadas != 1) && (pontos == 7)) {
                System.out.println("Voçê perdeu!!!");
                break;
            }

            System.out.println("Deseja girar novamente ? [S/N] ");
            String resp = sc.next();

            if (resp.equalsIgnoreCase("N")) {
                break;
            }
            rodadas++;
            sc.close();
        }
    }

    public static int giraDados() {
        int dado1 = randomDados();
        int dado2 = randomDados();
        System.out.println("Dado 1: " + dado1);
        System.out.println("Dado 2: " + dado2);
        int pontos = somaDados(dado1, dado2);
        System.out.println("A soma dos dados foi " + pontos);
        return pontos;
    }

    public static int somaDados(int dado1, int dado2) {
        return (dado1 + dado2);
    }

    public static int randomDados() {
        return (int) Math.floor(Math.random() * (7 - 1) + 1);
    }
}
