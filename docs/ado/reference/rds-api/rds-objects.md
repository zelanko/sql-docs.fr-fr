---
title: Objets RDS | Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
helpviewer_keywords:
- objects [ADO], RDS
- RDS objects [ADO]
ms.assetid: f2ac8b3b-f968-41c4-a504-7aee3538b7c7
author: rothja
ms.author: jroth
ms.openlocfilehash: 45f4851acf2d3c92807a571f6c8c6b436b86936b
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764830"
---
# <a name="rds-objects"></a>Objets RDS
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
|||  
|-|-|  
|[DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|Lie un **jeu d’enregistrements** de requêtes de données à un ou plusieurs contrôles (par exemple, une zone de texte, un contrôle de grille ou une zone de liste déroulante) pour afficher les données du **Recordset** sur une page Web.<br /><br /> L’objet **DataControl** est sécurisé pour l’écriture de scripts.|  
|[DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|Implémente des méthodes qui fournissent un accès en lecture/écriture aux données des sources de données spécifiées pour les applications côté client.<br /><br /> L’objet **DataFactory** n’est pas sûr pour l’écriture de scripts.|  
|[DataSpace (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)|Crée des proxies côté client pour des objets métier personnalisés situés sur la couche intermédiaire.<br /><br /> L’objet **DataSpace** est sécurisé pour l’écriture de scripts.|  
|[IRDSService, interface (RDS)](../../../ado/reference/rds-api/irdsservice-interface-rds.md)|Expose la méthode [InvokeService (RDS)](../../../ado/reference/rds-api/invokeservice-rds.md) , qui est utilisée pour retourner un pointeur vers l’interface demandée sur une version plus puissante de l’objet.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence sur l’API RDS](../../../ado/reference/rds-api/rds-api-reference.md)


