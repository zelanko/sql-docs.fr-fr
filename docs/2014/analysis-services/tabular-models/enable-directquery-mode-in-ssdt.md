---
title: Activer le Mode Création DirectQuery (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 71fc7ebd-2e86-4a76-994b-66d3a57bcc9b
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 93b95dc39c0efb088003af9d5fb8b68cfce11ce9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37310409"
---
# <a name="enable-directquery-design-mode-ssas-tabular"></a>Activer le mode Création DirectQuery (SSAS Tabulaire)
  Pour créer un modèle en mode DirectQuery, vous devez d'abord modifier l'environnement au moment de la conception afin qu'il prenne en charge l'utilisateur du mode DirectQuery. Dans ce cas, le concepteur effectue également les opérations suivantes :  
  
-   Il active l'utilisation des propriétés de déploiement DirectQuery.  
  
-   Il modifie la base de données de l'espace de travail de façon à ce qu'elle s'exécute en mode hybride qui utilise le cache pour la conception. Lorsque vous déployez réellement le modèle, la valeur de mode spécifiée dans les propriétés de déploiement du projet est rétablie.  
  
-   Il désactive les fonctionnalités de création qui ne sont pas compatibles avec le mode DirectQuery.  
  
-   Il valide le modèle existant.  
  
 Cette procédure explique comment activer le mode DirectQuery dans le concepteur.  
  
### <a name="to-enable-use-of-directquery-in-a-model"></a>Pour activer l'utilisation de DirectQuery dans un modèle  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le fichier solution.  
  
2.  Dans l'Explorateur d'objets, double-cliquez sur le fichier Model.bim.  
  
3.  Dans le volet **Propriétés** , affectez à la propriété **DirectQueryMode**la valeur **Activé**.  
  
4.  En cas de erreurs, dans Visual Studio, ouvrez la **Liste d'erreurs** et résolvez tous les problèmes qui empêcheraient le modèle de basculer en mode DirectQuery.  
  
## <a name="see-also"></a>Voir aussi  
 [Le Mode DirectQuery &#40;SSAS tabulaire&#41;](directquery-mode-ssas-tabular.md)  
  
  
