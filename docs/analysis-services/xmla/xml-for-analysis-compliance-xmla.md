---
title: "Conformité XML for Analysis (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- compliance [XML for Analysis]
- XML for Analysis, compliance
- XMLA, extended functionality
- XML for Analysis, extended functionality
- XMLA, compliance
- extending XML for Analysis
ms.assetid: d987d320-5581-4454-ad45-68e3a22175b6
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5657f57d1f7eee76efb51da0c4bd3ff278aa47ac
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="xml-for-analysis-compliance-xmla"></a>Conformité XML for Analysis (XMLA)
  La spécification XML for Analysis 1.1 décrit une norme ouverte qui prend en charge l'accès aux sources de données qui résident sur Internet. Cette rubrique détaille le niveau de compatibilité avec la spécification XML for Analysis 1.1 est pris en charge par [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="compliant-items"></a>Éléments conformes  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est conforme avec tous les éléments obligatoires répertoriés dans la spécification XML for Analysis 1.1. Qui plus est, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] implémente l'élément facultatif suivant décrit dans la spécification XML for Analysis 1.1.  
  
|Élément|Spécification|Implémentation|  
|----------|-------------------|--------------------|  
|Prise en charge de la session|Les éléments d'en-tête SOAP répertoriés dans la section relative à la prise en charge de l'état dans XML for Analysis pour la spécification XML for Analysis 1.1.|Tous les éléments d'en-tête SOAP répertoriés sont pris en charge par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], tel que décrit dans la spécification.|  
  
## <a name="extensions"></a>Extensions  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] permet également d'étendre la spécification XML for Analysis 1.1 afin de prendre en charge les fonctionnalités et les outils supplémentaires suivants.  
  
|Élément|Spécification|Implémentation|  
|----------|-------------------|--------------------|  
|Négociation de protocole|Aucune information contenue dans la spécification XML for Analysis 1.1|Élément d’en-tête ProtocolCapabilities ajouté par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour prendre en charge la négociation des fonctionnalités de protocole.|  
|Commandes XML for Analysis (XMLA) prises en charge par la méthode Discover|Les commandes suivantes sont prises en charge par la spécification XML for Analysis 1.1 :<br /><br /> [Élément d’instruction &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)|Les commandes suivantes sont prises en charge par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] :<br /><br /> [ALTER, élément &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)<br /><br /> [Élément Backup &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)<br /><br /> [Élément de lot &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)<br /><br /> [Élément BeginTransaction &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)<br /><br /> [Annuler, élément &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)<br /><br /> [Élément ClearCache &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md)<br /><br /> [Élément CommitTransaction &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)<br /><br /> [Créer, élément &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)<br /><br /> [Supprimer l’élément &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md)<br /><br /> [Élément DesignAggregations &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md)<br /><br /> [Supprimer l’élément &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)<br /><br /> [Insérer un élément &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)<br /><br /> [Verrouiller l’élément &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)<br /><br /> [Élément MergePartitions &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)<br /><br /> [Élément NotifyTableChange &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md)<br /><br /> [Élément Process &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)<br /><br /> [Restaurer l’élément &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)<br /><br /> [Élément RollbackTransaction &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)<br /><br /> [Élément d’instruction &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)<br /><br /> [S’abonner, élément &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md)<br /><br /> [Synchroniser, élément &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)<br /><br /> [Déverrouiller l’élément &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)<br /><br /> [Mettre à jour, élément &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)<br /><br /> [Élément UpdateCells &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)|  
|Erreurs de colonne dans les ensembles de lignes tabulaires|Non répertoriées dans la spécification XML for Analysis 1.1.|Le [erreur](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md) élément est utilisé par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour signaler des erreurs pour les éléments de colonne contenus dans un [ligne](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md) élément.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence XML for Analysis &#40;XMLA&#41;](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  
