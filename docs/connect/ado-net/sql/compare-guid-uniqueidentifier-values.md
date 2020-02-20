---
title: Comparaison du GUID et des valeurs uniqueidentifier
description: Montre comment utiliser des valeurs GUID et uniqueidentifier dans SQL Server et .NET.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 35fc93a9ce6eb5b1709c6671adb21eb3030dea63
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75247853"
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>Comparaison du GUID et des valeurs uniqueidentifier

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Le type de données d’identificateur global unique (GUID) dans SQL Server est représenté par le type de données `uniqueidentifier`, qui stocke une valeur binaire de 16 octets. Un GUID est un nombre binaire, principalement utilisé en tant qu’identificateur qui doit être unique dans un réseau qui comprend de nombreux ordinateurs répartis sur plusieurs sites. Les GUID peuvent être générés en appelant la fonction Transact-SQL NEWID et sont assurés d’être uniques dans le monde entier. Pour plus d’informations, consultez [uniqueidentifier (Transact-SQL)](../../../t-sql/data-types/uniqueidentifier-transact-sql.md).  
  
## <a name="working-with-sqlguid-values"></a>Utilisation des valeurs SqlGuid  
Étant donné que les GUID sont des valeurs longues et peut intelligibles, ils sont utiles pour les utilisateurs. Si des GUID générés de manière aléatoire sont utilisés pour des valeurs clés et que vous insérez un grand nombre de lignes, vous recevez des e/s aléatoires dans vos index, ce qui peut avoir un impact négatif sur les performances. Les GUID sont également relativement volumineux lorsqu’ils sont comparés à d’autres types de données. En général, nous vous recommandons d’utiliser des GUID uniquement pour des scénarios très étroits pour lesquels aucun autre type de données ne convient.  
  
### <a name="comparing-guid-values"></a>Comparaison des valeurs GUID  
Des opérateurs de comparaison peuvent être utilisés avec des valeurs `uniqueidentifier`. Toutefois, le classement n'est pas effectué par la comparaison des configurations binaires des deux valeurs. Les seules opérations autorisées sur une valeur `uniqueidentifier` sont les comparaisons (=, <>, \<, >, \<=, >=) et la vérification de la valeur NULL (IS NULL et IS NOT NULL). Aucun autre opérateur arithmétique n'est autorisé.  
  
<xref:System.Guid> et <xref:System.Data.SqlTypes.SqlGuid> disposent d’une méthode `CompareTo` pour comparer différentes valeurs de GUID. Toutefois, `System.Guid.CompareTo` et `SqlTypes.SqlGuid.CompareTo` sont implémentés différemment. <xref:System.Data.SqlTypes.SqlGuid> implémente `CompareTo` à l'aide du comportement de SQL Server, dans lequel les 6 derniers octets d'une valeur sont importants. <xref:System.Guid> évalue les 16 octets. L’exemple suivant illustre cette différence de comportement. La première section de code affiche des valeurs <xref:System.Guid> non triées et la deuxième section de code affiche les valeurs <xref:System.Guid> triées. La troisième section affiche les valeurs <xref:System.Data.SqlTypes.SqlGuid> triées. Le résultat est affiché sous la liste de codes.  
  
[!code-csharp[DataWorks SqlGuid#1](~/../sqlclient/doc/samples/SqlGuid.cs#1)]
  
Cet exemple produit les résultats suivants.  
  
```console
Unsorted Guids:  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
  
Sorted Guids:  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
  
Sorted SqlGuids:  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
```  
  
## <a name="next-steps"></a>Étapes suivantes
- [Types de données SQL Server et ADO.NET](sql-server-data-types.md)
