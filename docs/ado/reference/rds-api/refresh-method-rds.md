---
title: Refresh, méthode (RDS) | Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
f1_keywords:
- Refresh
- RDS.DataControl::Refresh
- DataControl::Refresh
helpviewer_keywords:
- Refresh method [RDS]
ms.assetid: c90a8050-0ff4-4c83-9925-261f2f2ccfe9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9992b0f7e7281ec318f978ff487107fc832c961f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66697522"
---
# <a name="refresh-method-rds"></a>Refresh, méthode (RDS)
Actualise la source de données spécifiée dans le [Connect](../../../ado/reference/rds-api/connect-property-rds.md) propriété et des mises à jour les résultats de requête.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DataControl.Refresh  
```  
  
#### <a name="parameters"></a>Paramètres  
 *DataControl*  
 Une variable objet qui représente un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) objet.  
  
## <a name="remarks"></a>Notes  
 Vous devez définir le [Connect](../../../ado/reference/rds-api/connect-property-rds.md), [Server](../../../ado/reference/rds-api/server-property-rds.md), et [SQL](../../../ado/reference/rds-api/sql-property.md) propriétés avant d’utiliser le **Actualiser** (méthode). Tous les contrôles liés aux données sur le formulaire associé à un **RDS. DataControl** objet reflétera le nouveau jeu d’enregistrements. Toutes les existantes [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet est libéré, et toutes les modifications non enregistrées sont ignorées. Le **Actualiser** méthode fait automatiquement du premier enregistrement l’enregistrement actif.  
  
 Il est judicieux d’appeler le **Actualiser** méthode régulièrement lorsque vous travaillez avec des données. Si vous récupérez des données, puis laissez sur un ordinateur client pendant un certain temps, il est susceptible de devenir obsolètes. Il est possible que les modifications que vous apportez vont échouer, car une autre personne a peut-être modifié l’enregistrement et valide les modifications avant vous.  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Refresh, exemple de méthode (VB)](../../../ado/reference/ado-api/refresh-method-example-vb.md)   
 [Refresh, exemple de méthode (VBScript)](../../../ado/reference/rds-api/refresh-method-example-vbscript.md)   
 [Boutons de commande de carnet d’adresses](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [CancelUpdate, méthode (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Refresh, méthode (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)   
 [SubmitChanges, méthode (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


