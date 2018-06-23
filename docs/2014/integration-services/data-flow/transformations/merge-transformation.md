---
title: Fusion, transformation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.mergetrans.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- merging data [Integration Services]
- Merge transformation
- combining datasets
- datasets [Integration Services], merging
ms.assetid: cff8690c-07ac-46a0-aab5-20bd4848c677
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 59af833bb371e8a3fcf43e175343cda807a8feb7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143533"
---
# <a name="merge-transformation"></a>transformation de fusion
  La transformation de fusion combine deux datasets triés en un seul datasets. Les lignes de chaque ensemble de données sont insérées dans la sortie en fonction des valeurs de leurs colonnes clés.  
  
 L'intégration de la transformation de fusion dans un flux de données permet de réaliser les tâches suivantes :  
  
-   Fusionner des données de deux sources de données, telles que des tables et des fichiers.  
  
-   Créer des ensembles de données complexes en imbriquant des transformations de fusion.  
  
-   Fusionner des lignes à nouveau après avoir corrigé les erreurs affectant les données.  
  
 La transformation de fusion est similaire aux transformations d'union totale. Utilisez la transformation d'union totale au lieu de la transformation de fusion dans les situations suivantes :  
  
-   Les entrées de transformation ne sont pas triées.  
  
-   La sortie combinée n'a pas besoin d'être triée.  
  
-   La transformation a au moins trois entrées.  
  
## <a name="input-requirements"></a>Spécifications relatives aux entrées  
 La transformation de fusion requiert des données triées pour ses entrées. Pour plus d’informations sur cette spécification importante, consultez [Trier des données pour les transformations de fusion et de jointure de fusion](sort-data-for-the-merge-and-merge-join-transformations.md).  
  
 La transformation de fusion requiert également que les colonnes fusionnées dans ses entrées aient des métadonnées correspondantes. Par exemple, vous ne pouvez pas fusionner une colonne de type de données numérique avec une colonne de type de données caractère. Si les données sont du type de données chaîne, la colonne de la deuxième entrée doit avoir une longueur inférieure ou égale à celle de la colonne de la première entrée avec laquelle elle est fusionnée.  
  
 Dans le Concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , l’interface utilisateur de la transformation de fusion mappe automatiquement les colonnes qui ont les mêmes métadonnées. Vous pouvez ensuite mapper manuellement les colonnes ayant des types de données compatibles.  
  
 Cette transformation a deux entrées et une sortie. Elle ne prend pas en charge de sortie d'erreur.  
  
## <a name="configuration-of-the-merge-transformation"></a>Configuration de la transformation de fusion  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans la boîte de dialogue **Éditeur de transformation de fusion** , consultez [Éditeur de transformation de fusion](../../merge-transformation-editor.md).  
  
 Pour plus d'informations sur les propriétés définissables par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../../common-properties.md)  
  
-   [Propriétés personnalisées des transformations](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Pour plus d'informations sur la définition des propriétés, consultez les rubriques suivantes :  
  
-   [Définir les propriétés d’un composant de flux de données](../set-the-properties-of-a-data-flow-component.md)  
  
-   [Trier des données pour les transformations de fusion et de jointure de fusion](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Transformation de jointure de fusion](merge-join-transformation.md)   
 [Union All Transformation](union-all-transformation.md)   
 [Flux de données](../data-flow.md)   
 [Transformations Integration Services](integration-services-transformations.md)  
  
  