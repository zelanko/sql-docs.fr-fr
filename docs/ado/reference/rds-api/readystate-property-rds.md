---
title: ReadyState, propriété (RDS) | Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ReadyState property [ADO]
ms.assetid: 5be75bc7-1171-4440-a37e-c8cc6b5cd865
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 54f122c178a663c1080093d1f6d391a4869c3ac6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47632567"
---
# <a name="readystate-property-rds"></a>ReadyState, propriété (RDS)
Indique la progression d’un [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) de l’objet lorsqu’il récupère des données dans son [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**adcReadyStateLoaded**|La requête actuelle est en cours d’exécution et aucune ligne n’a été extraite. Le **DataControl** l’objet **Recordset** n’est pas disponible pour utilisation.|  
|**adcReadyStateInteractive**|Un ensemble initial de lignes récupérées par la requête actuelle a été stocké dans le **DataControl** l’objet **Recordset** et sont disponibles pour utilisation. Les lignes restantes sont toujours en cours d’extraction.|  
|**adcReadyStateComplete**|Toutes les lignes récupérées par la requête en cours ont été stockés dans le **DataControl** l’objet **Recordset** et sont disponibles pour utilisation.<br /><br /> Cet état sera également exister si une opération abandonnée en raison d’une erreur, ou si le **Recordset** objet n’est pas initialisé.|  
  
> [!NOTE]
>  Chaque fichier exécutable côté client qui utilise ces constantes doit fournir les déclarations. Vous pouvez couper et coller les déclarations des constantes à partir du fichier Adcvbs.inc, situé dans le dossier d’installation par défaut pour la bibliothèque de services Bureau à distance.  
  
## <a name="remarks"></a>Notes  
 Utilisez le [onReadyStateChange](../../../ado/reference/rds-api/onreadystatechange-event-rds.md) événement pour surveiller les modifications dans le **ReadyState** propriété lors d’une opération de requête asynchrone. Cela est plus efficace que de manière périodique et vérifiant la valeur de la propriété.  
  
 Si une erreur se produit pendant une opération asynchrone, le **ReadyState** modifications apportées aux propriétés **adcReadyStateComplete**, le [état](../../../ado/reference/ado-api/state-property-ado.md) propriété passe de **adStateExecuting** à **adStateClosed**et le **Recordset** objet [valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété reste *Nothing* .  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Propriété ReadyState, exemple (VBScript)](../../../ado/reference/rds-api/readystate-property-example-vbscript.md)   
 [Cancel, méthode (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [ExecuteOptions, propriété (RDS)](../../../ado/reference/rds-api/executeoptions-property-rds.md)


