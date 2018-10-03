---
title: Résumé du modèle d’objet RDS | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS objects [ADO], object model summary
- RDS object model [ADO]
ms.assetid: 909f9af7-31db-4eec-ad52-650ce74dac2f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0421f5eead03d6e3641054b9c26dc1d4dac838e6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47822128"
---
# <a name="rds-object-model-summary"></a>Résumé du modèle objet RDS
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
|Object|Description|  
|------------|-----------------|  
|[RDS.DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)|Cet objet contient une méthode pour obtenir un serveur proxy. Le proxy peut être la valeur par défaut ou un programme serveur personnalisé (objet métier). Le programme du serveur peut être appelé sur Internet, un intranet, un réseau local ou être une bibliothèque de liens dynamiques locale.<br /><br /> Le **DataSpace** objet est sécurisé pour le script.|  
|[RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|Cet objet représente le programme de serveur par défaut. Il exécute le comportement par défaut RDS données récupération et mise à jour.<br /><br /> Le **DataFactory** objet n’est pas sécurisé pour le script.|  
|[RDS.DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)|Cet objet peut appeler automatiquement la **RDS. DataSpace** et **RDSServer.DataFactory** objets.<br /><br /> Cet objet permet d’appeler le comportement de récupération ou de mise à jour de données de services Bureau à distance par défaut.<br /><br /> Cet objet permet également aux contrôles visuels accéder aux retourné **Recordset** objet.<br /><br /> Le **DataControl** objet est sécurisé pour le script.|  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)   
 [Scénario RDS](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [Didacticiel RDS](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Utilisation et sécurité de RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


