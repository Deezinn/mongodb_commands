# Lista de Comandos do MongoDB

## 📌 Comandos Básicos

| Comando | Função | Exemplo |
|---------|--------|---------|
| `db.createCollection()` | Cria uma nova coleção. | `db.createCollection("minhaColecao")` |
| `db.collection.insertOne()` | Insere um único documento em uma coleção. | `db.minhaColecao.insertOne({ nome: "João", idade: 30 })` |
| `db.collection.insertMany()` | Insere múltiplos documentos em uma coleção. | `db.minhaColecao.insertMany([{ nome: "Maria", idade: 25 }, { nome: "Pedro", idade: 35 }])` |
| `db.collection.find()` | Retorna todos os documentos que correspondem a uma consulta. | `db.minhaColecao.find({ idade: { $gt: 20 } })` |
| `db.collection.findOne()` | Retorna um único documento que corresponde a uma consulta. | `db.minhaColecao.findOne({ nome: "João" })` |

## 🔄 Atualização de Dados

| Comando | Função | Exemplo |
|---------|--------|---------|
| `db.collection.updateOne()` | Atualiza um único documento que corresponde a uma consulta. | `db.minhaColecao.updateOne({ nome: "João" }, { $set: { idade: 31 } })` |
| `db.collection.updateMany()` | Atualiza múltiplos documentos que correspondem a uma consulta. | `db.minhaColecao.updateMany({ idade: { $lt: 30 } }, { $set: { status: "jovem" } })` |

## ❌ Remoção de Dados

| Comando | Função | Exemplo |
|---------|--------|---------|
| `db.collection.deleteOne()` | Remove um único documento que corresponde a uma consulta. | `db.minhaColecao.deleteOne({ nome: "Pedro" })` |
| `db.collection.deleteMany()` | Remove múltiplos documentos que correspondem a uma consulta. | `db.minhaColecao.deleteMany({ idade: { $gt: 30 } })` |

## 📊 Consultas e Estatísticas

| Comando | Função | Exemplo |
|---------|--------|---------|
| `db.collection.countDocuments()` | Conta o número de documentos que correspondem a uma consulta. | `db.minhaColecao.countDocuments({ idade: { $gt: 20 } })` |
| `db.collection.distinct()` | Retorna um array de valores distintos para um campo especificado. | `db.minhaColecao.distinct("nome")` |
| `db.collection.aggregate()` | Processa dados de documentos e retorna resultados computados. | `db.minhaColecao.aggregate([{ $match: { idade: { $gt: 20 } } }, { $group: { _id: "$status", total: { $sum: 1 } } }])` |

## 🔍 Índices

| Comando | Função | Exemplo |
|---------|--------|---------|
| `db.collection.createIndex()` | Cria um índice em um campo especificado. | `db.minhaColecao.createIndex({ nome: 1 })` |
| `db.collection.dropIndex()` | Remove um índice de uma coleção. | `db.minhaColecao.dropIndex("nome_1")` |
| `db.collection.getIndexes()` | Retorna uma lista de índices em uma coleção. | `db.minhaColecao.getIndexes()` |

## 📂 Gerenciamento de Coleções

| Comando | Função | Exemplo |
|---------|--------|---------|
| `db.collection.renameCollection()` | Renomeia uma coleção. | `db.minhaColecao.renameCollection("novaColecao")` |
| `db.collection.drop()` | Remove uma coleção do banco de dados. | `db.minhaColecao.drop()` |
| `db.collection.bulkWrite()` | Executa operações de escrita em massa. | `db.minhaColecao.bulkWrite([{ insertOne: { document: { nome: "Ana", idade: 28 } } }, { updateOne: { filter: { nome: "João" }, update: { $set: { idade: 32 } } } }])` |

## 🔄 Operações Avançadas

| Comando | Função | Exemplo |
|---------|--------|---------|
| `db.collection.replaceOne()` | Substitui um único documento que corresponde a uma consulta. | `db.minhaColecao.replaceOne({ nome: "Ana" }, { nome: "Ana", idade: 29, cidade: "São Paulo" })` |
| `db.collection.find().sort()` | Ordena os documentos retornados por uma consulta. | `db.minhaColecao.find().sort({ idade: -1 })` |
| `db.collection.find().limit()` | Limita o número de documentos retornados por uma consulta. | `db.minhaColecao.find().limit(5)` |
| `db.collection.find().skip()` | Pula um número especificado de documentos em uma consulta. | `db.minhaColecao.find().skip(10)` |
| `db.collection.find().projection()` | Seleciona campos específicos para retornar em uma consulta. | `db.minhaColecao.find({}, { nome: 1, idade: 1 })` |
| `db.collection.watch()` | Assiste mudanças em uma coleção. | `const changeStream = db.minhaColecao.watch(); changeStream.on("change", (change) => console.log(change))` |
| `db.collection.stats()` | Retorna estatísticas sobre uma coleção. | `db.minhaColecao.stats()` |
| `db.collection.validate()` | Valida a integridade de uma coleção. | `db.minhaColecao.validate()` |
| `db.collection.explain()` | Fornece informações sobre como uma operação será executada. | `db.minhaColecao.find({ idade: { $gt: 20 } }).explain("executionStats")` |

## 🛠 Outras Operações

| Comando | Função | Exemplo |
|---------|--------|---------|
| `db.collection.mapReduce()` | Processa documentos e retorna resultados agregados. | `db.minhaColecao.mapReduce(function() { emit(this.nome, 1) }, function(key, values) { return Array.sum(values) }, { out: "resultadoMapReduce" })` |
| `db.collection.save()` | Insere um documento ou atualiza se já existir. | `db.minhaColecao.save({ _id: 1, nome: "Carlos", idade: 40 })` |
| `db.collection.findOneAndUpdate()` | Encontra um documento e o atualiza. | `db.minhaColecao.findOneAndUpdate({ nome: "Carlos" }, { $set: { idade: 41 } })` |
| `db.collection.findOneAndDelete()` | Encontra um documento e o deleta. | `db.minhaColecao.findOneAndDelete({ nome: "Carlos" })` |
| `db.collection.findOneAndReplace()` | Encontra um documento e o substitui. | `db.minhaColecao.findOneAndReplace({ nome: "Carlos" }, { nome: "Carlos", idade: 42, cidade: "Rio" })` |
| `db.collection.dropIndexes()` | Remove todos os índices de uma coleção. | `db.minhaColecao.dropIndexes()` |
| `db.collection.reIndex()` | Recria todos os índices de uma coleção. | `db.minhaColecao.reIndex()` |
| `db.collection.dataSize()` | Retorna o tamanho dos dados de uma coleção. | `db.minhaColecao.dataSize()` |
| `db.collection.totalSize()` | Retorna o tamanho total de uma coleção, incluindo índices. | `db.minhaColecao.totalSize()` |
| `db.collection.storageSize()` | Retorna o tamanho de armazenamento de uma coleção. | `db.minhaColecao.storageSize()` |
| `db.collection.totalIndexSize()` | Retorna o tamanho total dos índices de uma coleção. | `db.minhaColecao.totalIndexSize()` |
| `db.collection.convertToCapped()` | Converte uma coleção para uma coleção limitada (capped). | `db.minhaColecao.convertToCapped(1024)` |

---
✅ **Este documento reúne os principais comandos do MongoDB para manipulação de dados!**
