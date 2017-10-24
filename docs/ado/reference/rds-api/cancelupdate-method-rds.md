---
title: "CancelUpdate, méthode (RDS) | Documents Microsoft"
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
helpviewer_keywords:
- CancelUpdate method [RDS]
ms.assetid: 76d8a6e9-bc6c-4ea0-8e7a-2bae5ed06650
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9b8e41e0cd963b87b73fc65b3f149f22f3a67b76
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="cancelupdate-method-rds"></a>CancelUpdate, méthode (RDS)
Annule les modifications apportées à la ligne actuelle ou nouvelle d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et Windows Server 2012, les composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (consultez Windows 8 et [Cookbook de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client Bureau à distance seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. La migration vers les applications qui utilisent des services Bureau à distance [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DataControl.CancelUpdate  
```  
  
#### <a name="parameters"></a>Paramètres  
 *DataControl*  
 Une variable objet qui représente un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) objet.  
  
## <a name="remarks"></a>Notes  
 Le Service de curseur pour OLE DB conserve à la fois une copie des valeurs d’origine et un cache des modifications. Lorsque vous appelez **CancelUpdate**, le cache des modifications est réinitialisé à vide et tous les contrôles dépendants sont actualisés avec les données d’origine.  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de méthode CancelUpdate (VBScript)](../../../ado/reference/rds-api/cancelupdate-method-example-vbscript.md)   
 [Boutons de commande de carnet d’adresses](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [Cancel (méthode) (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Cancel (méthode) (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [CancelBatch, méthode (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [CancelUpdate, méthode (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Refresh, méthode (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [SubmitChanges, méthode (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)



