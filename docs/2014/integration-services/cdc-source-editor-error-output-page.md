---
title: Éditeur de Source CDC (Page sortie d’erreur) | Microsoft Docs
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
- sql12.ssis.designer.cdcsource.errorhandling.f1
ms.assetid: 8a4c2cb8-fd2f-4c45-824f-b93473a8981e
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5131f6f2b7735bd083b68e25d2237119d689faf7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37203879"
---
# <a name="cdc-source-editor-error-output-page"></a>Éditeur de source CDC (page Sortie d'erreur)
  Utilisez la page **Sortie d'erreur** de la boîte de dialogue **Éditeur de source CDC** pour sélectionner les options de gestion des erreurs.  
  
 Pour en savoir plus sur la source CDC, consultez [CDC Source](data-flow/cdc-source.md).  
  
## <a name="task-list"></a>Liste des tâches  
 **Pour ouvrir l'Éditeur de source CDC (page Sortie d'erreur)**  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], ouvrez le package [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] qui possède la source CDC.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la source CDC.  
  
3.  Dans l' **Éditeur de source CDC**, cliquez sur **Sortie d'erreur**.  
  
## <a name="options"></a>Options  
 **Entrée/sortie**  
 Affichez le nom de la source de données.  
  
 **Colonne**  
 Affichez les colonnes externes (sources) que vous avez sélectionnées dans la page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de source CDC** .  
  
 **Erreur**  
 Sélectionnez la façon dont la source CDC doit gérer les erreurs dans un flux : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Troncation**  
 Sélectionnez la façon dont la source CDC doit gérer la troncation dans un flux : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Description**  
 Non utilisé.  
  
 **Définir cette valeur sur les cellules sélectionnées**  
 Sélectionnez la façon dont la source CDC gère l'ensemble des cellules sélectionnées lorsqu'une erreur ou une troncation se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Appliquer**  
 Appliquez les options de gestion des erreurs aux cellules sélectionnées.  
  
## <a name="error-handling-options"></a>Options de gestion des erreurs  
 Vous pouvez utiliser les options suivantes pour configurer la façon dont la source CDC gère les erreurs et les troncations.  
  
 **Composant défaillant**  
 La tâche de flux de données échoue lorsqu'une erreur ou une troncation a lieu. Il s'agit du comportement par défaut.  
  
 **Ignorer l'échec**  
 L'erreur ou la troncation est ignorée et la ligne de données est dirigée vers la sortie de la source CDC.  
  
 **Rediriger le flux**  
 La ligne de données qui présente l'erreur ou la troncation est dirigée vers la sortie d'erreur de la source CDC. Dans ce cas, la gestion des erreurs de la source CDC est utilisée. Pour plus d'informations, consultez [CDC Source](data-flow/cdc-source.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de Source CDC &#40;Page Gestionnaire de connexions&#41;](../../2014/integration-services/cdc-source-editor-connection-manager-page.md)   
 [Éditeur de Source CDC &#40;Page colonnes&#41;](../../2014/integration-services/cdc-source-editor-columns-page.md)  
  
  
