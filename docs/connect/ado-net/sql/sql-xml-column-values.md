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
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: aa02072e139c2446ae67086ef43668af4403890c
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75244012"
---
# <a name="sql-xml-column-values"></a>Valeurs des colonnes SQL XML

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Server prend en charge le type de données `xml` et les développeurs peuvent extraire des ensembles de résultats incluant ce type à l’aide d’un comportement standard de la classe <xref:Microsoft.Data.SqlClient.SqlCommand>. Une colonne `xml` peut être récupérée comme n’importe quelle colonne (dans un <xref:Microsoft.Data.SqlClient.SqlDataReader>, par exemple), mais si vous souhaitez utiliser le contenu de la colonne au format XML, vous devez utiliser un <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Exemple  
L’application console suivante sélectionne deux lignes contenant chacune une colonne `xml` dans la table **Sales.Store** de la base de données **AdventureWorks** pour une instance de <xref:Microsoft.Data.SqlClient.SqlDataReader>. Pour chaque ligne, la valeur de la colonne `xml` est lue à l’aide de la méthode <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlXml%2A> de <xref:Microsoft.Data.SqlClient.SqlDataReader>. La valeur est stockée dans un <xref:System.Xml.XmlReader>. Notez que vous devez utiliser <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlXml%2A> plutôt que la méthode <xref:System.Data.IDataRecord.GetValue%2A> si vous souhaitez définir le contenu sur une variable <xref:System.Data.SqlTypes.SqlXml> ; <xref:System.Data.IDataRecord.GetValue%2A> renvoie la valeur de la colonne `xml` sous la forme d’une chaîne.  
  
> [!NOTE]
>  L’exemple de base de données **AdventureWorks** n’est pas installé par défaut quand vous installez SQL Server. Vous pouvez l’installer en exécutant le programme d’installation de SQL Server.  
  
[!code-csharp [SqlDataReader_GetSqlXml#1](~/../sqlclient/doc/samples/SqlDataReader_GetSqlXml.cs#1)]
  
## <a name="next-steps"></a>Étapes suivantes
- <xref:System.Data.SqlTypes.SqlXml>
- [Données XML dans SQL Server](xml-data-sql-server.md)
