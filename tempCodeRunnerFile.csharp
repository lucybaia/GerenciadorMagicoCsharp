using System;
using System.Collections.Generic;
using System.Linq;

// 1. Classe para representar um Item Mágico
public class ItemMagico
{
    // Propriedades do item
    public string Nome { get; set; }
    public string Tipo { get; set; } // Ex: Arma, Cura, Amuleto, Chave
    public string Efeito { get; set; }

    // Construtor para facilitar a criação de novos itens
    public ItemMagico(string nome, string tipo, string efeito)
    {
        Nome = nome;
        Tipo = tipo;
        Efeito = efeito;
    }

    // Método para exibir o item no console
    public void ExibirDetalhes()
    {
        Console.WriteLine($"  - Nome: {Nome}");
        Console.WriteLine($"    Tipo: {Tipo}");
        Console.WriteLine($"    Efeito: {Efeito}");
    }
}

// 2. Classe principal do programa
public class Program
{
    // A lista para armazenar o inventário
    private static List<ItemMagico> Inventario = new List<ItemMagico>();

    public static void Main(string[] args)
    {
        // Inicializa o inventário com alguns itens
        Inventario.Add(new ItemMagico("Cajado Estelar", "Arma", "Aumenta o poder mágico em 20%."));
        Inventario.Add(new ItemMagico("Poção de Cura Rápida", "Cura", "Restaura todos os Pontos de Vida (HP)."));

        Console.WriteLine("=======================================");
        Console.WriteLine("  INVENTÁRIO MÁGICO DA MAHOU SHOUJO");
        Console.WriteLine("=======================================");

        bool rodando = true;
        while (rodando)
        {
            ExibirMenu();
            string escolha = Console.ReadLine();
            Console.WriteLine();

            switch (escolha)
            {
                case "1":
                    VerInventario();
                    break;
                case "2":
                    ColetarNovoItem();
                    break;
                case "3":
                    UsarItem();
                    break;
                case "4":
                    rodando = false;
                    Console.WriteLine("A Garota Mágica encerrou a sessão. Até a próxima aventura!");
                    break;
                default:
                    Console.WriteLine("Escolha inválida. Tente novamente.");
                    break;
            }
            Console.WriteLine("---------------------------------------");
        }
    }

    // 3. Método para exibir o menu de opções
    private static void ExibirMenu()
    {
        Console.WriteLine("\nEscolha uma opção:");
        Console.WriteLine("1. Ver Inventário");
        Console.WriteLine("2. Coletar Novo Item");
        Console.WriteLine("3. Usar Item");
        Console.WriteLine("4. Sair");
        Console.Write("Opção: ");
    }

    // 4. Lógica para visualizar o inventário
    private static void VerInventario()
    {
        if (Inventario.Any())
        {
            Console.WriteLine("--- Conteúdo do Inventário ---");
            foreach (var item in Inventario)
            {
                item.ExibirDetalhes();
                Console.WriteLine();
            }
            Console.WriteLine($"Total de itens: {Inventario.Count}");
        }
        else
        {
            Console.WriteLine("O inventário está vazio. Hora de ir em busca de tesouros!");
        }
    }

    // 5. Lógica para adicionar um novo item
    private static void ColetarNovoItem()
    {
        Console.WriteLine("--- Coletar Novo Item ---");
        Console.Write("Nome do Item: ");
        string nome = Console.ReadLine();

        Console.Write("Tipo do Item (ex: Arma, Cura, Amuleto): ");
        string tipo = Console.ReadLine();

        Console.Write("Efeito do Item: ");
        string efeito = Console.ReadLine();

        // Cria o novo objeto e adiciona à lista
        ItemMagico novoItem = new ItemMagico(nome, tipo, efeito);
        Inventario.Add(novoItem);

        Console.WriteLine($"\n[SUCESSO] O item '{nome}' foi adicionado ao inventário!");
    }

    // 6. Lógica para usar (remover) um item
    private static void UsarItem()
    {
        Console.WriteLine("--- Usar Item ---");
        Console.Write("Digite o NOME do item que deseja usar: ");
        string nomeParaUsar = Console.ReadLine();

        // Procura o item no inventário (usando LINQ para simplificar)
        ItemMagico itemEncontrado = Inventario.FirstOrDefault(i => i.Nome.Equals(nomeParaUsar, StringComparison.OrdinalIgnoreCase));

        if (itemEncontrado != null)
        {
            // Remove o item da lista
            Inventario.Remove(itemEncontrado);

            // Simula o uso
            Console.WriteLine($"\nA Garota Mágica usou '{itemEncontrado.Nome}'!");
            Console.WriteLine($"Efeito ativado: {itemEncontrado.Efeito}");
            
            // Lógica simples extra baseada no tipo
            if (itemEncontrado.Tipo.Equals("Cura", StringComparison.OrdinalIgnoreCase))
            {
                Console.WriteLine("... Sentindo-se totalmente revigorada!");
            }
            else if (itemEncontrado.Tipo.Equals("Arma", StringComparison.OrdinalIgnoreCase))
            {
                Console.WriteLine("... O inimigo recebeu um ataque devastador!");
            }
        }
        else
        {
            Console.WriteLine($"\n[ERRO] O item '{nomeParaUsar}' não foi encontrado no inventário.");
        }
    }
}