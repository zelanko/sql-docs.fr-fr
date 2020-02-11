---
title: MSSQLSERVER_18264 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18264 (Database Engine error)
ms.assetid: 3050fc56-2be5-43cf-916b-50a3ac5f89aa
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2445b0c62347d84beb4690541871bfdec8d1ca3a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62869554"
---
# <a name="mssqlserver_18264"></a>MSSQLSERVER_18264
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Microsoft SQL Server|  
|ID de l’événement|18264|  
|Source de l’événement|MSSQLENGINE|  
|Composant|SQLEngine|  
|Nom symbolique|STRMIO_DBDUMP|  
|Texte du message|Base de données sauvegardée. Base de données : %s, date de création (heure) : %s(%s), pages vidées : %d, premier numéro séquentiel : %s, dernier numéro séquentiel : %s, nombre d'unités de vidage : %d, informations sur l'unité : (%s). Ce message est fourni uniquement à titre d'information. Aucune action de l'utilisateur n'est requise.|  
  
## <a name="explanation"></a>Explication  
 Par défaut, chaque sauvegarde réussie ajoute ce message d'information au journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et au journal des événements système. Si vous sauvegardez très fréquemment le journal des transactions, ces messages peuvent rapidement s’accumuler, créer des journaux des erreurs très volumineux et compliquer la recherche d’autres messages.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vous pouvez supprimer ces entrées de journal à l’aide de l’indicateur de trace [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**3226**. Cela est utile si vous exécutez des sauvegardes de fichiers journaux fréquentes et si aucun de vos scripts ne dépend de ces entrées.  
  
 Pour plus d'informations sur les indicateurs de trace, consultez la documentation en ligne de SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Indicateurs de trace &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)  
  
  
