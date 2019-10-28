---
title: Valeurs des colonnes SQL XML
description: Montre comment extraire et utiliser des données XML extraites de SQL Server.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: d8dc9d5100f71fed39c1e4166882230451dd139e
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451930"
---
# <a name="sql-xml-column-values"></a>Valeurs des colonnes SQL XML

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Server prend en charge le type de données `xml` et les développeurs peuvent extraire des ensembles de résultats incluant ce type à l’aide d’un comportement standard de la classe <xref:Microsoft.Data.SqlClient.SqlCommand>. Une colonne `xml` peut être récupérée comme n’importe quelle colonne (dans un <xref:Microsoft.Data.SqlClient.SqlDataReader>, par exemple), mais si vous souhaitez utiliser le contenu de la colonne au format XML, vous devez utiliser un <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Exemple  
L’application console suivante sélectionne deux lignes contenant chacune une colonne `xml` dans la table **Sales.Store** de la base de données **AdventureWorks** pour une instance de <xref:Microsoft.Data.SqlClient.SqlDataReader>. Pour chaque ligne, la valeur de la colonne `xml` est lue à l’aide de la méthode <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlXml%2A> de <xref:Microsoft.Data.SqlClient.SqlDataReader>. La valeur est stockée dans un <xref:System.Xml.XmlReader>. Notez que vous devez utiliser <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlXml%2A> plutôt que la méthode <xref:System.Data.IDataRecord.GetValue%2A> si vous souhaitez définir le contenu sur une variable <xref:System.Data.SqlTypes.SqlXml> ;  <xref:System.Data.IDataRecord.GetValue%2A> retourne la valeur de la colonne `xml` sous la forme d’une chaîne.  
  
> [!NOTE]
>  L’exemple de base de données **AdventureWorks** n’est pas installé par défaut quand vous installez SQL Server. Vous pouvez l’installer en exécutant le programme d’installation de SQL Server.  
  
[!code-csharp[DataWorks SqlDataReader_GetSqlXml#1](~/../sqlclient/doc/samples/SqlDataReader_GetSqlXml.cs#1)]
  
## <a name="next-steps"></a>Étapes suivantes
- <xref:System.Data.SqlTypes.SqlXml>
- [Données XML dans SQL Server](xml-data-sql-server.md)
