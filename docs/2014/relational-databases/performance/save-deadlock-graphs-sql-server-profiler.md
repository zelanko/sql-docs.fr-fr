---
title: Enregistrer des graphiques d’interblocage (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- deadlocks [SQL Server], saving deadlock graphs
- graphs [SQL Server]
- saving deadlock graphs
ms.assetid: bf1fc906-abd6-4a89-842e-da0d66b2defe
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 33757ad1f8085ce141b8e206f2c3fd99c7dcba90
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63150703"
---
# <a name="save-deadlock-graphs-sql-server-profiler"></a>Enregistrer les événements Deadlock Graph (Générateur de profils SQL Server)
  Cette rubrique décrit comment enregistrer un événement Deadlock Graph à l'aide du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Les événements Deadlock Graph sont enregistrés sous forme de fichiers XML.  
  
### <a name="to-save-deadlock-graph-events-separately"></a>Pour enregistrer séparément les événements Deadlock Graph  
  
1.  Dans le menu **Fichier** , cliquez sur **Nouvelle trace**, puis connectez-vous à une instance de SQL Server.  
  
     La boîte de dialogue **Propriétés de la trace**apparaît.  
  
    > [!NOTE]  
    >  Si la case **Démarrer le suivi juste après avoir établi la connexion** est cochée, la boîte de dialogue **Propriétés de la trace**ne s’affiche pas et la trace se lance. Pour désactiver ce paramètre, accédez au menu **Outils**, cliquez sur **Options**et désactivez la case à cocher **Démarrer le suivi juste après avoir établi la connexion** .  
  
2.  Dans la boîte de dialogue Propriétés de la trace, saisissez un nom pour la trace dans la zone**Nom de la trace** .  
  
3.  Dans la liste **Utiliser le modèle** , sélectionnez un modèle de trace comme base ou sélectionnez **Vide** si vous ne souhaitez pas utiliser de modèle.  
  
4.  Procédez de l'une des manières suivantes :  
  
    -   Activez la case à cocher**Enregistrer dans le fichier** pour capturer la trace dans un fichier. Spécifiez une valeur dans **Définir la taille de fichier maximale**.  
  
         Au besoin, activez les cases à cocher **Activer la substitution de fichier** et **Le serveur traite les données de trace**.  
  
    -   Activez la case à cocher **Enregistrer dans la table** pour capturer la trace dans une table de base de données.  
  
         Au besoin, cliquez sur **Définir le nombre de lignes maximal**et spécifiez une valeur.  
  
5.  Le cas échéant, activez la case à cocher **Activer l'heure d'arrêt de la trace** et indiquez une date et une heure d'arrêt.  
  
6.  Cliquez sur l’onglet **Sélection des événements**.  
  
7.  Dans la liste **Événements,** développez la catégorie d’événements **Verrous**et sélectionnez la case à cocher **Deadlock graph**. Si la catégorie d'événements Verrous n'est pas disponible, activez la case à cocher **Afficher tous les événements** pour l'afficher.  
  
     La boîte de dialogue **Paramètres d’extraction des événements**est ajoutée à la boîte de dialogue **Propriétés de la trace**.  
  
8.  Dans le menu **Paramètres d’extraction des événements**cliquez sur **Enregistrer les événements Deadlock XML séparément**.  
  
9. Dans la boîte de dialogue **Enregistrer sous** , entrez le nom du fichier dans lequel les événements Deadlock Graph doivent être stockés.  
  
10. Cliquez sur **Tous les lots Deadlock XML dans un seul fichier** pour enregistrer tous les événements Deadlock Graph dans un seul fichier XML, ou cliquez sur **Chaque lot Deadlock XML dans un fichier différent**pour créer un fichier XML pour chaque événement Deadlock Graph.  
  
 Après avoir enregistré le fichier Deadlock, vous pouvez l'ouvrir dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour plus d’informations, consultez [Procédure : Ouvrir, afficher et imprimer un fichier d’interblocage &#40;SQL Server Management Studio&#41;](open-view-and-print-a-deadlock-file-sql-server-management-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser des blocages à l'aide de SQL Server Profiler](../../tools/sql-server-profiler/analyze-deadlocks-with-sql-server-profiler.md)  
  
  
