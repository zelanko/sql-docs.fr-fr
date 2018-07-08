---
title: Séparateur de capture de données modifiées | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsplitter.f1
ms.assetid: 167bc5c6-fa36-439d-987c-b20acd1a77e2
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 72dc97b5018e48b12fa460e508d3f9b84e222a39
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37148430"
---
# <a name="cdc-splitter"></a>Séparateur de capture de données modifiées
  Le séparateur de capture de données modifiées fractionne un flux de lignes de modification d'un flux de données de source CDC en flux de données distincts pour les opérations d'insertion, de mise à jour et de suppression. Le flux de données est fractionné en fonction de la colonne requise `__$operation` et de ses valeurs standard dans les tables de modification de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
|Valeur de l'opération|Sortie|Description|  
|------------------------|------------|-----------------|  
| 1|DELETE|Ligne supprimée|  
|2|Insert|Ligne insérée (non disponible en cas d’utilisation du mode de capture de données modifiées **Net avec fusion** )|  
|3|Update|Ligne avant la mise à jour (disponible uniquement en cas d’utilisation du mode de capture de données modifiées **Tout avec les anciennes valeurs** )|  
|4|Update|Ligne après la mise à jour (suit avant la mise à jour)|  
|5|Update|Ligne de fusion (disponible uniquement en cas d’utilisation du mode de capture de données modifiées **Net avec fusion** )|  
|Autres|Error||  
  
 Vous pouvez utiliser le séparateur pour vous connecter aux sorties INSERT, DELETE et UPDATE afin d'effectuer d'autres opérations de traitement.  
  
 La transformation de séparateur de capture de données modifiées a une sortie standard et une sortie d'erreur.  
  
## <a name="error-handling"></a>Gestion des erreurs  
 La transformation de séparateur de capture de données modifiées a une sortie d'erreur. Les lignes d'entrée avec une valeur de colonne $operation non valide sont considérées comme incorrectes et sont gérées conformément à la propriété **ErrorRowDisposition** de l'entrée.  
  
 La sortie d'erreur du composant contient les colonnes de sortie suivantes :  
  
-   **Code d'erreur**: la valeur est 1.  
  
-   **Colonne d’erreur**: colonne source à l’origine de l’erreur (pour les erreurs de conversion).  
  
-   **Colonnes de ligne d'erreur**: colonnes d'entrée de la ligne à l'origine de l'erreur.  
  
## <a name="configuring-the-cdc-splitter"></a>Configuration du séparateur de capture de données modifiées  
 Le séparateur de capture de données modifiées ne comporte aucune propriété configurable.  
  
 Pour plus d'informations sur l'utilisation du séparateur de capture de données modifiées, consultez Composants de capture de données modifiées pour Microsoft SQL Server Integration Services.  
  
 La boîte de dialogue **Éditeur avancé** contient les propriétés qui peuvent être définies par programme.  
  
 Pour ouvrir la boîte de dialogue **Éditeur avancé** :  
  
-   Sur l'écran **Flux de données** de votre projet [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] , cliquez avec le bouton droit sur le séparateur de capture de données modifiées, puis sélectionnez **Afficher l'éditeur avancé**.  
  
## <a name="see-also"></a>Voir aussi  
 [Diriger le flux de capture de données modifiées en fonction du type de modification](direct-the-cdc-stream-according-to-the-type-of-change.md)  
  
  
