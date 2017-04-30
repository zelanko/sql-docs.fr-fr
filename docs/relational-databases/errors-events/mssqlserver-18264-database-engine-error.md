---
title: MSSQLSERVER_18264 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 18264 (Database Engine error)
ms.assetid: 3050fc56-2be5-43cf-916b-50a3ac5f89aa
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 06ae22f5e2e7344a5934493bb893a07bdb20383a
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver18264"></a>MSSQLSERVER_18264
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Microsoft SQL Server|  
|ID d'événement|18264|  
|Source de l'événement|MSSQLENGINE|  
|Composant|SQLEngine|  
|Nom symbolique|STRMIO_DBDUMP|  
|Texte du message|Base de données sauvegardée. Base de données : %s, date de création (heure) : %s(%s), pages vidées : %d, premier numéro séquentiel : %s, dernier numéro séquentiel : %s, nombre d'unités de vidage : %d, informations sur l'unité : (%s). Ce message est fourni uniquement à titre d'information. Aucune action de l'utilisateur n'est requise.|  
  
## <a name="explanation"></a>Explication  
Par défaut, chaque sauvegarde réussie ajoute ce message d'information au journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et au journal des événements système. Si vous sauvegardez très fréquemment le journal des transactions, ces messages peuvent rapidement s’accumuler, créer des journaux des erreurs très volumineux et compliquer la recherche d’autres messages.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Vous pouvez supprimer ces entrées de journal à l’aide de l’indicateur de trace [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **3226**. Cela est utile si vous exécutez des sauvegardes de fichiers journaux fréquentes et si aucun de vos scripts ne dépend de ces entrées.  
  
Pour plus d'informations sur les indicateurs de trace, consultez la documentation en ligne de SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
[Indicateurs de trace &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
  

