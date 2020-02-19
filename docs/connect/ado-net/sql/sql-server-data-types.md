---
title: Types de données SQL Server et ADO.NET
description: Décrit l’utilisation des types de données SQL Server et leur interaction avec les types de données .NET.
ms.date: 08/15/2019
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 46edb611f29c447f7e1ca2228212ef3e0d594fff
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75244041"
---
# <a name="sql-server-data-types-and-adonet"></a>Types de données SQL Server et ADO.NET

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Server et .NET sont basés sur des systèmes de types différents, ce qui peut entraîner une perte de données potentielle. Pour préserver l’intégrité des données, le fournisseur de données Microsoft SqlClient pour SQL Server (<xref:Microsoft.Data.SqlClient>) fournit des méthodes d’accesseur typées pour travailler avec des données SQL Server. Vous pouvez utiliser les énumérations dans les classes <xref:System.Data.SqlDbType> pour spécifier les types de données <xref:Microsoft.Data.SqlClient.SqlParameter>.  
  
SQL Server 2008 introduit de nouveaux types de données conçus pour répondre aux besoins professionnels pour travailler avec des données de date et d’heure, structurées, semi-structurées et non structurées. Ceux-ci sont décrits dans la Documentation en ligne de SQL Server 2008.  
  
Les types de données SQL Server qui peuvent être utilisés dans votre application dépendent de la version de SQL Server que vous utilisez. Pour plus d’informations, consultez [Types de données (Moteur de base de données)](https://go.microsoft.com/fwlink/?LinkID=107468) dans la documentation en ligne de SQL Server.
  
## <a name="in-this-section"></a>Contenu de cette section  
[SqlTypes et le DataSet](sqltypes-dataset.md)  
Décrit la prise en charge de type pour `SqlTypes` dans le `DataSet`.  
  
[Traitement des valeurs Null](handle-null-values.md)  
Montre comment utiliser des valeurs null et une logique à trois valeurs.  
  
[Comparaison du GUID et des valeurs uniqueidentifier](compare-guid-uniqueidentifier-values.md)  
Montre comment utiliser des valeurs GUID et uniqueidentifier dans SQL Server et .NET.  
  
[Données de date et d’heure](date-time-data.md)  
Décrit comment utiliser les nouveaux types de données de date et d’heure introduits dans SQL Server 2008.  
  
[UDT volumineux](large-udts.md)  
Montre comment récupérer des données à partir des UDT de valeur élevée introduits dans SQL Server 2008.  
  
[Données XML dans SQL Server](xml-data-sql-server.md)  
Décrit comment utiliser des données XML extraites de SQL Server.  
  
## <a name="reference"></a>Informations de référence  
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
