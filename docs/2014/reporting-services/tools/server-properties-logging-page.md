---
title: Propriétés du serveur (page Enregistrement) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.logging.f1
ms.assetid: b338deab-4868-4951-9f22-0605add2fc95
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a04c27fd790a1ad5c4ba453b43af5983a6440e3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66099527"
---
# <a name="server-properties-logging-page"></a>Propriétés du serveur (page Enregistrement)
  Utilisez cette page pour définir des limites sur les données du rapport d'exécution qui sont recueillies par un serveur de rapports. Les données d'exécution sont stockées en interne dans la base de données du serveur de rapports. Vous pouvez effectuer le suivi de l'activité des rapports pour le serveur de rapports qui s'exécute en mode natif ou mode intégré SharePoint. Si le serveur de rapports fait partie d'un déploiement avec montée en puissance parallèle, le journal d'exécution des rapports gère un enregistrement de l'ensemble de l'activité des rapports pour tout le déploiement dans un seul fichier journal.  
  
 Pour ouvrir cette page, démarrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à un serveur de rapports, cliquez avec le bouton droit sur le nom du serveur de rapports et sélectionnez **Propriétés**. Cliquez sur **Enregistrement** pour ouvrir cette page.  
  
## <a name="options"></a>Options  
 **Activer la journalisation de l’exécution des rapports**  
 Cliquez pour créer et stocker des informations sur l'activité des rapports sur le serveur. Si cette option est activée, le serveur de rapports effectuera le suivi des rapports qui sont utilisés, de la fréquence de traitement des rapports, du type d'opération de rapport effectuée, du format de sortie et de la personne qui a exécuté le rapport. Pour plus d’informations sur les points de données supplémentaires capturés dans le journal, consultez [Journal d’exécution du serveur de rapports et vue ExecutionLog3](../report-server/report-server-executionlog-and-the-executionlog3-view.md).  
  
 **Supprimer les entrées de journal antérieures à ce nombre de jours**  
 Spécifiez le nombre de jours après lesquels les entrées du journal seront effacées du journal d'exécution des rapports. La valeur par défaut est 60 jours.  
  
## <a name="see-also"></a>Voir aussi  
 [Définir les propriétés du serveur de rapports &#40;Management Studio&#41;](set-report-server-properties-management-studio.md)   
 [Se connecter à un serveur de rapports dans Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Fichiers journaux et sources de Reporting Services](../report-server/reporting-services-log-files-and-sources.md)   
 [Aide du serveur de rapports dans Management Studio accessible par la touche F1](report-server-in-management-studio-f1-help.md)   
 [Journal des exécutions du serveur de rapports et vue ExecutionLog3](../report-server/report-server-executionlog-and-the-executionlog3-view.md)  
  
  
