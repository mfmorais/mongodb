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
    db.italians.find({"age":{$gt: 65}});

    { "_id" : ObjectId("5e66dd05f33974bdf098ec2d"), "firstname" : "Emanuela", "surname" : "Fiore", "username" : "user100", "age" : 73, "email" : "Emanuela.Fiore@uol.com.br", "bloodType" : "O+", "id_num" : "845815017768", "registerDate" : ISODate("2008-01-23T03:39:58.206Z"), "ticketNumber" : 2063, "jobs" : [ "Libras", "Psicologia" ], "favFruits" : [ "Banana", "Pêssego", "Maçã" ], "movies" : [ { "title" : "Clube da Luta (1999)", "rating" : 0.61 } ], "father" : { "firstname" : "Manuela", "surname" : "Fiore", "age" : 93 }, "cat" : { "name" : "Tiziana", "age" : 17 }, "dog" : { "name" : "Ilaria", "age" : 7 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec39"), "firstname" : "Dario", "surname" : "De Angelis", "username" : "user112", "age" : 68, "email" : "Dario.De Angelis@live.com", "bloodType" : "B+", "id_num" : "334365246071", "registerDate" : ISODate("2009-04-28T11:13:25.823Z"), "ticketNumber" : 1112, "jobs" : [ "Gestão de Recursos Humanos", "Eletrotécnica Industrial" ], "favFruits" : [ "Uva", "Tangerina", "Mamão" ], "movies" : [ { "title" : "Seven: Os Sete Crimes Capitais (1995)", "rating" : 3.56 }, { "title" : "O Poderoso Chefão II (1974)", "rating" : 1.5 }, { "title" : "O Silêncio dos Inocentes (1991)", "rating" : 1.05 }, { "title" : "Um Estranho no Ninho (1975)", "rating" : 4.72 } ], "cat" : { "name" : "Valeira", "age" : 8 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec3c"), "firstname" : "Giusy", "surname" : "Fontana", "username" : "user115", "age" : 75, "email" : "Giusy.Fontana@live.com", "bloodType" : "A-", "id_num" : "511751668376", "registerDate" : ISODate("2019-04-28T20:10:11.458Z"), "ticketNumber" : 9314, "jobs" : [ "Comunicação e Informação", "Secretariado" ], "favFruits" : [ "Mamão" ], "movies" : [ { "title" : "Forrest Gump: O Contador de Histórias (1994)", "rating" : 1.03 }, { "title" : "O Silêncio dos Inocentes (1991)", "rating" : 3.64 } ], "dog" : { "name" : "Domenico", "age" : 10 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec3f"), "firstname" : "Mattia", "surname" : "Martinelli", "username" : "user118", "age" : 72, "email" : "Mattia.Martinelli@outlook.com", "bloodType" : "B-", "id_num" : "353318751345", "registerDate" : ISODate("2009-07-29T16:28:22.370Z"), "ticketNumber" : 3641, "jobs" : [ "Educação Física", "Estética e Cosmética" ], "favFruits" : [ "Melancia", "Melancia" ], "movies" : [ { "title" : "Batman: O Cavaleiro das Trevas (2008)", "rating" : 0.41 }, { "title" : "Matrix (1999)", "rating" : 3.41 }, { "title" : "12 Homens e uma Sentença (1957)", "rating" : 3.96 }, { "title" : "Seven: Os Sete Crimes Capitais (1995)", "rating" : 4.21 }, { "title" : "Matrix (1999)", "rating" : 1.62 } ], "mother" : { "firstname" : "Nicola", "surname" : "Martinelli", "age" : 89 }, "cat" : { "name" : "Eleonora", "age" : 10 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec41"), "firstname" : "Alex", "surname" : "Rossi", "username" : "user120", "age" : 75, "email" : "Alex.Rossi@outlook.com", "bloodType" : "AB-", "id_num" : "511806271753", "registerDate" : ISODate("2007-10-05T23:04:48.711Z"), "ticketNumber" : 8852, "jobs" : [ "Relações Públicas", "Jogos Digitais" ], "favFruits" : [ "Maçã", "Tangerina" ], "movies" : [ { "title" : "O Resgate do Soldado Ryan (1998)", "rating" : 1.44 } ], "father" : { "firstname" : "Marta", "surname" : "Rossi", "age" : 112 }, "cat" : { "name" : "Sabrina", "age" : 13 } }
```

3. Identifique todos os jovens (pessoas entre 12 a 18 anos).

```
    db.italians.find({"age":{$gt: 12, $lt: 18}});

    { "_id" : ObjectId("5e66dd05f33974bdf098ec50"), "firstname" : "Serena", "surname" : "Carbone", "username" : "user135", "age" : 13, "email" : "Serena.Carbone@yahoo.com", "bloodType" : "O+", "id_num" : "157282038275", "registerDate" : ISODate("2012-04-30T02:15:46.316Z"), "ticketNumber" : 3484, "jobs" : [ "Processos Metalúrgicos" ], "favFruits" : [ "Banana", "Goiaba" ], "movies" : [ { "title" : "Vingadores: Ultimato (2019)", "rating" : 3.21 } ] }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec5e"), "firstname" : "Cinzia", "surname" : "Rinaldi", "username" : "user149", "age" : 14, "email" : "Cinzia.Rinaldi@live.com", "bloodType" : "AB+", "id_num" : "165474047174", "registerDate" : ISODate("2015-05-03T15:28:38.168Z"), "ticketNumber" : 6393, "jobs" : [ "Teatro", "Gestão em Saúde" ], "favFruits" : [ "Tangerina" ], "movies" : [ { "title" : "Seven: Os Sete Crimes Capitais (1995)", "rating" : 2.87 }, { "title" : "1917 (2019)", "rating" : 1.09 }, { "title" : "Vingadores: Ultimato (2019)", "rating" : 4.93 }, { "title" : "O Resgate do Soldado Ryan (1998)", "rating" : 4.33 } ], "cat" : { "name" : "Claudio", "age" : 12 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec5f"), "firstname" : "Pietro", "surname" : "Ferrari", "username" : "user150", "age" : 13, "email" : "Pietro.Ferrari@uol.com.br", "bloodType" : "O-", "id_num" : "265704553157", "registerDate" : ISODate("2008-03-16T23:29:06.160Z"), "ticketNumber" : 4273, "jobs" : [ "Manutenção de aeronaves" ], "favFruits" : [ "Melancia", "Banana" ], "movies" : [ { "title" : "A Origem (2010)", "rating" : 1.03 }, { "title" : "O Silêncio dos Inocentes (1991)", "rating" : 3.18 }, { "title" : "Um Sonho de Liberdade (1994)", "rating" : 4.42 } ], "cat" : { "name" : "Giorgio", "age" : 1 }, "dog" : { "name" : "Luca", "age" : 7 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec65"), "firstname" : "Dario", "surname" : "Barbieri", "username" : "user156", "age" : 14, "email" : "Dario.Barbieri@gmail.com", "bloodType" : "B-", "id_num" : "440757151758", "registerDate" : ISODate("2012-10-20T11:59:48.312Z"), "ticketNumber" : 9082, "jobs" : [ "Agronomia", "Engenharia de Inovação" ], "favFruits" : [ "Banana", "Banana" ], "movies" : [ { "title" : "1917 (2019)", "rating" : 3.24 } ], "father" : { "firstname" : "Mirko", "surname" : "Barbieri", "age" : 42 }, "dog" : { "name" : "Raffaele", "age" : 17 } }
    { "_id" : ObjectId("5e66dd06f33974bdf098ec8f"), "firstname" : "Pietro", "surname" : "Martinelli", "username" : "user198", "age" : 14, "email" : "Pietro.Martinelli@hotmail.com", "bloodType" : "B+", "id_num" : "200603684634", "registerDate" : ISODate("2018-03-01T11:36:23.653Z"), "ticketNumber" : 8111, "jobs" : [ "Engenharia Cartográfica e de Agrimensura" ], "favFruits" : [ "Uva", "Pêssego" ], "movies" : [ { "title" : "Clube da Luta (1999)", "rating" : 0.48 } ], "mother" : { "firstname" : "Stefano", "surname" : "Martinelli", "age" : 33 }, "cat" : { "name" : "Gianluca", "age" : 6 }, "dog" : { "name" : "Alessandra", "age" : 11 } }

```

4. Identifique quantas pessoas tem gatos, quantas tem cachorro e quantas
não tem nenhum dos dois

```
    db.italians.find({ "cat": { $exists: true} });

    { "_id" : ObjectId("5e66dd05f33974bdf098ec2d"), "firstname" : "Emanuela", "surname" : "Fiore", "username" : "user100", "age" : 73, "email" : "Emanuela.Fiore@uol.com.br", "bloodType" : "O+", "id_num" : "845815017768", "registerDate" : ISODate("2008-01-23T03:39:58.206Z"), "ticketNumber" : 2063, "jobs" : [ "Libras", "Psicologia" ], "favFruits" : [ "Banana", "Pêssego", "Maçã" ], "movies" : [ { "title" : "Clube da Luta (1999)", "rating" : 0.61 } ], "father" : { "firstname" : "Manuela", "surname" : "Fiore", "age" : 93 }, "cat" : { "name" : "Tiziana", "age" : 17 }, "dog" : { "name" : "Ilaria", "age" : 7 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec2f"), "firstname" : "Mauro", "surname" : "Sanna", "username" : "user102", "age" : 65, "email" : "Mauro.Sanna@hotmail.com", "bloodType" : "A-", "id_num" : "778861110011", "registerDate" : ISODate("2008-12-12T19:33:22.754Z"), "ticketNumber" : 6088, "jobs" : [ "Gestão de Seguros" ], "favFruits" : [ "Melancia", "Kiwi" ], "movies" : [ { "title" : "1917 (2019)", "rating" : 1.01 }, { "title" : "O Poderoso Chefão II (1974)", "rating" : 0.3 } ], "cat" : { "name" : "Silvia", "age" : 5 }, "dog" : { "name" : "Silvia", "age" : 2 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec30"), "firstname" : "Michele", "surname" : "Damico", "username" : "user103", "age" : 11, "email" : "Michele.Damico@uol.com.br", "bloodType" : "B+", "id_num" : "764084688466", "registerDate" : ISODate("2016-04-23T05:29:18.410Z"), "ticketNumber" : 4996, "jobs" : [ "Silvicultura" ], "favFruits" : [ "Mamão", "Uva", "Pêssego" ], "movies" : [ { "title" : "Três Homens em Conflito (1966)", "rating" : 4.53 }, { "title" : "Vingadores: Ultimato (2019)", "rating" : 1.24 }, { "title" : "Intocáveis (2011)", "rating" : 1.04 } ], "cat" : { "name" : "Chiara", "age" : 0 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec31"), "firstname" : "Maria", "surname" : "Leone", "username" : "user104", "age" : 6, "email" : "Maria.Leone@yahoo.com", "bloodType" : "O-", "id_num" : "617344550540", "registerDate" : ISODate("2019-05-25T13:06:44.921Z"), "ticketNumber" : 3981, "jobs" : [ "Gestão de Cooperativas" ], "favFruits" : [ "Kiwi" ], "movies" : [ { "title" : "O Poderoso Chefão (1972)", "rating" : 3.12 }, { "title" : "Batman: O Cavaleiro das Trevas (2008)", "rating" : 2.99 } ], "cat" : { "name" : "Alessandro", "age" : 12 }, "dog" : { "name" : "Claudio", "age" : 16 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec33"), "firstname" : "Massimiliano", "surname" : "Bellini", "username" : "user106", "age" : 12, "email" : "Massimiliano.Bellini@outlook.com", "bloodType" : "A-", "id_num" : "304620477164", "registerDate" : ISODate("2011-06-06T10:16:58.449Z"), "ticketNumber" : 6713, "jobs" : [ "Eventos" ], "favFruits" : [ "Laranja" ], "movies" : [ { "title" : "Os Sete Samurais (1954)", "rating" : 4.55 }, { "title" : "Interestelar (2014)", "rating" : 2.89 }, { "title" : "A Vida é Bela (1997)", "rating" : 0.15 } ], "cat" : { "name" : "Rosa", "age" : 9 } }


    db.italians.find({ "dog": { $exists: true} });

    { "_id" : ObjectId("5e66dd05f33974bdf098ec2d"), "firstname" : "Emanuela", "surname" : "Fiore", "username" : "user100", "age" : 73, "email" : "Emanuela.Fiore@uol.com.br", "bloodType" : "O+", "id_num" : "845815017768", "registerDate" : ISODate("2008-01-23T03:39:58.206Z"), "ticketNumber" : 2063, "jobs" : [ "Libras", "Psicologia" ], "favFruits" : [ "Banana", "Pêssego", "Maçã" ], "movies" : [ { "title" : "Clube da Luta (1999)", "rating" : 0.61 } ], "father" : { "firstname" : "Manuela", "surname" : "Fiore", "age" : 93 }, "cat" : { "name" : "Tiziana", "age" : 17 }, "dog" : { "name" : "Ilaria", "age" : 7 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec2e"), "firstname" : "Elisa", "surname" : "Fontana", "username" : "user101", "age" : 37, "email" : "Elisa.Fontana@hotmail.com", "bloodType" : "AB-", "id_num" : "501024608875", "registerDate" : ISODate("2015-08-03T03:55:39.499Z"), "ticketNumber" : 5714, "jobs" : [ "Negócios Imobiliários" ], "favFruits" : [ "Pêssego", "Goiaba" ], "movies" : [ { "title" : "Intocáveis (2011)", "rating" : 1.87 }, { "title" : "O Poderoso Chefão (1972)", "rating" : 3.06 }, { "title" : "Parasita (2019)", "rating" : 1.2 }, { "title" : "A Origem (2010)", "rating" : 0.36 } ], "dog" : { "name" : "Lucia", "age" : 11 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec2f"), "firstname" : "Mauro", "surname" : "Sanna", "username" : "user102", "age" : 65, "email" : "Mauro.Sanna@hotmail.com", "bloodType" : "A-", "id_num" : "778861110011", "registerDate" : ISODate("2008-12-12T19:33:22.754Z"), "ticketNumber" : 6088, "jobs" : [ "Gestão de Seguros" ], "favFruits" : [ "Melancia", "Kiwi" ], "movies" : [ { "title" : "1917 (2019)", "rating" : 1.01 }, { "title" : "O Poderoso Chefão II (1974)", "rating" : 0.3 } ], "cat" : { "name" : "Silvia", "age" : 5 }, "dog" : { "name" : "Silvia", "age" : 2 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec31"), "firstname" : "Maria", "surname" : "Leone", "username" : "user104", "age" : 6, "email" : "Maria.Leone@yahoo.com", "bloodType" : "O-", "id_num" : "617344550540", "registerDate" : ISODate("2019-05-25T13:06:44.921Z"), "ticketNumber" : 3981, "jobs" : [ "Gestão de Cooperativas" ], "favFruits" : [ "Kiwi" ], "movies" : [ { "title" : "O Poderoso Chefão (1972)", "rating" : 3.12 }, { "title" : "Batman: O Cavaleiro das Trevas (2008)", "rating" : 2.99 } ], "cat" : { "name" : "Alessandro", "age" : 12 }, "dog" : { "name" : "Claudio", "age" : 16 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec36"), "firstname" : "Emanuele", "surname" : "Conte", "username" : "user109", "age" : 20, "email" : "Emanuele.Conte@uol.com.br", "bloodType" : "O-", "id_num" : "556802164300", "registerDate" : ISODate("2009-10-20T14:56:10.203Z"), "ticketNumber" : 9780, "jobs" : [ "Enfermagem", "Sistemas de Informação" ], "favFruits" : [ "Kiwi" ], "movies" : [ { "title" : "1917 (2019)", "rating" : 4.08 }, { "title" : "A Felicidade Não se Compra (1946)", "rating" : 3.66 }, { "title" : "Forrest Gump: O Contador de Histórias (1994)", "rating" : 2.83 } ], "father" : { "firstname" : "Eleonora", "surname" : "Conte", "age" : 37 }, "dog" : { "name" : "Lorenzo", "age" : 16 } }


    db.italians.find({ $and: [ { "cat": { $exists: false} }, { "dog": { $exists: false} } ] });
    
    { "_id" : ObjectId("5e66dd05f33974bdf098ec32"), "firstname" : "Eleonora", "surname" : "Monti", "username" : "user105", "age" : 24, "email" : "Eleonora.Monti@uol.com.br", "bloodType" : "A+", "id_num" : "241445011605", "registerDate" : ISODate("2009-05-26T17:09:24.103Z"), "ticketNumber" : 4769, "jobs" : [ "Agrimensura" ], "favFruits" : [ "Kiwi", "Uva" ], "movies" : [ { "title" : "Um Estranho no Ninho (1975)", "rating" : 2.41 }, { "title" : "Os Sete Samurais (1954)", "rating" : 0.76 }, { "title" : "A Felicidade Não se Compra (1946)", "rating" : 1.95 }, { "title" : "A Viagem de Chihiro (2001)", "rating" : 3.78 }, { "title" : "O Silêncio dos Inocentes (1991)", "rating" : 2.19 } ] }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec37"), "firstname" : "Sara", "surname" : "Serra", "username" : "user110", "age" : 35, "email" : "Sara.Serra@live.com", "bloodType" : "AB-", "id_num" : "312375652707", "registerDate" : ISODate("2012-12-17T11:59:47.578Z"), "ticketNumber" : 6552, "jobs" : [ "Engenharia Ambiental e Sanitária", "Turismo" ], "favFruits" : [ "Maçã" ], "movies" : [ { "title" : "A Lista de Schindler (1993)", "rating" : 1.28 }, { "title" : "Matrix (1999)", "rating" : 1.23 }, { "title" : "Interestelar (2014)", "rating" : 4.5 }, { "title" : "Intocáveis (2011)", "rating" : 2.47 } ], "father" : { "firstname" : "Fabrizio", "surname" : "Serra", "age" : 55 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec3b"), "firstname" : "Roberta", "surname" : "Serra", "username" : "user114", "age" : 54, "email" : "Roberta.Serra@live.com", "bloodType" : "B+", "id_num" : "444046702860", "registerDate" : ISODate("2007-11-15T11:28:46.165Z"), "ticketNumber" : 2510, "jobs" : [ "Fisioterapia", "Informática Biomédica" ], "favFruits" : [ "Maçã", "Pêssego" ], "movies" : [ { "title" : "O Senhor dos Anéis: A Sociedade do Anel (2001)", "rating" : 1.21 }, { "title" : "Forrest Gump: O Contador de Histórias (1994)", "rating" : 1.4 }, { "title" : "1917 (2019)", "rating" : 4.83 }, { "title" : "A Vida é Bela (1997)", "rating" : 2.78 }, { "title" : "Guerra nas Estrelas (1977)", "rating" : 3.46 } ] }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec3d"), "firstname" : "Teresa", "surname" : "Marino", "username" : "user116", "age" : 25, "email" : "Teresa.Marino@outlook.com", "bloodType" : "O-", "id_num" : "621774388405", "registerDate" : ISODate("2019-07-04T10:59:17.209Z"), "ticketNumber" : 2217, "jobs" : [ "Naturologia", "Comércio Exterior" ], "favFruits" : [ "Tangerina", "Banana" ], "movies" : [ { "title" : "O Senhor dos Anéis: As Duas Torres (2002)", "rating" : 4.38 } ] }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec3e"), "firstname" : "Valentina", "surname" : "Martino", "username" : "user117", "age" : 62, "email" : "Valentina.Martino@hotmail.com", "bloodType" : "A-", "id_num" : "520407505760", "registerDate" : ISODate("2020-02-13T02:17:01.366Z"), "ticketNumber" : 9300, "jobs" : [ "Produção Cênica" ], "favFruits" : [ "Pêssego", "Tangerina", "Tangerina" ], "movies" : [ { "title" : "O Senhor dos Anéis: As Duas Torres (2002)", "rating" : 1.78 } ] }

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
     db.italians.find({$where: function() { return this.cat != null && this.dog != null }});
    
    { "_id" : ObjectId("5e66dd05f33974bdf098ec2d"), "firstname" : "Emanuela", "surname" : "Fiore", "username" : "user100", "age" : 73, "email" : "Emanuela.Fiore@uol.com.br", "bloodType" : "O+", "id_num" : "845815017768", "registerDate" : ISODate("2008-01-23T03:39:58.206Z"), "ticketNumber" : 2063, "jobs" : [ "Libras", "Psicologia" ], "favFruits" : [ "Banana", "Pêssego", "Maçã" ], "movies" : [ { "title" : "Clube da Luta (1999)", "rating" : 0.61 } ], "father" : { "firstname" : "Manuela", "surname" : "Fiore", "age" : 93 }, "cat" : { "name" : "Tiziana", "age" : 17 }, "dog" : { "name" : "Ilaria", "age" : 7 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec2f"), "firstname" : "Mauro", "surname" : "Sanna", "username" : "user102", "age" : 65, "email" : "Mauro.Sanna@hotmail.com", "bloodType" : "A-", "id_num" : "778861110011", "registerDate" : ISODate("2008-12-12T19:33:22.754Z"), "ticketNumber" : 6088, "jobs" : [ "Gestão de Seguros" ], "favFruits" : [ "Melancia", "Kiwi" ], "movies" : [ { "title" : "1917 (2019)", "rating" : 1.01 }, { "title" : "O Poderoso Chefão II (1974)", "rating" : 0.3 } ], "cat" : { "name" : "Silvia", "age" : 5 }, "dog" : { "name" : "Silvia", "age" : 2 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec31"), "firstname" : "Maria", "surname" : "Leone", "username" : "user104", "age" : 6, "email" : "Maria.Leone@yahoo.com", "bloodType" : "O-", "id_num" : "617344550540", "registerDate" : ISODate("2019-05-25T13:06:44.921Z"), "ticketNumber" : 3981, "jobs" : [ "Gestão de Cooperativas" ], "favFruits" : [ "Kiwi" ], "movies" : [ { "title" : "O Poderoso Chefão (1972)", "rating" : 3.12 }, { "title" : "Batman: O Cavaleiro das Trevas (2008)", "rating" : 2.99 } ], "cat" : { "name" : "Alessandro", "age" : 12 }, "dog" : { "name" : "Claudio", "age" : 16 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec44"), "firstname" : "Chiara", "surname" : "Mariani", "username" : "user123", "age" : 65, "email" : "Chiara.Mariani@uol.com.br", "bloodType" : "O+", "id_num" : "630532613880", "registerDate" : ISODate("2009-01-02T09:50:44.449Z"), "ticketNumber" : 5159, "jobs" : [ "Biocombustíveis", "Musicoterapia" ], "favFruits" : [ "Melancia" ], "movies" : [ { "title" : "Harakiri (1962)", "rating" : 1.94 }, { "title" : "Gladiador (2000)", "rating" : 3.71 }, { "title" : "O Senhor dos Anéis: O Retorno do Rei (2003)", "rating" : 2.78 }, { "title" : "Harakiri (1962)", "rating" : 4.14 }, { "title" : "Harakiri (1962)", "rating" : 2.74 } ], "father" : { "firstname" : "Alberto", "surname" : "Mariani", "age" : 102 }, "cat" : { "name" : "Marco", "age" : 9 }, "dog" : { "name" : "Giorgio", "age" : 15 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec4a"), "firstname" : "Anna", "surname" : "Greco", "username" : "user129", "age" : 75, "email" : "Anna.Greco@hotmail.com", "bloodType" : "O-", "id_num" : "416148162856", "registerDate" : ISODate("2009-01-12T08:19:31.732Z"), "ticketNumber" : 9573, "jobs" : [ "Linguística" ], "favFruits" : [ "Laranja" ], "movies" : [ { "title" : "Coringa (2019)", "rating" : 2.95 }, { "title" : "Os Sete Samurais (1954)", "rating" : 0.63 } ], "cat" : { "name" : "Gabiele", "age" : 4 }, "dog" : { "name" : "Giorgio", "age" : 3 } }

