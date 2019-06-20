---
title: MoveFirst, MoveLast, MoveNext et MovePrevious, méthodes (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- MoveLast method [RDS]
- MovePrevious method [RDS]
- MoveFirst method [RDS]
- MoveNext method [RDS]
ms.assetid: 45c80bb5-136f-4204-9df2-78740fa55574
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7d3a46791d81557b3e93da4a0d330d118e5b00b5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66712534"
---
# <a name="movefirst-movelast-movenext-and-moveprevious-methods-rds"></a>MoveFirst, MoveLast, MoveNext et MovePrevious, méthodes (RDS)
Déplace vers le premier, au dernier enregistrement suivant ou précédent dans une certaine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DataControl.Recordset.{MoveFirst | MoveLast | MoveNext | MovePrevious}  
```  
  
#### <a name="parameters"></a>Paramètres  
 *DataControl*  
 Une variable objet qui représente un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) objet.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la **déplacer** méthodes avec la **RDS. DataControl** objet pour naviguer dans les enregistrements de données dans les contrôles liés aux données sur une page Web. Par exemple, supposons que vous affichez un **Recordset** dans une grille en le liant à un **RDS. DataControl** objet. Vous pouvez ajouter des boutons premier, dernier, suivant et précédent que les utilisateurs peuvent cliquer pour accéder au premier, dernier, suivant, ou l’enregistrement précédent dans la liste affichée **Recordset**. Pour cela, vous devez appeler la **MoveFirst**, **MoveLast**, **MoveNext**, et **MovePrevious** méthodes de la **RDS. DataControl** de l’objet dans les procédures onClick pour les boutons premier, dernier, suivant et précédent, respectivement. Le [exemple de carnet d’adresses](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md) montre comment effectuer cette opération.  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Move, méthode (ADO)](../../../ado/reference/ado-api/move-method-ado.md)   
 [MoveFirst, MoveLast, MoveNext et MovePrevious, méthodes (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [MoveRecord, méthode (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)


