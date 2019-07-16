---
title: BeginTrans, CommitTrans et RollbackTrans, méthodes (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::raw_RollbackTrans
- Connection15::CommitTrans
- Connection15::raw_CommitTrans
- Connection15::raw_BeginTrans
- Connection15::BeginTrans
- Connection15::RollbackTrans
helpviewer_keywords:
- BeginTrans method [ADO]
- CommitTrans method [ADO]
- RollbackTrans method [ADO]
ms.assetid: d4683472-4120-4236-8640-fa9ae289e23e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c3a8bc22e57d91ab64bdbbc5fc694575a8aa8ff9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67920528"
---
# <a name="begintrans-committrans-and-rollbacktrans-methods-ado"></a>BeginTrans, CommitTrans et RollbackTrans, méthodes (ADO)
Ces méthodes de transaction gèrent le traitement des transactions dans un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) de l’objet comme suit :  
  
-   **BeginTrans** commence une nouvelle transaction.  
  
-   **CommitTrans** enregistre les modifications et termine la transaction actuelle. Il peut également démarrer une nouvelle transaction.  
  
-   **RollbackTrans** annule toutes les modifications apportées pendant la transaction en cours et termine la transaction. Il peut également démarrer une nouvelle transaction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
level = object.BeginTrans()  
object.BeginTrans  
object.CommitTrans  
object.RollbackTrans  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **BeginTrans** peut être appelé comme une fonction qui retourne un **Long** variable indiquant le niveau d’imbrication de la transaction.  
  
#### <a name="parameters"></a>Paramètres  
 *object*  
 Un **connexion** objet.  
  
## <a name="connection"></a>Connexion  
 Utilisez ces méthodes avec un **connexion** lorsque vous souhaitez enregistrer ou annuler une série de modifications apportées aux données sources comme une unité unique de l’objet. Par exemple, pour transférer des fonds entre comptes, vous soustrayez un montant d’un et ajoutez la même quantité à l’autre. Si une mise à jour échoue, les comptes ne sont pas équilibrent. Intégration de ces modifications dans une transaction ouverte permet de s’assurer que soit la totalité soit aucune des modifications traversent.  
  
> [!NOTE]
>  Tous les fournisseurs prennent en charge les transactions. Vérifiez que la propriété définis par le fournisseur «**Transaction DDL**» s’affiche dans le **connexion** l’objet [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection, indiquant que le fournisseur prend en charge transactions. Si le fournisseur ne prend pas en charge les transactions, l’appelant une de ces méthodes retournent une erreur.  
  
 Après avoir appelé la **BeginTrans** (méthode), le fournisseur sera validée n’est plus instantanément les modifications que vous apportez jusqu'à ce que vous appeliez **CommitTrans** ou **RollbackTrans** pour mettre fin à la transaction.  
  
 Pour les fournisseurs qui prennent en charge les transactions imbriquées, en appelant le **BeginTrans** méthode dans une transaction ouverte démarre une nouvelle transaction imbriquée. La valeur de retour indique le niveau d’imbrication : une valeur de retour de « 1 » indique que vous avez ouvert une transaction de niveau supérieur (autrement dit, la transaction n'est pas imbriquée dans une autre transaction), « 2 » indique que vous avez ouvert une transaction de second niveau (une transaction imbriquée dans une transaction de niveau supérieur), et ainsi de suite. Appel **CommitTrans** ou **RollbackTrans** affecte uniquement le plus récemment ouvert transaction ; vous devez fermer ou annuler la transaction actuelle avant de résoudre les transactions de niveau supérieurs.  
  
 Appel de la **CommitTrans** méthode enregistre les modifications apportées dans une transaction ouverte sur la connexion et se termine la transaction. Appel de la **RollbackTrans** méthode annule les modifications apportées dans une transaction ouverte et met fin à la transaction. Lorsqu’il n’existe aucune transaction ouverte, l’appel de ces méthodes génère une erreur.  
  
 Selon le **connexion** l’objet [attributs](../../../ado/reference/ado-api/attributes-property-ado.md) propriété, en appelant le **CommitTrans** ou **RollbackTrans** méthodes peuvent Démarrer automatiquement une nouvelle transaction. Si le **attributs** propriété est définie sur **adXactCommitRetaining**, le fournisseur lance automatiquement une nouvelle transaction après une **CommitTrans** appeler. Si le **attributs** propriété est définie sur **adXactAbortRetaining**, le fournisseur lance automatiquement une nouvelle transaction après une **RollbackTrans** appeler.  
  
## <a name="remote-data-service"></a>Service de données distant  
 Le **BeginTrans**, **CommitTrans**, et **RollbackTrans** méthodes ne sont pas disponibles sur une côté client **connexion** objet.  
  
## <a name="applies-to"></a>S'applique à  
 [Connection, objet (ADO MD)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [BeginTrans, CommitTrans et RollbackTrans, méthodes-exemple (VB)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vb.md)   
 [BeginTrans, CommitTrans et RollbackTrans, méthodes-exemple (VC ++)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vc.md)   
 [Attributes, propriété (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
