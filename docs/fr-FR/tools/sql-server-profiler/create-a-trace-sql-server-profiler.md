---
title: Créer une Trace (SQL Server Profiler) | Documents Microsoft
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: sql-server-profiler
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], creating
ms.assetid: 0302fa6d-d2b5-43fe-ad70-7a337575b112
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 9b40c4ab9616ec4d7a1271c5e3b5c1a0a36be2e7
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="create-a-trace-sql-server-profiler"></a>Créer une trace (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Cette rubrique explique comment utiliser [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour créer une trace.  
  
### <a name="to-create-a-trace"></a>Pour créer une trace  
  
1.  Dans le menu **Fichier** , cliquez sur **Nouvelle trace**et connectez-vous à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     La boîte de dialogue **Propriétés de la trace** s'affiche.  
  
    > **REMARQUE :** La boîte de dialogue **Propriétés de la trace** ne s’affiche pas et la trace démarre en lieu et place, si l’option **Démarrer le suivi juste après avoir établi la connexion** est sélectionnée. Pour désactiver ce paramètre, dans le menu **Outils**, cliquez sur **Options**, puis désactivez la case à cocher Démarrer le suivi juste après avoir établi la connexion.  
  
2.  Dans la zone **Nom de la trace** , tapez un nom pour la trace.  
  
3.  Dans la liste **Utiliser le modèle** , sélectionnez un modèle de trace comme base ou sélectionnez **Vide** si vous ne souhaitez pas utiliser de modèle.  
  
4.  Pour enregistrer les résultats de la trace, réalisez l'une des actions suivantes :  
  
    -   Cliquez sur **Enregistrer dans le fichier** pour capturer la trace dans un fichier. Spécifiez une valeur dans **Définir la taille de fichier maximale**. La valeur par défaut est 5 mégaoctets (Mo).  
  
         Éventuellement, sélectionnez **Activer la substitution de fichier** pour créer automatiquement de nouveaux fichiers quand la taille maximale du fichier est atteinte. Vous pouvez également éventuellement sélectionner **Le serveur traite les données de trace**pour forcer le service exécutant la trace à traiter les données de trace en lieu et place de l’application cliente. Lorsque le serveur traite les données de trace, aucun événement n'est ignoré, même dans des conditions extrêmes, mais les performances du serveur peuvent en être affectées.  
  
    -   Cliquez sur **Enregistrer dans la table** pour capturer la trace dans une table de base de données.  
  
         Au besoin, cliquez sur **Définir le nombre de lignes maximal**et spécifiez une valeur.  
  
    > **ATTENTION :** Lorsque vous n'enregistrez pas les résultats de la trace dans un fichier ou dans une table, vous pouvez afficher la trace lorsque le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] est ouvert. Cependant, vous perdez les résultats de la trace après l'avoir arrêtée et fermé le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Pour éviter de perdre les résultats de la trace, cliquez sur l’option **Enregistrer** du menu **Fichier** pour les enregistrer avant de fermer [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
5.  Le cas échéant, activez la case à cocher **Activer l'heure d'arrêt de la trace** et indiquez une date et une heure d'arrêt.  
  
6.  Pour ajouter ou supprimer des événements, des colonnes de données ou des filtres, cliquez sur l’onglet **Sélection des événements**  . Pour plus d’informations, consultez [Spécifier les événements et les colonnes de données d’un fichier de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md).  
  
7.  Cliquez sur **Exécuter** pour démarrer la trace.  
  
## <a name="see-also"></a>Voir aussi  
 [Autorisations nécessaires pour exécuter SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md)   
 [Modèles et autorisations du générateur de SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [Corréler une trace aux données du journal de performances Windows &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)  
  
  
