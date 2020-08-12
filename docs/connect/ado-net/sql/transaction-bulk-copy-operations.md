---
title: Transaction et opérations de copie en bloc
description: Décrit comment effectuer une opération de copie en bloc dans une transaction, y compris la validation ou la restauration de la transaction.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: f6f0cbc9-f7bf-4d6e-875f-ad1ba0b4aa62
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 685bb349366ad955248a05e23ec030788dcbc63d
ms.sourcegitcommit: 6b3569977b034554883a94d73d1c4df6e2f74fe2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85106913"
---
# <a name="transaction-and-bulk-copy-operations"></a>Transaction et opérations de copie en bloc

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Les opérations de copie en bloc peuvent être effectuées comme des opérations isolées ou dans le cadre d'une transaction à plusieurs étapes. Cette dernière option permet d'effectuer plusieurs opérations de copie en bloc dans la même transaction ainsi que d'autres opérations de base de données (telles que des insertions, mises à jour et suppressions), tout en étant en mesure de valider ou restaurer toute la transaction.  
  
Par défaut, une opération de copie en bloc est effectuée comme une opération isolée. L'opération de copie en bloc se produit de façon non transactionnelle, sans possibilité de restauration. Si vous devez restaurer tout ou partie de la copie en bloc en cas d’erreur, vous pouvez :

 - Utiliser une transaction managée par <xref:Microsoft.Data.SqlClient.SqlBulkCopy>

 - Effectuer une opération de copie en bloc dans une transaction existante

 - Inscrivez-vous dans **System.Transactions** <xref:System.Transactions.Transaction>.  
  
## <a name="performing-a-non-transacted-bulk-copy-operation"></a>Exécution d'une opération de copie en bloc non transactionnelle  
L’application console suivante montre ce qui se passe quand une opération de copie en bloc non transactionnelle rencontre une erreur au cours de l’opération.  
  
Dans l’exemple, la table source et la table de destination incluent une colonne `Identity` nommée **ProductID**. Le code commence par préparer la table de destination en supprimant toutes les lignes, puis en insérant une ligne dont la colonne **ProductID** existe dans la table source. Par défaut, une nouvelle valeur pour la colonne `Identity` est générée dans la table de destination pour chaque ligne ajoutée. Dans cet exemple, quand la connexion est ouverte, une option est définie qui oblige le processus de chargement en bloc à utiliser à la place les valeurs `Identity` de la table source.  
  
L’opération de copie en bloc est exécutée avec la propriété <xref:Microsoft.Data.SqlClient.SqlBulkCopy.BatchSize%2A> définie avec la valeur 10. Quand l'opération rencontre la ligne non valide, une exception est levée. Dans ce premier exemple, l'opération de copie en bloc est non transactionnel. Tous les lots copiés jusqu’au moment de l’erreur sont validés. Le lot contenant la clé dupliquée est restauré, et l’opération de copie en bloc est interrompue avant le traitement des lots restants.  
  
> [!NOTE]
>  Cet exemple ne s’exécutera pas, sauf si vous avez créé les tables de travail comme décrit dans [Configuration de l’exemple de copie en bloc](bulk-copy-example-setup.md). Ce code est fourni uniquement pour illustrer la syntaxe de l’utilisation de **SqlBulkCopy**. Si les tables source et de destination se trouvent dans la même instance SQL Server, il est plus facile et plus rapide d’utiliser une instruction Transact-SQL `INSERT … SELECT` pour copier les données.  
  
