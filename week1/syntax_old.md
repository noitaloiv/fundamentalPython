---
layout: default
title: "Week 1: Introduction to Python"
---

# Syntax

Nu när du har skapat samt ställt in din arbetsyta och skrivit ditt första program i Python är det dags att fördjupa dig i Python-syntaxens värld. Man kan likna en syntax med hur grammatiken fungerar i det svenska språket där man skriver på ett visst sätt för att andra ska förstå vad du menar.

Utöver syntaxen så finns det även vissa regler och mönster som styr hur ditt "språk" ser ut, vilka säkerställer att datorn kan tolka och förstå dina kommandon korrekt. För att dra paralleller till det svenska språket så kan detta t.e.x. tänkas vara att vi måste använda fullständiga meningar. 

I detta kapitel kommer vi att visa exempel på strukturen för språket Python samt några regler som vi behöver anpassa oss efter.

## Att förstå Python-syntaxen

I syfte om att förstå syntaxen i Python, låt oss bryta ned och beskriva varje beståndsdel var för sig.

### Värden och typer

Ett värde är ett grundläggande ting - såsom en bokstav, ett tecken, eller en siffra - vilket ett program kan manipulera (exempelvis kombinera med andra värden, utföra beräkningar på värdet och dylikt). I Kapitel 1.2 så stötte vi på ett textuellt värde i form av `"Hello, world!"` när vi skrev vårt första program - som utmynnade i att skriva ut texten `"Hello, world!"`.

