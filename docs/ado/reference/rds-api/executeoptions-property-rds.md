---
description: ExecuteOptions, propriété (RDS)
title: ExecuteOptions, propriété (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ExecuteOptions property [ADO], VBScript example
ms.assetid: 62a4fd88-afc3-4f1f-b978-40710a30c4e9
author: rothja
ms.author: jroth
ms.openlocfilehash: dacac570cac3525593f281e52742f4efeb8cba4b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439031"
---
# <a name="executeoptions-property-rds"></a>ExecuteOptions, propriété (RDS)
Indique si l’exécution asynchrone est activée.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne l’une des valeurs suivantes.  
  
|Constant|Description|  
|--------------|-----------------|  
|**adcExecSync**|Exécute la prochaine actualisation de l’ensemble d' [enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md) de façon synchrone.|  
|**adcExecAsync**|Par défaut. Exécute de façon asynchrone la prochaine actualisation du **jeu d’enregistrements** .|  
  
> [!NOTE]
>  Chaque fichier exécutable qui utilise ces constantes doit fournir des déclarations pour eux. Vous pouvez couper et coller les déclarations de constantes que vous souhaitez à partir du fichier Adcvbs. Inc, situé dans le dossier d’installation par défaut de la bibliothèque RDS.  
  
## <a name="remarks"></a>Notes  
 Si **ExecuteOptions** a la valeur **adcExecAsync**, alors l’appel d' **actualisation** suivant est exécuté de façon asynchrone sur le [RDS. ](../../../ado/reference/rds-api/datacontrol-object-rds.md) **Jeu d’enregistrements**de l’objet DataControl.  
  
 Si vous essayez d’appeler [Reset](../../../ado/reference/rds-api/reset-method-rds.md), [Refresh](../../../ado/reference/rds-api/refresh-method-rds.md), [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md), [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)ou [Recordset](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) pendant une autre opération asynchrone qui peut modifier le [RDS. ](../../../ado/reference/rds-api/datacontrol-object-rds.md) Le **jeu d’enregistrements** de l’objet DataControl est en cours d’exécution, une erreur se produit.  
  
 Si une erreur se produit pendant une opération asynchrone, **RDS. ** La valeur de [ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md) de l’objet DataControl passe de **adcReadyStateLoaded** à **adcReadyStateComplete**, et la valeur de la propriété **Recordset** reste *Nothing*.  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ExecuteOptions et FetchOptions, exemples de propriétés (VBScript)](../../../ado/reference/rds-api/executeoptions-and-fetchoptions-properties-example-vbscript.md)   
 [Cancel, méthode (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)


