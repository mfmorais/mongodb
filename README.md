# Atividade Prática – MongoDB


### Exercício 1- Aquecendo com os pets

1. Adicione outro Peixe e um Hamster com nome Frodo
```
    db.pets.insert({name: "Frodo", species: "Hamster"});

    WriteResult({ "nInserted" : 1 })

    db.pets.insert({name: "Frodo", species: "Peixe"});

    WriteResult({ "nInserted" : 1 })
```

2. Faça uma contagem dos pets na coleção

```
    db.pets.count();

    8
```

3. Retorne apenas um elemento o método prático possível

```
    db.pets.findOne();

    {
        "_id" : ObjectId("5e629e883f80ea9cb9d1a470"),
        "name" : "Mike",
        "species" : "Hamster"
    }
```

4. Identifique o ID para o Gato Kilha.

```
    db.pets.find( {"name": "Kilha", "species": "Gato"} );

    { 
        "_id" : ObjectId("5e629ee53f80ea9cb9d1a472"), 
        "name" : "Kilha", 
        "species" : "Gato" 
    }
```

5. Faça uma busca pelo ID e traga o Hamster Mike

```
    db.pets.find({"_id" : ObjectId("5e629e883f80ea9cb9d1a470")});

    { 
        "_id" : ObjectId("5e629e883f80ea9cb9d1a470"), 
        "name" : "Mike", 
        "species" : "Hamster" 
    }
```

6. Use o find para trazer todos os Hamsters

```
    db.pets.find({"species": "Hamster"});

    { 
        "_id" : ObjectId("5e629e883f80ea9cb9d1a470"), 
        "name" : "Mike", 
        "species" : "Hamster" 
    }
    { 
        "_id" : ObjectId("5e62a1553f80ea9cb9d1a476"), 
        "name" : "Frodo", 
        "species" : "Hamster" 
    }
```

7. Use o find para listar todos os pets com nome Mike

```
    db.pets.find( {"name": "Mike"});

    { 
        "_id" : ObjectId("5e629e883f80ea9cb9d1a470"), 
        "name" : "Mike", 
        "species" : "Hamster" 
    }
    { 
        "_id" : ObjectId("5e629eeb3f80ea9cb9d1a473"), 
        "name" : "Mike", 
        "species" : "Cachorro" 
    }
```

8. Liste apenas o documento que é um Cachorro chamado Mik

```
    db.pets.find( {"name": "Mike", "species" : "Cachorro"});

    { 
        "_id" : ObjectId("5e629eeb3f80ea9cb9d1a473"), 
        "name" : "Mike", 
        "species" : "Cachorro" 
    }
```

### Exercício 2 – Mama mia!

1. Liste/Conte todas as pessoas que tem exatamente 99 anos. Você pode usar um count para indicar a quantidade.

```
    db.italians.find({"age":{$eq: 99}}).count();

    0
```

2. Identifique quantas pessoas são elegíveis atendimento prioritário
(pessoas com mais de 65 anos)


```
    db.italians.find({"age":{$gt: 65}}).count();

    1714
```

3. Identifique todos os jovens (pessoas entre 12 a 18 anos).

```
    db.italians.find({"age":{$gt: 12, $lt: 18}}).count();

    667
```

4. Identifique quantas pessoas tem gatos, quantas tem cachorro e quantas
não tem nenhum dos dois

```
    db.italians.find({ "cat": { $exists: true} }).count();

    6073

    db.italians.find({ "dog": { $exists: true} }).count();

    3986

    db.italians.find({ $and: [ { "cat": { $exists: false} }, { "dog": { $exists: false} } ] }).count();
    
    2294
```

5. Liste/Conte todas as pessoas acima de 60 anos que tenham gato

```
    db.italians.find({ $and: [ {"age":{$gt: 60}}, {"cat": { $exists: false}} ] }).count();

    901
```

6. Liste/Conte todos os jovens com cachorro

```
    db.italians.find({ $and: [ {"age":{$gt: 12, $lt: 18}}, { "dog": { $exists: false} } ] }).count();

    383
```

7. Utilizando o $where, liste todas as pessoas que tem gato e cachorro

```
     db.italians.find({$where: function() { return this.cat != null && this.dog != null }}).count();
    
    2353
```

8. Liste todas as pessoas mais novas que seus respectivos gatos.

```
    db.italians.find({$where: function() { return this.cat != null && this.age < this.cat.age }}).count();

    662
```

9. Liste as pessoas que tem o mesmo nome que seu bichano (gatou ou
cachorro)

```
    db.italians.find({$where: function() { return this.cat != null && this.firstname == this.cat.name }}).count();

    69
```

10. Projete apenas o nome e sobrenome das pessoas com tipo de sangue de
fator RH negativo

```
    db.italians.find({"bloodType" : {$regex : "-$"}}).count();

    5054
```

11. Projete apenas os animais dos italianos. Devem ser listados os animais
com nome e idade. Não mostre o identificado do mongo (ObjectId)

```
    db.italians.find({ $or: [ { "cat": { $exists: true} }, { "dog": { $exists: true} } ] }, { "_id": 1, "cat": 1, "dog": 1}).count();
    
    7706
```

12. Quais são as 5 pessoas mais velhas com sobrenome Rossi?

```
    db.italians.find({ "surname": "Rossi"}).sort({"age": -1}).limit(5).count();

    5
```

13. Crie um italiano que tenha um leão como animal de estimação. Associe
um nome e idade ao bichano

