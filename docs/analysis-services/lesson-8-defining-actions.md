---
title: "Leçon 8 : Définition des Actions | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 15459396-83c9-48a0-b10a-99ae38768c79
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1d080c99d9d3fc1a1fcdfb8e6a4e183850462f94
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="lesson-8-defining-actions"></a>Leçon 8 : Définition des actions
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]Dans cette leçon, vous allez apprendre à définir des actions dans votre [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] projet. Une action est simplement une instruction MDX (Multidimensional Expressions) qui est stockée dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et peut être incorporée dans des applications clientes et démarrée par un utilisateur.  
  
> [!NOTE]  
> Les projets achevés de toutes les leçons de ce didacticiel sont disponibles en ligne. Vous pouvez sauter des leçons en utilisant le projet achevé de la leçon précédente comme point de départ. [Cliquez ici](http://go.microsoft.com/fwlink/?LinkID=221866) pour télécharger les exemples de projet de ce didacticiel.  
  
[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] prend en charge les types d’actions décrits dans le tableau suivant.  
  
|||  
|-|-|  
|CommandLine|Exécute une commande à partir de l'invite de commandes.|  
|Dataset|Renvoie un groupe de données à une application cliente.|  
|Extraction|Retourne une instruction d'extraction comme expression que le client exécute pour retourner un ensemble de lignes.|  
|Html|Exécute un script HTML dans un navigateur Internet.|  
|Propriétaire|Effectue une opération en utilisant une interface différente de celles répertoriées dans ce tableau.|  
|Rapport|Soumet une demande paramétrable basée sur une URL à un serveur de rapports et renvoie un rapport à une application cliente.|  
|Ensemble de lignes|Renvoie un ensemble de lignes à une application cliente.|  
|.|Exécute une commande OLE DB.|  
|URL|Affiche une page web dynamique dans un navigateur Internet.|  
  
Les actions permettent aux utilisateurs de démarrer une application ou d'effectuer d'autres étapes dans le contexte d'un élément sélectionné. Pour plus d’informations, consultez [Actions &#40;Analysis Services - Données multidimensionnelles&#41;](../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md), [Actions dans les modèles multidimensionnels](../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)  
  
> [!NOTE]  
> Pour obtenir des exemples d'actions, consultez les exemples d'action de l'onglet Modèles du volet Outils de calcul ou dans les exemples de l'entrepôt de données [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW. Pour plus d’informations sur l’installation de cette base de données, consultez [Installer les exemples de données et de projets pour le didacticiel sur la modélisation multidimensionnelle Analysis Services](../analysis-services/install-sample-data-and-projects.md).  
  
Cette leçon inclut la tâche suivante :  
  
[Définition et utilisation d'une action d'extraction](../analysis-services/lesson-8-1-defining-and-using-a-drillthrough-action.md)  
Dans cette tâche, vous définissez, utilisez puis modifiez une action d'extraction à travers la relation de dimension de fait que vous avez définie antérieurement dans ce didacticiel.  
  
## <a name="next-lesson"></a>Leçon suivante  
[Leçon 9 : Définition de perspectives et de traductions](../analysis-services/lesson-9-defining-perspectives-and-translations.md)  
  
## <a name="see-also"></a>Voir aussi  
[Scénario du didacticiel Analysis Services](../analysis-services/analysis-services-tutorial-scenario.md)  
[Modélisation multidimensionnelle &#40;didacticiel Adventure Works&#41;](../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)  
[Actions &#40;Analysis Services - Données multidimensionnelles&#41;](../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md)  
[Actions dans les modèles multidimensionnels](../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)  
  
  
  