```

8. Liste todas as pessoas mais novas que seus respectivos gatos.

```
    db.italians.find({
        $where: function() { return this.cat != null && this.age < this.cat.age }
    });

    { "_id" : ObjectId("5e66dd05f33974bdf098ec31"), "firstname" : "Maria", "surname" : "Leone", "username" : "user104", "age" : 6, "email" : "Maria.Leone@yahoo.com", "bloodType" : "O-", "id_num" : "617344550540", "registerDate" : ISODate("2019-05-25T13:06:44.921Z"), "ticketNumber" : 3981, "jobs" : [ "Gestão de Cooperativas" ], "favFruits" : [ "Kiwi" ], "movies" : [ { "title" : "O Poderoso Chefão (1972)", "rating" : 3.12 }, { "title" : "Batman: O Cavaleiro das Trevas (2008)", "rating" : 2.99 } ], "cat" : { "name" : "Alessandro", "age" : 12 }, "dog" : { "name" : "Claudio", "age" : 16 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec3a"), "firstname" : "Elisabetta", "surname" : "Rossetti", "username" : "user113", "age" : 8, "email" : "Elisabetta.Rossetti@yahoo.com", "bloodType" : "AB-", "id_num" : "212515734663", "registerDate" : ISODate("2011-07-03T08:55:17.491Z"), "ticketNumber" : 3618, "jobs" : [ "Odontologia" ], "favFruits" : [ "Maçã", "Mamão", "Banana" ], "movies" : [ { "title" : "Seven: Os Sete Crimes Capitais (1995)", "rating" : 1.38 }, { "title" : "Batman: O Cavaleiro das Trevas (2008)", "rating" : 2.96 }, { "title" : "12 Homens e uma Sentença (1957)", "rating" : 1.82 } ], "cat" : { "name" : "Sergio", "age" : 11 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec54"), "firstname" : "Mirko", "surname" : "Palmieri", "username" : "user139", "age" : 2, "email" : "Mirko.Palmieri@outlook.com", "bloodType" : "A+", "id_num" : "478842477448", "registerDate" : ISODate("2008-11-06T00:54:00.241Z"), "ticketNumber" : 5140, "jobs" : [ "Jogos Digitais" ], "favFruits" : [ "Goiaba", "Melancia", "Uva" ], "movies" : [ { "title" : "O Silêncio dos Inocentes (1991)", "rating" : 1.19 } ], "cat" : { "name" : "Simone", "age" : 6 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec68"), "firstname" : "Michele", "surname" : "Silvestri", "username" : "user159", "age" : 3, "email" : "Michele.Silvestri@gmail.com", "bloodType" : "A-", "id_num" : "080653174420", "registerDate" : ISODate("2008-10-04T17:35:22.032Z"), "ticketNumber" : 9667, "jobs" : [ "Ciências Atuariais", "Engenharia Acústica" ], "favFruits" : [ "Laranja", "Goiaba" ], "movies" : [ { "title" : "A Origem (2010)", "rating" : 0.76 }, { "title" : "1917 (2019)", "rating" : 2.11 }, { "title" : "O Poderoso Chefão II (1974)", "rating" : 0.27 }, { "title" : "Forrest Gump: O Contador de Histórias (1994)", "rating" : 2.3 }, { "title" : "Intocáveis (2011)", "rating" : 0.45 } ], "cat" : { "name" : "Valentina", "age" : 11 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec71"), "firstname" : "Angela", "surname" : "Lombardo", "username" : "user168", "age" : 2, "email" : "Angela.Lombardo@gmail.com", "bloodType" : "A+", "id_num" : "062712413558", "registerDate" : ISODate("2011-11-10T20:57:48.629Z"), "ticketNumber" : 6558, "jobs" : [ "Sistemas para Internet" ], "favFruits" : [ "Pêssego", "Laranja" ], "movies" : [ { "title" : "O Poderoso Chefão (1972)", "rating" : 4.92 }, { "title" : "Um Estranho no Ninho (1975)", "rating" : 1.38 } ], "cat" : { "name" : "Alessio", "age" : 17 } }

```

9. Liste as pessoas que tem o mesmo nome que seu bichano (gatou ou
cachorro)

```
    db.italians.find({
        $where: function() { return this.cat != null && this.firstname == this.cat.name }
    });

    { "_id" : ObjectId("5e66dd06f33974bdf098ecca"), "firstname" : "Giacomo", "surname" : "Caruso", "username" : "user257", "age" : 6, "email" : "Giacomo.Caruso@hotmail.com", "bloodType" : "AB+", "id_num" : "366646347112", "registerDate" : ISODate("2012-07-02T12:06:30.428Z"), "ticketNumber" : 7958, "jobs" : [ "Estudos de Mídia" ], "favFruits" : [ "Banana" ], "movies" : [ { "title" : "1917 (2019)", "rating" : 2.67 }, { "title" : "Interestelar (2014)", "rating" : 2.97 }, { "title" : "Seven: Os Sete Crimes Capitais (1995)", "rating" : 3.21 } ], "cat" : { "name" : "Giacomo", "age" : 8 } }
    { "_id" : ObjectId("5e66dd06f33974bdf098edaf"), "firstname" : "Alessandra", "surname" : "Grassi", "username" : "user486", "age" : 39, "email" : "Alessandra.Grassi@hotmail.com", "bloodType" : "B-", "id_num" : "645137345116", "registerDate" : ISODate("2014-03-05T14:41:36.369Z"), "ticketNumber" : 3085, "jobs" : [ "Museologia" ], "favFruits" : [ "Pêssego", "Maçã" ], "movies" : [ { "title" : "Um Estranho no Ninho (1975)", "rating" : 2.75 } ], "cat" : { "name" : "Alessandra", "age" : 3 } }
    { "_id" : ObjectId("5e66dd06f33974bdf098edd6"), "firstname" : "Elena", "surname" : "De Santis", "username" : "user525", "age" : 13, "email" : "Elena.De Santis@gmail.com", "bloodType" : "O+", "id_num" : "753558763151", "registerDate" : ISODate("2014-03-28T23:33:36.261Z"), "ticketNumber" : 3911, "jobs" : [ "Ciência da Computação" ], "favFruits" : [ "Mamão", "Uva", "Kiwi" ], "movies" : [ { "title" : "Um Sonho de Liberdade (1994)", "rating" : 0.8 }, { "title" : "Star Wars, Episódio V: O Império Contra-Ataca (1980)", "rating" : 2.3 } ], "cat" : { "name" : "Elena", "age" : 17 } }
    { "_id" : ObjectId("5e66dd06f33974bdf098ee66"), "firstname" : "Gianni", "surname" : "Marino", "username" : "user669", "age" : 52, "email" : "Gianni.Marino@outlook.com", "bloodType" : "A-", "id_num" : "580138821821", "registerDate" : ISODate("2011-06-27T12:26:58.853Z"), "ticketNumber" : 6776, "jobs" : [ "Processos Gerenciais", "Engenharia Mecânica" ], "favFruits" : [ "Melancia" ], "movies" : [ { "title" : "Guerra nas Estrelas (1977)", "rating" : 4.51 }, { "title" : "Coringa (2019)", "rating" : 0.72 }, { "title" : "Batman: O Cavaleiro das Trevas (2008)", "rating" : 3.78 }, { "title" : "1917 (2019)", "rating" : 4.89 } ], "cat" : { "name" : "Gianni", "age" : 2 } }
    { "_id" : ObjectId("5e66dd06f33974bdf098ee6f"), "firstname" : "Rita", "surname" : "Barbieri", "username" : "user678", "age" : 57, "email" : "Rita.Barbieri@gmail.com", "bloodType" : "B+", "id_num" : "432205706380", "registerDate" : ISODate("2011-01-09T18:24:49.754Z"), "ticketNumber" : 564, "jobs" : [ "Engenharia de Minas" ], "favFruits" : [ "Goiaba", "Goiaba", "Goiaba" ], "movies" : [ { "title" : "A Felicidade Não se Compra (1946)", "rating" : 3.88 } ], "cat" : { "name" : "Rita", "age" : 3 }, "dog" : { "name" : "Daniela", "age" : 4 } }