[!code-csharp[DataWorks SqlBulkCopyOptions_Default#1](~/../sqlclient/doc/samples/SqlBulkCopyOptions_Default.cs#1)]
  
## <a name="performing-a-dedicated-bulk-copy-operation-in-a-transaction"></a>Exécution d’une opération de copie en bloc dédiée dans une transaction  
Par défaut, une opération de copie en bloc est sa propre transaction. Si vous voulez effectuer une opération de copie en bloc dédiée, créez une instance de <xref:Microsoft.Data.SqlClient.SqlBulkCopy> avec une chaîne de connexion, ou utilisez un objet <xref:Microsoft.Data.SqlClient.SqlConnection> existant sans transaction active. L’opération de copie en bloc crée une transaction dans chaque scénario, puis valide ou restaure la transaction.  
  
Vous pouvez spécifier explicitement l’option <xref:Microsoft.Data.SqlClient.SqlBulkCopyOptions.UseInternalTransaction> dans le constructeur de classe <xref:Microsoft.Data.SqlClient.SqlBulkCopy> pour exécuter une opération de copie en bloc dans sa propre transaction. Chaque lot de l’opération s’exécutera dans une transaction distincte.  
  
> [!NOTE]
>  Puisque des lots différents sont exécutés dans différentes transactions, si une erreur se produit pendant l'opération de copie en bloc, toutes les lignes du lot actuel sont restaurées, mais les lignes des lots précédents restent dans la base de données.  
  
L’application console suivante est similaire à l’exemple précédent, à une exception près : dans cet exemple, l’opération de copie en bloc gère ses propres transactions. Tous les lots copiés jusqu’au moment de l’erreur sont validés. Le lot contenant la clé dupliquée est restauré, et l’opération de copie en bloc est interrompue avant le traitement des lots restants. 
  
> [!IMPORTANT]
>  Cet exemple ne s’exécutera pas, sauf si vous avez créé les tables de travail comme décrit dans [Configuration de l’exemple de copie en bloc](bulk-copy-example-setup.md). Ce code est fourni uniquement pour illustrer la syntaxe de l’utilisation de **SqlBulkCopy**. Si les tables source et de destination se trouvent dans la même instance SQL Server, il est plus facile et plus rapide d’utiliser une instruction Transact-SQL `INSERT … SELECT` pour copier les données.  
  
[!code-csharp[DataWorks SqlBulkCopyOptions_UseInternalTransaction#1](~/../sqlclient/doc/samples/SqlBulkCopyOptions_UseInternalTransaction.cs#1)]
  
## <a name="using-existing-transactions"></a>Utilisation de transactions existantes  
Vous pouvez spécifier un objet <xref:Microsoft.Data.SqlClient.SqlTransaction> existant en tant que paramètre dans un constructeur <xref:Microsoft.Data.SqlClient.SqlBulkCopy>. Dans ce cas, l’opération de copie en bloc est effectuée dans la transaction existante, et aucune modification n’est apportée à l’état de la transaction (elle n’est ni validée ni abandonnée). Cette méthode permet à une application d'inclure l'opération de copie en bloc dans une transaction avec d'autres opérations de base de données. Toutefois, si vous ne spécifiez pas d’objet <xref:Microsoft.Data.SqlClient.SqlTransaction> et que vous transmettez une référence null et que la connexion a une transaction active, une exception est levée.   
  
Si vous devez restaurer toute l'opération de copie en bloc en raison d'une erreur, ou si la copie en bloc doit s'exécuter dans le cadre d'un processus plus vaste pouvant être restauré, vous pouvez fournir un objet <xref:Microsoft.Data.SqlClient.SqlTransaction> au constructeur <xref:Microsoft.Data.SqlClient.SqlBulkCopy>.  
  
L’application console suivante est similaire au premier exemple (non transactionnelle), à une exception près : dans cet exemple, l’opération de copie en bloc est incluse dans une transaction externe plus vaste. Quand l'erreur de violation de clé primaire se produit, toute la transaction est restaurée et aucune ligne n'est ajoutée à la table de destination.  
  
> [!IMPORTANT]
>  Cet exemple ne s’exécutera pas, sauf si vous avez créé les tables de travail comme décrit dans [Configuration de l’exemple de copie en bloc](bulk-copy-example-setup.md). Ce code est fourni uniquement pour illustrer la syntaxe de l’utilisation de **SqlBulkCopy**. Si les tables source et de destination se trouvent dans la même instance SQL Server, il est plus facile et plus rapide d’utiliser une instruction Transact-SQL `INSERT … SELECT` pour copier les données.  
  
[!code-csharp[DataWorks SqlBulkCopy_ExternalTransaction#1](~/../sqlclient/doc/samples/SqlBulkCopy_ExternalTransaction.cs#1)]
  
## <a name="next-steps"></a>Étapes suivantes
- [Opérations de copie en bloc dans SQL Server](bulk-copy-operations-sql-server.md)
