---
title: Suppression d’enregistrements à l’aide de la méthode Delete | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, deleting records
- deleting records [ADO]
- editing data [ADO], Delete method
- Delete method [ADO]
ms.assetid: bfed5cfa-7f57-463b-9da2-0c612a079d30
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5a862a244f06c64767f41529b4fff36881895a0b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925556"
---
# <a name="deleting-records-using-the-delete-method"></a>Suppression d’enregistrements avec la méthode Delete
À l’aide de la **supprimer** méthode marque l’enregistrement actif ou un groupe d’enregistrements dans une **Recordset** objet pour la suppression. Si le **Recordset** objet n’autorise pas de suppression de l’enregistrement, une erreur se produit. Si vous êtes en mode de mise à jour immédiate, suppressions se produisent immédiatement dans la base de données. Si un enregistrement ne peut pas être supprimé avec succès (en raison de violations d’intégrité de base de données, par exemple), l’enregistrement reste en mode édition après l’appel à **mise à jour.** Cela signifie que vous devez annuler la mise à jour à l’aide [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) avant de déplacer l’enregistrement en cours (par exemple, à l’aide de [fermer](../../../ado/reference/ado-api/close-method-ado.md), [déplacer](../../../ado/reference/ado-api/move-method-ado.md), ou [ NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)).  
  
 Si vous êtes en mode de mise à jour par lot, les enregistrements marqués pour suppression à partir du cache et la suppression se produit lorsque vous appelez le **UpdateBatch** (méthode). (Pour afficher les enregistrements supprimés, définissez le **filtre** propriété **adFilterAffectedRecords** après **supprimer** est appelée.)  
  
 Tente de récupérer les valeurs de champ à partir de l’enregistrement supprimé génère une erreur. Après avoir supprimé l’enregistrement en cours, l’enregistrement supprimé reste actif jusqu'à ce que vous déplacez vers un autre enregistrement. Une fois que vous vous éloignez de l’enregistrement supprimé, il n’est plus accessible.  
  
 Si vous imbriquez des suppressions dans une transaction, vous pouvez récupérer les enregistrements supprimés à l’aide de la **RollbackTrans** (méthode). Si vous êtes en mode de mise à jour par lot, vous pouvez annuler une suppression en attente ou un groupe de suppressions en attente à l’aide de la **CancelBatch** (méthode).  
  
 Si la tentative de suppression des enregistrements échoue en raison d’un conflit avec les données sous-jacentes (par exemple, un enregistrement déjà supprimé par un autre utilisateur), le fournisseur retourne des avertissements dans le **erreurs** collection mais n’interrompt ne pas le programme exécution. Une erreur d’exécution se produit uniquement en cas de conflits sur tous les enregistrements demandés.  
  
 Si le **Unique Table** propriété dynamique a la valeur et le **Recordset** est le résultat de l’exécution d’une opération de jointure sur plusieurs tables, le **supprimer** méthode supprimer les lignes uniquement à partir de la table nommée dans le **Unique Table** propriété.  
  
 Le **supprimer** méthode prend un argument facultatif qui vous permet de spécifier les enregistrements affectés par la **supprimer** opération. Les seules valeurs valides pour cet argument sont une des suivante ADO **AffectEnum** constantes énumérées :  
  
-   **adAffectCurrent** affecte uniquement l’enregistrement actif.  
  
-   **adAffectGroup** affecte uniquement les enregistrements qui répondent à des cours **filtre** paramètre de propriété. Le **filtre** propriété doit être définie sur une **FilterGroupEnum** valeur ou un tableau de **signets** pour utiliser cette option.  
  
 Le code suivant montre un exemple de spécification **adAffectGroup** lors de l’appel le **supprimer** (méthode). Cet exemple ajoute des enregistrements à l’exemple **Recordset** et met à jour de la base de données. Ensuite il filtre le **Recordset** à l’aide de la **adFilterAffectedRecords** constante énumérée de filtre, ce qui laisse uniquement les enregistrements qui vient d’être ajoutés soit visible dans le **Recordset.** Enfin, il appelle le **supprimer** (méthode) et spécifie que tous les enregistrements qui répondent à des cours **filtre** le paramètre de propriété (les nouveaux enregistrements) doit être supprimé.  
  
```  
'BeginDeleteGroup  
    'add some bogus records  
    With objRs  
        For i = 0 To 8  
            .AddNew  
            .Fields("CompanyName") = "Shipper Number " & i + 1  
            .Fields("Phone") = "(425) 555-000" & (i + 1)  
            .Update  
        Next i  
  
        ' update  
        .UpdateBatch  
  
        'filter on newly added records  
        .Filter = adFilterAffectedRecords  
        Debug.Print "Deleting the " & .RecordCount & _  
                    " records you just added."  
  
        'delete the newly added bogus records  
        .Delete adAffectGroup  
        .Filter = adFilterNone  
        Debug.Print .RecordCount & " records remain."  
    End With  
'EndDeleteGroup  
```
