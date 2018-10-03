---
title: Propriété Status (objet Field ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field::Status
- Field::get_Status
- Field::GetStatus
helpviewer_keywords:
- Status property [ADO Field]
ms.assetid: 8cd1f7f4-0a3a-4f07-b8ba-6582e70140ad
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 11a39cf6f30e7a4892d6f2df5c8c373ab6847632
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47741517"
---
# <a name="status-property-ado-field"></a>Status, propriété (objet Field ADO)
Indique l’état d’un [champ](../../../ado/reference/ado-api/field-object.md) objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md) valeur. La valeur par défaut est **adFieldOK**.  
  
## <a name="remarks"></a>Notes  
  
## <a name="record-field-status"></a>Champ État de l’enregistrement  
 Modifications apportées à la valeur d’un **champ** objet dans la collection de champs d’un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) objet sont mis en cache jusqu'à ce que l’objet [mise à jour](../../../ado/reference/ado-api/update-method.md) méthode est appelée. À ce stade, si la modification à la valeur du champ a provoqué une erreur, OLE DB génère l’erreur **DB_E_ERRORSOCCURRED** (2147749409). La propriété Status d’un de la **champ** des objets dans le **champs** collection qui a provoqué l’erreur contiendra une valeur comprise entre le [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md) décrivant la cause de le problème.  
  
 Pour améliorer les performances, les ajouts et les suppressions à la [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collections de la **enregistrement** objet sont mis en cache jusqu'à ce que le **mise à jour** méthode est appelée et ensuite les modifications sont effectuées dans une mise à jour optimiste de traitement par lots. Si le **mise à jour** méthode n’est pas appelée, le serveur n’est pas mis à jour. Si les mises à jour échouent, une erreur du fournisseur OLE DB (DB_E_ERRORSOCCURRED) est retournée et le **état** propriété indique les valeurs combinées du code d’état de fonctionnement et d’erreur. Par exemple, **adFieldPendingInsert ou supprimé**. Le **état** propriété pour chaque **champ** peut être utilisé pour déterminer pourquoi le **champ** a été pas ajouté, modifié ou supprimé.  
  
 Nombreux types de problèmes rencontrés lors de l’ajout, modification ou suppression d’un **champ** sont signalées par le biais du **état** propriété. Par exemple, si l’utilisateur supprime un **champ**, elle est marquée pour suppression à partir de la **champs** collection. Si le **mise à jour** renvoie une erreur car l’utilisateur a tenté de supprimer un **champ** pour lesquels ils n’ont pas d’autorisation, le **champ** aura un  **État** de **adFieldPermissionDenied OR adFieldPendingDelete**. Appelant le [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) méthode restaure les valeurs d’origine et affecte le **état** à **adFieldOK**.  
  
 De même, le **mise à jour** méthode peut retourner une erreur, car un nouveau **champ** a été ajouté et affecter une valeur inappropriée. Dans ce cas, la nouvelle **champ** se trouvent dans le **champs** collection et un état de **adFieldPendingInsert** et, éventuellement, **stocké** (en fonction de votre fournisseur). Vous pouvez fournir une valeur appropriée pour le nouveau **champ** et appelez **mise à jour** à nouveau.  
  
## <a name="recordset-field-status"></a>État du champ de jeu d’enregistrements  
 Modifications apportées à la valeur d’un **champ** objet dans la collection de champs de l’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) sont mis en cache jusqu'à ce que l’objet [mise à jour](../../../ado/reference/ado-api/update-method.md) méthode est appelée. À ce stade, si la modification à la valeur du champ a provoqué une erreur, OLE DB génère l’erreur **DB_E_ERRORSOCCURRED** (2147749409). La propriété Status d’un de la **champ** des objets dans le **champs** collection qui a provoqué l’erreur contiendra une valeur comprise entre le [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md) décrivant la cause de le problème.  
  
## <a name="applies-to"></a>S'applique à  
 [Field, objet](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Status, exemple de propriété (objet Field) (VB)](../../../ado/reference/ado-api/status-property-example-field-vb.md)   
 [Status, exemple de propriété (VC++)](../../../ado/reference/ado-api/status-property-example-vc.md)   
