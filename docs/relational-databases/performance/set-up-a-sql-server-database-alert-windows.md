---
title: "Configurer une alerte de base de données SQL Server (Windows) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- alerts [SQL Server], creating
ms.assetid: 65d2c5c1-921f-4eff-9ef7-149170ab61e8
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8eabe827b89c3931523bda848e01471853cbde6b
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="set-up-a-sql-server-database-alert-windows"></a>Configurer une alerte de base de données SQL Server (Windows)
  À l'aide du Moniteur système, vous pouvez créer une alerte qui se déclenche quand le seuil d'un compteur du Moniteur système est franchi. En réponse à l'alerte, le Moniteur système peut lancer une application, telle qu'une application personnalisée écrite pour prendre en charge la condition d'alerte. Par exemple, vous pouvez créer une alerte déclenchée quand le nombre de blocages dépasse une valeur spécifique.  
  
 Vous pouvez également définir des alertes à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Alertes](http://msdn.microsoft.com/library/3f57d0f0-4781-46ec-82cd-b751dc5affef).  
  
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
 [Créer une alerte de base de données SQL Server](../../relational-databases/performance-monitor/create-a-sql-server-database-alert.md)  
  
  