```

10. Projete apenas o nome e sobrenome das pessoas com tipo de sangue de
fator RH negativo

```
    db.italians.find({"bloodType" : {$regex : "-$"}});

    { "_id" : ObjectId("5e66dd05f33974bdf098ec2e"), "firstname" : "Elisa", "surname" : "Fontana", "username" : "user101", "age" : 37, "email" : "Elisa.Fontana@hotmail.com", "bloodType" : "AB-", "id_num" : "501024608875", "registerDate" : ISODate("2015-08-03T03:55:39.499Z"), "ticketNumber" : 5714, "jobs" : [ "Negócios Imobiliários" ], "favFruits" : [ "Pêssego", "Goiaba" ], "movies" : [ { "title" : "Intocáveis (2011)", "rating" : 1.87 }, { "title" : "O Poderoso Chefão (1972)", "rating" : 3.06 }, { "title" : "Parasita (2019)", "rating" : 1.2 }, { "title" : "A Origem (2010)", "rating" : 0.36 } ], "dog" : { "name" : "Lucia", "age" : 11 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec2f"), "firstname" : "Mauro", "surname" : "Sanna", "username" : "user102", "age" : 65, "email" : "Mauro.Sanna@hotmail.com", "bloodType" : "A-", "id_num" : "778861110011", "registerDate" : ISODate("2008-12-12T19:33:22.754Z"), "ticketNumber" : 6088, "jobs" : [ "Gestão de Seguros" ], "favFruits" : [ "Melancia", "Kiwi" ], "movies" : [ { "title" : "1917 (2019)", "rating" : 1.01 }, { "title" : "O Poderoso Chefão II (1974)", "rating" : 0.3 } ], "cat" : { "name" : "Silvia", "age" : 5 }, "dog" : { "name" : "Silvia", "age" : 2 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec31"), "firstname" : "Maria", "surname" : "Leone", "username" : "user104", "age" : 6, "email" : "Maria.Leone@yahoo.com", "bloodType" : "O-", "id_num" : "617344550540", "registerDate" : ISODate("2019-05-25T13:06:44.921Z"), "ticketNumber" : 3981, "jobs" : [ "Gestão de Cooperativas" ], "favFruits" : [ "Kiwi" ], "movies" : [ { "title" : "O Poderoso Chefão (1972)", "rating" : 3.12 }, { "title" : "Batman: O Cavaleiro das Trevas (2008)", "rating" : 2.99 } ], "cat" : { "name" : "Alessandro", "age" : 12 }, "dog" : { "name" : "Claudio", "age" : 16 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec33"), "firstname" : "Massimiliano", "surname" : "Bellini", "username" : "user106", "age" : 12, "email" : "Massimiliano.Bellini@outlook.com", "bloodType" : "A-", "id_num" : "304620477164", "registerDate" : ISODate("2011-06-06T10:16:58.449Z"), "ticketNumber" : 6713, "jobs" : [ "Eventos" ], "favFruits" : [ "Laranja" ], "movies" : [ { "title" : "Os Sete Samurais (1954)", "rating" : 4.55 }, { "title" : "Interestelar (2014)", "rating" : 2.89 }, { "title" : "A Vida é Bela (1997)", "rating" : 0.15 } ], "cat" : { "name" : "Rosa", "age" : 9 } }
    { "_id" : ObjectId("5e66dd05f33974bdf098ec34"), "firstname" : "Lucia", "surname" : "Piras", "username" : "user107", "age" : 33, "email" : "Lucia.Piras@gmail.com", "bloodType" : "A-", "id_num" : "752865356855", "registerDate" : ISODate("2011-04-19T23:30:42.173Z"), "ticketNumber" : 2354, "jobs" : [ "Análise e Desenvolvimento de Sistemas", "Fisioterapia" ], "favFruits" : [ "Kiwi", "Tangerina", "Kiwi" ], "movies" : [ { "title" : "Intocáveis (2011)", "rating" : 3.58 }, { "title" : "Três Homens em Conflito (1966)", "rating" : 2.94 }, { "title" : "O Senhor dos Anéis: A Sociedade do Anel (2001)", "rating" : 1.62 } ], "mother" : { "firstname" : "Sergio", "surname" : "Piras", "age" : 53 }, "cat" : { "name" : "Filipo", "age" : 5 } }
```

11. Projete apenas os animais dos italianos. Devem ser listados os animais
com nome e idade. Não mostre o identificado do mongo (ObjectId)

```
    db.italians.find({ 
        $or: [ { "cat": { $exists: true} }, 
        { "dog": { $exists: true} } ] }, 
        { "_id": 0, "cat": 1, "dog": 1}
    );
    
    { "cat" : { "name" : "Tiziana", "age" : 17 }, "dog" : { "name" : "Ilaria", "age" : 7 } }
    { "dog" : { "name" : "Lucia", "age" : 11 } }
    { "cat" : { "name" : "Silvia", "age" : 5 }, "dog" : { "name" : "Silvia", "age" : 2 } }
    { "cat" : { "name" : "Chiara", "age" : 0 } }
    { "cat" : { "name" : "Alessandro", "age" : 12 }, "dog" : { "name" : "Claudio", "age" : 16 } }

```

12. Quais são as 5 pessoas mais velhas com sobrenome Rossi?

```
    db.italians.find({ "surname": "Rossi"}).sort({"age": -1}).limit(5);

    { "_id" : ObjectId("5e66dd0bf33974bdf0990159"), "firstname" : "Rita", "surname" : "Rossi", "username" : "user5520", "age" : 79, "email" : "Rita.Rossi@uol.com.br", "bloodType" : "O+", "id_num" : "688531070341", "registerDate" : ISODate("2019-01-15T08:08:53.404Z"), "ticketNumber" : 5965, "jobs" : [ "Engenharia de Software" ], "favFruits" : [ "Goiaba", "Mamão", "Pêssego" ], "movies" : [ { "title" : "A Vida é Bela (1997)", "rating" : 1.4 }, { "title" : "O Resgate do Soldado Ryan (1998)", "rating" : 2.11 }, { "title" : "Clube da Luta (1999)", "rating" : 3.28 }, { "title" : "Cidade de Deus (2002)", "rating" : 3.05 }, { "title" : "À Espera de um Milagre (1999)", "rating" : 2.44 } ] }
    { "_id" : ObjectId("5e66dd0ef33974bdf0990ed3"), "firstname" : "Raffaele", "surname" : "Rossi", "username" : "user8970", "age" : 79, "email" : "Raffaele.Rossi@live.com", "bloodType" : "B+", "id_num" : "614357065835", "registerDate" : ISODate("2016-05-02T08:06:01.705Z"), "ticketNumber" : 2445, "jobs" : [ "Comunicação Organizacional" ], "favFruits" : [ "Banana" ], "movies" : [ { "title" : "Intocáveis (2011)", "rating" : 1.04 }, { "title" : "O Senhor dos Anéis: A Sociedade do Anel (2001)", "rating" : 2.61 }, { "title" : "Harakiri (1962)", "rating" : 0.36 }, { "title" : "Clube da Luta (1999)", "rating" : 3.69 } ], "cat" : { "name" : "Mirko", "age" : 5 }, "dog" : { "name" : "Gianluca", "age" : 13 } }
    { "_id" : ObjectId("5e66dd0bf33974bdf09901a7"), "firstname" : "Claudio", "surname" : "Rossi", "username" : "user5598", "age" : 78, "email" : "Claudio.Rossi@uol.com.br", "bloodType" : "O-", "id_num" : "748862042174", "registerDate" : ISODate("2011-09-27T13:56:59.580Z"), "ticketNumber" : 2354, "jobs" : [ "Produção Editorial", "Engenharia Civil" ], "favFruits" : [ "Banana" ], "movies" : [ { "title" : "O Senhor dos Anéis: A Sociedade do Anel (2001)", "rating" : 3.28 }, { "title" : "Um Estranho no Ninho (1975)", "rating" : 4.77 }, { "title" : "A Felicidade Não se Compra (1946)", "rating" : 2.51 }, { "title" : "Coringa (2019)", "rating" : 0.84 } ], "mother" : { "firstname" : "Fabrizio", "surname" : "Rossi", "age" : 109 }, "cat" : { "name" : "Stefano", "age" : 6 }, "dog" : { "name" : "Federica", "age" : 11 } }
    { "_id" : ObjectId("5e66dd0df33974bdf0990ce9"), "firstname" : "Massimo", "surname" : "Rossi", "username" : "user8480", "age" : 78, "email" : "Massimo.Rossi@live.com", "bloodType" : "AB+", "id_num" : "347035546577", "registerDate" : ISODate("2008-06-27T01:45:52.181Z"), "ticketNumber" : 4469, "jobs" : [ "Segurança no Trabalho", "Engenharia de Software" ], "favFruits" : [ "Mamão", "Mamão", "Mamão" ], "movies" : [ { "title" : "Três Homens em Conflito (1966)", "rating" : 0.31 }, { "title" : "O Resgate do Soldado Ryan (1998)", "rating" : 4.72 }, { "title" : "O Silêncio dos Inocentes (1991)", "rating" : 3.95 } ], "cat" : { "name" : "Valeira", "age" : 17 }, "dog" : { "name" : "Gianni", "age" : 7 } }
    { "_id" : ObjectId("5e66dd07f33974bdf098f1c0"), "firstname" : "Giulia", "surname" : "Rossi", "username" : "user1527", "age" : 77, "email" : "Giulia.Rossi@live.com", "bloodType" : "O+", "id_num" : "158483412640", "registerDate" : ISODate("2015-11-12T02:24:10.915Z"), "ticketNumber" : 2721, "jobs" : [ "Segurança da Informação" ], "favFruits" : [ "Banana", "Mamão", "Goiaba" ], "movies" : [ { "title" : "O Silêncio dos Inocentes (1991)", "rating" : 3.83 }, { "title" : "A Viagem de Chihiro (2001)", "rating" : 0.49 }, { "title" : "Um Sonho de Liberdade (1994)", "rating" : 2.7 } ], "cat" : { "name" : "Gianni", "age" : 17 }, "dog" : { "name" : "Alessandra", "age" : 15 } }
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

    db.italians.update(
        {"_id": ObjectId("5e683d8e6fcb8e074981eaad")}, 
        $inc: { "age": 1, "cat.age": 1, "dog.age": 1}
    );

    WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```

16. O Corona Vírus chegou na Itália e misteriosamente atingiu pessoas
somente com gatos e de 66 anos. Remova esses italianos.

```
    db.italians.remove({ 
        $and: [ { "age": 66 }, { "cat": { $exists: true} }, { "dog": { $exists: false} } 
    });

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
    db.italians.aggregate([{ 
        $project: { 
            _id: 0, 
            fullname: { $concat: [ "$firstname", " ", "$surname" ] } 
        } 
    }]);

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

    { "_id" : ObjectId("52853800bb1177ca391c180f"), "Ticker" : "AB", "Profit Margin" : 0.896, "Institutional Ownership" : 0.368, "EPS growth past 5 years" : -0.348, "Total Debt/Equity" : 0, "Return on Assets" : 0.086, "Sector" : "Financial", "P/S" : 13.25, "Change from Open" : 0.0047, "Performance (YTD)" : 0.3227, "Performance (Week)" : -0.0302, "Insider Transactions" : 0.5973, "P/B" : 1.4, "EPS growth quarter over quarter" : 2.391, "Payout Ratio" : 1.75, "Performance (Quarter)" : 0.0929, "Forward P/E" : 12.58, "P/E" : 15.82, "200-Day Simple Moving Average" : 0.0159, "Shares Outstanding" : 92.26, "Earnings Date" : ISODate("2013-10-24T12:30:00Z"), "52-Week High" : -0.1859, "Change" : -0.0009, "Analyst Recom" : 3, "Volatility (Week)" : 0.0264, "Country" : "USA", "Return on Equity" : 0.087, "50-Day Low" : 0.123, "Price" : 21.5, "50-Day High" : -0.0574, "Return on Investment" : 0.033, "Shares Float" : 86.66, "Dividend Yield" : 0.0743, "EPS growth next 5 years" : 0.08, "Industry" : "Asset Management", "Beta" : 1.63, "Operating Margin" : 1, "EPS (ttm)" : 1.36, "PEG" : 1.98, "Float Short" : 0.0253, "52-Week Low" : 0.4687, "Average True Range" : 0.59, "EPS growth next year" : 0.0654, "Sales growth past 5 years" : -0.298, "Company" : "AllianceBernstein Holding L.P.", "Gap" : -0.0056, "Relative Volume" : 0.63, "Volatility (Month)" : 0.0298, "Market Cap" : 1985.39, "Volume" : 199677, "Short Ratio" : 6.3, "Performance (Half Year)" : -0.1159, "Relative Strength Index (14)" : 50.05, "Insider Ownership" : 0.002, "20-Day Simple Moving Average" : -0.007, "Performance (Month)" : 0.0847, "P/Free Cash Flow" : 93.21, "Institutional Transactions" : 0.0818, "Performance (Year)" : 0.3884, "LT Debt/Equity" : 0, "Average Volume" : 348.08, "EPS growth this year" : 1.567, "50-Day Simple Moving Average" : 0.0458 }
    { "_id" : ObjectId("52853801bb1177ca391c1895"), "Ticker" : "AGNC", "Profit Margin" : 0.972, "Institutional Ownership" : 0.481, "EPS growth past 5 years" : -0.0107, "Total Debt/Equity" : 8.56, "Return on Assets" : 0.022, "Sector" : "Financial", "P/S" : 3.77, "Change from Open" : 0.0102, "Performance (YTD)" : -0.1652, "Performance (Week)" : -0.017, "Insider Transactions" : 0.4931, "P/B" : 0.86, "EPS growth quarter over quarter" : -8.2, "Payout Ratio" : 0.79, "Performance (Quarter)" : -0.0083, "Forward P/E" : 7.64, "P/E" : 3.68, "200-Day Simple Moving Average" : -0.1282, "Shares Outstanding" : 390.6, "Earnings Date" : ISODate("2013-10-28T20:30:00Z"), "52-Week High" : -0.2938, "P/Cash" : 3.93, "Change" : 0.0131, "Analyst Recom" : 2.6, "Volatility (Week)" : 0.0268, "Country" : "USA", "Return on Equity" : 0.205, "50-Day Low" : 0.0695, "Price" : 21.71, "50-Day High" : -0.1066, "Return on Investment" : 0.015, "Shares Float" : 383.97, "Dividend Yield" : 0.1493, "EPS growth next 5 years" : 0.035, "Industry" : "REIT - Residential", "Beta" : 0.51, "Sales growth quarter over quarter" : 0.073, "Operating Margin" : 0.67, "EPS (ttm)" : 5.82, "PEG" : 1.05, "Float Short" : 0.0311, "52-Week Low" : 0.1117, "Average True Range" : 0.52, "EPS growth next year" : -0.3603, "Company" : "American Capital Agency Corp.", "Gap" : 0.0028, "Relative Volume" : 0.71, "Volatility (Month)" : 0.02, "Market Cap" : 8370.56, "Volume" : 4576064, "Gross Margin" : 0.746, "Short Ratio" : 1.69, "Performance (Half Year)" : -0.2136, "Relative Strength Index (14)" : 43.53, "Insider Ownership" : 0.003, "20-Day Simple Moving Average" : -0.0318, "Performance (Month)" : -0.042, "Institutional Transactions" : 0.0077, "Performance (Year)" : -0.1503, "LT Debt/Equity" : 0, "Average Volume" : 7072.83, "EPS growth this year" : -0.169, "50-Day Simple Moving Average" : -0.0376 }
    { "_id" : ObjectId("52853801bb1177ca391c1950"), "Ticker" : "ARCC", "Profit Margin" : 0.654, "Institutional Ownership" : 0.513, "EPS growth past 5 years" : 0.105, "Total Debt/Equity" : 0.59, "Return on Assets" : 0.08, "Sector" : "Financial", "P/S" : 5.87, "Change from Open" : 0.0105, "Performance (YTD)" : 0.0805, "Performance (Week)" : 0.0023, "P/B" : 1.08, "EPS growth quarter over quarter" : 0.22, "Payout Ratio" : 0.714, "Performance (Quarter)" : 0.0548, "Forward P/E" : 10.69, "P/E" : 8.32, "200-Day Simple Moving Average" : 0.046, "Shares Outstanding" : 266.17, "Earnings Date" : ISODate("2013-11-05T13:30:00Z"), "52-Week High" : -0.0014, "P/Cash" : 46.93, "Change" : 0.0082, "Analyst Recom" : 2, "Volatility (Week)" : 0.0129, "Country" : "USA", "Return on Equity" : 0.13, "50-Day Low" : 0.0527, "Price" : 17.86, "50-Day High" : -0.0014, "Return on Investment" : 0.056, "Shares Float" : 279.11, "Dividend Yield" : 0.0858, "EPS growth next 5 years" : 0.08, "Industry" : "Diversified Investments", "Beta" : 1.62, "Sales growth quarter over quarter" : 0.16, "Operating Margin" : 0.485, "EPS (ttm)" : 2.13, "PEG" : 1.04, "Float Short" : 0.0146, "52-Week Low" : 0.2192, "Average True Range" : 0.21, "EPS growth next year" : 0.0209, "Sales growth past 5 years" : 0.317, "Company" : "Ares Capital Corporation", "Gap" : -0.0023, "Relative Volume" : 0.68, "Volatility (Month)" : 0.0109, "Market Cap" : 4716.6, "Volume" : 938330, "Gross Margin" : 0.528, "Short Ratio" : 2.68, "Performance (Half Year)" : 0.0267, "Relative Strength Index (14)" : 61.2, "20-Day Simple Moving Average" : 0.0211, "Performance (Month)" : 0.0381, "Institutional Transactions" : 0.0183, "Performance (Year)" : 0.1574, "LT Debt/Equity" : 0, "Average Volume" : 1522.64, "EPS growth this year" : 0.417, "50-Day Simple Moving Average" : 0.0272 }
    { "_id" : ObjectId("52853801bb1177ca391c195a"), "Ticker" : "ARI", "Profit Margin" : 0.576, "Institutional Ownership" : 0.631, "EPS growth past 5 years" : 0.1829, "Total Debt/Equity" : 0.28, "Return on Assets" : 0.046, "Sector" : "Financial", "P/S" : 9.35, "Change from Open" : 0.0214, "Performance (YTD)" : 0.0803, "Performance (Week)" : -0.0055, "Insider Transactions" : -0.0353, "P/B" : 0.89, "EPS growth quarter over quarter" : -0.413, "Payout Ratio" : 1.159, "Performance (Quarter)" : 0.0861, "Forward P/E" : 9.57, "P/E" : 11.88, "200-Day Simple Moving Average" : 0.0497, "Shares Outstanding" : 37.37, "Earnings Date" : ISODate("2013-11-04T21:30:00Z"), "52-Week High" : -0.0404, "P/Cash" : 3.88, "Change" : 0.024, "Analyst Recom" : 2.1, "Volatility (Week)" : 0.0135, "Country" : "USA", "Return on Equity" : 0.064, "50-Day Low" : 0.1598, "Price" : 16.67, "50-Day High" : 0.0109, "Return on Investment" : 0.044, "Shares Float" : 36.7, "Dividend Yield" : 0.0983, "EPS growth next 5 years" : 0.025, "Industry" : "REIT - Diversified", "Beta" : 0.55, "Sales growth quarter over quarter" : 0.309, "Operating Margin" : 0.682, "EPS (ttm)" : 1.37, "PEG" : 4.75, "Float Short" : 0.0182, "52-Week Low" : 0.2179, "Average True Range" : 0.24, "EPS growth next year" : 0.1739, "Company" : "Apollo Commercial Real Estate Finance, Inc.", "Gap" : 0.0025, "Relative Volume" : 1.48, "Volatility (Month)" : 0.0152, "Market Cap" : 608.45, "Volume" : 299352, "Gross Margin" : 0.919, "Short Ratio" : 3.01, "Performance (Half Year)" : -0.0502, "Relative Strength Index (14)" : 68.71, "Insider Ownership" : 0.004, "20-Day Simple Moving Average" : 0.0331, "Performance (Month)" : 0.0376, "P/Free Cash Flow" : 126.76, "Institutional Transactions" : 0.0318, "Performance (Year)" : 0.1259, "LT Debt/Equity" : 0.28, "Average Volume" : 222.35, "EPS growth this year" : 0.193, "50-Day Simple Moving Average" : 0.0673 }
    { "_id" : ObjectId("52853801bb1177ca391c1968"), "Ticker" : "ARR", "Profit Margin" : 0.848, "Institutional Ownership" : 0.318, "EPS growth past 5 years" : 0.813, "Total Debt/Equity" : 8.92, "Return on Assets" : 0.031, "Sector" : "Financial", "P/S" : 1.7, "Change from Open" : 0.0223, "Performance (YTD)" : -0.2821, "Performance (Week)" : -0.0025, "Insider Transactions" : 0.2313, "P/B" : 0.68, "Payout Ratio" : 0.474, "Performance (Quarter)" : -0.0195, "Forward P/E" : 6.79, "P/E" : 1.88, "200-Day Simple Moving Average" : -0.1454, "Shares Outstanding" : 372.59, "Earnings Date" : ISODate("2013-10-28T04:00:00Z"), "52-Week High" : -0.3453, "P/Cash" : 1.87, "Change" : 0.0249, "Analyst Recom" : 2.6, "Volatility (Week)" : 0.024, "Country" : "USA", "Return on Equity" : 0.308, "50-Day Low" : 0.0728, "Price" : 4.12, "50-Day High" : -0.0678, "Return on Investment" : 0.011, "Shares Float" : 366.32, "Dividend Yield" : 0.1493, "EPS growth next 5 years" : -0.049, "Industry" : "REIT - Residential", "Beta" : 0.3, "Operating Margin" : 0.858, "EPS (ttm)" : 2.14, "Float Short" : 0.0415, "52-Week Low" : 0.1495, "Average True Range" : 0.09, "EPS growth next year" : -0.0878, "Company" : "ARMOUR Residential REIT, Inc.", "Gap" : 0.0025, "Relative Volume" : 1.37, "Volatility (Month)" : 0.0218, "Market Cap" : 1497.82, "Volume" : 6608855, "Short Ratio" : 2.87, "Performance (Half Year)" : -0.2651, "Relative Strength Index (14)" : 51.26, "Insider Ownership" : 0.002, "20-Day Simple Moving Average" : -0.0024, "Performance (Month)" : -0.0099, "P/Free Cash Flow" : 10.46, "Institutional Transactions" : 0.0016, "Performance (Year)" : -0.286, "LT Debt/Equity" : 0, "Average Volume" : 5299, "EPS growth this year" : 7.533, "50-Day Simple Moving Average" : 0.0048 }
    { "_id" : ObjectId("52853801bb1177ca391c1998"), "Ticker" : "ATHL", "Profit Margin" : 0.732, "Institutional Ownership" : 0.753, "EPS growth past 5 years" : 0, "Total Debt/Equity" : 1.81, "Current Ratio" : 0.5, "Return on Assets" : 0.218, "Sector" : "Basic Materials", "P/S" : 10.42, "Change from Open" : 0.0088, "Performance (YTD)" : 0.1851, "Performance (Week)" : 0.1049, "Quick Ratio" : 0.5, "Insider Transactions" : -0.2682, "P/B" : 7.24, "EPS growth quarter over quarter" : -0.566, "Payout Ratio" : 0, "Performance (Quarter)" : 0.2007, "Forward P/E" : 27.38, "P/E" : 28.16, "200-Day Simple Moving Average" : 0.0877, "Shares Outstanding" : 66.34, "Earnings Date" : ISODate("2013-11-11T21:30:00Z"), "52-Week High" : -0.0439, "P/Cash" : 866.67, "Change" : 0.0126, "Analyst Recom" : 2.3, "Volatility (Week)" : 0.0678, "Country" : "USA", "Return on Equity" : 0.528, "50-Day Low" : 0.2479, "Price" : 33.07, "50-Day High" : -0.0439, "Return on Investment" : 0.08, "Shares Float" : 76.13, "EPS growth next 5 years" : 0.5, "Industry" : "Independent Oil & Gas", "Sales growth quarter over quarter" : 0.964, "Operating Margin" : 0.394, "EPS (ttm)" : 1.16, "PEG" : 0.56, "Float Short" : 0.0046, "52-Week Low" : 0.3097, "Average True Range" : 1.53, "EPS growth next year" : 0.6013, "Company" : "Athlon Energy Inc.", "Gap" : 0.0037, "Relative Volume" : 0.59, "Volatility (Month)" : 0.0464, "Market Cap" : 2166.66, "Volume" : 177265, "Gross Margin" : 0.791, "Short Ratio" : 1.07, "Relative Strength Index (14)" : 56.58, "Insider Ownership" : 0.09, "20-Day Simple Moving Average" : 0.0373, "Performance (Month)" : 0.0102, "LT Debt/Equity" : 1.81, "Average Volume" : 330.36, "EPS growth this year" : 0, "50-Day Simple Moving Average" : 0.0476 }
    { "_id" : ObjectId("52853801bb1177ca391c19f6"), "Ticker" : "AYR", "Profit Margin" : 0.548, "Institutional Ownership" : 0.745, "EPS growth past 5 years" : -0.228, "Total Debt/Equity" : 2.08, "Return on Assets" : 0.066, "Sector" : "Services", "P/S" : 1.92, "Change from Open" : 0.0058, "Performance (YTD)" : 0.5577, "Performance (Week)" : -0.0032, "Insider Transactions" : -0.0052, "P/B" : 0.83, "EPS growth quarter over quarter" : -0.656, "Payout Ratio" : 0.123, "Performance (Quarter)" : 0.1566, "Forward P/E" : 10.45, "P/E" : 126.07, "200-Day Simple Moving Average" : 0.2063, "Shares Outstanding" : 70.35, "Earnings Date" : ISODate("2013-10-31T12:30:00Z"), "52-Week High" : -0.0257, "P/Cash" : 5.58, "Change" : 0.0042, "Analyst Recom" : 2.6, "Volatility (Week)" : 0.0202, "Country" : "USA", "Return on Equity" : 0.257, "50-Day Low" : 0.1304, "Price" : 18.99, "50-Day High" : -0.0257, "Return on Investment" : 0.007, "Shares Float" : 64.67, "Dividend Yield" : 0.0349, "EPS growth next 5 years" : 0.292, "Industry" : "Rental & Leasing Services", "Beta" : 2.07, "Sales growth quarter over quarter" : -0.016, "Operating Margin" : 0.457, "EPS (ttm)" : 0.15, "PEG" : 4.32, "Float Short" : 0.0327, "52-Week Low" : 0.8106, "Average True Range" : 0.37, "EPS growth next year" : 0.4873, "Sales growth past 5 years" : 0.125, "Company" : "Aircastle LTD", "Gap" : -0.0016, "Relative Volume" : 0.39, "Volatility (Month)" : 0.0193, "Market Cap" : 1330.3, "Volume" : 200382, "Short Ratio" : 3.78, "Performance (Half Year)" : 0.2295, "Relative Strength Index (14)" : 58.67, "Insider Ownership" : 0.008, "20-Day Simple Moving Average" : 0.0054, "Performance (Month)" : 0.0849, "P/Free Cash Flow" : 3.39, "Institutional Transactions" : -0.0268, "Performance (Year)" : 0.7493, "LT Debt/Equity" : 2.08, "Average Volume" : 559.42, "EPS growth this year" : -0.72, "50-Day Simple Moving Average" : 0.0545 }
    { "_id" : ObjectId("52853801bb1177ca391c1a97"), "Ticker" : "BK", "Profit Margin" : 0.63, "Institutional Ownership" : 0.826, "EPS growth past 5 years" : -0.03, "Total Debt/Equity" : 0.53, "Return on Assets" : 0.006, "Sector" : "Financial", "P/S" : 11.32, "Change from Open" : -0.0015, "Performance (YTD)" : 0.3095, "Performance (Week)" : 0.0195, "Insider Transactions" : -0.1546, "P/B" : 1.07, "EPS growth quarter over quarter" : 0.344, "Payout Ratio" : 0.304, "Performance (Quarter)" : 0.0898, "Forward P/E" : 13.19, "P/E" : 18.03, "200-Day Simple Moving Average" : 0.127, "Shares Outstanding" : 1148.72, "Earnings Date" : ISODate("2013-10-16T12:30:00Z"), "52-Week High" : -0.0069, "P/Cash" : 0.22, "Change" : 0.003, "Analyst Recom" : 2.7, "Volatility (Week)" : 0.0216, "Country" : "USA", "Return on Equity" : 0.06, "50-Day Low" : 0.1255, "Price" : 33.1, "50-Day High" : -0.0069, "Return on Investment" : 0.042, "Shares Float" : 1146.23, "Dividend Yield" : 0.0182, "EPS growth next 5 years" : 0.066, "Industry" : "Asset Management", "Beta" : 1.16, "Sales growth quarter over quarter" : -0.025, "EPS (ttm)" : 1.83, "PEG" : 2.73, "Float Short" : 0.0125, "52-Week Low" : 0.4512, "Average True Range" : 0.54, "EPS growth next year" : 0.096, "Sales growth past 5 years" : -0.092, "Company" : "The Bank of New York Mellon Corporation", "Gap" : 0.0045, "Relative Volume" : 0.61, "Volatility (Month)" : 0.0155, "Market Cap" : 37907.89, "Volume" : 2578576, "Short Ratio" : 3.1, "Performance (Half Year)" : 0.1156, "Relative Strength Index (14)" : 63.27, "Insider Ownership" : 0.001, "20-Day Simple Moving Average" : 0.032, "Performance (Month)" : 0.0749, "Institutional Transactions" : 0.0015, "Performance (Year)" : 0.4019, "LT Debt/Equity" : 0.53, "Average Volume" : 4611.68, "EPS growth this year" : 0, "50-Day Simple Moving Average" : 0.0626 }
    { "_id" : ObjectId("52853801bb1177ca391c1abd"), "Ticker" : "BLX", "Profit Margin" : 0.588, "Institutional Ownership" : 0.281, "EPS growth past 5 years" : 0.045, "Total Debt/Equity" : 3.73, "Return on Assets" : 0.017, "Sector" : "Financial", "P/S" : 5.22, "Change from Open" : 0.0103, "Performance (YTD)" : 0.2812, "Performance (Week)" : -0.0131, "P/B" : 1.19, "EPS growth quarter over quarter" : -0.506, "Payout Ratio" : 0.372, "Performance (Quarter)" : 0.0597, "Forward P/E" : 9.32, "P/E" : 13.01, "200-Day Simple Moving Average" : 0.1134, "Shares Outstanding" : 38.22, "Earnings Date" : ISODate("2013-10-16T12:30:00Z"), "52-Week High" : -0.0161, "P/Cash" : 1.71, "Change" : 0.0095, "Analyst Recom" : 1.7, "Volatility (Week)" : 0.023, "Country" : "Panama", "Return on Equity" : 0.137, "50-Day Low" : 0.1075, "Price" : 26.54, "50-Day High" : -0.0161, "Return on Investment" : 0.027, "Shares Float" : 29.25, "Dividend Yield" : 0.0456, "EPS growth next 5 years" : 0.0698, "Industry" : "Foreign Money Center Banks", "Beta" : 1.19, "Sales growth quarter over quarter" : 0, "Operating Margin" : 0.809, "EPS (ttm)" : 2.02, "PEG" : 1.86, "Float Short" : 0.0296, "52-Week Low" : 0.366, "Average True Range" : 0.49, "EPS growth next year" : 0.2192, "Sales growth past 5 years" : -0.062, "Company" : "Banco Latinoamericano de Comercio Exterior, S.A", "Gap" : -0.0008, "Relative Volume" : 1.05, "Volatility (Month)" : 0.0205, "Market Cap" : 1004.75, "Volume" : 102478, "Short Ratio" : 8.07, "Performance (Half Year)" : 0.1597, "Relative Strength Index (14)" : 60.34, "Insider Ownership" : 0.0706, "20-Day Simple Moving Average" : 0.0098, "Performance (Month)" : 0.0554, "P/Free Cash Flow" : 56.77, "Institutional Transactions" : 0.0149, "Performance (Year)" : 0.2983, "LT Debt/Equity" : 1.91, "Average Volume" : 107.45, "EPS growth this year" : 0.098, "50-Day Simple Moving Average" : 0.0498 }
    { "_id" : ObjectId("52853801bb1177ca391c1af0"), "Ticker" : "BPO", "Profit Margin" : 0.503, "Institutional Ownership" : 0.958, "EPS growth past 5 years" : 0.354, "Total Debt/Equity" : 1.15, "Current Ratio" : 1, "Return on Assets" : 0.043, "Sector" : "Financial", "P/S" : 4.04, "Change from Open" : 0.001, "Performance (YTD)" : 0.1519, "Performance (Week)" : -0.0052, "Quick Ratio" : 1, "P/B" : 0.9, "EPS growth quarter over quarter" : -0.415, "Payout Ratio" : 0.235, "Performance (Quarter)" : 0.1825, "Forward P/E" : 18.74, "P/E" : 8.65, "200-Day Simple Moving Average" : 0.1124, "Shares Outstanding" : 505, "Earnings Date" : ISODate("2011-02-11T13:30:00Z"), "52-Week High" : -0.022, "P/Cash" : 22.13, "Change" : 0.0021, "Analyst Recom" : 3.1, "Volatility (Week)" : 0.0127, "Country" : "USA", "Return on Equity" : 0.115, "50-Day Low" : 0.1976, "Price" : 19.15, "50-Day High" : -0.022, "Return on Investment" : 0.015, "Shares Float" : 504.86, "Dividend Yield" : 0.0293, "EPS growth next 5 years" : 0.0735, "Industry" : "Property Management", "Beta" : 1.64, "Sales growth quarter over quarter" : 0.01, "Operating Margin" : 0.552, "EPS (ttm)" : 2.21, "PEG" : 1.18, "Float Short" : 0.0062, "52-Week Low" : 0.2728, "Average True Range" : 0.23, "EPS growth next year" : -0.105, "Sales growth past 5 years" : -0.043, "Company" : "Brookfield Properties Corporation", "Gap" : 0.001, "Relative Volume" : 0.17, "Volatility (Month)" : 0.0112, "Market Cap" : 9650.55, "Volume" : 249482, "Gross Margin" : 0.621, "Short Ratio" : 1.9, "Performance (Half Year)" : 0.0269, "Relative Strength Index (14)" : 62.08, "Insider Ownership" : 0.4972, "20-Day Simple Moving Average" : 0.012, "Performance (Month)" : 0.0154, "Institutional Transactions" : -0.004, "Performance (Year)" : 0.2482, "LT Debt/Equity" : 1.15, "Average Volume" : 1650.73, "EPS growth this year" : -0.212, "50-Day Simple Moving Average" : 0.0538 }

```

2. Liste as ações com perdas (limite a 10 novamente)

```
    db.stocks.find({"Return on Investment":{$lt: 0}}).limit(10);

    { "_id" : ObjectId("52853800bb1177ca391c1806"), "Ticker" : "AAOI", "Profit Margin" : -0.023, "Institutional Ownership" : 0.114, "EPS growth past 5 years" : 0, "Current Ratio" : 1.5, "Return on Assets" : -0.048, "Sector" : "Technology", "P/S" : 2.3, "Change from Open" : -0.0215, "Performance (YTD)" : 0.2671, "Performance (Week)" : -0.0381, "Quick Ratio" : 0.9, "EPS growth quarter over quarter" : -1, "Forward P/E" : 12.77, "200-Day Simple Moving Average" : 0.0654, "Shares Outstanding" : 12.6, "52-Week High" : -0.0904, "P/Cash" : 16.23, "Change" : -0.0269, "Analyst Recom" : 1.8, "Volatility (Week)" : 0.0377, "Country" : "USA", "Return on Equity" : 0.043, "50-Day Low" : 0.3539, "Price" : 12.28, "50-Day High" : -0.0904, "Return on Investment" : -0.004, "Shares Float" : 11.46, "Industry" : "Semiconductor - Integrated Circuits", "Sales growth quarter over quarter" : 0.256, "Operating Margin" : -0.007, "EPS (ttm)" : -0.13, "Float Short" : 0.0011, "52-Week Low" : 0.3539, "Average True Range" : 0.63, "EPS growth next year" : 38.52, "Company" : "Applied Optoelectronics, Inc.", "Gap" : -0.0055, "Relative Volume" : 0.12, "Volatility (Month)" : 0.0608, "Market Cap" : 159.06, "Volume" : 12203, "Gross Margin" : 0.292, "Short Ratio" : 0.12, "Insider Ownership" : 0.021, "20-Day Simple Moving Average" : -0.0251, "Performance (Month)" : 0.2397, "Average Volume" : 110.95, "EPS growth this year" : 0.833, "50-Day Simple Moving Average" : 0.0654 }
    { "_id" : ObjectId("52853800bb1177ca391c180b"), "Ticker" : "AAU", "Institutional Ownership" : 0.059, "EPS growth past 5 years" : -0.232, "Total Debt/Equity" : 0, "Current Ratio" : 44.8, "Return on Assets" : -0.207, "Sector" : "Basic Materials", "P/S" : 250.21, "Change from Open" : -0.0159, "Performance (YTD)" : -0.6057, "Performance (Week)" : -0.0385, "Quick Ratio" : 44, "P/B" : 1.58, "EPS growth quarter over quarter" : 0.333, "Performance (Quarter)" : -0.399, "200-Day Simple Moving Average" : -0.2745, "Shares Outstanding" : 60.05, "52-Week High" : -0.6242, "P/Cash" : 4.78, "Change" : -0.008, "Volatility (Week)" : 0.0617, "Country" : "Canada", "Return on Equity" : -0.209, "50-Day Low" : 0.0333, "Price" : 1.24, "50-Day High" : -0.2994, "Return on Investment" : -0.203, "Shares Float" : 52.97, "Industry" : "Gold", "Beta" : 0.43, "EPS (ttm)" : -0.16, "Float Short" : 0.0093, "52-Week Low" : 0.1273, "Average True Range" : 0.06, "Sales growth past 5 years" : -0.156, "Company" : "Almaden Minerals Ltd.", "Gap" : 0.008, "Relative Volume" : 0.32, "Volatility (Month)" : 0.0468, "Market Cap" : 75.06, "Volume" : 34762, "Short Ratio" : 4.14, "Performance (Half Year)" : -0.1935, "Relative Strength Index (14)" : 36.92, "Insider Ownership" : 0.0536, "20-Day Simple Moving Average" : -0.0722, "Performance (Month)" : 0.0246, "Institutional Transactions" : 1.7402, "Performance (Year)" : -0.5117, "LT Debt/Equity" : 0, "Average Volume" : 119.04, "EPS growth this year" : -2.417, "50-Day Simple Moving Average" : -0.1017 }
    { "_id" : ObjectId("52853800bb1177ca391c180c"), "Ticker" : "AAV", "Profit Margin" : -0.232, "Institutional Ownership" : 0.58, "EPS growth past 5 years" : -0.265, "Total Debt/Equity" : 0.32, "Current Ratio" : 0.8, "Return on Assets" : -0.032, "Sector" : "Basic Materials", "P/S" : 2.64, "Change from Open" : 0.0286, "Performance (YTD)" : 0.1914, "Performance (Week)" : 0.0158, "Quick Ratio" : 0.8, "P/B" : 0.63, "EPS growth quarter over quarter" : 1.556, "Performance (Quarter)" : 0.0349, "200-Day Simple Moving Average" : 0.0569, "Shares Outstanding" : 168.38, "Earnings Date" : ISODate("2011-03-16T04:00:00Z"), "52-Week High" : -0.1242, "Change" : 0.0233, "Analyst Recom" : 2.7, "Volatility (Week)" : 0.0381, "Country" : "Canada", "Return on Equity" : -0.055, "50-Day Low" : 0.1127, "Price" : 3.95, "50-Day High" : -0.0436, "Return on Investment" : -0.068, "Shares Float" : 167.07, "Industry" : "Oil & Gas Drilling & Exploration", "Beta" : 2.05, "Sales growth quarter over quarter" : 0.399, "Operating Margin" : 0.102, "EPS (ttm)" : -0.34, "Float Short" : 0.0008, "52-Week Low" : 0.4158, "Average True Range" : 0.12, "EPS growth next year" : -0.667, "Sales growth past 5 years" : -0.121, "Company" : "Advantage Oil & Gas Ltd.", "Gap" : -0.0052, "Relative Volume" : 0.85, "Volatility (Month)" : 0.0303, "Market Cap" : 649.96, "Volume" : 116750, "Gross Margin" : 0.682, "Short Ratio" : 0.89, "Performance (Half Year)" : 0.0078, "Relative Strength Index (14)" : 52.62, "Insider Ownership" : 0.0025, "20-Day Simple Moving Average" : -0.0001, "Performance (Month)" : 0.0158, "Institutional Transactions" : 0.0402, "Performance (Year)" : 0.1386, "LT Debt/Equity" : 0.32, "Average Volume" : 149.81, "EPS growth this year" : 0.42, "50-Day Simple Moving Average" : 0.023 }
    { "_id" : ObjectId("52853800bb1177ca391c1815"), "Ticker" : "ABCD", "Profit Margin" : -0.645, "Institutional Ownership" : 0.186, "EPS growth past 5 years" : -0.195, "Current Ratio" : 1.4, "Return on Assets" : -0.416, "Sector" : "Services", "P/S" : 0.41, "Change from Open" : 0, "Performance (YTD)" : 0.2072, "Performance (Week)" : 0.0229, "Quick Ratio" : 1.2, "Insider Transactions" : -0.0267, "EPS growth quarter over quarter" : 1.022, "Performance (Quarter)" : -0.0496, "200-Day Simple Moving Average" : 0.0446, "Shares Outstanding" : 47.36, "Earnings Date" : ISODate("2013-11-07T21:30:00Z"), "52-Week High" : -0.2757, "P/Cash" : 1.37, "Change" : 0, "Analyst Recom" : 2, "Volatility (Week)" : 0.0737, "Country" : "USA", "Return on Equity" : 3.596, "50-Day Low" : 0.072, "Price" : 1.34, "50-Day High" : -0.2299, "Return on Investment" : -0.876, "Shares Float" : 15.11, "Industry" : "Education & Training Services", "Beta" : 1.7, "Sales growth quarter over quarter" : 0.059, "Operating Margin" : 0.048, "EPS (ttm)" : -2.06, "Float Short" : 0.0007, "52-Week Low" : 0.5952, "Average True Range" : 0.09, "Sales growth past 5 years" : 0.084, "Company" : "Cambium Learning Group, Inc.", "Gap" : 0, "Relative Volume" : 0.04, "Volatility (Month)" : 0.0584, "Market Cap" : 63.46, "Volume" : 1600, "Gross Margin" : 0.552, "Short Ratio" : 0.21, "Performance (Half Year)" : 0.1356, "Relative Strength Index (14)" : 48.07, "Insider Ownership" : 0.003, "20-Day Simple Moving Average" : 0.0037, "Performance (Month)" : -0.0074, "P/Free Cash Flow" : 2.47, "Institutional Transactions" : -0.095, "Performance (Year)" : 0.6543, "Average Volume" : 48.58, "EPS growth this year" : -1.533, "50-Day Simple Moving Average" : -0.064 }
    { "_id" : ObjectId("52853800bb1177ca391c1817"), "Ticker" : "ABFS", "Profit Margin" : -0.005, "Institutional Ownership" : 0.921, "EPS growth past 5 years" : -0.164, "Total Debt/Equity" : 0.31, "Current Ratio" : 1.3, "Return on Assets" : -0.01, "Sector" : "Services", "P/S" : 0.37, "Change from Open" : -0.006, "Performance (YTD)" : 2.3474, "Performance (Week)" : 0.1949, "Quick Ratio" : 1.3, "Insider Transactions" : 0.1293, "P/B" : 1.69, "EPS growth quarter over quarter" : -0.591, "Performance (Quarter)" : 0.3813, "Forward P/E" : 18.66, "200-Day Simple Moving Average" : 0.6449, "Shares Outstanding" : 25.69, "Earnings Date" : ISODate("2013-11-11T13:30:00Z"), "52-Week High" : -0.0166, "P/Cash" : 6.87, "Change" : -0.0082, "Analyst Recom" : 2.8, "Volatility (Week)" : 0.0625, "Country" : "USA", "Return on Equity" : -0.022, "50-Day Low" : 0.474, "Price" : 31.44, "50-Day High" : -0.0166, "Return on Investment" : -0.008, "Shares Float" : 24.3, "Dividend Yield" : 0.0038, "EPS growth next 5 years" : 0.1, "Industry" : "Trucking", "Beta" : 1.91, "Sales growth quarter over quarter" : 0.13, "Operating Margin" : -0.006, "EPS (ttm)" : -0.4, "Float Short" : 0.1176, "52-Week Low" : 3.9271, "Average True Range" : 1.58, "EPS growth next year" : 7.0142, "Sales growth past 5 years" : 0.024, "Company" : "Arkansas Best Corporation", "Gap" : -0.0022, "Relative Volume" : 0.73, "Volatility (Month)" : 0.0537, "Market Cap" : 814.5, "Volume" : 351906, "Gross Margin" : 0.212, "Short Ratio" : 5.44, "Performance (Half Year)" : 0.8592, "Relative Strength Index (14)" : 67.77, "Insider Ownership" : 0.034, "20-Day Simple Moving Average" : 0.1304, "Performance (Month)" : 0.3319, "P/Free Cash Flow" : 13.67, "Institutional Transactions" : 0.0328, "Performance (Year)" : 3.4336, "LT Debt/Equity" : 0.2, "Average Volume" : 525.42, "EPS growth this year" : -2.348, "50-Day Simple Moving Average" : 0.1974 }
    { "_id" : ObjectId("52853800bb1177ca391c181b"), "Ticker" : "ABMC", "Profit Margin" : -0.0966, "Institutional Ownership" : 0.12, "EPS growth past 5 years" : 0, "Total Debt/Equity" : 0.63, "Current Ratio" : 1.74, "Return on Assets" : -0.1194, "Sector" : "Healthcare", "P/S" : 0.34, "Change from Open" : 0, "Performance (YTD)" : 0.3077, "Performance (Week)" : 0.1333, "Quick Ratio" : 0.57, "P/B" : 1, "EPS growth quarter over quarter" : -2.4252, "Performance (Quarter)" : 0, "200-Day Simple Moving Average" : 0.0413, "Shares Outstanding" : 21.74, "Earnings Date" : ISODate("2013-11-11T05:00:00Z"), "52-Week High" : -0.3929, "P/Cash" : 6.26, "Change" : 0, "Volatility (Week)" : 0.0695, "Country" : "USA", "Return on Equity" : -0.2455, "50-Day Low" : 1.4286, "Price" : 0.17, "50-Day High" : -0.0556, "Return on Investment" : -0.1961, "Shares Float" : 18.7, "Industry" : "Diagnostic Substances", "Beta" : 1.71, "Sales growth quarter over quarter" : -0.1896, "Operating Margin" : -0.0734, "EPS (ttm)" : -0.05, "Float Short" : 0.0003, "52-Week Low" : 1.4286, "Average True Range" : 0.02, "Sales growth past 5 years" : 0.0028, "Company" : "American Bio Medica Corp.", "Gap" : 0, "Relative Volume" : 0.04, "Volatility (Month)" : 0.0517, "Market Cap" : 3.7, "Volume" : 0, "Gross Margin" : 0.3916, "Short Ratio" : 0.43, "Performance (Half Year)" : 0.0625, "Relative Strength Index (14)" : 56.93, "Insider Ownership" : 0.14, "20-Day Simple Moving Average" : 0.1039, "Performance (Month)" : 0.2143, "Institutional Transactions" : -0.1183, "Performance (Year)" : -0.0556, "LT Debt/Equity" : 0.2, "Average Volume" : 13.73, "EPS growth this year" : 0.1416, "50-Day Simple Moving Average" : 0.1502 }
    { "_id" : ObjectId("52853800bb1177ca391c1821"), "Ticker" : "ABX", "Profit Margin" : -0.769, "Institutional Ownership" : 0.739, "EPS growth past 5 years" : -0.206, "Total Debt/Equity" : 1.13, "Current Ratio" : 1.8, "Return on Assets" : -0.241, "Sector" : "Basic Materials", "P/S" : 1.32, "Change from Open" : -0.0019, "Performance (YTD)" : -0.4728, "Performance (Week)" : -0.0131, "Quick Ratio" : 1, "P/B" : 1.33, "EPS growth quarter over quarter" : -0.727, "Performance (Quarter)" : -0.084, "Forward P/E" : 8.19, "200-Day Simple Moving Average" : -0.1368, "Shares Outstanding" : 1001, "Earnings Date" : ISODate("2011-02-17T13:30:00Z"), "52-Week High" : -0.4877, "P/Cash" : 7.94, "Change" : 0.0014, "Analyst Recom" : 2.6, "Volatility (Week)" : 0.0202, "Country" : "Canada", "Return on Equity" : -0.592, "50-Day Low" : 0.0581, "Price" : 18.13, "50-Day High" : -0.121, "Return on Investment" : -0.017, "Shares Float" : 997.93, "Dividend Yield" : 0.011, "EPS growth next 5 years" : 0.02, "Industry" : "Gold", "Beta" : 0.46, "Sales growth quarter over quarter" : -0.122, "Operating Margin" : 0.366, "EPS (ttm)" : -10.08, "Float Short" : 0.0118, "52-Week Low" : 0.3525, "Average True Range" : 0.57, "EPS growth next year" : -0.16, "Sales growth past 5 years" : 0.193, "Company" : "Barrick Gold Corporation", "Gap" : 0.0033, "Relative Volume" : 1.09, "Volatility (Month)" : 0.0277, "Market Cap" : 18118.1, "Volume" : 17478164, "Gross Margin" : 0.444, "Short Ratio" : 0.67, "Performance (Half Year)" : -0.0479, "Relative Strength Index (14)" : 41.96, "20-Day Simple Moving Average" : -0.0436, "Performance (Month)" : 0.018, "Institutional Transactions" : 0.0315, "Performance (Year)" : -0.474, "LT Debt/Equity" : 1.07, "Average Volume" : 17602.98, "EPS growth this year" : -1.147, "50-Day Simple Moving Average" : -0.0239 }
    { "_id" : ObjectId("52853800bb1177ca391c1822"), "Ticker" : "ACAD", "Institutional Ownership" : 0.929, "EPS growth past 5 years" : 0.25, "Total Debt/Equity" : 0, "Current Ratio" : 26.5, "Return on Assets" : -0.221, "Sector" : "Healthcare", "P/S" : 407.82, "Change from Open" : -0.0431, "Performance (YTD)" : 3.9419, "Performance (Week)" : 0.0943, "Quick Ratio" : 26.5, "Insider Transactions" : 0.2417, "P/B" : 10.54, "EPS growth quarter over quarter" : -0.1, "Performance (Quarter)" : 0.1713, "200-Day Simple Moving Average" : 0.4127, "Shares Outstanding" : 83.41, "Earnings Date" : ISODate("2013-11-06T21:30:00Z"), "52-Week High" : -0.2311, "P/Cash" : 9.33, "Change" : -0.0052, "Analyst Recom" : 1.9, "Volatility (Week)" : 0.0625, "Country" : "USA", "Return on Equity" : -0.268, "50-Day Low" : 0.1634, "Price" : 22.86, "50-Day High" : -0.2311, "Return on Investment" : -0.246, "Shares Float" : 90.65, "EPS growth next 5 years" : 0.2, "Industry" : "Biotechnology", "Beta" : 2.68, "Sales growth quarter over quarter" : -0.167, "EPS (ttm)" : -0.34, "Float Short" : 0.099, "52-Week Low" : 11.7, "Average True Range" : 1.8, "EPS growth next year" : -0.205, "Sales growth past 5 years" : -0.084, "Company" : "ACADIA Pharmaceuticals, Inc.", "Gap" : 0.0396, "Relative Volume" : 0.46, "Volatility (Month)" : 0.0706, "Market Cap" : 1916.76, "Volume" : 1066506, "Short Ratio" : 3.51, "Performance (Half Year)" : 0.7663, "Relative Strength Index (14)" : 50.31, "Insider Ownership" : 0.001, "20-Day Simple Moving Average" : 0.0006, "Performance (Month)" : -0.0065, "Institutional Transactions" : 0.0151, "Performance (Year)" : 9.891, "LT Debt/Equity" : 0, "Average Volume" : 2558.02, "EPS growth this year" : 0.136, "50-Day Simple Moving Average" : -0.0391 }
    { "_id" : ObjectId("52853800bb1177ca391c1826"), "Ticker" : "ACCL", "Profit Margin" : -0.014, "Institutional Ownership" : 0.911, "EPS growth past 5 years" : -0.421, "Total Debt/Equity" : 0, "Current Ratio" : 1.4, "Return on Assets" : -0.006, "Sector" : "Technology", "P/S" : 3.13, "Change from Open" : 0.0011, "Performance (YTD)" : 0.0331, "Performance (Week)" : 0.0108, "Quick Ratio" : 1.4, "Insider Transactions" : -0.1768, "P/B" : 2.1, "Performance (Quarter)" : 0.0331, "Forward P/E" : 24.35, "200-Day Simple Moving Average" : 0.0112, "Shares Outstanding" : 55.66, "Earnings Date" : ISODate("2013-10-30T20:30:00Z"), "52-Week High" : -0.071, "P/Cash" : 4.14, "Change" : -0.0064, "Analyst Recom" : 2.3, "Volatility (Week)" : 0.0189, "Country" : "USA", "Return on Equity" : -0.01, "50-Day Low" : 0.0322, "Price" : 9.29, "50-Day High" : -0.071, "Return on Investment" : -0.086, "Shares Float" : 55.4, "EPS growth next 5 years" : 0.2, "Industry" : "Application Software", "Beta" : 0.84, "Sales growth quarter over quarter" : 0.01, "Operating Margin" : -0.091, "EPS (ttm)" : -0.05, "Float Short" : 0.0179, "52-Week Low" : 0.1987, "Average True Range" : 0.21, "EPS growth next year" : 0.1294, "Sales growth past 5 years" : 0.153, "Company" : "Accelrys Inc.", "Gap" : -0.0075, "Relative Volume" : 0.31, "Volatility (Month)" : 0.0236, "Market Cap" : 520.42, "Volume" : 33912, "Gross Margin" : 0.679, "Short Ratio" : 8.32, "Performance (Half Year)" : 0.0872, "Relative Strength Index (14)" : 45.52, "Insider Ownership" : 0.0092, "20-Day Simple Moving Average" : -0.018, "Performance (Month)" : -0.0032, "Institutional Transactions" : 0.0133, "Performance (Year)" : 0.0747, "LT Debt/Equity" : 0, "Average Volume" : 118.95, "EPS growth this year" : -7.333, "50-Day Simple Moving Average" : -0.0226 }
    { "_id" : ObjectId("52853800bb1177ca391c182c"), "Ticker" : "ACFN", "Institutional Ownership" : 0.455, "EPS growth past 5 years" : -0.186, "Total Debt/Equity" : 0.01, "Current Ratio" : 3.5, "Return on Assets" : -0.341, "Sector" : "Industrial Goods", "P/S" : 2.94, "Change from Open" : 0.0765, "Performance (YTD)" : -0.5714, "Performance (Week)" : -0.0826, "Quick Ratio" : 2.8, "Insider Transactions" : 0.1254, "P/B" : 1.54, "EPS growth quarter over quarter" : -1.222, "Performance (Quarter)" : -0.4781, "200-Day Simple Moving Average" : -0.4874, "Shares Outstanding" : 18.09, "Earnings Date" : ISODate("2013-11-12T21:30:00Z"), "52-Week High" : -0.6444, "P/Cash" : 4.53, "Change" : 0.0571, "Analyst Recom" : 2, "Volatility (Week)" : 0.0892, "Country" : "USA", "Return on Equity" : -0.441, "50-Day Low" : 0.2351, "Price" : 3.52, "50-Day High" : -0.4723, "Return on Investment" : -0.343, "Shares Float" : 20.58, "Dividend Yield" : 0.042, "EPS growth next 5 years" : 0.3, "Industry" : "Aerospace/Defense Products & Services", "Beta" : 0.23, "Sales growth quarter over quarter" : -0.088, "EPS (ttm)" : -1.19, "Float Short" : 0.1489, "52-Week Low" : 0.2351, "Average True Range" : 0.34, "EPS growth next year" : 0.563, "Sales growth past 5 years" : 0.317, "Company" : "Acorn Energy, Inc.", "Gap" : -0.018, "Relative Volume" : 0.74, "Volatility (Month)" : 0.0883, "Market Cap" : 60.24, "Volume" : 189178, "Gross Margin" : 0.293, "Short Ratio" : 10.94, "Performance (Half Year)" : -0.5988, "Relative Strength Index (14)" : 41, "Insider Ownership" : 0.064, "20-Day Simple Moving Average" : -0.0499, "Performance (Month)" : -0.0206, "Institutional Transactions" : 0.0278, "Performance (Year)" : -0.5595, "LT Debt/Equity" : 0, "Average Volume" : 280.12, "EPS growth this year" : -3.906, "50-Day Simple Moving Average" : -0.2451 }
```

3. Liste as 10 ações mais rentáveis

```
    db.stocks.find().sort({"Return on Investment": -1}).limit(10);

    { "_id" : ObjectId("52853809bb1177ca391c29c8"), "Ticker" : "PBT", "Profit Margin" : 0.97, "Institutional Ownership" : 0.128, "EPS growth past 5 years" : -0.044, "Total Debt/Equity" : 0, "Return on Assets" : 9.43, "Sector" : "Basic Materials", "P/S" : 18.11, "Change from Open" : 0.0169, "Performance (YTD)" : 0.2272, "Performance (Week)" : -0.0172, "P/B" : 713, "EPS growth quarter over quarter" : -0.324, "Payout Ratio" : 1, "Performance (Quarter)" : 0.0978, "P/E" : 18.76, "200-Day Simple Moving Average" : 0.1051, "Shares Outstanding" : 46.61, "Earnings Date" : ISODate("2013-11-04T05:00:00Z"), "52-Week High" : -0.1051, "P/Cash" : 179.63, "Change" : 0.0147, "Volatility (Week)" : 0.0244, "Country" : "USA", "50-Day Low" : 0.1026, "Price" : 14.47, "50-Day High" : -0.1051, "Return on Investment" : 67.5, "Shares Float" : 46.61, "Dividend Yield" : 0.0835, "EPS growth next 5 years" : 0.1, "Industry" : "Independent Oil & Gas", "Beta" : 0.81, "Sales growth quarter over quarter" : -0.304, "Operating Margin" : 0.967, "EPS (ttm)" : 0.76, "PEG" : 1.88, "Float Short" : 0.0041, "52-Week Low" : 0.2838, "Average True Range" : 0.37, "Sales growth past 5 years" : -0.043, "Company" : "Permian Basin Royalty Trust", "Gap" : -0.0021, "Relative Volume" : 0.92, "Volatility (Month)" : 0.0266, "Market Cap" : 664.64, "Volume" : 117417, "Short Ratio" : 1.35, "Performance (Half Year)" : 0.1844, "Relative Strength Index (14)" : 48.68, "20-Day Simple Moving Average" : -0.0314, "Performance (Month)" : -0.0219, "Institutional Transactions" : 0.0345, "Performance (Year)" : 0.1883, "LT Debt/Equity" : 0, "Average Volume" : 141.5, "EPS growth this year" : -0.147, "50-Day Simple Moving Average" : 0.0104 }
    { "_id" : ObjectId("52853808bb1177ca391c28e9"), "Ticker" : "NWBO", "Institutional Ownership" : 0.246, "EPS growth past 5 years" : 0.316, "Current Ratio" : 0.1, "Sector" : "Healthcare", "P/S" : 153.61, "Change from Open" : -0.062, "Performance (YTD)" : 0.5224, "Performance (Week)" : 0.4937, "Quick Ratio" : 0.1, "EPS growth quarter over quarter" : 0.6, "Performance (Quarter)" : 0.338, "200-Day Simple Moving Average" : 0.2881, "Shares Outstanding" : 29.11, "52-Week High" : -0.3363, "P/Cash" : 69.12, "Change" : -0.0442, "Analyst Recom" : 1.3, "Volatility (Week)" : 0.143, "Country" : "USA", "Return on Equity" : 3.822, "50-Day Low" : 0.4645, "Price" : 4.54, "50-Day High" : -0.0865, "Return on Investment" : 36.5, "Shares Float" : 25.41, "Industry" : "Biotechnology", "Beta" : 1.45, "Sales growth quarter over quarter" : 0, "EPS (ttm)" : -4.31, "Float Short" : 0.0288, "52-Week Low" : 0.5235, "Average True Range" : 0.3, "EPS growth next year" : 0.286, "Company" : "Northwest Biotherapeutics, Inc.", "Gap" : 0.0189, "Relative Volume" : 3.01, "Volatility (Month)" : 0.0686, "Market Cap" : 138.25, "Volume" : 891125, "Short Ratio" : 2.23, "Performance (Half Year)" : 0.3049, "Relative Strength Index (14)" : 72.64, "Insider Ownership" : 0.0986, "20-Day Simple Moving Average" : 0.2728, "Performance (Month)" : 0.3971, "Institutional Transactions" : 0.0129, "Performance (Year)" : -0.1533, "Average Volume" : 327.62, "EPS growth this year" : -0.025, "50-Day Simple Moving Average" : 0.315 }
    { "_id" : ObjectId("5285380fbb1177ca391c315f"), "Ticker" : "WAVX", "Institutional Ownership" : 0.084, "EPS growth past 5 years" : 0.038, "Current Ratio" : 0.4, "Return on Assets" : -2.069, "Sector" : "Technology", "P/S" : 1.28, "Change from Open" : 0, "Performance (YTD)" : -0.5833, "Performance (Week)" : -0.1045, "Quick Ratio" : 0.4, "EPS growth quarter over quarter" : 0.571, "Performance (Quarter)" : -0.1667, "200-Day Simple Moving Average" : -0.3842, "Shares Outstanding" : 28.32, "Earnings Date" : ISODate("2013-11-07T21:30:00Z"), "52-Week High" : -0.717, "P/Cash" : 37.76, "Change" : 0, "Analyst Recom" : 3, "Volatility (Week)" : 0.053, "Country" : "USA", "Return on Equity" : 7.13, "50-Day Low" : 0.0909, "Price" : 1.2, "50-Day High" : -0.1724, "Return on Investment" : 26, "Shares Float" : 31.1, "Industry" : "Security Software & Services", "Beta" : 1.15, "Sales growth quarter over quarter" : -0.141, "Operating Margin" : -0.974, "EPS (ttm)" : -1.26, "Float Short" : 0.0439, "52-Week Low" : 0.3793, "Average True Range" : 0.08, "Sales growth past 5 years" : 0.355, "Company" : "Wave Systems Corp.", "Gap" : 0, "Relative Volume" : 0.5, "Volatility (Month)" : 0.0642, "Market Cap" : 33.98, "Volume" : 48718, "Gross Margin" : 0.695, "Short Ratio" : 12.59, "Performance (Half Year)" : -0.3333, "Relative Strength Index (14)" : 43.81, "Insider Ownership" : 0.0048, "20-Day Simple Moving Average" : -0.0365, "Performance (Month)" : -0.1111, "Institutional Transactions" : -0.0137, "Performance (Year)" : -0.5385, "Average Volume" : 108.34, "EPS growth this year" : -1.765, "50-Day Simple Moving Average" : -0.0701 }
    { "_id" : ObjectId("52853807bb1177ca391c2779"), "Ticker" : "MSB", "Profit Margin" : 0.963, "Institutional Ownership" : 0.155, "EPS growth past 5 years" : 0.11, "Total Debt/Equity" : 0, "Return on Assets" : 2.701, "Sector" : "Financial", "P/S" : 11.35, "Change from Open" : 0.0183, "Performance (YTD)" : -0.0047, "Performance (Week)" : -0.0236, "P/B" : 78.47, "EPS growth quarter over quarter" : -0.301, "Payout Ratio" : 1.08, "Performance (Quarter)" : 0.1841, "P/E" : 11.77, "200-Day Simple Moving Average" : 0.1835, "Shares Outstanding" : 13.12, "Earnings Date" : ISODate("2013-12-02T05:00:00Z"), "52-Week High" : -0.0803, "P/Cash" : 49.81, "Change" : 0.0166, "Analyst Recom" : 3, "Volatility (Week)" : 0.0207, "Country" : "USA", "50-Day Low" : 0.2447, "Price" : 23.93, "50-Day High" : -0.0366, "Return on Investment" : 25.583, "Shares Float" : 13.08, "Dividend Yield" : 0.0867, "Industry" : "Diversified Investments", "Beta" : 1.71, "Sales growth quarter over quarter" : -0.297, "Operating Margin" : 0.963, "EPS (ttm)" : 2, "Float Short" : 0.0136, "52-Week Low" : 0.4742, "Average True Range" : 0.68, "Sales growth past 5 years" : 0.108, "Company" : "Mesabi Trust", "Gap" : -0.0017, "Relative Volume" : 0.54, "Volatility (Month)" : 0.0307, "Market Cap" : 308.84, "Volume" : 33449, "Short Ratio" : 2.61, "Performance (Half Year)" : 0.1974, "Relative Strength Index (14)" : 65.56, "Insider Ownership" : 0.0032, "20-Day Simple Moving Average" : 0.0715, "Performance (Month)" : 0.1776, "Institutional Transactions" : -0.0216, "Performance (Year)" : 0.0026, "LT Debt/Equity" : 0, "Average Volume" : 68.26, "EPS growth this year" : -0.075, "50-Day Simple Moving Average" : 0.1329 }
    { "_id" : ObjectId("5285380bbb1177ca391c2cbe"), "Ticker" : "SBR", "Profit Margin" : 0.959, "Institutional Ownership" : 0.103, "EPS growth past 5 years" : -0.017, "Total Debt/Equity" : 0, "Return on Assets" : 9.406, "Sector" : "Financial", "P/S" : 13.84, "Change from Open" : 0.0037, "Performance (YTD)" : 0.379, "Performance (Week)" : 0.0061, "P/B" : 154.48, "EPS growth quarter over quarter" : -0.082, "Payout Ratio" : 1.031, "Performance (Quarter)" : 0.0225, "P/E" : 14.44, "200-Day Simple Moving Average" : 0.049, "Shares Outstanding" : 14.58, "Earnings Date" : ISODate("2013-11-08T05:00:00Z"), "52-Week High" : -0.0314, "P/Cash" : 154.84, "Change" : 0.0041, "Volatility (Week)" : 0.0126, "Country" : "USA", "50-Day Low" : 0.038, "Price" : 51.19, "50-Day High" : -0.0228, "Return on Investment" : 12.78, "Shares Float" : 14.58, "Dividend Yield" : 0.0928, "Industry" : "Diversified Investments", "Beta" : 0.73, "Sales growth quarter over quarter" : -0.079, "Operating Margin" : 0.959, "EPS (ttm)" : 3.53, "Float Short" : 0.0007, "52-Week Low" : 0.4177, "Average True Range" : 0.65, "Sales growth past 5 years" : -0.016, "Company" : "Sabine Royalty Trust", "Gap" : 0.0004, "Relative Volume" : 0.68, "Volatility (Month)" : 0.0121, "Market Cap" : 743.24, "Volume" : 9429, "Short Ratio" : 0.7, "Performance (Half Year)" : 0.0163, "Relative Strength Index (14)" : 54.33, "20-Day Simple Moving Average" : 0.0079, "Performance (Month)" : -0.0156, "Institutional Transactions" : -0.0228, "Performance (Year)" : 0.222, "LT Debt/Equity" : 0, "Average Volume" : 15.39, "EPS growth this year" : -0.107, "50-Day Simple Moving Average" : 0.0068 }
    { "_id" : ObjectId("52853802bb1177ca391c1ba4"), "Ticker" : "CBMX", "Institutional Ownership" : 0.034, "EPS growth past 5 years" : 0.16, "Total Debt/Equity" : 0.05, "Current Ratio" : 2.8, "Return on Assets" : -2.222, "Sector" : "Healthcare", "P/S" : 1.47, "Change from Open" : -0.0116, "Performance (YTD)" : -0.5379, "Performance (Week)" : 0.0655, "Quick Ratio" : 2.6, "Insider Transactions" : 0.0037, "P/B" : 1.52, "EPS growth quarter over quarter" : 0.8, "Performance (Quarter)" : -0.1947, "200-Day Simple Moving Average" : -0.2225, "Shares Outstanding" : 3.55, "Earnings Date" : ISODate("2013-11-13T05:00:00Z"), "52-Week High" : -0.826, "P/Cash" : 1.52, "Change" : 0.0086, "Volatility (Week)" : 0.0986, "Country" : "USA", "Return on Equity" : -5.745, "50-Day Low" : 0.0987, "Price" : 2.46, "50-Day High" : -0.2542, "Return on Investment" : 11.5, "Shares Float" : 4.59, "Industry" : "Medical Laboratories & Research", "Beta" : -0.12, "Sales growth quarter over quarter" : 0.154, "Operating Margin" : -0.966, "EPS (ttm)" : -5.32, "Float Short" : 0.1105, "52-Week Low" : 0.7579, "Average True Range" : 0.16, "Sales growth past 5 years" : -0.021, "Company" : "CombiMatrix Corporation", "Gap" : 0.0205, "Relative Volume" : 0.31, "Volatility (Month)" : 0.0561, "Market Cap" : 8.66, "Volume" : 30808, "Gross Margin" : 0.458, "Short Ratio" : 4.67, "Performance (Half Year)" : -0.2628, "Relative Strength Index (14)" : 36.61, "Insider Ownership" : 0.001, "20-Day Simple Moving Average" : -0.0798, "Performance (Month)" : -0.1254, "Institutional Transactions" : -0.0474, "Performance (Year)" : -0.2129, "LT Debt/Equity" : 0.02, "Average Volume" : 108.62, "EPS growth this year" : -0.092, "50-Day Simple Moving Average" : -0.1187 }
    { "_id" : ObjectId("52853809bb1177ca391c294d"), "Ticker" : "OMEX", "Institutional Ownership" : 0.455, "EPS growth past 5 years" : 0.143, "Current Ratio" : 0.5, "Return on Assets" : -0.598, "Sector" : "Services", "P/S" : 16.98, "Change from Open" : 0.0117, "Performance (YTD)" : -0.2795, "Performance (Week)" : -0.0138, "Quick Ratio" : 0.4, "Insider Transactions" : 0.1724, "EPS growth quarter over quarter" : 0.548, "Performance (Quarter)" : -0.289, "200-Day Simple Moving Average" : -0.305, "Shares Outstanding" : 79.35, "Earnings Date" : ISODate("2013-11-04T05:00:00Z"), "52-Week High" : -0.4176, "P/Cash" : 16.49, "Change" : 0.007, "Analyst Recom" : 2, "Volatility (Week)" : 0.1024, "Country" : "USA", "Return on Equity" : 1.271, "50-Day Low" : 0.1712, "Price" : 2.15, "50-Day High" : -0.3223, "Return on Investment" : 7.8, "Shares Float" : 75.01, "Industry" : "Business Services", "Beta" : 1.28, "Sales growth quarter over quarter" : -0.93, "EPS (ttm)" : -0.22, "Float Short" : 0.2003, "52-Week Low" : 0.1712, "Average True Range" : 0.22, "Sales growth past 5 years" : 0.167, "Company" : "Odyssey Marine Exploration Inc.", "Gap" : -0.0047, "Relative Volume" : 0.84, "Volatility (Month)" : 0.1046, "Market Cap" : 169.8, "Volume" : 894268, "Gross Margin" : 0.96, "Short Ratio" : 12.81, "Performance (Half Year)" : -0.3375, "Relative Strength Index (14)" : 36.89, "Insider Ownership" : 0.018, "20-Day Simple Moving Average" : -0.1539, "Performance (Month)" : -0.1894, "Institutional Transactions" : 0.0034, "Performance (Year)" : -0.2015, "Average Volume" : 1173.4, "EPS growth this year" : 0.107, "50-Day Simple Moving Average" : -0.2198 }
    { "_id" : ObjectId("5285380cbb1177ca391c2dd8"), "Ticker" : "SPCB", "Institutional Ownership" : 0.079, "EPS growth past 5 years" : 0.156, "Total Debt/Equity" : 0, "Current Ratio" : 1.4, "Return on Assets" : 3.033, "Sector" : "Technology", "P/S" : 17.52, "Change from Open" : 0.0138, "Performance (YTD)" : 6.0678, "Performance (Week)" : 0, "Quick Ratio" : 1.3, "P/B" : 83.4, "EPS growth quarter over quarter" : 2, "Payout Ratio" : 0, "Performance (Quarter)" : 0.127, "P/E" : 37.91, "200-Day Simple Moving Average" : 0.6753, "Shares Outstanding" : 36.98, "52-Week High" : -0.304, "P/Cash" : 1541.94, "Change" : 0.0211, "Volatility (Week)" : 0.0473, "Country" : "Israel", "50-Day Low" : 0.1665, "Price" : 4.26, "50-Day High" : -0.2012, "Return on Investment" : 6.5, "Shares Float" : 3.31, "Industry" : "Security Software & Services", "Beta" : 0.81, "Sales growth quarter over quarter" : -0.091, "Operating Margin" : 0.273, "EPS (ttm)" : 0.11, "Float Short" : 0.0004, "52-Week Low" : 100.0325, "Average True Range" : 0.33, "Sales growth past 5 years" : -0.061, "Company" : "SuperCom Ltd.", "Gap" : 0.0072, "Relative Volume" : 0.77, "Volatility (Month)" : 0.081, "Market Cap" : 154.19, "Volume" : 12947, "Gross Margin" : 0.886, "Short Ratio" : 0.07, "Performance (Half Year)" : 2.5042, "Relative Strength Index (14)" : 46.11, "20-Day Simple Moving Average" : -0.0183, "Performance (Month)" : 0.0425, "P/Free Cash Flow" : 48.19, "Performance (Year)" : 7.1765, "LT Debt/Equity" : 0, "Average Volume" : 18.68, "EPS growth this year" : 0.556, "50-Day Simple Moving Average" : -0.0692 }
    { "_id" : ObjectId("52853806bb1177ca391c2442"), "Ticker" : "IPCI", "Institutional Ownership" : 0.005, "EPS growth past 5 years" : 0.171, "Current Ratio" : 1.2, "Return on Assets" : -2.031, "Sector" : "Healthcare", "Change from Open" : 0.0058, "Performance (YTD)" : -0.324, "Performance (Week)" : -0.0452, "Quick Ratio" : 1.2, "EPS growth quarter over quarter" : -0.25, "Performance (Quarter)" : -0.0815, "Forward P/E" : 12.07, "200-Day Simple Moving Average" : -0.0987, "Shares Outstanding" : 20.23, "52-Week High" : -0.5349, "P/Cash" : 14.24, "Change" : 0.0237, "Analyst Recom" : 1.7, "Volatility (Week)" : 0.0607, "Country" : "Canada", "Return on Equity" : 3.377, "50-Day Low" : 0.0613, "Price" : 1.73, "50-Day High" : -0.2607, "Return on Investment" : 5.941, "Shares Float" : 15.05, "Industry" : "Drug Delivery", "Beta" : 0.62, "EPS (ttm)" : -0.35, "Float Short" : 0.0413, "52-Week Low" : 0.1533, "Average True Range" : 0.1, "EPS growth next year" : 1.4, "Company" : "IntelliPharmaCeutics International Inc.", "Gap" : 0.0178, "Relative Volume" : 0.14, "Volatility (Month)" : 0.0484, "Market Cap" : 34.18, "Volume" : 26179, "Short Ratio" : 2.93, "Performance (Half Year)" : -0.0506, "Relative Strength Index (14)" : 39.06, "Insider Ownership" : 0.3916, "20-Day Simple Moving Average" : -0.0458, "Performance (Month)" : -0.1152, "Institutional Transactions" : -0.056, "Performance (Year)" : -0.3525, "Average Volume" : 212.1, "EPS growth this year" : -0.091, "50-Day Simple Moving Average" : -0.0966 }
    { "_id" : ObjectId("52853807bb1177ca391c26ea"), "Ticker" : "MGT", "Institutional Ownership" : 0.13, "EPS growth past 5 years" : 0.26, "Total Debt/Equity" : 0.01, "Current Ratio" : 7.3, "Return on Assets" : -1.033, "Sector" : "Services", "P/S" : 47.99, "Change from Open" : 0.0233, "Performance (YTD)" : -0.2176, "Performance (Week)" : 0.0634, "Quick Ratio" : 7.3, "P/B" : 1.29, "EPS growth quarter over quarter" : -0.769, "Performance (Quarter)" : -0.2506, "200-Day Simple Moving Average" : -0.1993, "Shares Outstanding" : 4.77, "Earnings Date" : ISODate("2013-11-14T05:00:00Z"), "52-Week High" : -0.4788, "P/Cash" : 2.29, "Change" : 0.0166, "Volatility (Week)" : 0.0482, "Country" : "United Kingdom", "Return on Equity" : -3.45, "50-Day Low" : 0.2329, "Price" : 3.07, "50-Day High" : -0.2991, "Return on Investment" : 5.444, "Shares Float" : 5.95, "Industry" : "Business Services", "Beta" : 1.61, "Sales growth quarter over quarter" : 0.196, "EPS (ttm)" : -2.65, "Float Short" : 0.0642, "52-Week Low" : 0.2329, "Average True Range" : 0.23, "Sales growth past 5 years" : 0.32, "Company" : "MGT Capital Investments, Inc.", "Gap" : -0.0066, "Relative Volume" : 3.43, "Volatility (Month)" : 0.0803, "Market Cap" : 14.4, "Volume" : 215568, "Gross Margin" : 0.333, "Short Ratio" : 5.54, "Performance (Half Year)" : -0.267, "Relative Strength Index (14)" : 45.97, "Insider Ownership" : 0.2005, "20-Day Simple Moving Average" : -0.0055, "Performance (Month)" : -0.0958, "Institutional Transactions" : -0.0313, "Performance (Year)" : -0.4509, "LT Debt/Equity" : 0, "Average Volume" : 68.83, "EPS growth this year" : 0.321, "50-Day Simple Moving Average" : -0.1183 }
```

4. Qual foi o setor mais rentável?

```
    db.stocks.aggregate([
        { $group: { _id: "$Sector", total: { $sum: "$Return on Investment" } } },
        { $sort: { total: -1 } }
    ])

    { "_id" : "Financial", "total" : 173.027 }
    { "_id" : "Basic Materials", "total" : 74.8355 }
    { "_id" : "Industrial Goods", "total" : 19.4201 }
    { "_id" : "Services", "total" : 18.2744 }
    { "_id" : "Consumer Goods", "total" : 14.8236 }
    { "_id" : "Utilities", "total" : 2.66 }
    { "_id" : "Conglomerates", "total" : 0.8658 }
    { "_id" : "Technology", "total" : -33.8144 }
    { "_id" : "Healthcare", "total" : -231.7402 }
```

5. Ordene as ações pelo profit e usando um cursor, liste as ações.

```
    db.stocks.find().sort( { "Profit Margin": -1 } ).limit(10);

    { "_id" : ObjectId("52853801bb1177ca391c1af3"), "Ticker" : "BPT", "Profit Margin" : 0.994, "Institutional Ownership" : 0.098, "EPS growth past 5 years" : 0.025, "Total Debt/Equity" : 0, "Sector" : "Basic Materials", "P/S" : 8.81, "Change from Open" : 0.0125, "Performance (YTD)" : 0.2758, "Performance (Week)" : -0.018, "P/B" : 2620, "EPS growth quarter over quarter" : -0.087, "Payout Ratio" : 1.001, "Performance (Quarter)" : -0.0556, "P/E" : 8.87, "200-Day Simple Moving Average" : -0.0305, "Shares Outstanding" : 21.4, "Earnings Date" : ISODate("2013-11-11T05:00:00Z"), "52-Week High" : -0.159, "P/Cash" : 1682.04, "Change" : 0.0064, "Volatility (Week)" : 0.0151, "Country" : "USA", "50-Day Low" : 0.0136, "Price" : 79.1, "50-Day High" : -0.0973, "Shares Float" : 21.4, "Dividend Yield" : 0.1103, "Industry" : "Oil & Gas Refining & Marketing", "Beta" : 0.77, "Sales growth quarter over quarter" : -0.086, "Operating Margin" : 0.994, "EPS (ttm)" : 8.86, "Float Short" : 0.0173, "52-Week Low" : 0.3422, "Average True Range" : 1.37, "Sales growth past 5 years" : 0.024, "Company" : "BP Prudhoe Bay Royalty Trust", "Gap" : -0.0061, "Relative Volume" : 0.93, "Volatility (Month)" : 0.016, "Market Cap" : 1682.04, "Volume" : 71575, "Short Ratio" : 4.41, "Performance (Half Year)" : 0.0022, "Relative Strength Index (14)" : 38.01, "20-Day Simple Moving Average" : -0.0318, "Performance (Month)" : -0.079, "Institutional Transactions" : -0.0057, "Performance (Year)" : 0.1837, "LT Debt/Equity" : 0, "Average Volume" : 84.15, "EPS growth this year" : -0.012, "50-Day Simple Moving Average" : -0.0496 }
    { "_id" : ObjectId("52853802bb1177ca391c1b69"), "Ticker" : "CACB", "Profit Margin" : 0.994, "Institutional Ownership" : 0.547, "EPS growth past 5 years" : -0.584, "Total Debt/Equity" : 0, "Return on Assets" : 0.039, "Sector" : "Financial", "P/S" : 4.66, "Change from Open" : -0.0137, "Performance (YTD)" : -0.1869, "Performance (Week)" : 0.0079, "Insider Transactions" : 1.0755, "P/B" : 1.28, "EPS growth quarter over quarter" : 25.422, "Payout Ratio" : 0, "Performance (Quarter)" : -0.1314, "Forward P/E" : 42.42, "P/E" : 4.71, "200-Day Simple Moving Average" : -0.1709, "Shares Outstanding" : 47.17, "Earnings Date" : ISODate("2013-11-13T21:30:00Z"), "52-Week High" : -0.2994, "P/Cash" : 2.26, "Change" : -0.0118, "Analyst Recom" : 3, "Volatility (Week)" : 0.0353, "Country" : "USA", "Return on Equity" : 0.336, "50-Day Low" : 0.006, "Price" : 5.03, "50-Day High" : -0.2066, "Return on Investment" : 0.346, "Shares Float" : 40.67, "EPS growth next 5 years" : 0.05, "Industry" : "Regional - Pacific Banks", "Beta" : 2.34, "Sales growth quarter over quarter" : -0.101, "Operating Margin" : 0.027, "EPS (ttm)" : 1.08, "PEG" : 0.94, "Float Short" : 0.0088, "52-Week Low" : 0.0817, "Average True Range" : 0.19, "EPS growth next year" : -0.8904, "Sales growth past 5 years" : -0.203, "Company" : "Cascade Bancorp", "Gap" : 0.002, "Relative Volume" : 1.35, "Volatility (Month)" : 0.0399, "Market Cap" : 240.11, "Volume" : 21432, "Short Ratio" : 20.55, "Performance (Half Year)" : -0.1239, "Relative Strength Index (14)" : 29.61, "Insider Ownership" : 0.009, "20-Day Simple Moving Average" : -0.0729, "Performance (Month)" : -0.1039, "Institutional Transactions" : 0.0004, "Performance (Year)" : 0.0241, "LT Debt/Equity" : 0, "Average Volume" : 17.39, "EPS growth this year" : 1.12, "50-Day Simple Moving Average" : -0.116 }
    { "_id" : ObjectId("5285380bbb1177ca391c2c3c"), "Ticker" : "ROYT", "Profit Margin" : 0.99, "Institutional Ownership" : 0.696, "EPS growth past 5 years" : 0, "Total Debt/Equity" : 0, "Return on Assets" : 0.255, "Sector" : "Basic Materials", "P/S" : 7.62, "Change from Open" : 0, "Performance (YTD)" : -0.1408, "Performance (Week)" : -0.0447, "Insider Transactions" : -0.5437, "P/B" : 2.03, "EPS growth quarter over quarter" : 1.75, "Payout Ratio" : 0.338, "Performance (Quarter)" : -0.2202, "Forward P/E" : 7.92, "P/E" : 7.68, "200-Day Simple Moving Average" : -0.1864, "Shares Outstanding" : 38.58, "52-Week High" : -0.243, "Change" : 0.0037, "Analyst Recom" : 2.4, "Volatility (Week)" : 0.0174, "Country" : "USA", "Return on Equity" : 0.255, "50-Day Low" : 0.0088, "Price" : 13.72, "50-Day High" : -0.243, "Return on Investment" : 0.15, "Shares Float" : 38.58, "Dividend Yield" : 0.1295, "EPS growth next 5 years" : 0.126, "Industry" : "Independent Oil & Gas", "Sales growth quarter over quarter" : 1.6, "Operating Margin" : 0.99, "EPS (ttm)" : 1.78, "PEG" : 0.61, "Float Short" : 0.0042, "52-Week Low" : 0.0088, "Average True Range" : 0.3, "EPS growth next year" : -0.0655, "Company" : "Pacific Coast Oil Trust", "Gap" : 0.0037, "Relative Volume" : 0.75, "Volatility (Month)" : 0.0201, "Market Cap" : 527.43, "Volume" : 262050, "Short Ratio" : 0.42, "Performance (Half Year)" : -0.1978, "Relative Strength Index (14)" : 20.73, "Insider Ownership" : 0.5205, "20-Day Simple Moving Average" : -0.0644, "Performance (Month)" : -0.1237, "Institutional Transactions" : 0.0154, "Performance (Year)" : -0.1141, "LT Debt/Equity" : 0, "Average Volume" : 388.63, "EPS growth this year" : 0.745, "50-Day Simple Moving Average" : -0.1265 }
    { "_id" : ObjectId("52853808bb1177ca391c281b"), "Ticker" : "NDRO", "Profit Margin" : 0.986, "Institutional Ownership" : 0.532, "EPS growth past 5 years" : 0, "Total Debt/Equity" : 0, "Return on Assets" : 0.078, "Sector" : "Basic Materials", "P/S" : 8.11, "Change from Open" : 0, "Performance (YTD)" : -0.2111, "Performance (Week)" : -0.0369, "Insider Transactions" : -0.3613, "P/B" : 0.67, "EPS growth quarter over quarter" : -0.378, "Payout Ratio" : 0.313, "Performance (Quarter)" : -0.1716, "Forward P/E" : 7.53, "P/E" : 8.23, "200-Day Simple Moving Average" : -0.1708, "Shares Outstanding" : 33, "Earnings Date" : ISODate("2013-11-11T05:00:00Z"), "52-Week High" : -0.2732, "Change" : -0.0073, "Analyst Recom" : 2.3, "Volatility (Week)" : 0.0224, "Country" : "USA", "Return on Equity" : 0.078, "50-Day Low" : 0.0437, "Price" : 12.17, "50-Day High" : -0.2028, "Return on Investment" : 0.091, "Shares Float" : 33, "Dividend Yield" : 0.1476, "EPS growth next 5 years" : -0.061, "Industry" : "Independent Oil & Gas", "Sales growth quarter over quarter" : -0.388, "Operating Margin" : 0.986, "EPS (ttm)" : 1.49, "Float Short" : 0.0011, "52-Week Low" : 0.0437, "Average True Range" : 0.26, "EPS growth next year" : 0.1097, "Company" : "Enduro Royalty Trust", "Gap" : -0.0073, "Relative Volume" : 1.43, "Volatility (Month)" : 0.0205, "Market Cap" : 404.58, "Volume" : 406061, "Short Ratio" : 0.12, "Performance (Half Year)" : -0.2106, "Relative Strength Index (14)" : 33.3, "Insider Ownership" : 0.6, "20-Day Simple Moving Average" : -0.0471, "Performance (Month)" : 0.0381, "Institutional Transactions" : 0.1111, "Performance (Year)" : -0.1987, "LT Debt/Equity" : 0, "Average Volume" : 311.39, "EPS growth this year" : 4.677, "50-Day Simple Moving Average" : -0.0824 }
    { "_id" : ObjectId("5285380fbb1177ca391c318e"), "Ticker" : "WHZ", "Profit Margin" : 0.982, "Institutional Ownership" : 0.199, "EPS growth past 5 years" : 0, "Total Debt/Equity" : 0, "Return on Assets" : 0.321, "Sector" : "Basic Materials", "P/S" : 4.79, "Change from Open" : -0.0042, "Performance (YTD)" : 0.0782, "Performance (Week)" : 0.0369, "P/B" : 1.67, "EPS growth quarter over quarter" : -0.337, "Payout Ratio" : 1.003, "Performance (Quarter)" : 0.0955, "P/E" : 4.88, "200-Day Simple Moving Average" : 0.0993, "Shares Outstanding" : 18.4, "52-Week High" : -0.0668, "P/Cash" : 1319.28, "Change" : -0.0042, "Analyst Recom" : 3, "Volatility (Week)" : 0.0183, "Country" : "USA", "Return on Equity" : 0.321, "50-Day Low" : 0.12, "Price" : 14.28, "50-Day High" : -0.0138, "Return on Investment" : 0.28, "Shares Float" : 18.4, "Dividend Yield" : 0.2064, "Industry" : "Independent Oil & Gas", "Sales growth quarter over quarter" : -0.343, "Operating Margin" : 0.982, "EPS (ttm)" : 2.94, "Float Short" : 0.004, "52-Week Low" : 0.2081, "Average True Range" : 0.26, "Company" : "Whiting USA Trust II", "Gap" : 0, "Relative Volume" : 2.18, "Volatility (Month)" : 0.0194, "Market Cap" : 263.86, "Volume" : 244298, "Short Ratio" : 0.6, "Performance (Half Year)" : 0.1282, "Relative Strength Index (14)" : 68.85, "20-Day Simple Moving Average" : 0.0301, "Performance (Month)" : 0.0864, "Institutional Transactions" : 0.0834, "Performance (Year)" : -0.0311, "LT Debt/Equity" : 0, "Average Volume" : 123.73, "50-Day Simple Moving Average" : 0.0734 }
    { "_id" : ObjectId("52853808bb1177ca391c27bd"), "Ticker" : "MVO", "Profit Margin" : 0.976, "Institutional Ownership" : 0.048, "EPS growth past 5 years" : 0.044, "Total Debt/Equity" : 0, "Return on Assets" : 1.258, "Sector" : "Basic Materials", "P/S" : 8.25, "Change from Open" : 0.0176, "Performance (YTD)" : 0.2883, "Performance (Week)" : -0.0007, "P/B" : 11.04, "EPS growth quarter over quarter" : -0.147, "Payout Ratio" : 1, "Performance (Quarter)" : 0.0678, "P/E" : 8.43, "200-Day Simple Moving Average" : 0.0422, "Shares Outstanding" : 11.5, "Earnings Date" : ISODate("2013-11-11T05:00:00Z"), "52-Week High" : -0.0998, "Change" : 0.0131, "Analyst Recom" : 4, "Volatility (Week)" : 0.0108, "Country" : "USA", "Return on Equity" : 1.258, "50-Day Low" : 0.0765, "Price" : 27.75, "50-Day High" : -0.0611, "Return on Investment" : 1.355, "Shares Float" : 8.63, "Dividend Yield" : 0.1431, "EPS growth next 5 years" : 0.07, "Industry" : "Oil & Gas Drilling & Exploration", "Beta" : 0.45, "Sales growth quarter over quarter" : -0.143, "Operating Margin" : 0.979, "EPS (ttm)" : 3.25, "PEG" : 1.2, "Float Short" : 0.0123, "52-Week Low" : 0.3994, "Average True Range" : 0.54, "Sales growth past 5 years" : 0.043, "Company" : "MV Oil Trust", "Gap" : -0.0044, "Relative Volume" : 0.36, "Volatility (Month)" : 0.0202, "Market Cap" : 314.98, "Volume" : 14403, "Short Ratio" : 2.44, "Performance (Half Year)" : 0.0367, "Relative Strength Index (14)" : 55.11, "Insider Ownership" : 0.25, "20-Day Simple Moving Average" : 0.0181, "Performance (Month)" : 0.0092, "Institutional Transactions" : -0.0054, "Performance (Year)" : 0.2008, "LT Debt/Equity" : 0, "Average Volume" : 43.54, "EPS growth this year" : 0.029, "50-Day Simple Moving Average" : 0.0058 }
    { "_id" : ObjectId("52853801bb1177ca391c1895"), "Ticker" : "AGNC", "Profit Margin" : 0.972, "Institutional Ownership" : 0.481, "EPS growth past 5 years" : -0.0107, "Total Debt/Equity" : 8.56, "Return on Assets" : 0.022, "Sector" : "Financial", "P/S" : 3.77, "Change from Open" : 0.0102, "Performance (YTD)" : -0.1652, "Performance (Week)" : -0.017, "Insider Transactions" : 0.4931, "P/B" : 0.86, "EPS growth quarter over quarter" : -8.2, "Payout Ratio" : 0.79, "Performance (Quarter)" : -0.0083, "Forward P/E" : 7.64, "P/E" : 3.68, "200-Day Simple Moving Average" : -0.1282, "Shares Outstanding" : 390.6, "Earnings Date" : ISODate("2013-10-28T20:30:00Z"), "52-Week High" : -0.2938, "P/Cash" : 3.93, "Change" : 0.0131, "Analyst Recom" : 2.6, "Volatility (Week)" : 0.0268, "Country" : "USA", "Return on Equity" : 0.205, "50-Day Low" : 0.0695, "Price" : 21.71, "50-Day High" : -0.1066, "Return on Investment" : 0.015, "Shares Float" : 383.97, "Dividend Yield" : 0.1493, "EPS growth next 5 years" : 0.035, "Industry" : "REIT - Residential", "Beta" : 0.51, "Sales growth quarter over quarter" : 0.073, "Operating Margin" : 0.67, "EPS (ttm)" : 5.82, "PEG" : 1.05, "Float Short" : 0.0311, "52-Week Low" : 0.1117, "Average True Range" : 0.52, "EPS growth next year" : -0.3603, "Company" : "American Capital Agency Corp.", "Gap" : 0.0028, "Relative Volume" : 0.71, "Volatility (Month)" : 0.02, "Market Cap" : 8370.56, "Volume" : 4576064, "Gross Margin" : 0.746, "Short Ratio" : 1.69, "Performance (Half Year)" : -0.2136, "Relative Strength Index (14)" : 43.53, "Insider Ownership" : 0.003, "20-Day Simple Moving Average" : -0.0318, "Performance (Month)" : -0.042, "Institutional Transactions" : 0.0077, "Performance (Year)" : -0.1503, "LT Debt/Equity" : 0, "Average Volume" : 7072.83, "EPS growth this year" : -0.169, "50-Day Simple Moving Average" : -0.0376 }
    { "_id" : ObjectId("5285380ebb1177ca391c3101"), "Ticker" : "VOC", "Profit Margin" : 0.971, "Institutional Ownership" : 0.161, "EPS growth past 5 years" : 0, "Total Debt/Equity" : 0, "Return on Assets" : 0.253, "Sector" : "Basic Materials", "P/S" : 9.03, "Change from Open" : -0.0129, "Performance (YTD)" : 0.4186, "Performance (Week)" : 0.0103, "P/B" : 2.44, "EPS growth quarter over quarter" : -0.304, "Payout Ratio" : 1, "Performance (Quarter)" : 0.1116, "P/E" : 9.3, "200-Day Simple Moving Average" : 0.2104, "Shares Outstanding" : 17, "52-Week High" : -0.0417, "P/Cash" : 948.6, "Change" : 0.0024, "Analyst Recom" : 3, "Volatility (Week)" : 0.0289, "Country" : "USA", "Return on Equity" : 0.253, "50-Day Low" : 0.1106, "Price" : 16.78, "50-Day High" : -0.0417, "Return on Investment" : 0.304, "Shares Float" : 12.75, "Dividend Yield" : 0.1266, "Industry" : "Independent Oil & Gas", "Sales growth quarter over quarter" : -0.286, "Operating Margin" : 0.971, "EPS (ttm)" : 1.8, "Float Short" : 0.006, "52-Week Low" : 0.529, "Average True Range" : 0.47, "Company" : "VOC Energy Trust", "Gap" : 0.0155, "Relative Volume" : 0.47, "Volatility (Month)" : 0.0292, "Market Cap" : 284.58, "Volume" : 32718, "Short Ratio" : 0.98, "Performance (Half Year)" : 0.2847, "Relative Strength Index (14)" : 54.66, "Insider Ownership" : 0.3505, "20-Day Simple Moving Average" : 0.009, "Performance (Month)" : 0.0582, "Institutional Transactions" : -0.0349, "Performance (Year)" : 0.3892, "LT Debt/Equity" : 0, "Average Volume" : 77.47, "EPS growth this year" : 0.542, "50-Day Simple Moving Average" : 0.0418 }
    { "_id" : ObjectId("52853807bb1177ca391c279a"), "Ticker" : "MTR", "Profit Margin" : 0.97, "Institutional Ownership" : 0.024, "EPS growth past 5 years" : -0.217, "Total Debt/Equity" : 0, "Return on Assets" : 0.518, "Sector" : "Financial", "P/S" : 12.1, "Change from Open" : -0.0038, "Performance (YTD)" : 0.1833, "Performance (Week)" : -0.0241, "P/B" : 7.82, "EPS growth quarter over quarter" : -0.255, "Payout Ratio" : 0.997, "Performance (Quarter)" : 0.0156, "P/E" : 12.68, "200-Day Simple Moving Average" : -0.0568, "Shares Outstanding" : 1.86, "Earnings Date" : ISODate("2013-11-11T05:00:00Z"), "52-Week High" : -0.1539, "P/Cash" : 23.5, "Change" : -0.0135, "Volatility (Week)" : 0.018, "Country" : "USA", "Return on Equity" : 0.593, "50-Day Low" : 0.0168, "Price" : 21.14, "50-Day High" : -0.1062, "Return on Investment" : 0.655, "Shares Float" : 1.86, "Dividend Yield" : 0.0845, "Industry" : "Diversified Investments", "Beta" : 0.93, "Sales growth quarter over quarter" : -0.222, "Operating Margin" : 0.939, "EPS (ttm)" : 1.69, "Float Short" : 0.0004, "52-Week Low" : 0.2026, "Average True Range" : 0.53, "Sales growth past 5 years" : -0.208, "Company" : "Mesa Royalty Trust", "Gap" : -0.0098, "Relative Volume" : 1.14, "Volatility (Month)" : 0.0226, "Market Cap" : 39.95, "Volume" : 4150, "Short Ratio" : 0.2, "Performance (Half Year)" : -0.1221, "Relative Strength Index (14)" : 34.54, "Insider Ownership" : 0.0385, "20-Day Simple Moving Average" : -0.0408, "Performance (Month)" : -0.0294, "Institutional Transactions" : -0.4527, "Performance (Year)" : 0.0418, "LT Debt/Equity" : 0, "Average Volume" : 3.97, "EPS growth this year" : -0.348, "50-Day Simple Moving Average" : -0.0539 }
    { "_id" : ObjectId("52853809bb1177ca391c2946"), "Ticker" : "OLP", "Profit Margin" : 0.97, "Institutional Ownership" : 0.481, "EPS growth past 5 years" : 0.008, "Total Debt/Equity" : 0.91, "Return on Assets" : 0.072, "Sector" : "Financial", "P/S" : 8.28, "Change from Open" : 0.0072, "Performance (YTD)" : 0.0398, "Performance (Week)" : -0.0156, "Insider Transactions" : 0.0039, "P/B" : 1.2, "EPS growth quarter over quarter" : 1.261, "Payout Ratio" : 0.456, "Performance (Quarter)" : -0.0804, "Forward P/E" : 10.48, "P/E" : 22.12, "200-Day Simple Moving Average" : -0.0742, "Shares Outstanding" : 14.84, "Earnings Date" : ISODate("2013-05-06T04:00:00Z"), "52-Week High" : -0.2453, "P/Cash" : 7.31, "Change" : 0.0077, "Analyst Recom" : 3, "Volatility (Week)" : 0.0166, "Country" : "USA", "Return on Equity" : 0.146, "50-Day Low" : 0.027, "Price" : 20.28, "50-Day High" : -0.1166, "Return on Investment" : 0.051, "Shares Float" : 13.88, "Dividend Yield" : 0.0695, "EPS growth next 5 years" : 0.111, "Industry" : "REIT - Diversified", "Beta" : 2.2, "Sales growth quarter over quarter" : 0.099, "Operating Margin" : 0.537, "EPS (ttm)" : 0.91, "PEG" : 1.99, "Float Short" : 0.0126, "52-Week Low" : 0.2285, "Average True Range" : 0.45, "EPS growth next year" : 0.171, "Sales growth past 5 years" : 0.06, "Company" : "One Liberty Properties Inc.", "Gap" : 0.0005, "Relative Volume" : 0.2, "Volatility (Month)" : 0.023, "Market Cap" : 298.81, "Volume" : 6907, "Gross Margin" : 0.983, "Short Ratio" : 4.64, "Performance (Half Year)" : -0.2219, "Relative Strength Index (14)" : 37.17, "Insider Ownership" : 0.158, "20-Day Simple Moving Average" : -0.0315, "Performance (Month)" : -0.0455, "Institutional Transactions" : 0.0003, "Performance (Year)" : 0.1663, "LT Debt/Equity" : 0.91, "Average Volume" : 37.56, "EPS growth this year" : -0.013, "50-Day Simple Moving Average" : -0.0356 }
```

6. Renomeie o campo “Profit Margin” para apenas “profit”.

```
    db.stocks.updateMany( {}, { $rename: { "Profit Margin": "profit" } } )

    { "acknowledged" : true, "matchedCount" : 6756, "modifiedCount" : 4302 }
```

7. Agora liste apenas a empresa e seu respectivo resultado

```

```

8. Analise as ações. É uma bola de cristal na sua mão... Quais as três ações
você investiria?

```

```

9. Liste as ações agrupadas por setor

```
   db.italians.aggregate([ {
        "$group": { 
            "Sector": { "$in":  [ "Banana", "Maçã" ] }
        }
    } ])

```

### Exercício 4 – Fraude na Enron!

1. Liste as pessoas que enviaram e-mails (de forma distinta, ou seja, sem
repetir). Quantas pessoas são?

```
    db.stocks.aggregate([{$group:{_id:'$sender'}}, {$limit:10}])

    { "_id" : "ssmith@uwtgc.org" }
    { "_id" : "confadmin@ziffenergy.com" }
    { "_id" : "tally@ssprd2.net" }
    { "_id" : "wefinvitation@forbes.com" }
    { "_id" : "cheryltd@tbardranch.com" }
    { "_id" : "tour@rice.edu" }
    { "_id" : "im1timescape@netscape.net" }
    { "_id" : "mailings@cnn.com" }
    { "_id" : "looksee@rocketmail.com" }
    { "_id" : "iertx@hern.org" }
```

2. Contabilize quantos e-mails tem a palavra “fraud”

```
    db.stocks.find({ "text" : {$regex : "fraud"} }).count();

    23
```