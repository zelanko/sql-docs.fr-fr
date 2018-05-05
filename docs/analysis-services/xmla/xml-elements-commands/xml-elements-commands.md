---
title: Commandes (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- commands [XML for Analysis]
- XML for Analysis, commands
- XMLA, commands
ms.assetid: c8a93ea6-8eb5-4204-b037-69cb442a0082
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 644d4d443bf1731d03519141efc93f35f2eda4ee
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="xml-elements---commands"></a>Éléments XML - commandes
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Cette section de référence contient du code XML pour les éléments Analysis (XMLA) qui peuvent être utilisés dans le **commande** élément pendant une **Execute** appel de méthode.  
  
|Élément| Description|  
|-------------|-----------------|  
|[Élément ALTER (XMLA)](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)|Contient des éléments ASSL (Analysis Services Scripting Language) utilisés par la méthode [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) pour modifier des objets dans une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Élément Backup](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)|Sauvegarde une [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de données à un fichier de sauvegarde.|  
|[Élément de lot](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)|Effectue XML d’un ou plusieurs pour les commandes Analysis (XMLA) comme un traitement par lots, dans l’ordre ou en parallèle, sur une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Élément BeginTransaction](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)|Démarre une transaction sur la session actuelle par une instance Analysis Services.|  
|[Élément Cancel](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)|Annule une commande en cours d'exécution dans une instance Analysis Services.|  
|[Élément ClearCache](../../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md)|Efface le cache mémoire de l'objet spécifié dans une instance Analysis Services.|  
|[Élément CommitTransaction](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)|Valide une transaction dans la session actuelle avec une instance Analysis Services.|  
|[Créer l’élément](../../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)|Contient des éléments d’Analysis Services Scripting Language (ASSL) utilisés par le [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) méthode pour créer des objets sur une instance Analysis Services.|  
|[Élément Delete](../../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md)|Supprime un objet dans une instance Analysis Services.|  
|[Élément DesignAggregations](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md)|Crée des agrégations pour une conception d'agrégation dans une instance Analysis Services.|  
|[Élément DROP](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)|Supprime des membres d'attribut d'une dimension.|  
|[Élément INSERT](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)|Insère des membres d'attribut dans une dimension.|  
|[Élément Lock](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)|Verrouille un objet spécifié dans une instance Analysis Services.|  
|[Élément MergePartitions](../../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)|Fusionne les données d'une ou plusieurs partitions sources dans une partition cible, puis supprime les partitions sources.|  
|[Élément NotifyTableChange](../../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md)|Notifie une instance Analysis Services qu'une modification a été apportée à des tables dans une source de données spécifiée.|  
|[Élément Process](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|Traite des objets sur une instance Analysis Services.|  
|[Élément Restore](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|Restaure une base de données Analysis Services à partir d'un fichier de sauvegarde.|  
|[Élément RollbackTransaction](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)|Restaure une transaction dans la session en cours avec une instance Analysis Services.|  
|[Élément d’instruction](../../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)|Contient une requête ou une instruction à envoyer à l’aide de la [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) procédé à une instance d’Analysis Services.|  
|[Élément SUBSCRIBE](../../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md)|Procède à l'abonnement à une trace et retourne un ensemble de lignes contenant les événements de trace d'une instance Analysis Services.|  
|[Élément Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|Synchronise une base de données Analysis Services avec une autre base de données existante.|  
|[Élément Unlock](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)|Déverrouille un verrou spécifié dans une instance Analysis Services.|  
|[Update (élément)](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)|Met à jour les membres d'attribut d'une dimension.|  
|[Élément UpdateCells](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)|Met à jour des cellules dans un cube activé en écriture.|  
  
  
