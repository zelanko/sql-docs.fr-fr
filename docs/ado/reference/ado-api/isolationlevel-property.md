---
title: "Propriété IsolationLevel | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Connection15::IsolationLevel
helpviewer_keywords:
- IsolationLevel property
ms.assetid: ea84e4b2-fbf2-4eef-b9ce-796b22e21800
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: aff806c29bd72244c44011ab513affc77438e874
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="isolationlevel-property"></a>Propriété IsolationLevel
Indique le niveau d’isolement d’une [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un [IsolationLevelEnum](../../../ado/reference/ado-api/isolationlevelenum.md) valeur. La valeur par défaut est **adXactReadCommitted**.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **IsolationLevel** propriété à définir l’isolation au niveau d’un **connexion** objet. Le paramètre ne prendre effet qu’après la prochaine fois que vous appelez le [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) (méthode). Si le niveau d’isolation demandé n’est pas disponible, le fournisseur peut renvoyer le niveau d’isolation supérieur suivant sans mettre à jour le **IsolationLevel** propriété.  
  
 Le **IsolationLevel** propriété est en lecture/écriture.  
  
> [!NOTE]
>  **Utilisation du Service de données à distance** lorsqu’il est utilisé sur un côté client **connexion** objet, le **IsolationLevel** propriété peut être définie uniquement sur **: adXactUnspecified**. Étant donné que les utilisateurs travaillent avec déconnecté **Recordset** d’objets dans un cache côté client, il peut y avoir des problèmes multi-utilisateur. Par exemple, lorsque deux utilisateurs différents tentent de mettre à jour le même enregistrement, Remote Data Service simplement permet à l’utilisateur qui met à jour l’enregistrement de tout d’abord « win ». Demande de mise à jour du second utilisateur échoue avec une erreur.  
  
## <a name="applies-to"></a>S'applique à  
 [Objet de connexion (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [IsolationLevel et Mode, propriétés-exemple (VB)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vb.md)   
 [IsolationLevel et Mode, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vc.md)   

