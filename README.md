# 1-codigo-pra-estudo-em-rust-e-go-lang-pra-iniciante
# 📚 Estudos de Rust e Go

> **"Estou iniciando o curso de Rust e Go Lang, começando com código simples."**

Este repositório contém dois programas equivalentes escritos em **Rust** e **Go**, com o mesmo objetivo: praticar entrada de dados, operações matemáticas, ordenação e comparações. Cada linha está comentada para fins de estudo.

---

## 🎯 Objetivo do exercício

Criar um programa que:

1. Peça **três números** ao usuário;
2. **Some** os três números;
3. Peça um **divisor**;
4. **Divida** a soma pelo divisor (resultado = média);
5. **Ordene** os três números do maior para o menor;
6. Mostre a **ordem** e se cada número é **maior, menor ou igual** à média.

---

## 📁 Estrutura do repositório

---

## 🦀 Versão em Rust (`rust/main.rs`)

```rust
// Importa o módulo de entrada/saída da biblioteca padrão do Rust.
use std::io;

// Função principal — ponto de entrada do programa.
fn main() {
    // ===== 1. LER OS TRÊS NÚMEROS =====

    // Exibe uma mensagem pedindo o primeiro número.
    println!("Digite o 1º número:");
    // Cria uma String vazia e mutável para guardar a entrada do usuário.
    let mut s1 = String::new();
    // Lê uma linha do teclado e guarda em s1. "unwrap()" encerra o programa se der erro.
    io::stdin().read_line(&mut s1).unwrap();
    // Remove espaços/quebra de linha e converte o texto para f64 (número decimal).
    let n1: f64 = s1.trim().parse().unwrap();

    // Repete o processo para o segundo número.
    println!("Digite o 2º número:");
    let mut s2 = String::new();
    io::stdin().read_line(&mut s2).unwrap();
    let n2: f64 = s2.trim().parse().unwrap();

    // Repete o processo para o terceiro número.
    println!("Digite o 3º número:");
    let mut s3 = String::new();
    io::stdin().read_line(&mut s3).unwrap();
    let n3: f64 = s3.trim().parse().unwrap();

    // ===== 2. SOMAR OS TRÊS NÚMEROS =====

    // Soma os três valores lidos.
    let soma = n1 + n2 + n3;
    // Mostra o resultado da soma.
    println!("Soma = {}", soma);

    // ===== 3. LER O DIVISOR =====

    // Pede ao usuário o número pelo qual a soma será dividida.
    println!("Digite um número para dividir a soma:");
    let mut s4 = String::new();
    io::stdin().read_line(&mut s4).unwrap();
    // Converte o texto digitado para f64.
    let divisor: f64 = s4.trim().parse().unwrap();

    // ===== 4. DIVIDIR E MOSTRAR O RESULTADO =====

    // Calcula a média dividindo a soma pelo divisor.
    let media = soma / divisor;
    // Mostra o resultado da divisão.
    println!("Resultado da divisão (média) = {}", media);

    // ===== 5. GUARDAR OS NÚMEROS EM UM ARRAY E ORDENAR =====

    // Cria um array mutável com os três números.
    let mut numeros = [n1, n2, n3];
    // Ordena do maior para o menor usando uma função de comparação.
    // "partial_cmp" retorna Option; "unwrap" garante que o valor existe.
    numeros.sort_by(|a, b| b.partial_cmp(a).unwrap());

    // ===== 6. MOSTRAR A ORDEM EM RELAÇÃO À MÉDIA =====

    // Cabeçalho da listagem.
    println!("\nOrdem (maior -> menor) em relação à média:");

    // Percorre o array com índice (i) e valor (num).
    for (i, num) in numeros.iter().enumerate() {
        // Compara o número atual com a média.
        if *num > media {
            // Se for maior, imprime a posição e a relação.
            println!("{}º lugar: {} -> MAIOR que a média", i + 1, num);
        } else if *num < media {
            // Se for menor, imprime a posição e a relação.
            println!("{}º lugar: {} -> MENOR que a média", i + 1, num);
        } else {
            // Se for igual, imprime a posição e a relação.
            println!("{}º lugar: {} -> IGUAL à média", i + 1, num);
        }
    }
}

cd rust
rustc main.rs -o programa
./programa

// Declara o pacote principal — todo programa executável em Go começa assim.
package main

// Importa os pacotes necessários.
import (
	"bufio"   // Leitura com buffer (mais confiável para entrada do usuário).
	"fmt"     // Formatação e impressão no console.
	"os"      // Acesso ao sistema operacional (stdin).
	"sort"    // Algoritmos de ordenação.
	"strconv" // Conversão entre string e números.
	"strings" // Manipulação de strings (TrimSpace).
)

// Função principal — ponto de entrada do programa.
func main() {
	// Cria um leitor de entrada padrão (teclado).
	reader := bufio.NewReader(os.Stdin)

	// ===== 1. LER OS TRÊS NÚMEROS =====

	// Pede o primeiro número.
	fmt.Println("Digite o 1º número:")
	// Lê a linha digitada até o Enter.
	s1, _ := reader.ReadString('\n')
	// Remove espaços/quebra de linha e converte para float64.
	n1, _ := strconv.ParseFloat(strings.TrimSpace(s1), 64)

	// Pede o segundo número.
	fmt.Println("Digite o 2º número:")
	s2, _ := reader.ReadString('\n')
	n2, _ := strconv.ParseFloat(strings.TrimSpace(s2), 64)

	// Pede o terceiro número.
	fmt.Println("Digite o 3º número:")
	s3, _ := reader.ReadString('\n')
	n3, _ := strconv.ParseFloat(strings.TrimSpace(s3), 64)

	// ===== 2. SOMAR OS TRÊS NÚMEROS =====

	// Soma os três valores.
	soma := n1 + n2 + n3
	// Mostra o resultado.
	fmt.Println("Soma =", soma)

	// ===== 3. LER O DIVISOR =====

	// Pede o divisor.
	fmt.Println("Digite um número para dividir a soma:")
	s4, _ := reader.ReadString('\n')
	// Converte para float64.
	divisor, _ := strconv.ParseFloat(strings.TrimSpace(s4), 64)

	// ===== 4. DIVIDIR E MOSTRAR O RESULTADO =====

	// Calcula a média.
	media := soma / divisor
	// Mostra o resultado.
	fmt.Println("Resultado da divisão (média) =", media)

	// ===== 5. GUARDAR OS NÚMEROS EM UM SLICE E ORDENAR =====

	// Cria um slice (array dinâmico) com os três números.
	numeros := []float64{n1, n2, n3}
	// Ordena do maior para o menor usando função de comparação.
	sort.Slice(numeros, func(i, j int) bool {
		return numeros[i] > numeros[j]
	})

	// ===== 6. MOSTRAR A ORDEM EM RELAÇÃO À MÉDIA =====

	fmt.Println("\nOrdem (maior -> menor) em relação à média:")

	// Percorre o slice com índice (i) e valor (num).
	for i, num := range numeros {
		// Compara o número atual com a média.
		if num > media {
			// Se for maior, imprime a posição e a relação (2 casas decimais).
			fmt.Printf("%dº lugar: %.2f -> MAIOR que a média\n", i+1, num)
		} else if num < media {
			// Se for menor.
			fmt.Printf("%dº lugar: %.2f -> MENOR que a média\n", i+1, num)
		} else {
			// Se for igual.
			fmt.Printf("%dº lugar: %.2f -> IGUAL à média\n", i+1, num)
		}
	}
}

cd go
go run main.go
