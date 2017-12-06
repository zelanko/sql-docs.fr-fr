---
title: "Les propriétés TCP/IP (onglet protocoles) | Documents Microsoft"
ms.custom: 
ms.date: 08/24/2016
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
caps.latest.revision: "38"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fe54bf4b1cb0d2e99b5276b440bf30374e788954
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
---
# <a name="tcpip-properties-protocols-tab"></a>Propriétés de TCP/IP (onglet Protocoles)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Utilisez le **propriétés TCP/IP** boîte de dialogue pour configurer les options pour le protocole TCP/IP. Cliquez sur **TCP/IP** dans le volet gauche pour afficher les configurations de chaque adresse IP dans le volet d’informations.  
  
 Pour appliquer les modifications, redémarrez Microsoft SQL Servermust.  
  
## <a name="options"></a>Options  
 **Activé**  
 Les valeurs possibles sont **Yes** et **No**.  
  
 **Keep Alive**  
 Spécifiez la fréquence (millisecondes) à laquelle les paquets de maintien d'activité sont transmis pour vérifier si l'ordinateur situé à l'extrémité distante d'une connexion est toujours disponible.  
  
 **Écouter tout**  
 Spécifiez si SQL Server doit écouter sur toutes les adresses IP liées aux cartes réseau de l'ordinateur. Si vous choisissez la valeur **No**, configurez chaque adresse IP séparément en utilisant la boîte de dialogue des propriétés de chaque adresse IP. Si vous choisissez la valeur **Yes**, les paramètres de la zone des propriétés de **IPAll** s’appliquent à toutes les adresses IP. La valeur par défaut est **Yes**.  
  
 **Aucun délai**  
 SQL Serverdoes n’implémente pas les modifications apportées à cette propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Choix d'un protocole réseau](https://msdn.microsoft.com/library/ms187892(v=sql.130).aspx)   
 [Création d’une chaîne de connexion valide à l’aide du protocole TCP/IP](creating-a-valid-connection-string-using-tcp-ip.md)  
  
  
