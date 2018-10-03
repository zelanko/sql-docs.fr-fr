---
title: Mettre en corrélation une Trace avec les données de journal de performances Windows (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], logs
ms.assetid: e1b3072c-8daf-49a7-9895-c8cccd2adb95
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 75af6924104764f372eefd0731799ec3566d0a0f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48049149"
---
# <a name="correlate-a-trace-with-windows-performance-log-data-sql-server-profiler"></a>Corréler une trace aux données du journal de performances Windows (SQL Server Profiler)
  [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] peut corréler les compteurs du Moniteur système de Microsoft Windows avec [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] événements. Le Moniteur système Windows consigne dans des journaux de performances l'activité du système pour des compteurs spécifiés.  
  
> [!NOTE]  
>  Pour plus d'informations sur le partage de journaux entre plusieurs versions de Windows, consultez la procédure à la fin de cette rubrique.  
  
### <a name="to-correlate-a-trace-with-performance-log-data"></a>Pour corréler une trace aux données du journal de performances  
  
1.  Dans [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], ouvrez un fichier de trace ou une table de trace enregistrée. Il est impossible de corréler une trace d'exécution qui regroupe encore des données d'événement. Pour garantir la précision de la corrélation aux données du Moniteur système, la trace doit contenir les colonnes de données **StartTime** et **EndTime** .  
  
2.  Dans le menu [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] **du** , cliquez sur **Importer les données de performances**.  
  
3.  Dans la boîte de dialogue **Ouvrir** , sélectionnez un fichier qui contient un journal de performances. Les données du journal de performances doivent être capturées pendant la même période que celle de la capture des données de trace.  
  
4.  Dans la boîte de dialogue **Limite des compteurs de performances** , activez les cases à cocher correspondant aux objets et aux compteurs du Moniteur système que vous souhaitez afficher aux côtés de la trace. Cliquez sur **OK.**  
  
5.  Sélectionnez un événement dans la fenêtre des événements de trace ou faites défiler plusieurs lignes adjacentes dans la fenêtre des événements de trace à l'aide des touches de direction. La barre rouge verticale de la fenêtre **Données du Moniteur système** indique les données du journal de performances corrélées à l’événement de trace sélectionné.  
  
6.  Cliquez sur un point qui vous intéresse dans le graphique du Moniteur système. La ligne de trace correspondante la plus proche dans le temps est sélectionnée. Pour agrandir un intervalle de temps, cliquez sur le pointeur de la souris et faites-le glisser dans le graphique du Moniteur système.  
  
### <a name="to-create-performance-logs-that-can-be-shared-among-different-versions-of-windows"></a>Pour créer des journaux de performances pouvant être partagés avec différentes versions de Windows  
  
1.  Dans le Panneau de configuration, ouvrez **Outils d’administration**, puis double-cliquez sur **Performances**.  
  
2.  Dans la boîte de dialogue **Performances** , développez **Journaux et alertes de performances**, cliquez avec le bouton droit sur **Journaux de compteurs**, puis cliquez sur **Nouveaux paramètres de journal**.  
  
3.  Tapez un nom pour le journal de compteurs, puis cliquez sur **OK**.  
  
4.  Sous l’onglet **Général** , cliquez sur **Ajouter des compteurs**.  
  
5.  Dans la liste **Objet de performance** , sélectionnez un objet de performance à surveiller. Les noms des objets de performances [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour des instances par défaut de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] commencent par [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et les instances nommées commencent par MSSQL$*instanceName*.  
  
6.  Ajoutez autant de compteurs que nécessaire pour votre instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et d'autres valeurs importantes, telles que le temps processeur et le temps du disque.  
  
7.  Quand vous avez terminé d’ajouter les compteurs, cliquez sur **Fermer**.  
  
8.  Définissez les valeurs de l’intervalle **Période d’échantillonnage des données** . Commencez par un intervalle modeste, par exemple 5 minutes, puis modifiez-le si nécessaire.  
  
9. Sous l’onglet **Fichiers journaux** choisissez **Fichier texte (séparé par des virgules)** dans la liste **Type de fichier journal** . Vous pouvez partager entre plusieurs versions de Windows les fichiers texte de journal délimités par une virgule et les afficher ultérieurement dans des outils de création de rapports tels que Microsoft Excel.  
  
10. Sous l’onglet **Planification** , spécifiez une planification de surveillance.  
  
11. Cliquez sur **OK** pour créer le journal de performances.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles et autorisations du générateur de SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [Démarrer SQL Server Profiler](../tools/sql-server-profiler/start-sql-server-profiler.md)  
  
  
