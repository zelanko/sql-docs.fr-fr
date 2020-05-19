---
title: SubmitChanges, méthode (RDS) | Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SubmitChanges method [ADO]
ms.assetid: 250062a4-13c4-4bed-807d-8b9ad81536d4
author: rothja
ms.author: jroth
ms.openlocfilehash: 3a11adb93f3de8f0887eefe964f1c85836ccc43e
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82750582"
---
# <a name="submitchanges-method-rds"></a>SubmitChanges, méthode (RDS)
Soumet les modifications en attente du [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) mis à jour localement et mis à jour dans la source de données spécifiée dans la propriété [Connect](../../../ado/reference/rds-api/connect-property-rds.md) ou [URL](../../../ado/reference/rds-api/url-property-rds.md) .  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DataControl.SubmitChanges DataFactory.SubmitChanges Connection, Recordset  
```  
  
#### <a name="parameters"></a>Paramètres  
 *DataControl*  
 Variable objet qui représente un objet [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) .  
  
 *DataFactory*  
 Variable objet qui représente un objet [RDSServer. DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) .  
  
 *Connection*  
 Valeur de **chaîne** qui représente la connexion créée avec le **RDS. **Propriété [Connect](../../../ado/reference/rds-api/connect-property-rds.md) de l’objet DataControl.  
  
 *Recordset*  
 Variable objet qui représente un objet **Recordset** .  
  
## <a name="remarks"></a>Remarques  
 Les propriétés [Connect](../../../ado/reference/rds-api/connect-property-rds.md), [Server](../../../ado/reference/rds-api/server-property-rds.md)et [SQL](../../../ado/reference/rds-api/sql-property.md) doivent être définies avant que vous puissiez utiliser la méthode **SubmitChanges** avec le **RDS. DataControl** .  
  
 Si vous appelez la méthode [CancelUpdate](../../../ado/reference/rds-api/cancelupdate-method-rds.md) après avoir appelé **SubmitChanges** pour le même objet **Recordset** , l’appel **CancelUpdate** échoue parce que les modifications ont déjà été validées.  
  
 Seuls les enregistrements modifiés sont envoyés en vue de leur modification, et toutes les modifications réussissent ou toutes les modifications échouent ensemble.  
  
 Vous pouvez utiliser **SubmitChanges** uniquement avec l’objet **RDSServer. DataFactory** par défaut. Les objets métier personnalisés ne peuvent pas utiliser cette méthode.  
  
 Si la propriété **URL** a été définie, **SubmitChanges** envoie les modifications à l’emplacement spécifié par l’URL.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[DataFactory, objet (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [SubmitChanges, exemple de méthode (VBScript)](../../../ado/reference/rds-api/submitchanges-method-example-vbscript.md)   
 [Boutons de commande du carnet d’adresses](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [CancelUpdate, méthode (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Refresh, méthode (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)



