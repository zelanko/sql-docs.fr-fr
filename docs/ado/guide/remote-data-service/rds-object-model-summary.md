---
title: Résumé du modèle objet RDS | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS objects [ADO], object model summary
- RDS object model [ADO]
ms.assetid: 909f9af7-31db-4eec-ad52-650ce74dac2f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6c455d816b3ba5a9606d09e3b05e54583e11ca41
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67922533"
---
# <a name="rds-object-model-summary"></a>Résumé du modèle objet RDS
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
|Object|Description|  
|------------|-----------------|  
|[RDS.DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)|Cet objet contient une méthode pour obtenir un serveur proxy. Le proxy peut être la valeur par défaut ou un programme serveur personnalisé (objet métier). Le programme serveur peut être appelé sur Internet, sur un intranet, sur un réseau local ou sur une bibliothèque de liens dynamiques locale.<br /><br /> L’objet **DataSpace** est sécurisé pour l’écriture de scripts.|  
|[RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|Cet objet représente le programme serveur par défaut. Il exécute le comportement par défaut de la récupération et de la mise à jour des données RDS.<br /><br /> L’objet **DataFactory** n’est pas sûr pour l’écriture de scripts.|  
|[RDS.DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)|Cet objet peut appeler automatiquement le **RDS. Objets DataSpace** et **RDSServer. DataFactory** .<br /><br /> Utilisez cet objet pour appeler le comportement par défaut de la récupération ou de la mise à jour des données RDS.<br /><br /> Cet objet fournit également les moyens pour les contrôles visuels d’accéder à l’objet **Recordset** retourné.<br /><br /> L’objet **DataControl** est sécurisé pour l’écriture de scripts.|  
  
## <a name="see-also"></a>Voir aussi  
 [Notions de base sur RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)   
 [Scénario RDS](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [Didacticiel RDS](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Utilisation et sécurité de RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