`"Hello, world!"` är ett exempel på ett textuellt värde, men värden kan även vara av andra typer. Textuella värden, som består av mer än ett tecken, kallas exempelvis för stängar (strings) medan heltalet 2 skulle klassificeras som just ett heltal (integer). Du (såväl som Python-kompilatorn) kan särskilja en sträng från ett heltal baserat på huruvida värdet är omgivet av sitationstecken (").

Likt hur vi tidigare skrev ut `"Hello, world!"` med hjälp av `print()`-funktionen så skulle vi likväl kunna skriva ut ett heltal med: `print(23)`. Detta då allt som hanteras genom terminalen (d.v.s. input och output) automatiskt kommer att behandlas som textuella värden. 

Om du skulle vara osäker på vilken typ ett värde har så kan kompilatorn berätta det för dig genom användningen av `type`-funktionen: 

``` python
# Exempel 1
print(type("Hello, world!"))
# will print <class 'str'>
print(type(23))
# will print <class 'int'>
```

Notera gärna att `#`-symbolen indikerar startpunkten för en kommentar. En kommentar kan vara körbar kod, fritext eller principiellt vad du än kan tänkas vilja skriva. Kommentarer är något som kompilatorn kommer att ignorera när koden körs, d.v.s. att det enbart är till för dig och andra utvecklare - exempelvis för att tillhandahålla beskrivande text för den kod du skrivit.

Det är möjligt att skriva kommentarer över en eller flera rader där `#`-symbolen nyttjas för enradiga kommentarer och `'''` kan nyttjas för att skriva kommentarer över flera rader, t.ex. enligt: 
```python
# Exempel 2
print(type("Hello, world!"))
print(type(23))
'''
the first row will print <class 'int'> and
the second row will print <class 'str'>
'''
```

Det finns självfallet även andra typer av värden som inte riktigt passar som varken ett heltal eller en sträng. Exempelvis behandlas decimaltal annorlunda än heltal och klassificeras därför som typen `float`.
```python
# Exempel 2
print(type(3.2))
# will print <class 'float'>
```

Vi skulle nu även kunna testa vårt påstående avseende att datorn tolkar strängar som de värden som anges inom situationstecken. Exempelvis kan vi genom `type`-funktionen se att `"3.2"` och `3.2` inte är samma typ:
``` python
# Exempel 3
print(type("3.2"))
# will print <class 'str'>
print(type(3.2))
# will print <class 'float'>
```

Det är även viktigt att ta formatet på värdet i beaktande när man anger det. Exempelvis så skulle `type(1,000,000)` generera ett felmeddelande då det inte kan tolkas som ett giltigt heltal p.g.a. de kommatecken som nyttjas. Det skulle istället snarare tolkas som en kommaseparerad lista som innehåller värdena `1 0 0`, vilket vi kan se ett exempel på om vi försöker skriva ut det enligt:
``` python
# Exempel 4
print(1,000,000)
# will print 1 0 0
```
Ovan felaktiga tolkning är ett exempel på ett s.k. _semantiskt fel_, d.v.s. att koden kan utföras utan att ett faktiskt felmeddelande genereras, men det kommer att resultera i ett annat värde än vad vi förväntar oss. Om vi istället skulle försöka utföra koden: `type(1,000,000)` så skulle vi få ett s.k. _kompileringsfel_ när vi försöker kompilera (köra) koden. Ett kompileringsfel innefattar med andra ord att koden inte är körbar medan semantiska fel istället kan resultera i körbar kod som ger oförväntade resultat.

### Variabler
En av de mest kraftfulla funktionerna i ett programmeringsspråk är förmågan att manipulera variabler. En variabel är ett namn som refererar till ett värde.

Genom tilldelning så kan vi skapa variabler och tillhandahålla dem med värden: 
```python
# Exempel 1
message = "Hello, world!"
student_age = 22
pi = 3.14159
```

I ovan exempel så ser vi tre olika tilldelningar som resulterar i tre olika variabler. På den första raden så tilldelas variabeln `message` strängen `"Hello, world!"`, på den andra raden tilldelas variabeln `studentAge` heltalet `22` och på den tredje raden tilldelas variabeln `pi` flyttalet `3.14159`.

Notera att vi för `"Hello, world!"` använder dubbla situationstecken för att omsluta strängen. Generellt sett har ' och " samma funktion i Python, men om en sträng innehåller ett enda '-tecken (t.ex. ordet it's all ogre) så måste det omslutas av dubbla situationstecken ("it's all ogre") för att tolkas som en sträng.

Tidigare så har vi angivit värdet som vi vill skriva ut direkt inom parenteserna för `print()`-funktionen (t.ex. `print(3.2)`), men det är även möjligt att ange representationen av ett värde - d.v.s. en variabel:  
```python
# Exempel 2
print(message)
# will print "Hello, world!"
print(student_age)
# will print 22
```

### Variabelnamn och nyckelord

Utvecklare väljer generellt meningsfulla och representativa namn för sina variabler. Detta för att utvecklaren själv såväl som andra enkelt ska förstå vad det är som variabeln i fråga representerar. Om vi föreställer oss ett scenario där vi ämnar lagra en användares angivna lösenord så är det möjligt att lagra det i stil med:
```python
# Exempel 1
x = "xHyra6h%"
```

Men det kan snabbt bli svårt att särskilja en variabel från en annan samt snabbt bilda sig en uppfattning av koden och dess syfte första gången man ser den. Det skulle således vara betydligt tydligare vilket värde variabeln representerar om vi istället hade något i stil med:
```python
# Exempel 2
user_password = "xHyra6h%"
```

Variabelnamn som sådana kan vara godtyckligt långa och innehålla bokstäver såväl som siffror (de måste dock inledas med en bokstav). Det finns dock vissa konventioner för namngivning i Python och dessa talar för att vi exempelvis inte nyttjar versaler i variabelnamn, även om Python accepterar sådan namngivning. D.v.s. att `Student_Age` och `student_age` skulle vara två olika variabler.

Underscore (_) kan förekomma i variabelnamn då vi vill att variabelnamnet ska bestå av flera ord, t.ex. `user_password`, `user_name`, och dylikt.

Du behöver inte vara orolig över att ange otillåtna variabelnamn då du snabbt kommer att bemötas av ett syntaxfel i de fall du har otillåtna namn. Exempelvis enligt:
```python
# Exempel 3
123 = "test"
SyntaxError: invalid syntax
a123 = "test"

ab$ = "test"
SyntaxError: invalid syntax
if = "test"
SyntaxError: invalid syntax
```

`123` är ett otillåtet namn då det inte inleds med en bokstav - därav att `a123` anses vara ett tillåtet namn. `ab$` är ett otillåtet namn då det innehåller specialtecknet `$`, men varför får vi ett syntaxfel i det sista fallet med `if`? Felet beror på att `if` råkar vara ett av 29 st. nyckelord som är integrerade i Python - d.v.s. att det är ord som redan uppfyller ett syfte genom att definiera språkets regler och struktur, vilket medför att de inte kan nyttjas som variabelnamn. Det skulle dock vara tillåtet om vi inte längre representerade nyckelordet genom att bygga vidare på variabelnamnet, t.ex. i stil med:
```python
# Exempel 4
if_old_age = "Sorry, you're too old to be eating of the children's menu"
```
Du kommer under denna kurs att stöta på fler nyckelord såsom `and`, `class`, `else`, `for`, etc. men vi kommer att introducera var och ett successivt allt eftersom att vi introducerar fler koncept och byggstenar i språket.

### "Påståenden" (statements)
Ett påstående är en instruktion som vår kompilator kan utföra. Vi har redan sett exempel på tre sorters påståenden: `print()`, `type()` och tilldelning.

När du skriver ett påstående i din Python-fil och sedan kör koden via terminalen (alt. kör kod direkt genom terminalen) så kommer Python att kompilera koden och visa eventuella resultat. Med eventuella resultat avses att exempelvis tilldelning i sig självt inte kommer att skriva ut något i terminalen, om inte variabeln efter tilldelningen skrivs ut med hjälp av `print()`.
```python
# Exempel 1
assignment = "A value"
# nothing happens

assignment = "A value"
print(assignment)
# will print "A value"
```

Ett Python-skript innehåller generellt sett en sekvens av påståenden. Om det finns mer än ett påstående (med tillhörande utskrift) så kommer resultaten att visas ett i taget allteftersom att resp. påstående kompileras/körs - vilket sker i en hierarkisk ordning (d.v.s. från påståendet på den första kodraden till påståendet på den sista kodraden).
```python
# Exempel 2
number = 10
print(number)
# will print 10
number = 20
number = 30
print(number)
# will print 30
```

### "Uttryck" (expressions)

Ett uttryck är en kombination av värden, variabler och operatorer. Om du skriver ett uttryck, exempelvis `2 + 2`, så kommer kompilatorn att tolka och visa resultatet:
```python
# Exempel 1
>>> 2 + 2
# will print: 4
```

Ett uttryck som sådant måste dock inte innehålla värden, variabler såväl som operatorer för att klassas som ett uttryck. Ett värde eller en variabel i sig kan exempelvis evalueras som ett uttryck:
```python
# Exempel 2
>>> 10
# will print: 10
>>> number = 5
>>> number
# will print: 5
```

Att utvärdera ett uttryck är dock inte riktigt samma sak som att skriva ut ett värde, likt hur vi gjort tidigare med funktionen `print()`.
```python
# Exempel 3
>>> hello = "Hello, world!"
>>> hello
# will print: 'Hello, world!'

>>> print(hello)
# will print: Hello, world!
```

När kompilatorn visar värdet för ett uttryck använder den med andra ord samma format som du skulle använda för att ange ett värde. När det gäller strängar innefattar det således att värdet innehåller situationstecken. Om vi istället använder funktionen `print()` så kommer utskriften dock enbart att visa det faktiska värdet.

I ett Python-script så kan alla uttryck vara tillåtna sådana (d.v.s. att inga fel genereras), men det betyder inte nödvändigtvis att det resulterar i något som är synligt för en användare. Exempelvis skulle vi kunna skriva något i stil med:
```python
# Exempel 4
test_1 = "msg"
test_2 = 22
test_3 = 4 + 5
```
Men då vi aldrig gör något med de variabler vi skapat så kommer inget att skrivas ut. 

### Operatorer och operander

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

### Operationer på strängar

Du kan generellt sett inte utföra matematiska operationer på strängar, även i de fall strängarna ser ut som siffror (t.ex. `"15"`). Detta innefattar att nedan uttryck inte är giltiga:
```python
# Exempel 1
message = "Heya"
message_two = message + 1
# will generate: TypeError: can only concatenate str (not "int") to str 
```

Som vi ser från felmeddelandet så reagerar kompilatorn inte på operatorn, `+`, utan på att vi försöker använda den med två olika datatyper (`str` + `int`). Vi tillåts nämligen att använda `+`-operatorn mellan två strängar för att konkatenera dem. Strängkonkatenering innefattar att vi slår ihop två strängar:
```python
# Exempel 2
message_a = "Heya"
message_b = ", Chris!"
message_c = message_a + message_b
message_d = message_b + message_a
print(message_c)
# will print: Heya, Chris!
print(message_d)
# will print: , Chris!Heya
```

Även operatorn `*` kan appliceras på strängar för att duplicera en sträng ett antal gånger. Exempelvis skulle `print("Python"*3)` resultera i utskriften `PythonPythonPython`.

### Komposition

Hittills har vi, till merparten, tittat på de olika beståndsdelarna i ett program (variabler, uttryck och påståenden) isolerat utan att prata om hur man kan kombinerar dem.

En av de mest användbara funktionerna i programmeringsspråk är dess förmåga att ta isolerade, små byggstenar och kombinera dem med andra byggstenar för att på så vis bygga ett omfattande program. Vi har sett några exempel på detta tidigare, exempelvis kombinationen av ett påstående (`print()`) med ett uttryck `(2+2)` enligt formen: `print(2+2)`. Noterbart är att beräkningen kommer att utföras först och att utskriften av summan sker därefter. Detta kan även appliceras med flertalet variabler, uttryck och påståenden i stil med:
```python
# Exempel 1
price = 20
print("The price for four cups of coffee is:", price*4, "which, with the group discount, comes out to:", price*4 - ((price*4)/100)*15)
# will print: The price for four cups of coffee is: 80 which, with the group discount, comes out to: 68.0
```

### Övningar
Övning 1   
Assume that we execute the following assignment statements:
```python
width = 17
height = 12.0
delimiter = '.'
```
For each of the following expressions, write the value of the expression and the type (of the value of the expression).
```python
width/2
width/2.0
height/3
1 + 2 * 5
delimiter * 5
```

Övning 2   
Practice using Python as a calculator:
The volume of a sphere with radius r is 4/3 π r3. What is the volume of a sphere with radius 5? Hint: 392.6 is wrong!
Suppose the cover price of a book is $24.95, but bookstores get a 40% discount. Shipping costs $3 for the first copy and 75 cents for each additional copy. What is the total wholesale cost for 60 copies?
If I leave my house at 6:52 am and run 1 mile at an easy pace (8:15 per mile), then 3 miles at tempo (7:12 per mile) and 1 mile at easy pace again, what time do I get home for breakfast?
