---
title: Types de données SQL Server et ADO.NET
description: Décrit l’utilisation des types de données SQL Server et leur interaction avec les types de données .NET.
ms.date: 08/15/2019
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 12ad13d6788ae2b8995289100883b06c5ab6d7c6
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452038"
---
# <a name="sql-server-data-types-and-adonet"></a>Types de données SQL Server et ADO.NET

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Server et .NET sont basés sur des systèmes de type différents, ce qui peut entraîner une perte de données potentielle. Pour préserver l’intégrité des données, le Fournisseur de données Microsoft SqlClient pour SQL Server (<xref:Microsoft.Data.SqlClient>) fournit des méthodes d’accesseur typées pour travailler avec des données SQL Server. Vous pouvez utiliser les énumérations dans les classes <xref:System.Data.SqlDbType> pour spécifier les types de données <xref:Microsoft.Data.SqlClient.SqlParameter>.  
  
SQL Server 2008 introduit de nouveaux types de données conçus pour répondre aux besoins de l’entreprise pour travailler avec des données de date et d’heure, structurées, semi-structurées et non structurées. Ceux-ci sont décrits dans la Documentation en ligne de SQL Server 2008.  
  
Les types de données SQL Server qui peuvent être utilisés dans votre application dépendent de la version de SQL Server que vous utilisez. Pour plus d’informations, consultez [types de données (moteur de base de données)](https://go.microsoft.com/fwlink/?LinkID=107468) à partir de documentation en ligne de SQL Server.
  
## <a name="in-this-section"></a>Contenu de cette section  
[SqlTypes et le DataSet](sqltypes-dataset.md)  
Décrit la prise en charge de type pour `SqlTypes` dans le `DataSet`.  
  
[Traitement des valeurs Null](handle-null-values.md)  
Montre comment utiliser des valeurs NULL et une logique à trois valeurs.  
  
[Comparaison du GUID et des valeurs uniqueidentifier](compare-guid-uniqueidentifier-values.md)  
Montre comment utiliser des valeurs GUID et uniqueidentifier dans SQL Server et .NET.  
  
[Données de date et d’heure](date-time-data.md)  
Décrit comment utiliser les nouveaux types de données de date et d’heure introduits dans SQL Server 2008.  
  
[UDT volumineux](large-udts.md)  
Montre comment récupérer des données à partir d’UDT de valeur élevée introduits dans SQL Server 2008.  
  
[Données XML dans SQL Server](xml-data-sql-server.md)  
Décrit comment utiliser des données XML extraites de SQL Server.  
  
## <a name="reference"></a>Référence  
<xref:System.Data.DataSet>  
Décrit la classe `DataSet` et tous ses membres.  
  
<xref:System.Data.SqlTypes>  
Décrit l’espace de noms `SqlTypes` et tous ses membres.  
  
<xref:System.Data.SqlDbType>  
Décrit l’énumération `SqlDbType` et tous ses membres.  
  
<xref:System.Data.DbType>  
Décrit l’énumération `DbType` et tous ses membres.  
  
## <a name="next-steps"></a>Étapes suivantes
- [Paramètres table](table-valued-parameters.md)
- [Données binaires et à valeurs élevées SQL Server](sql-server-binary-large-value-data.md)
