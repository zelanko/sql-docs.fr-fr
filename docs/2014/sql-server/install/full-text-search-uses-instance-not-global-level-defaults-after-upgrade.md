---
title: La mise à niveau entraînera la recherche en texte intégral à utiliser au niveau de l’instance, et non globaux, des analyseurs lexicaux et filtres par défaut | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- filters [Full-Text Search]
- word breakers [Full-Text Search]
ms.assetid: 93ee8fcb-d11c-49fa-8fac-51ed31a8f008
caps.latest.revision: 17
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 45ee5f8235aa79773bf3e92156701e47092c61c9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37311219"
---
# <a name="upgrading-will-cause-full-text-search-to-use-instance-level-not-global-word-breakers-and-filters-by-default"></a>La mise à niveau entraînera l'utilisation par défaut d'analyseurs lexicaux et de filtres de niveau d'instance, et non globaux, pour la recherche en texte intégral
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permet d'autoriser l'inscription au niveau des instances de nouveaux analyseurs lexicaux et filtres.  
  
## <a name="component"></a>Composant  
 Recherche en texte intégral  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autorise l'inscription au niveau des instances de nouveaux analyseurs lexicaux et filtres. Cette inscription au niveau des instances permet d'isoler ces dernières tant pour leur fonctionnalité que leur sécurité.  
  
## <a name="corrective-action"></a>Action corrective  
 Après la mise à niveau, utilisez `sp_fulltext_service` pour définir la propriété de service et `load_os_resources`, qui permet de charger les composants. Vous devez exécuter la commande suivante :  
  
 `sp_fulltext_service 'load_os_resources', 1`  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du Conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
