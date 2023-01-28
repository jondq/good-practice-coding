# REGULAR EXPRESSIONS

- `\w` una palabra
- `\d` digitos numericos
- `\S` Non space character
- `\s` caracter en blanco /spave/tab. El mismo caracter en mayuscula es la negacion de la version minuscula
- `.` Match any character
- `*` Greedy - todo
- `^` starts with al inicio. Tambien sirve como negacion
- `$` ends with
- `*` Many times
- `?` operador. Cero o una ocurrencia
- `+` quatifier aperator. opera hacia la izq 'una o más ocurrencias'
- `{n}` contador, n exacto de ocurrencias. 's{2}': 2 ocurrencias de s 
- `{n,m}` ente n y m ocurrencias
- `\` escapar un caracter especial. `\.`escapa el ., busca literal de .
- `[1-5]` creacon de una clase. digitos de 1-5. [\-\.] clase de -,.

## Ejemplos
- `\d{2}[\-\.]?` dos digitos seguido o no de -/. -> 35.; 65-, 68


## Python
`import re`  
`re.search(key,line)` Retorna True/false. key: regex

### Examples
`re.findall('\S+@\S+',line)` Correos electrónicos con min un caracter a la der e iz del @