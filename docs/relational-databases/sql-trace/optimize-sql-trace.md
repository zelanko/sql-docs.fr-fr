---
title: Optimiser Trace SQL | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time [SQL Server], traces
- SQL Trace, performance
- traces [SQL Server], performance
- performance [SQL Server], trace
ms.assetid: 50944218-925f-4576-aec8-4379846d7681
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 385a5a642b5554f42d4d40bea712bfd6181ee18b
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="optimize-sql-trace"></a>Optimiser Trace SQL
  Même si l'utilisation de la fonctionnalité de trace SQL représente un coût en termes de performances, du fait de l'utilisation de ressources système lors de la collecte de données, il existe plusieurs moyens de le minimiser. Pour limiter la baisse de performances induite par une trace, essayez les méthodes suivantes :  
  
-   Considérez l'utilisation de l'invite de commandes pour exécuter les traces. L'utilisation d'une interface utilisateur graphique entraîne une dégradation des performances. Pour plus d’informations, consultez [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md).  
  
-   Évitez d'inclure des événements qui se produisent fréquemment. Si possible, limitez la trace à des classes d'événements et des filtres spécifiques. Les ressources système requises pour prendre en charge le traçage sont moins importantes si le nombre d'événements de trace regroupés est limité.  
  
-   Limitez la trace à la collecte d'événements qui fournissent des données importantes. Par exemple, si votre trace vise à identifier les blocages, incluez la classe d’événements **Lock:Deadlock** mais pas la classe d’événements **Lock:Acquired** . Si vous incluez les deux classes d'événements, la trace devra répondre à chaque acquisition de verrou et votre coût d'exécution sera doublé.  
  
-   Évitez de collecter les données en double. Par exemple, si vous collectez les événements **SQL:BatchStarted** et **SQL:BatchCompleted**, vous pouvez limiter la taille de l’ensemble de résultats en collectant des données texte pour la classe d’événements **SQL:BatchStarted** seulement.  
  
-   Utilisez des filtres dans la définition de la trace. Par exemple, si vous savez qu’un certain utilisateur se plaint de faibles performances lors des requêtes ad hoc, créez un filtre sur **LoginName**. Définissez le filtre pour inclure uniquement les événements dont le paramètre **LoginName** correspond au nom de l’utilisateur.  
  
 Si vous avez besoin d'exécuter une trace pour les événements qui influent négativement sur les performances, vous pouvez limiter leur impact sur les performances du serveur en employant l'une des méthodes suivantes :  
  
-   Exécutez les traces sur des périodes plus courtes. Vous pouvez contrôler la durée d'exécution d'une trace en activant une heure d'arrêt. Ceci s'avère particulièrement important si vous ne pouvez pas limiter les classes d'événements ou filtrer un événement. En activant une heure d'arrêt, vous êtes assuré que la baisse des performances ne dure pas indéfiniment.  
  
-   Limitez la taille des résultats de la trace. Vous pouvez limiter la taille des résultats de la trace à une taille de fichier maximale. Cette stratégie est l'assurance que la baisse des performances cessera une fois que la taille limite de fichier atteinte (dans la mesure où l'option de substitution de fichier n'est pas activée).  
  
-   Limitez le nombre d'événements renvoyés. Le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] vous permet de limiter le nombre d'événements renvoyés en enregistrant la trace dans une table et en définissant le nombre de lignes maximal. Les résultats de la trace sont toujours renvoyés à l'écran du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] après que le nombre de lignes maximal a été atteint, mais le coût d'enregistrement des résultats dans une table est éliminé.  
  
## <a name="see-also"></a>Voir aussi  
 [Filtrer une trace](../../relational-databases/sql-trace/filter-a-trace.md)  
  
  
