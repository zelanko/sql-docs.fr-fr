---
title: Propriétés de planification (page Rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.reportserver.scheduleproperties.reports.f1
ms.assetid: 7db728bd-4b08-43ef-a49a-e8dcdd37cf89
caps.latest.revision: 20
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: c8789d3781042c8240e3beb3a8f808941449eddd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144435"
---
# <a name="schedule-properties-reports-page"></a>Propriétés de planification (page Rapports)
  Utilisez cette page pour afficher la liste de tous les rapports qui utilisent cette planification partagée. Les planifications peuvent être utilisées pour actualiser les instantanés de rapport, générer un historique de rapport, déclencher un abonnement ou faire expirer une copie mise en cache du rapport. Pour savoir comment la planification est utilisée, consultez les informations sur les propriétés et les abonnements du rapport.  
  
 Bien que cette page affiche chaque rapport qui utilise la planification partagée, elle n'indique pas le nombre de fois où la planification partagée est utilisée dans cet unique rapport. Par exemple, supposons que 20 abonnés différents au rapport des ventes de l'entreprise utilisent tous la même planification partagée pour déclencher le traitement des abonnements. Dans ce cas, le rapport des ventes de l'entreprise apparaîtra seulement une fois dans cette liste, même s'il contient 20 références à la planification partagée.  
  
 Pour ouvrir cette page, démarrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], se connecter à un serveur de rapports, ouvrez le **les planifications partagées** dossier, cliquez sur une planification partagée, sélectionnez **propriétés**, puis cliquez sur **rapports** .  
  
> [!NOTE]  
>  Cette fonctionnalité n'est pas disponible dans toutes les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prises en charge par les éditions de SQL Server 2012](http://go.microsoft.com/fwlink/?linkid=232473) (http://go.microsoft.com/fwlink/?linkid=232473).  
  
## <a name="options"></a>Options  
 **Dossier**  
 Spécifie le chemin d'accès au rapport.  
  
 **Rapport**  
 Définit le nom du rapport qui utilise la planification.  
  
## <a name="see-also"></a>Voir aussi  
 [Create, Modify, and Delete Schedules](../subscriptions/create-modify-and-delete-schedules.md)   
 [Planifications](../subscriptions/schedules.md)   
 [Aide du serveur de rapports dans Management Studio accessible par la touche F1](report-server-in-management-studio-f1-help.md)   
 [Se connecter à un serveur de rapports dans Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Configurer les propriétés générales d’un rapport &#40;le Gestionnaire de rapports&#41;](../configure-general-properties-for-a-report-report-manager.md)  
  
  