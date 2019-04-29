---
title: IsolationLevel, propriété | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::IsolationLevel
helpviewer_keywords:
- IsolationLevel property
ms.assetid: ea84e4b2-fbf2-4eef-b9ce-796b22e21800
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c2557c5859f10c7651cfc97fc3c849c00c26e985
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63027921"
---
# <a name="isolationlevel-property"></a>IsolationLevel, propriété
Indique le niveau d’isolation pour un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un [IsolationLevelEnum](../../../ado/reference/ado-api/isolationlevelenum.md) valeur. La valeur par défaut est **adXactReadCommitted**.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **IsolationLevel** propriété à définir l’isolation au niveau d’un **connexion** objet. Le paramètre n’entre pas en vigueur jusqu'à ce que la prochaine fois que vous appelez le [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) (méthode). Si le niveau d’isolation demandé n’est pas disponible, le fournisseur peut renvoyer le niveau d’isolation supérieur suivant sans mettre à jour le **IsolationLevel** propriété.  
  
 Le **IsolationLevel** propriété est en lecture/écriture.  
  
> [!NOTE]
>  **Utilisation de Service de données à distance** lorsqu’il est utilisé sur une côté client **connexion** objet, le **IsolationLevel** propriété peut être définie uniquement au **: adXactUnspecified**. Étant donné que les utilisateurs travaillent avec déconnecté **Recordset** objets sur un cache côté client, il peut y avoir des problèmes multi-utilisateur. Par exemple, lorsque deux utilisateurs différents tentent de mettre à jour le même enregistrement, Remote Data Service simplement permet à l’utilisateur qui met à jour l’enregistrement de tout d’abord « win ». Demande de mise à jour du second utilisateur échoue avec une erreur.  
  
## <a name="applies-to"></a>S'applique à  
 [Connection, objet (ADO MD)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [IsolationLevel et Mode, propriétés-exemple (VB)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vb.md)   
 [IsolationLevel et Mode, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vc.md)   
