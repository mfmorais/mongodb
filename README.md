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
        "_id" : ObjectId("5e629ee53f80ea9cb9d1a472"), "name" : "Kilha", 
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
        "_id" : ObjectId("5e629e883f80ea9cb9d1a470"), "name" : "Mike", 
        "species" : "Hamster" 
    }
    { 
        "_id" : ObjectId("5e62a1553f80ea9cb9d1a476"), "name" : "Frodo", 
        "species" : "Hamster" 
    }
```

7. Use o find para listar todos os pets com nome Mike

```
    db.pets.find( {"name": "Mike"});

    { 
        "_id" : ObjectId("5e629e883f80ea9cb9d1a470"), "name" : "Mike", 
        "species" : "Hamster" 
    }
    { 
        "_id" : ObjectId("5e629eeb3f80ea9cb9d1a473"), "name" : "Mike", 
        "species" : "Cachorro" 
    }
```

8. Liste apenas o documento que é um Cachorro chamado Mik

```
    db.pets.find( {"name": "Mike", "species" : "Cachorro"});

    { 
        "_id" : ObjectId("5e629eeb3f80ea9cb9d1a473"), "name" : "Mike", 
        "species" : "Cachorro" 
    }
```