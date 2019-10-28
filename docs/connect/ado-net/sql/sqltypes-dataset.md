---
title: SqlTypes et le DataSet
description: Décrit la prise en charge de type pour SqlTypes dans le jeu de données.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 70efb8615a70677c709abd6d9129c63de9420ffc
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451983"
---
# <a name="sqltypes-and-the-dataset"></a>SqlTypes et le DataSet

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

ADO.NET 2,0 a introduit une prise en charge améliorée du type pour l' `DataSet` via l’espace de noms <xref:System.Data.SqlTypes>. Les types de <xref:System.Data.SqlTypes> sont conçus pour fournir des types de données avec la même sémantique et la même précision que les types de données d’une base de données SQL Server. Chaque type de données dans <xref:System.Data.SqlTypes> a un type de données équivalent dans SQL Server, avec la même représentation de données sous-jacentes.  
  
L’utilisation de <xref:System.Data.SqlTypes> directement dans une <xref:System.Data.DataSet> confère plusieurs avantages lors de l’utilisation de SQL Server types de données. <xref:System.Data.SqlTypes> prend en charge la même sémantique que SQL Server les types de données natifs. La spécification de l’une des <xref:System.Data.SqlTypes> dans la définition d’un <xref:System.Data.DataColumn> élimine la perte de précision qui peut se produire lors de la conversion de types de données décimales ou numériques en l’un des types de données common language runtime (CLR).  

L’exemple suivant crée un objet <xref:System.Data.DataTable>, définissant de façon explicite les types de données <xref:System.Data.DataColumn> en utilisant <xref:System.Data.SqlTypes> au lieu de types CLR. Le code remplit l’objet <xref:System.Data.DataTable> de données de la table Sales.SalesOrderDetail dans la base de données AdventureWorks dans SQL Server. La sortie affichée dans la fenêtre de console affiche le type de données de chaque colonne et les valeurs récupérées à partir de SQL Server.  
  
[!code-csharp[DataWorks DataColumn_DataType#1](~/../sqlclient/doc/samples/DataColumn_DataType.cs#1)]
