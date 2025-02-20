*tempconv*
=====
Biblioteca escrita em Go para conversões simples de temperatura. Extraída do livro **A Linguagem de Programação Go**, de Alan A. A. Donovan e Brian Kernighan. 

Como usar?
----
Faça o download da biblioteca:

`go get https://github.com/ufla-gcc259/aula-git-parte-2@v1.0.1`

Pronto, agora é só usar:
```go
package main

import (
	"fmt"

	"github.com/ufla-gcc259/aula-git-parte-2/tempconv"
)

func main() {
	fmt.Printf("Que frio! %v\n", tempconv.AbsoluteZeroC) // Que frio! -273.15°C
	fmt.Printf("Fervendo! %v\n", tempconv.CToF(tempconv.BoilingC)) // Fervendo! 212°F
}
```
Exemplo de Uso:
----

```go

package main
/* 
* Este códio é um exemplo de uso da biblioteca tempconv.
* 
*
*/
import (
	"fmt"
	"os"
	"strconv"
	"github.com/ufla-gcc259/aula-git-parte-2/tempconv"
)

func main() {
	// recebe o valor passado por parametro
	argsWithProg := os.Args
	if len(argsWithProg) != 2 { // verifica numero de parametros
		uso()
	} else{
		// verifica se parametro é numérico
		if value, err := strconv.ParseFloat(argsWithProg[1], 64); err != nil { 
			uso()
		} else {
			
			// valor Celsius e Fahrenheit
			tempCelsius := tempconv.Celsius(value)
			tempFahrenheit := tempconv.Fahrenheit(value)
			// impressão da conversão do valor como Celsius para Fahrenheit e vice-versa
			if (tempFahrenheit < tempconv.CToF(tempconv.AbsoluteZeroC)){
				fmt.Printf("O valor entrado (%f) está abaixo do Zero Absoluto na escala Fahrenheit (%v) e na escala Celsius (%v)\n", 
					value, tempconv.CToF(tempconv.AbsoluteZeroC), tempconv.AbsoluteZeroC)
			} else if (tempCelsius < tempconv.AbsoluteZeroC){
				fmt.Printf("O valor entrado (%f) está abaixo do Zero Absoluto na escala Celsius (%v) \n",
					value, tempconv.AbsoluteZeroC)
				fmt.Printf("%v = %v\n", tempFahrenheit, tempconv.FToC(tempFahrenheit))
			} else {
				
				fmt.Printf("%v = %v\n", tempCelsius, tempconv.CToF(tempCelsius))
				fmt.Printf("%v = %v\n", tempFahrenheit, tempconv.FToC(tempFahrenheit))
			}
		}
	}
}

func uso(){
	fmt.Println("Para executar corretamente o exemplo, passe apenas um valor numérico como parametro:\ngo run ./exemple.go <valor numérico>")
}


```
Outras linguagens?
----
Versões da biblioteca *tempconv* para outras linguagens:

> *Todo*


Licença
-----

> *Todo*


Como contribuir?
----
Escolha uma *issue* dentre as [disponíveis](https://github.com/ufla-gcc259/aula-git-parte-2/issues), avise à comunidade que você está trabalhando nela e envie um *Pull Request*, quando terminar.
