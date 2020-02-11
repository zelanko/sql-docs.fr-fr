---
title: Mettre à niveau les transformations de recherche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Lookup transformation and upgrading
- upgrading caching for Lookup transformation
- upgrading Lookup transformation
ms.assetid: d9b2c281-91ee-4e20-bdf0-0cd77d4a4241
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: eae7433569972c217161f1681b2f7089c7604335
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66091508"
---
# <a name="upgrade-lookup-transformations"></a>Mettre à niveau des transformations de recherche
  Lorsque vous effectuez une mise à niveau de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], pensez à modifier les packages pour tirer parti des nouvelles fonctionnalités de la transformation de recherche. Cette transformation prend en charge les types de mise en cache et les options de sortie des données disponibles dans [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]. Pour plus d’informations sur la mise en cache et les sorties de données supplémentaires, consultez [Lookup transformation](../../integration-services/data-flow/transformations/lookup-transformation.md).  
  
 Dans [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)], les types de mise en cache disponibles sont la mise en cache complète, la mise en cache partielle et l'absence de mise en cache. Dans [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], vous pouvez configurer une transformation de recherche afin d'utiliser l'un de ces types de mise en cache. Pour plus d’informations sur la façon d’implémenter une mise en cache partielle ou aucune mise en cache, consultez [implémenter une recherche en mode aucun cache ou cache partiel](../../integration-services/data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md). Pour plus d’informations sur l’implémentation de la mise en cache complète, consultez [implémenter une transformation de recherche en mode cache complet à l’aide du gestionnaire de connexions du cache](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md) et [implémenter une transformation de recherche en mode cache complet à l’aide du gestionnaire de connexions OLE DB](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md).  
  
 Dans [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)], la transformation de recherche comportait une entrée, une sortie et une sortie d'erreur. Les lignes de l'entrée qui possédaient des entrées correspondantes dans le jeu de données de référence étaient gérées par la sortie. Les lignes de l'entrée qui ne possédaient pas d'entrées correspondantes étaient traitées en tant qu'erreurs et pouvaient être redirigées vers la sortie d'erreur. Dans [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], la transformation de recherche comporte deux sorties : une sortie avec correspondance et une sortie sans correspondance.  
  
 Par défaut, lorsque vous exécutez une transformation de recherche créée dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] traite les lignes sans entrées correspondantes comme des erreurs et vous permet de rediriger ces lignes vers une sortie d'erreur. Vous avez la possibilité de configurer la transformation de recherche afin de traiter les lignes comme si elles n'étaient pas des erreurs et de rediriger ces lignes vers la sortie sans correspondance.  
  
 Pour plus d’informations, consultez [éditeur de transformation de recherche &#40;&#41;de page général ](../../integration-services/general-page-of-integration-services-designers-options.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Transformation de recherche](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
  
