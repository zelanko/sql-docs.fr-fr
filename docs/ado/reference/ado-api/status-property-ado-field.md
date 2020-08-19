---
description: Status, propriété (objet Field ADO)
title: Status, propriété (champ ADO) | Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 9ef4e7b00823dcf9ce9da341ced08418a55a4bc8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441951"
---
# <a name="status-property-ado-field"></a>Status, propriété (objet Field ADO)
Indique l’état d’un objet de [champ](../../../ado/reference/ado-api/field-object.md) .  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md) . La valeur par défaut est **adFieldOK**.  
  
## <a name="remarks"></a>Notes  
  
## <a name="record-field-status"></a>État du champ d’enregistrement  
 Les modifications apportées à la valeur d’un objet **champ** dans la collection Fields d’un objet [Record](../../../ado/reference/ado-api/record-object-ado.md) sont mises en cache jusqu’à ce que la méthode [Update](../../../ado/reference/ado-api/update-method.md) de l’objet soit appelée. À ce stade, si la modification de la valeur du champ est à l’origine d’une erreur, OLE DB génère l’erreur **DB_E_ERRORSOCCURRED** (2147749409). La propriété Status de l’un des objets **Field** de la collection **Fields** à l’origine de l’erreur contient une valeur du [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md) décrivant la cause du problème.  
  
 Pour améliorer les performances, les ajouts et les suppressions dans les collections [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) de l’objet **Record** sont mis en cache jusqu’à ce que la méthode **Update** soit appelée, puis les modifications sont apportées dans une mise à jour optimiste par lot. Si la méthode **Update** n’est pas appelée, le serveur n’est pas mis à jour. Si des mises à jour échouent, une erreur de fournisseur de OLE DB (DB_E_ERRORSOCCURRED) est retournée et la propriété **Status** indique les valeurs combinées de l’opération et du code d’état d’erreur. Par exemple, **ADFIELDPENDINGINSERT ou adFieldPermissionDenied**. La propriété **Status** de chaque **champ** peut être utilisée pour déterminer la raison pour laquelle le **champ** n’a pas été ajouté, modifié ou supprimé.  
  
 De nombreux types de problèmes rencontrés lors de l’ajout, de la modification ou de la suppression d’un **champ** sont signalés via la propriété **Status** . Par exemple, si l’utilisateur supprime un **champ**, il est marqué pour suppression de la collection de **champs** . Si la **mise à jour** suivante retourne une erreur parce que l’utilisateur a tenté de supprimer un **champ** pour lequel il n’a pas d’autorisation, le **champ** aura l' **État** **adFieldPermissionDenied ou adFieldPendingDelete**. L’appel de la méthode [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) restaure les valeurs d’origine et définit l' **État** sur **adFieldOK**.  
  
 De même, la méthode **Update** peut retourner une erreur, car un nouveau **champ** a été ajouté et une valeur incorrecte lui est affectée. Dans ce cas, le nouveau **champ** se trouve dans la collection de **champs** et a l’état **AdFieldPendingInsert** et peut-être **adFieldCantCreate** (selon votre fournisseur). Vous pouvez fournir une valeur appropriée pour le nouveau **champ** et appeler **à nouveau Update** .  
  
## <a name="recordset-field-status"></a>État du champ du Recordset  
 Les modifications apportées à la valeur d’un objet **champ** dans la collection Fields d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) sont mises en cache jusqu’à ce que la méthode [Update](../../../ado/reference/ado-api/update-method.md) de l’objet soit appelée. À ce stade, si la modification de la valeur du champ est à l’origine d’une erreur, OLE DB génère l’erreur **DB_E_ERRORSOCCURRED** (2147749409). La propriété Status de l’un des objets **Field** de la collection **Fields** à l’origine de l’erreur contient une valeur du [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md) décrivant la cause du problème.  
  
## <a name="applies-to"></a>S'applique à  
 [Objet Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Status, exemple de propriété (Field) (VB)](../../../ado/reference/ado-api/status-property-example-field-vb.md)   
 [Status, exemple de propriété (VC++)](../../../ado/reference/ado-api/status-property-example-vc.md)   
