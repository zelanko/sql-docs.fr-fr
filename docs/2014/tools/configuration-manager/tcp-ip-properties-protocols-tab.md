---
title: TCP - IP propriétés (onglet protocoles) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
caps.latest.revision: 36
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 169e1c0d19cecf50f7c995ff4b4d46f4badb32eb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249539"
---
# <a name="tcp---ip-properties-protocols-tab"></a>TCP - IP propriétés (onglet protocoles)
  La boîte de dialogue **Propriétés de TCP/IP** permet de configurer les options du protocole TCP/IP. Cliquez sur **TCP/IP** dans le volet gauche pour afficher les configurations de chaque adresse IP dans le volet d’informations.  
  
 Pour appliquer les modifications, redémarrez Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="options"></a>Options  
 **Activé**  
 Les valeurs possibles sont **Yes** et **No**.  
  
 **Keep Alive**  
 Spécifiez la fréquence (millisecondes) à laquelle les paquets de maintien d'activité sont transmis pour vérifier si l'ordinateur situé à l'extrémité distante d'une connexion est toujours disponible.  
  
 **Écouter tout**  
 Spécifiez si SQL Server doit écouter sur toutes les adresses IP liées aux cartes réseau de l'ordinateur. Si vous choisissez la valeur **No**, configurez chaque adresse IP séparément en utilisant la boîte de dialogue des propriétés de chaque adresse IP. Si vous choisissez la valeur **Yes**, les paramètres de la zone des propriétés de **IPAll** s’appliquent à toutes les adresses IP. La valeur par défaut est **Yes**.  
  
 **Aucun délai**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'implémente pas les modifications apportées à cette propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Choix d’un protocole réseau](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [Création d’une chaîne de connexion valide à l’aide du protocole TCP/IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
  
