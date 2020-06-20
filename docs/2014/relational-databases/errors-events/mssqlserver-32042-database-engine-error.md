---
title: MSSQLSERVER_32042 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 32042 (Database Engine error)
ms.assetid: 53a51c7a-dcd4-4c15-b4d2-6aaa9dce76da
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ec84e6898e0f7d45f9eba5d43074982679ff554e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85053954"
---
# <a name="mssqlserver_32042"></a>MSSQLSERVER_32042
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|32042|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQLErrorNum32042|  
|Texte du message|L'alerte relative au journal non envoyé s'est déclenchée. La valeur actuelle de '%d' dépasse le seuil '%d'.|  
  
## <a name="explanation"></a>Explication  
 Cet événement de mise en miroir de bases de données est émis sur l'instance du serveur principal pour indiquer que la quantité de journal non envoyé a atteint la valeur de seuil définie par l'utilisateur. En règle générale, cet événement se produit car les performances du système ont changé. Soit la bande passante entre les deux systèmes a diminué, soit la charge a augmenté.  
  
 La quantité de journal non envoyé est une mesure de performance qui peut vous aider à évaluer le risque de perte de données exprimé en kilo-octets (Ko) de journal non envoyé. Cette mesure s’avère particulièrement appropriée pour les sessions en mode hautes performances. Toutefois, elle est également adaptée aux sessions en mode haute sécurité lorsque la mise en miroir est interrompue ou suspendue suite à une déconnexion des serveurs partenaires.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez les charges incombant aux instances du serveur principal et du serveur miroir et à leur connexion réseau pour déterminer la cause du problème.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Utiliser des seuils d’avertissement et d’alertes sur des métriques de performances de mise en miroir &#40;SQL Server&#41;](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  
