---
title: Apache Spark synchroniseren voor externe tabeldefinities in een serverloze SQL-pool (preview)
description: Overzicht van hoe u query’s kunt uitvoeren op Spark-tabellen met behulp van een serverloze SQL-pool (preview)
services: synapse-analytics
author: julieMSFT
ms.service: synapse-analytics
ms.topic: overview
ms.subservice: sql
ms.date: 04/15/2020
ms.author: jrasnick
ms.reviewer: jrasnick
ms.openlocfilehash: ea4e7cd009be8a78faa0dcfab44371a350b6a200
ms.sourcegitcommit: 96918333d87f4029d4d6af7ac44635c833abb3da
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/04/2020
ms.locfileid: "93315833"
---
# <a name="synchronize-apache-spark-for-azure-synapse-external-table-definitions-in-serverless-sql-pool-preview"></a>Apache Spark synchroniseren voor externe tabeldefinities van Azure Synapse in een serverloze SQL-pool (preview)

Met een serverloze SQL-pool (preview) kunnen automatisch metagegevens worden gesynchroniseerd van Apache Spark. Er wordt een serverloze SQL-pooldatabase gemaakt voor elke database in serverloze Apache Spark-pools (preview). 

Voor elke externe Spark-tabel die is gebaseerd op Parquet en zich in Azure Storage bevindt, wordt een externe tabel gemaakt in een serverloze SQL-pooldatabase. Op deze manier kunt u uw Spark-pools afsluiten en nog steeds query’s uitvoeren op externe Spark-tabellen vanuit een serverloze SQL-pool.

Wanneer een tabel is gepartitioneerd in Spark, worden de bestanden in de opslag geordend in mappen. Serverloze SQL-pools maken gebruik van partitiemetagegevens en werken alleen met relevante mappen en bestanden voor uw query.

Synchronisatie van metagegevens wordt automatisch geconfigureerd voor elke serverloze Apache Spark-pool die is ingericht in de Azure Synapse-werkruimte. U kunt direct beginnen met het uitvoeren van query’s op externe Spark-tabellen.

Elke externe tabel van Spark Parquet die zich in Azure Storage bevindt, wordt vertegenwoordigd door een externe tabel in een dbo-schema dat overeenkomt met een serverloze SQL-pooldatabase. 

Voer voor externe Spark-tabelquery’s een query uit die is gericht op een externe [spark_table]. Voordat u het volgende voorbeeld uitvoert, moet u controleren of u de juiste [toegang tot het opslagaccount](develop-storage-files-storage-access-control.md) hebt waar de bestanden zich bevinden.

```sql
SELECT * FROM [db].dbo.[spark_table]
```

> [!NOTE]
> Toevoegen, verwijderen of wijzigen van externe Spark-tabelopdrachten voor een kolom wordt niet weerspiegeld de in externe tabel in een serverloze SQL-pool.

## <a name="apache-spark-data-types-to-sql-data-types-mapping"></a>Apache Spark-gegevenstypen toewijzen aan SQL-gegevenstypen

| Spark-gegevenstype | SQL-gegevenstype               |
| --------------- | --------------------------- |
| ByteType        | smallint                    |
| ShortType      | smallint                    |
| IntegerType     | int                         |
| LongType        | bigint                      |
| FloatType       | werkelijk                        |
| DoubleType      | float                       |
| DecimalType     | decimal                     |
| TimestampType   | datetime2                   |
| DateType        | date                        |
| StringType      | varchar(max)\*               |
| BinaryType      | varbinary                   |
| BooleanType     | bit                         |
| ArrayType       | varchar(max)\* (into JSON)\** |
| MapType         | varchar(max)\* (into JSON)\** |
| StructType      | varchar(max)\* (into JSON)\** |

\* De gebruikte sortering is Latin1_General_100_BIN2_UTF8.

\** ArrayType, MapType en StructType worden weergegeven als JSON’s.



## <a name="next-steps"></a>Volgende stappen

Ga naar het artikel [Storage-toegangsbeheer](develop-storage-files-storage-access-control.md) voor meer informatie over opslagtoegangsbeheer.
