# Operatorer och operander
Operatorer är speciella symboler som fungerar likt de nyckelord vi tidigare pratat om - d.v.s. att de representerar viss inbyggd funktionalitet, exempelvis + för addition och * för multiplikation. De värden som operatören använder kallas för operander, exempelvis skulle `4` resp. `5` i följande uttryck:  `4 + 5` agera operander för operationen addition.

Samtliga utav nedan matematiska uttryck är giltiga sådana: 
```python
# Exempel 1
20 * 32
hour - 2
3**2
14 - 4
10 / 2
(10 + 5) * 2 
```

Varje symbol representerar en operation. `+`-operationen avser addition, `-`-operationen avser subtraktion. `/`-operationen avser division och `*`-operationen avser multiplikation. D.v.s. att operationerna i Python är demsamma som i matematik. Även parenteser utvärderas på samma vis, d.v.s. att värdet från det sista uttrycket ovan skulle bli 30. Som du kanske gissat avser `**`-operationen avslutningsvis exponentiering.

I det fall vi har lagrat ett värde i en variabel så kommer varibeln att ersättas med dess värde innan operationen utförs. Detta sker automatiskt när koden körs av kompilatorn. 

Noterbart avseende divisionsberäkning är att Python utför decimaltalsdivision. D.v.s. att även om vi dividerar två heltal som resulterar i en jämn kvot såsom `6 / 2` så skulle resultatet bli 3.0 snarare än 3. Om man vill utföra heltalsdivision så behöver man istället nyttja operatorn `//`:
```python
# Exempel 2
>>> 10/2
# will print 5.0 
>>> 10//2
# will print 5 
```

I det fall man tillämpar heltalsdivision så kommer kompilatorn alltid avrunda resultatet nedåt:
```python
# Exempel 3
>>> 10/4
# will print 2.5 
>>> 10//4
# will print 2 
```
