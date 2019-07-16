---
title: Modèle de programmation RDS avec des objets | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS programming model [ADO]
- RDS objects [ADO]
ms.assetid: 07ce0ef0-72f1-48f4-823d-1b65d28c0926
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 06bf7c811074ba70741fe77b06037f9f69c9cda4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67922461"
---
# <a name="rds-programming-model-with-objects"></a>Modèle de programmation RDS avec des objets
L’objectif des services Bureau à distance consiste à accéder à et mettre à jour les sources de données via un intermédiaire tel qu’IIS. Le modèle de programmation spécifie la séquence d’activités nécessaires pour atteindre cet objectif. Le modèle objet spécifie les objets dont les méthodes et propriétés affectent le modèle de programmation.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Les RDS donnent les moyens d’effectuer la séquence d’actions suivante :  
  
-   Spécifiez le programme à appeler sur le serveur et obtenir un moyen (proxy) pour faire référence à celui-ci à partir du client ([RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)).  
  
-   Appeler le programme serveur. Passer des paramètres pour le programme de serveur qui identifie la source de données et de la commande à émettre (proxy ou [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)).  
  
-   Le programme serveur obtient un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet à partir de la source de données, généralement à l’aide d’ADO. Si vous le souhaitez, le **Recordset** objet est traité sur le serveur ([RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)).  
  
-   Le programme serveur retourne le dernier **Recordset** objet à l’application cliente (proxy).  
  
-   Sur le client, le **Recordset** objet est placé dans un formulaire qui peut être facilement utilisé par des contrôles visuels (contrôle visuel et **RDS. DataControl**).  
  
-   Modifications apportées à la **Recordset** objet sont envoyés sur le serveur et utilisées pour mettre à jour la source de données (**RDS. DataControl** ou **RDSServer.DataFactory**).  
  
## <a name="see-also"></a>Voir aussi  
 [Résumé du modèle objet RDS](../../../ado/guide/remote-data-service/rds-object-model-summary.md)   
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [DataFactory, objet (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)   
 [DataSpace, objet (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)   
 [Scénario RDS](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [Didacticiel RDS](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Utilisation et sécurité de RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


