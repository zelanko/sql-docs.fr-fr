---
title: Commandes (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- commands [XML for Analysis]
- XML for Analysis, commands
- XMLA, commands
ms.assetid: c8a93ea6-8eb5-4204-b037-69cb442a0082
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 215db39cdf87cff69f2bfefbc28e730590daec15
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37298889"
---
# <a name="commands-xmla"></a>Commandes (XMLA)
  Cette section de référence contient des éléments XML for Analysis (XMLA) qui peuvent être utilisés dans l'élément `Command` au cours d'un appel de méthode `Execute`.  
  
|Élément|Description|  
|-------------|-----------------|  
|[Alter, élément (XMLA)](alter-element-xmla.md)|Contient des éléments Analysis Services Scripting Language (ASSL) utilisés par le [Execute](../xml-elements-methods-execute.md) méthode pour modifier des objets sur une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Backup, élément](backup-element-xmla.md)|Sauvegarde un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de données à un fichier de sauvegarde.|  
|[Batch, élément](batch-element-xmla.md)|Effectue XML d’un ou plusieurs pour les commandes Analysis (XMLA) comme une opération de traitement par lots, séquentiellement ou en parallèle, sur une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[BeginTransaction, élément](begintransaction-element-xmla.md)|Démarre une transaction sur la session actuelle par une instance Analysis Services.|  
|[Cancel, élément](cancel-element-xmla.md)|Annule une commande en cours d'exécution dans une instance Analysis Services.|  
|[ClearCache, élément](clearcache-element-xmla.md)|Efface le cache mémoire de l'objet spécifié dans une instance Analysis Services.|  
|[CommitTransaction, élément](committransaction-element-xmla.md)|Valide une transaction dans la session actuelle avec une instance Analysis Services.|  
|[Create, élément](create-element-xmla.md)|Contient des éléments Analysis Services Scripting Language (ASSL) utilisés par le [Execute](../xml-elements-methods-execute.md) méthode pour créer des objets sur une instance Analysis Services.|  
|[Delete, élément](delete-element-xmla.md)|Supprime un objet dans une instance Analysis Services.|  
|[DesignAggregations, élément](designaggregations-element-xmla.md)|Crée des agrégations pour une conception d'agrégation dans une instance Analysis Services.|  
|[Drop, élément](drop-element-xmla.md)|Supprime des membres d'attribut d'une dimension.|  
|[Insert, élément](insert-element-xmla.md)|Insère des membres d'attribut dans une dimension.|  
|[Lock, élément](lock-element-xmla.md)|Verrouille un objet spécifié dans une instance Analysis Services.|  
|[MergePartitions, élément](mergepartitions-element-xmla.md)|Fusionne les données d'une ou plusieurs partitions sources dans une partition cible, puis supprime les partitions sources.|  
|[NotifyTableChange, élément](notifytablechange-element-xmla.md)|Notifie une instance Analysis Services qu'une modification a été apportée à des tables dans une source de données spécifiée.|  
|[Process, élément](process-element-xmla.md)|Traite des objets sur une instance Analysis Services.|  
|[Restore, élément](restore-element-xmla.md)|Restaure une base de données Analysis Services à partir d'un fichier de sauvegarde.|  
|[RollbackTransaction, élément](rollbacktransaction-element-xmla.md)|Restaure une transaction dans la session en cours avec une instance Analysis Services.|  
|[Statement, élément](statement-element-xmla.md)|Contient une requête ou une instruction doit être envoyé à l’aide de la [Execute](../xml-elements-methods-execute.md) méthode à une instance d’Analysis Services.|  
|[Subscribe, élément](subscribe-element-xmla.md)|Procède à l'abonnement à une trace et retourne un ensemble de lignes contenant les événements de trace d'une instance Analysis Services.|  
|[Synchronize, élément](synchronize-element-xmla.md)|Synchronise une base de données Analysis Services avec une autre base de données existante.|  
|[Unlock, élément](unlock-element-xmla.md)|Déverrouille un verrou spécifié dans une instance Analysis Services.|  
|[Update, élément](../xml-elements-commands/update-element-xmla.md)|Met à jour les membres d'attribut d'une dimension.|  
|[UpdateCells, élément](updatecells-element-xmla.md)|Met à jour des cellules dans un cube activé en écriture.|  
  
  
