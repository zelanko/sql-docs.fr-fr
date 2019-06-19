---
title: Transformer des données avec des transformations | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data flow [Integration Services], transformations
- transformations [Integration Services], about transformations
- transforming data [Integration Services]
ms.assetid: e1340b6f-ef75-4b14-af6f-823586eff0ed
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9fb4014688f1899e813d1df3e677caf9ad7bfbf1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62770299"
---
# <a name="transform-data-with-transformations"></a>Transformer des données avec des transformations
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] inclut trois types de composants de flux de données : les sources, les transformations et les destinations.  
  
 Le schéma suivant illustre un flux de données simple qui possède une source, deux transformations et une destination.  
  
 ![Data flow](../../media/mw-dts-08.gif "Data flow")  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Les transformations procurent la fonctionnalité suivante :  
  
-   Fractionnement, copie et fusion d'ensembles de lignes et opérations de recherche.  
  
-   Mise à jour de valeurs de colonnes et création de colonnes en appliquant des transformations telles que la modification de minuscules en majuscules.  
  
-   Exécution d'opérations Business Intelligence telles que le nettoyage de données, l'exploration de texte et l'exécution de requêtes de prédictions d'exploration de données.  
  
-   Création d'ensembles de lignes constitués de valeurs agrégées ou triées, d'échantillons de données ou de données croisées dynamiques et non croisées dynamiques.  
  
-   Exécution de tâches telles que l'exportation et l'importation de données, l'apport d'informations d'audit et l'utilisation de dimensions à variation lente.  
  
 Pour plus d’informations, consultez [Transformations Integration Services](integration-services-transformations.md).  
  
 Vous pouvez également écrire des transformations personnalisées. Pour plus d’informations, consultez [Développement d’un composant de flux de données personnalisé](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) et [Développement de types spécifiques de composants de flux de données](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md).  
  
 Après avoir ajouté la transformation au concepteur de flux de données, mais avant de configurer la transformation, vous devez connecter la transformation au flux de données en connectant la sortie d'une autre transformation ou source du flux de données à l'entrée de cette transformation. Le connecteur entre ces deux composants de flux de données porte le nom de chemin d'accès. Pour plus d’informations sur la connexion des composants et l’utilisation des chemins d’accès, consultez [Connecter des composants avec des chemins d’accès](../../connect-components-with-paths.md).  
  
### <a name="to-add-a-transformation-to-a-data-flow"></a>Pour ajouter une transformation à un flux de données  
  
-   [Ajouter ou supprimer un composant dans un flux de données](../add-or-delete-a-component-in-a-data-flow.md)  
  
### <a name="to-connect-a-transformation-to-a-data-flow"></a>Pour connecter une transformation à un flux de données  
  
-   [Connecter des composants dans un flux de données](../connect-components-in-a-data-flow.md)  
  
### <a name="to-set-the-properties-of-a-transformation"></a>Pour définir les propriétés d'une transformation  
  
-   [Définir les propriétés d’un composant de flux de données](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="see-also"></a>Voir aussi  
 [tâche de flux de données](../../control-flow/data-flow-task.md)   
 [Flux de données](../data-flow.md)   
 [Connecter des composants avec des chemins d’accès](../../connect-components-with-paths.md)   
 [Gestion des erreurs dans les données](../error-handling-in-data.md)   
 [Flux de données](../data-flow.md)  
  
  
