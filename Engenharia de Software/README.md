# Bertoti
# Atividade 1 -> COMENTARIO DO LIVRO

Vemos três diferenças críticas entre programação e engenharia de software: tempo, escala e as compensações em jogo. Em um projeto de engenharia de software, os engenheiros precisam estar mais preocupados com a passagem do tempo e com a eventual necessidade de mudanças. Numa organização de engenharia de software, precisamos de estar mais preocupados com a escala e a eficiência, tanto para o software que produzimos como para a organização que o produz. Finalmente, como engenheiros de software, somos solicitados a tomar decisões mais complexas com resultados de maior risco, muitas vezes baseados em estimativas imprecisas de tempo e crescimento. O que é engenharia de software ? R: Acredito que seja uma administração das funcionalidades, tecnologias, para poder dimensionar tempo, escalabilidade ou seja a estrutura de um projeto.

# Atividade 2 -> 3 exemplos de trade-offs (requisitos não funcionais) : R:

1 - Desempenho vs. Segurança: Aumentar a segurança, como usar criptografia robusta, pode diminuir o desempenho do sistema devido ao processamento extra necessário.

2 - Escalabilidade vs. Complexidade: Projetar um sistema para escalar facilmente pode aumentar a complexidade do código e a dificuldade de manutenção.

3 - Usabilidade vs. Funcionalidade: Adicionar mais funcionalidades pode tornar a interface do usuário mais complexa, afetando a usabilidade e a experiência do usuário.

# Atividade 3

Arquivo: Animal.java

 	package atividade3;

	// Criando classe publica e definindo os atributos com segurança privada
	public class Animal {
	private String raca;
	private String nome;
	
	// Criando construtor publico que atribui valor aos atributos da classe
	public Animal (String raca, String nome) {
		this.raca = raca;
		this.nome = nome;
	}

	// Criando metodos de acesso e modificação
	public String getRaca() {
		return raca;
	}

	public void setRaca(String raca) {
		this.raca = raca;
	}

	public String getNome() {
		return nome;
	}

	public void setNome(String nome) {
		this.nome = nome;
	}
		
	}

Arquivo: Petshop.java

  	package atividade3;
  
  	import java.util.LinkedList;
  	import java.util.List;
  
      // Criando classe Petshop atribuindo um atributo do tipo lista do objeto Animal
  	public class Petshop {
      // LinkedList é como se fosse um array de objetos
      private List<Animal> animais = new LinkedList<Animal>();
      
      // Criando um método para cadastrar um animal ao petshop
      public void cadastrarAnimal(Animal animal) {
          animais.add(animal);
      }
      
      // Criando método para buscar um animal na lista existente de animais do petshop
      public List<Animal> buscarAnimalPeloNome(String nome) {
          List<Animal> animaisEncontrados = new LinkedList<Animal>();
          
          // Verifica se o nome do animal é igual ao nome fornecido e o adiciona à lista de animais encontrados
          for(Animal animal : animais) {
              if(animal.getNome().equals(nome)) {
                  animaisEncontrados.add(animal);
              }
          }
          return animaisEncontrados;
      }
      
      /* Criando método para retornar uma lista com todos os animais cadastrados */
      public List<Animal> getAnimais() {
          return animais;
      }
    }
  
  Arquivo: TestAnimal.java

	package atividade3;

	import static org.junit.jupiter.api.Assertions.*;

	import java.util.List;

	import org.junit.jupiter.api.Test;

	class TestAnimal {

	@Test
	void test() {
		// Criando um objeto petshop do tipo Petshop
		Petshop petshop = new Petshop();
		
		// Criando objetos do tipo Animal
		Animal darlo = new Animal("Anta", "Darlo");
		Animal yllebasi = new Animal("Gata", "Yllebasi");
		
		// Usando o metodo cadastrarAnimal para adicionais 2 objetos ao petshop
		petshop.cadastrarAnimal(darlo);
		petshop.cadastrarAnimal(yllebasi);
		
		// Verificando se ao usar o metodo getAnimais retorna o tamanho 2 (quantidade de itens)
		assertEquals(petshop.getAnimais().size(), 2);
		
		// Usando metodo buscarAnimalPeloNome para buscar um animal pelo nome 'Darlo', e esta verificando se o Darlo tem a mesma raca do objeto darlo
		List<Animal> animal = petshop.buscarAnimalPeloNome("Darlo");
		assertEquals(animal.get(0).getRaca(), darlo.getRaca());
	}

	}	
