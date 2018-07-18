---
title: Configurer une alerte de base de données SQL Server (Windows) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server], creating
ms.assetid: 65d2c5c1-921f-4eff-9ef7-149170ab61e8
caps.latest.revision: 23
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8ae0709b9135bba9c5a71ba02de9a2d0b2f8a223
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37283125"
---
# <a name="set-up-a-sql-server-database-alert-windows"></a>Configurer une alerte de base de données SQL Server (Windows)
  À l'aide du Moniteur système, vous pouvez créer une alerte qui se déclenche quand le seuil d'un compteur du Moniteur système est franchi. En réponse à l'alerte, le Moniteur système peut lancer une application, telle qu'une application personnalisée écrite pour prendre en charge la condition d'alerte. Par exemple, vous pouvez créer une alerte déclenchée quand le nombre de blocages dépasse une valeur spécifique.  
  
 Vous pouvez également définir des alertes à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Alertes](../../ssms/agent/alerts.md).  
  
### <a name="to-set-up-a-sql-server-database-alert"></a>Pour installer une alerte de base de données SQL Server  
  
1.  Dans l’arborescence de navigation de la fenêtre Performances, développez **Journaux et alertes de performance**.  
  
2.  Cliquez avec le bouton droit sur **Alertes**, puis cliquez sur **Nouveaux paramètres d’alerte**.  
  
3.  Dans la boîte de dialogue **Nouveaux paramètres d’alerte** , entrez un nom pour la nouvelle alerte, puis cliquez sur **OK**.  
  
4.  Sous l’onglet **Général** de la boîte de dialogue de la nouvelle alerte, ajoutez un **commentaire**, puis cliquez sur **Ajouter** pour ajouter un compteur à l’alerte.  
  
     Chaque alerte doit avoir au moins un compteur.  
  
5.  Dans la boîte de dialogue Ajouter des compteurs, sélectionnez un objet SQL Server dans la liste **Objet de performance** , puis sélectionnez un compteur dans la zone **Sélectionner les compteurs dans la liste**.  
  
6.  Pour ajouter le compteur à l’alerte, cliquez sur **Ajouter**. Vous pouvez continuer à ajouter des compteurs, ou bien cliquer sur **Fermer** pour revenir à la boîte de dialogue de la nouvelle alerte.  
  
7.  Dans la boîte de dialogue de la nouvelle alerte, cliquez sur **Supérieur à** ou sur **Inférieur à**dans la liste **Avertir si la valeur est** , puis entrez une valeur de seuil dans la zone **Limite**.  
  
     L’alerte est générée lorsque la valeur du compteur est supérieure ou inférieure à la valeur du seuil (selon que vous avez sélectionné **Supérieur à** ou **Inférieur à**).  
  
8.  Dans les zones **Période d’échantillonnage des données** , définissez la fréquence d’échantillonnage.  
  
9. Sous l’onglet **Action** , définissez les actions qui doivent se produire lorsque l’alerte est déclenchée.  
  
10. Sous l’onglet **Planification** , définissez la planification de début et de fin de l’analyse d’alerte.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une alerte de base de données SQL Server](../performance-monitor/create-a-sql-server-database-alert.md)  
  
  
