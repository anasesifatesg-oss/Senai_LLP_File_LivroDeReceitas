import java.io.FileWriter;
import java.io.IOException;
import java.io.PrintWriter;
import java.util.ArrayList;
import java.util.Scanner;

public class LivroDeReceitas {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Receita: ");
        String nomeReceita = sc.nextLine();

        ArrayList<String> ingredientes = new ArrayList<>();
        ArrayList<String> quantidades = new ArrayList<>();
        ArrayList<String> passos = new ArrayList<>();

        System.out.println("\n=== INGREDIENTES ===");

        while (true) {
            System.out.print("Ingrediente: ");
            String ingrediente = sc.nextLine();

            if (ingrediente.isBlank()) {
                break;
            }

            System.out.print("Quantidade: ");
            String quantidade = sc.nextLine();

            ingredientes.add(ingrediente);
            quantidades.add(quantidade);
        }

        System.out.println("\n=== INSTRUÇÕES ===");

        int numeroPasso = 1;

        while (true) {
            System.out.print("Passo " + numeroPasso + ": ");
            String passo = sc.nextLine();

            if (passo.isBlank()) {
                break;
            }

            passos.add(passo);
            numeroPasso++;
        }

        System.out.println("\n==============================");
        System.out.println(nomeReceita);
        System.out.println();

        System.out.println("Ingredientes:");

        for (int i = 0; i < ingredientes.size(); i++) {
            System.out.println((i + 1) + ". " +
                    ingredientes.get(i) +
                    " - " +
                    quantidades.get(i));
        }

        System.out.println();
        System.out.println("Modo de Preparo:");

        for (int i = 0; i < passos.size(); i++) {
            System.out.println("Passo " + (i + 1) + ": " + passos.get(i));
        }

        try {
            String nomeArquivo = nomeReceita.replace(" ", "_") + ".txt";

            PrintWriter arquivo = new PrintWriter(
                    new FileWriter(nomeArquivo));

            arquivo.println(nomeReceita);
            arquivo.println();

            arquivo.println("Ingredientes:");

            for (int i = 0; i < ingredientes.size(); i++) {
                arquivo.println((i + 1) + ". " +
                        ingredientes.get(i) +
                        " - " +
                        quantidades.get(i));
            }

            arquivo.println();

            arquivo.println("Modo de Preparo:");

            for (int i = 0; i < passos.size(); i++) {
                arquivo.println("Passo " + (i + 1) +
                        ": " + passos.get(i));
            }

            arquivo.close();

            System.out.println("\nArquivo salvo com sucesso: "
                    + nomeArquivo);

        } catch (IOException e) {
            System.out.println("Erro ao salvar arquivo.");
        }

        sc.close();
    }
}
