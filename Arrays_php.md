# Arrays PHP

- Arrays Associativos 

#

### Comprar dois arrays valores

```
array_diff($ARRAY1,$ARRAY2);
```

### Comprar dois arrays keys

```
array_diff_key($ARRAY1,$ARRAY2);
```

### Montar array a partir de dois arrays com mesmo tamanho,chave e valor  

```
array_combine($ARRAY1,ARRAY2);
```



### Inverter array

```
array_flip($ARRAY);
```


### Juntar arrays 

```
array_merge($ARRAY1,$ARRAY2);
```

```
$ARRAY1 + $ARRAY2
```

Array unpacking
```
[...$array1,...$ARRAY2]
```

### Adicionar um elemento ao array

adiciona ao final do array
```
array_push($ARRAY1,$VALOR,...);
```

adiciona no inicio do array
```
array_unshift($ARRAY1,$VALOR,...);
```

move todos os elementos para esquerda  
```
array_shift($ARRAY1);
```

remove ultimo elemento
array_pop($ARRAY1);

### Extract 

receber array e cria variavel
```
extract($ARRAY)
```

### Compact 
receber valores e cria arrays
```
compact($VALOR1,$VALO2,$VALOR3);
```


## Funções

- Filter,map e reduce

