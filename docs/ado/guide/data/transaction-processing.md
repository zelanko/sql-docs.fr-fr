---
title: Traitement des transactions | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- transactions [ADO]
- data updates [ADO], transaction processing
- updating data [ADO], transaction processing
- nested transactions [ADO]
ms.assetid: 74ab6706-e2dc-42cb-af77-dbc58a9cf4ce
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cab6638704856baf873274807c0e2eff9a1f92d8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67923860"
---
# <a name="transaction-processing"></a>Traitement des transactions
Un *transaction* délimite le début et la fin d’une série d’opérations d’accès aux données exécutée sur une connexion. Selon les fonctionnalités transactionnelles de votre source de données, le **connexion** objet vous permet également de créer et gérer des transactions. Par exemple, si vous utilisez le fournisseur Microsoft OLE DB pour SQL Server pour accéder à une base de données sur Microsoft SQL Server, vous pouvez créer plusieurs transactions imbriquées pour les commandes que vous exécutez.  
  
 ADO garantit que les modifications apportées à une source de données résultant d’opérations dans une transaction se produisent avec succès ensemble ou pas du tout.  
  
 Si vous annulez la transaction, ou si un de ses opérations échoue, le résultat sera comme si aucune des opérations dans la transaction s’est produite. La source de données reste telle qu’elle était avant le début de la transaction.  
  
 ADO fournit les méthodes suivantes pour le contrôle des transactions : **BeginTrans**, **CommitTrans**, et **RollbackTrans**. Utilisez ces méthodes avec un **connexion** lorsque vous souhaitez enregistrer ou annuler une série de modifications apportées aux données sources comme une unité unique de l’objet. Par exemple, pour transférer des fonds entre comptes, vous soustrayez un montant d’un et ajoutez la même quantité à l’autre. Si une mise à jour échoue, les comptes ne sont pas équilibrent. Intégration de ces modifications dans une transaction ouverte permet de s’assurer que soit la totalité soit aucune des modifications traversent.  
  
> [!NOTE]
>  Tous les fournisseurs prennent en charge les transactions. Vérifiez que la propriété définis par le fournisseur «**Transaction DDL**» s’affiche dans le **connexion** l’objet [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection, indiquant que le fournisseur prend en charge transactions. Si le fournisseur ne prend pas en charge les transactions, l’appelant une de ces méthodes retournent une erreur.  
  
 Après avoir appelé la **BeginTrans** (méthode), le fournisseur sera validée n’est plus instantanément les modifications que vous apportez jusqu'à ce que vous appeliez **CommitTrans** ou **RollbackTrans** pour mettre fin à la transaction.  
  
 Appel de la **CommitTrans** méthode enregistre les modifications apportées dans une transaction ouverte sur la connexion et se termine la transaction. Appel de la **RollbackTrans** méthode annule les modifications apportées dans une transaction ouverte et met fin à la transaction. Lorsqu’il n’existe aucune transaction ouverte, l’appel de ces méthodes génère une erreur.  
  
 En fonction le **connexion** l’objet [attributs](../../../ado/reference/ado-api/attributes-property-ado.md) propriété, en appelant le **CommitTrans** ou **RollbackTrans** peut (méthode) Démarrer automatiquement une nouvelle transaction. Si le **attributs** propriété est définie sur **adXactCommitRetaining**, le fournisseur lance automatiquement une nouvelle transaction après une **CommitTrans** appeler. Si le **attributs** propriété est définie sur **adXactAbortRetaining**, le fournisseur lance automatiquement une nouvelle transaction après une **RollbackTrans** appeler.  
  
## <a name="transaction-isolation-level"></a>Niveau d’isolation de la transaction  
 Utilisez le **IsolationLevel** propriété à définir le niveau d’isolement d’une transaction sur une **connexion** objet. Le paramètre n’entre pas en vigueur jusqu'à ce que la prochaine fois que vous appelez le [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) (méthode). Si le niveau d’isolation demandé n’est pas disponible, le fournisseur peut renvoyer le niveau d’isolation supérieur suivant. Reportez-vous à la **IsolationLevel** propriété dans la référence du programmeur ADO pour plus d’informations sur les valeurs valides.  
  
## <a name="nested-transactions"></a>Transactions imbriquées  
 Pour les fournisseurs qui prennent en charge les transactions imbriquées, en appelant le **BeginTrans** méthode dans une transaction ouverte démarre une nouvelle transaction imbriquée. La valeur de retour indique le niveau d’imbrication : une valeur de retour de « 1 » indique que vous avez ouvert une transaction de niveau supérieur (autrement dit, la transaction n'est pas imbriquée dans une autre transaction), « 2 » indique que vous avez ouvert une transaction de second niveau (une transaction imbriquée dans une transaction de niveau supérieur), et ainsi de suite. Appel **CommitTrans** ou **RollbackTrans** affecte uniquement le plus récemment ouvert transaction ; vous devez fermer ou annuler la transaction actuelle avant de résoudre les transactions de niveau supérieurs.
