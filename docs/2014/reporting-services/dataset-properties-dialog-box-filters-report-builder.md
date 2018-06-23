---
title: Boîte de dialogue Propriétés du DataSet, filtres (Générateur de rapports) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- "10025"
ms.assetid: 933a6f44-4eb7-4e73-9c40-ac0fd17b23d3
caps.latest.revision: 14
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: beb0703212eb639483bbaa015b6fa89bba3a3068
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038105"
---
# <a name="dataset-properties-dialog-box-filters-report-builder"></a>Boîte de dialogue Propriétés du dataset, Filtres (Générateur de rapports)
  Sélectionnez **Filtres** dans la boîte de dialogue **Propriétés du dataset** pour créer des filtres pour le dataset.  
  
 Les filtres qui font partie d'une définition de dataset partagé sur le serveur de rapports affectent tous les rapports qui utilisent le dataset partagé. Des filtres supplémentaires pour le dataset partagé peuvent être spécifiés après que celui-ci a été ajouté à un rapport. Ces filtres affectent uniquement le rapport dans lequel ils sont définis.  
  
 Les filtres d'un dataset incorporé affectent uniquement le rapport dans lequel ils sont définis.  
  
 Pour plus d’informations, consultez [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Options  
 **Ajouter**  
 Ajoutez une nouvelle clause de filtre à la liste.  
  
 **Supprimer**  
 Supprimez la clause de filtre sélectionnée de la liste.  
  
 **Flèche haut**  
 Déplacez le filtre sélectionné vers le haut de la liste.  
  
 **Flèche bas**  
 Déplacez le filtre sélectionné vers le bas de la liste.  
  
 **Expression**  
 Tapez ou choisissez l'expression à laquelle vous souhaitez appliquer un filtre. Cliquez sur le bouton Expression (**fx**) pour modifier l’expression.  
  
 **Data type**  
 Sélectionnez le type de données du champ **Valeur**. Lorsque cela est possible, sélectionnez un type de données correspondant à celui du champ **Expression**.  
  
 Les valeurs dans **Expression** et **Valeur** doivent s’évaluer au même type de données. Par exemple, si **Expression** a pour valeur un champ du type de données System.Int32 et que **Valeur** a pour valeur 7, sélectionnez **Entier**dans la liste déroulante.  
  
 Si le type de données recherché ne figure pas dans la liste déroulante, écrivez une expression permettant de convertir la valeur en type de données correct. Pour plus d’informations, consultez [Exemples d’équations de filtre &#40;Générateur de rapports et SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md).  
  
 **Opérateur**  
 Choisissez l'opérateur à utiliser pour comparer l'expression et la valeur.  
  
 **Value**  
 Tapez l’expression ou la valeur à utiliser lors de l’évaluation de l’expression spécifiée dans la zone **Expression** . Cliquez sur le bouton Expression (**fx**) pour modifier l’expression.  
  
## <a name="see-also"></a>Voir aussi  
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](report-design/report-parameters-report-builder-and-report-designer.md)   
 [Ajouter un filtre à un jeu de données &#40;rapport Générateur et SSRS&#41;](report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)   
 [Expression utilise des rapports de &#40;rapport Générateur et SSRS&#41;](report-design/expression-uses-in-reports-report-builder-and-ssrs.md)  
  
  