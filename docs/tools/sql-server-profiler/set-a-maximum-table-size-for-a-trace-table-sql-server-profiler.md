---
title: Définir une taille maximale de table de trace (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- size [SQL Server], trace tables
- maximum table size for traces
ms.assetid: d0ae83e5-1c88-4a2e-be05-2c341280b978
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 1f4afa1f6f7070b041b20078c6a627f6debb00ad
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67729896"
---
# <a name="set-a-maximum-table-size-for-a-trace-table-sql-server-profiler"></a>Définir une taille maximale de table de trace (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette rubrique explique comment définir une taille maximale de table de trace à l'aide du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-set-a-maximum-table-size-for-a-trace-table"></a>Pour définir une taille maximale de table de trace  
  
1.  Dans le menu **Fichier** , cliquez sur **Nouvelle trace**, puis connectez-vous à une instance de SQL Server.  
  
     La boîte de dialogue **Propriétés de la trace**apparaît.  
  
    > [!NOTE]  
    >  Si la case **Démarrer le suivi juste après avoir établi la connexion**est cochée, la boîte de dialogue **Propriétés de la trace**ne s’affiche pas et le suivi se lance. Pour désactiver ce paramètre, accédez au menu **Outils**, cliquez sur **Options**et désactivez la case à cocher **Démarrer le suivi juste après avoir établi la connexion** .  
  
2.  Dans la zone **Nom de la trace** , tapez un nom pour la trace.  
  
3.  Dans la liste **Nom du modèle**, sélectionnez un modèle de trace.  
  
4.  Cochez la case **Enregistrer dans la table**.  
  
5.  Connectez-vous au serveur sur lequel vous voulez stocker la trace.  
  
     La boîte de dialogue **Table de destination** s’affiche.  
  
6.  Sélectionnez une base de données pour la trace dans la liste **Base de données** .  
  
7.  Dans la zone **Table** , tapez ou sélectionnez un nom pour la table.  
  
8.  Sélectionnez **Définir le nombre de lignes maximal** , puis spécifiez un nombre de lignes maximal pour la table de trace.  
  
    > [!NOTE]  
    >  Quand le nombre de lignes dans la table dépasse le maximum spécifié, les événements de la trace ne sont plus enregistrés, mais la trace continue.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
