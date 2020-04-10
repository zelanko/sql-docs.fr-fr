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
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 2704ceae26c58edc85b0cbc1f0fbe6cc98f64311
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80902000"
---
# <a name="sql-xml-column-values"></a>Valeurs des colonnes SQL XML

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

SQL Server prend en charge le type de données `xml` et les développeurs peuvent extraire des ensembles de résultats incluant ce type à l’aide d’un comportement standard de la classe <xref:Microsoft.Data.SqlClient.SqlCommand>. Une colonne `xml` peut être récupérée comme n’importe quelle colonne (dans un <xref:Microsoft.Data.SqlClient.SqlDataReader>, par exemple), mais si vous souhaitez utiliser le contenu de la colonne au format XML, vous devez utiliser un <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Exemple  
L’application console suivante sélectionne deux lignes contenant chacune une colonne `xml` dans la table **Sales.Store** de la base de données **AdventureWorks** pour une instance de <xref:Microsoft.Data.SqlClient.SqlDataReader>. Pour chaque ligne, la valeur de la colonne `xml` est lue à l’aide de la méthode <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlXml%2A> de <xref:Microsoft.Data.SqlClient.SqlDataReader>. La valeur est stockée dans un <xref:System.Xml.XmlReader>. Notez que vous devez utiliser <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlXml%2A> plutôt que la méthode <xref:System.Data.IDataRecord.GetValue%2A> si vous souhaitez définir le contenu sur une variable <xref:System.Data.SqlTypes.SqlXml> ; <xref:System.Data.IDataRecord.GetValue%2A> renvoie la valeur de la colonne `xml` sous la forme d’une chaîne.  
  
> [!NOTE]
>  L’exemple de base de données **AdventureWorks** n’est pas installé par défaut quand vous installez SQL Server. Vous pouvez l’installer en exécutant le programme d’installation de SQL Server.  
  
[!code-csharp [SqlDataReader_GetSqlXml#1](~/../sqlclient/doc/samples/SqlDataReader_GetSqlXml.cs#1)]
  
## <a name="next-steps"></a>Étapes suivantes
- <xref:System.Data.SqlTypes.SqlXml>
- [Données XML dans SQL Server](xml-data-sql-server.md)
