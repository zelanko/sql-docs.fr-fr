---
title: Conformité XML for Analysis (XMLA) | Documents Microsoft
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
helpviewer_keywords:
- compliance [XML for Analysis]
- XML for Analysis, compliance
- XMLA, extended functionality
- XML for Analysis, extended functionality
- XMLA, compliance
- extending XML for Analysis
ms.assetid: d987d320-5581-4454-ad45-68e3a22175b6
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: fb4279ab8c516f4db18310a03e7b85e389f2bc2b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045435"
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
|Négociation de protocole|Aucune information contenue dans la spécification XML for Analysis 1.1|[ProtocolCapabilities](xml-elements-headers/protocolcapabilities-element-xmla.md) élément d’en-tête ajouté par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour prendre en charge la négociation des fonctionnalités de protocole.|  
|Commandes XML for Analysis (XMLA) prises en charge par la méthode Discover|Les commandes suivantes sont prises en charge par la spécification XML for Analysis 1.1 :<br /><br /> -   [Élément d’instruction &#40;XMLA&#41;](xml-elements-commands/statement-element-xmla.md)|Les commandes suivantes sont prises en charge par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] :<br /><br /> -   [Élément ALTER &#40;XMLA&#41;](xml-elements-commands/alter-element-xmla.md)<br />-   [Élément de sauvegarde &#40;XMLA&#41;](xml-elements-commands/backup-element-xmla.md)<br />-   [Élément du lot &#40;XMLA&#41;](xml-elements-commands/batch-element-xmla.md)<br />-   [Élément BeginTransaction &#40;XMLA&#41;](xml-elements-commands/begintransaction-element-xmla.md)<br />-   [Élément Cancel &#40;XMLA&#41;](xml-elements-commands/cancel-element-xmla.md)<br />-   [Élément ClearCache &#40;XMLA&#41;](xml-elements-commands/clearcache-element-xmla.md)<br />-   [Élément CommitTransaction &#40;XMLA&#41;](xml-elements-commands/committransaction-element-xmla.md)<br />-   [Créer l’élément &#40;XMLA&#41;](xml-elements-commands/create-element-xmla.md)<br />-   [Supprimer l’élément &#40;XMLA&#41;](xml-elements-commands/delete-element-xmla.md)<br />-   [Élément DesignAggregations &#40;XMLA&#41;](xml-elements-commands/designaggregations-element-xmla.md)<br />-   [Élément DROP &#40;XMLA&#41;](xml-elements-commands/drop-element-xmla.md)<br />-   [Insérer l’élément &#40;XMLA&#41;](xml-elements-commands/insert-element-xmla.md)<br />-   [Verrouiller l’élément &#40;XMLA&#41;](xml-elements-commands/lock-element-xmla.md)<br />-   [Élément MergePartitions &#40;XMLA&#41;](xml-elements-commands/mergepartitions-element-xmla.md)<br />-   [Élément NotifyTableChange &#40;XMLA&#41;](xml-elements-commands/notifytablechange-element-xmla.md)<br />-   [Traiter l’élément &#40;XMLA&#41;](xml-elements-commands/process-element-xmla.md)<br />-   [Élément Restore &#40;XMLA&#41;](xml-elements-commands/restore-element-xmla.md)<br />-   [Élément RollbackTransaction &#40;XMLA&#41;](xml-elements-commands/rollbacktransaction-element-xmla.md)<br />-Élément SetPasswordEncryptionKey<br />-   [Élément d’instruction &#40;XMLA&#41;](xml-elements-commands/statement-element-xmla.md)<br />-   [Élément Subscribe &#40;XMLA&#41;](xml-elements-commands/subscribe-element-xmla.md)<br />-   [Élément Synchronize &#40;XMLA&#41;](xml-elements-commands/synchronize-element-xmla.md)<br />-   [Élément Unlock &#40;XMLA&#41;](xml-elements-commands/unlock-element-xmla.md)<br />-   [Mettre à jour d’élément &#40;XMLA&#41;](xml-elements-commands/update-element-xmla.md)<br />-   [Élément UpdateCells &#40;XMLA&#41;](xml-elements-commands/updatecells-element-xmla.md)|  
|Erreurs de colonne dans les ensembles de lignes tabulaires|Non répertoriées dans la spécification XML for Analysis 1.1.|Le [erreur](xml-elements-properties/error-element-xmla.md) élément est utilisé par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour signaler des erreurs pour les éléments de colonne contenus dans un [ligne](xml-elements-properties/error-element-xmla.md) élément.|  
  
## <a name="see-also"></a>Voir aussi  
 [XML for Analysis &#40;XMLA&#41; référence](xml-for-analysis-xmla-reference.md)  
  
  