```
    db.italians.insert({
        "firstname":"Magno",
        "surname":"Morais",
        "username":"magno127",
        "age":28,
        "email":"magno@uol.com.br",
        "bloodType":"A-",
        "id_num":"635837342657",
        "registerDate": ISODate("2020-03-10T00:10:38.431Z"),
        "ticketNumber":7305,
        "jobs":[
            "Programador JAVA"
        ],
        "favFruits":[
            "Tangerina",
            "Kiwi"
        ],
        "movies":[
            {
                "title":"Clube da Luta (1999)",
                "rating":1.59
            },
            {
                "title":"12 Homens e uma Sentença (1957)",
                "rating":2.19
            },
            {
                "title":"Harakiri (1962)",
                "rating":2.35
            }
        ],
        "leao":{
            "name":"Johnny Bravo",
            "age":5
        }
    });

    WriteResult({ "nInserted" : 1 })

```

14. Infelizmente o Leão comeu o italiano. Remova essa pessoa usando o Id.

```
    db.italians.deleteOne( {"_id": ObjectId("5e68373f653d71d52f2ccd97")});

    { "acknowledged" : true, "deletedCount" : 1 }
```

15. Passou um ano. Atualize a idade de todos os italianos e dos bichanos em 1.

```
    FALTA AJUSTAR

    db.italians.update({"_id": ObjectId("5e683d8e6fcb8e074981eaad")}, $inc: { "age": 1, "cat.age": 1, "dog.age": 1})

    WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```

16. O Corona Vírus chegou na Itália e misteriosamente atingiu pessoas
somente com gatos e de 66 anos. Remova esses italianos.

```
    db.italians.remove({ $and: [ { "age": 66 }, { "cat": { $exists: true} }, { "dog": { $exists: false} } });

    WriteResult({ "nRemoved" : 46 })
```

17. Utilizando o framework agregate, liste apenas as pessoas com nomes
iguais a sua respectiva mãe e que tenha gato ou cachorro.

```
    FALTA AJUSTAR
    
    db.italians.aggregate([ {
        "$match": { 
            /*$eq: { "$firstname":  "$mother.firstname" },*/
            $or: [{ cat: {$exists: true} }, { dog: {$exists: true} }]
        }
    } ])
```

18. Utilizando aggregate framework, faça uma lista de nomes única de
nomes. Faça isso usando apenas o primeiro nome

```
    db.italians.aggregate( [ { $project: { _id: 0, firstname: 1 } } ] );

    { "firstname" : "Emanuela" }
    { "firstname" : "Elisa" }
    { "firstname" : "Mauro" }
    { "firstname" : "Michele" }
    { "firstname" : "Maria" }
    { "firstname" : "Eleonora" }
    { "firstname" : "Massimiliano" }
    { "firstname" : "Lucia" }
    { "firstname" : "Gianluca" }
    { "firstname" : "Emanuele" }
    { "firstname" : "Sara" }
    { "firstname" : "Angela" }
    { "firstname" : "Dario" }
    { "firstname" : "Elisabetta" }
    { "firstname" : "Roberta" }
    { "firstname" : "Giusy" }
    { "firstname" : "Teresa" }
    { "firstname" : "Valentina" }
    { "firstname" : "Mattia" }
    { "firstname" : "Simona" }
```


19. Agora faça a mesma lista do item acima, considerando nome completo.

```
    db.italians.aggregate( [ { $project: { _id: 0, fullname: { $concat: [ "$firstname", " ", "$surname" ] } } } ] );

    { "fullname" : "Emanuela Fiore" }
    { "fullname" : "Elisa Fontana" }
    { "fullname" : "Mauro Sanna" }
    { "fullname" : "Michele Damico" }
    { "fullname" : "Maria Leone" }
    { "fullname" : "Eleonora Monti" }
    { "fullname" : "Massimiliano Bellini" }
    { "fullname" : "Lucia Piras" }
    { "fullname" : "Gianluca Orlando" }
    { "fullname" : "Emanuele Conte" }
    { "fullname" : "Sara Serra" }
    { "fullname" : "Angela Sorrentino" }
    { "fullname" : "Dario De Angelis" }
    { "fullname" : "Elisabetta Rossetti" }
    { "fullname" : "Roberta Serra" }
    { "fullname" : "Giusy Fontana" }
    { "fullname" : "Teresa Marino" }
    { "fullname" : "Valentina Martino" }
    { "fullname" : "Mattia Martinelli" }
    { "fullname" : "Simona Piras" }
```

20. Procure pessoas que gosta de Banana ou Maçã, tenham cachorro ou gato,
mais de 20 e menos de 60 anos.

```
    db.italians.aggregate([ {
        "$match": { 
            "favFruits": { "$in":  [ "Banana", "Maçã" ] },
            "age": { $gt: 20, $lt: 60 },
            $or: [{ cat: {$exists: true} }, { dog: {$exists: true} }]
        }
    } ])
```

### Exercício 3 - Stockbrokers

1. Liste as ações com profit acima de 0.5 (limite a 10 o resultado)

```
    db.stocks.find({"Profit Margin":{$gt: 0.5}}).limit(10)


```

2. Liste as ações com perdas (limite a 10 novamente)

3. Liste as 10 ações mais rentáveis

4. Qual foi o setor mais rentável?

5. Ordene as ações pelo profit e usando um cursor, liste as ações.

6. Renomeie o campo “Profit Margin” para apenas “profit”.

7. Agora liste apenas a empresa e seu respectivo resultado

8. Analise as ações. É uma bola de cristal na sua mão... Quais as três ações
você investiria?

9. Liste as ações agrupadas por setor


### Exercício 4 – Fraude na Enron!

1. Liste as pessoas que enviaram e-mails (de forma distinta, ou seja, sem
repetir). Quantas pessoas são?

2. Contabilize quantos e-mails tem a palavra “fraud”