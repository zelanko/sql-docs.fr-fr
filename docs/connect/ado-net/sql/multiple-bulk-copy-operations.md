---
title: Plusieurs opérations de copie en bloc
description: Décrit comment effectuer plusieurs opérations de copie en bloc de données dans une instance SQL Server à l’aide de la classe SqlBulkCopy.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: f052e70d55a789eab731f94ae086d2f47384593c
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896582"
---
# <a name="multiple-bulk-copy-operations"></a>Plusieurs opérations de copie en bloc

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Vous pouvez effectuer plusieurs opérations de copie en bloc à l’aide d’une seule instance d’une classe <xref:Microsoft.Data.SqlClient.SqlBulkCopy>. Si les paramètres des opérations changent entre les copies (par exemple le nom de la table de destination), vous devez les mettre à jour avant d’appeler l’une des méthodes **WriteToServer**, comme illustré dans l’exemple suivant. Sans modification explicite, toutes les valeurs de propriété restent identiques à celles utilisées lors de la précédente opération de copie pour une instance donnée.  
  
> [!NOTE]
>  L’exécution de plusieurs opérations de copie en bloc à l’aide de la même instance de <xref:Microsoft.Data.SqlClient.SqlBulkCopy> est généralement plus efficace que l’utilisation d’une instance distincte pour chaque opération.  
  
Si vous effectuez plusieurs opérations de copie en bloc à l’aide du même objet <xref:Microsoft.Data.SqlClient.SqlBulkCopy>, aucune restriction ne s’applique selon que les informations sources ou cibles sont égales ou différentes dans chaque opération. Toutefois, vous devez vous assurer que les informations d'association de colonnes sont définies correctement chaque fois que vous écrivez sur le serveur.  

## <a name="example"></a>Exemple

> [!IMPORTANT]
>  Cet exemple ne s’exécutera pas, sauf si vous avez créé les tables de travail comme décrit dans [Configuration de l’exemple de copie en bloc](bulk-copy-example-setup.md). Ce code est fourni uniquement pour illustrer la syntaxe de l’utilisation de **SqlBulkCopy**. Si les tables source et de destination se trouvent dans la même instance SQL Server, il est plus facile et plus rapide d’utiliser une instruction Transact-SQL `INSERT … SELECT` pour copier les données.  
  
[!code-csharp[DataWorks SqlBulkCopy_._ColumnMappingOrdersDetails#1](~/../sqlclient/doc/samples/SqlBulkCopy_ColumnMappingOrdersDetails.cs#1)]
  
## <a name="next-steps"></a>Étapes suivantes
- [Opérations de copie en bloc dans SQL Server](bulk-copy-operations-sql-server.md)
