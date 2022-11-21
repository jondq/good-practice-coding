# REGULAR EXPRESSIONS

- `.` Match any character. Representa cualquier caracter
- `^` starts with
- `$` ends with
- `*` Many times
- `\S` Non space character
- `+` quatifier aperator. opera hacia la izq 'una o más ocurrencias'
- `{n}` numero n exacto de ocurrencias. 's{2}': 2 ocurrencias de s 
- `{n,m}` ente n y m ocurrencias
- ``


## Python
`import re`  
`re.search(key,line)` Retorna True/false. key: regex

### Examples
`re.findall('\S+@\S+',line)` Correos electrónicos con min un caracter a la der e iz del @