---
title: Tri, transformation | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sorttrans.f1
helpviewer_keywords:
- Sort transformation
- descending sorts
- ascending sorts
- sorting data [Integration Services]
- multiple sorts
- duplicate data [Integration Services]
ms.assetid: 728c9351-84a8-4a89-be4d-d50d4adc04e0
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: dba1f3598abb8877721ff77d3dabcc8af8e0b94a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62899882"
---
# <a name="sort-transformation"></a>transformation de tri
  La transformation de tri trie les données d'entrée dans l'ordre croissant ou décroissant et copie les données triées dans sa sortie. Vous pouvez appliquer plusieurs tris à une entrée ; chaque tri est identifié par un chiffre qui détermine l'ordre de tri. La colonne qui possède le plus petit nombre est triée en premier, puis la colonne de tri ayant le deuxième plus petit nombre, et ainsi de suite. Par exemple, si une colonne nommée **PaysRégion** a un ordre de tri égal à 1 et qu’une colonne nommée **Ville** a un ordre de tri égal à 2, la sortie est triée par pays/région puis par ville. Un nombre positif indique que le tri est croissant, tandis qu'un nombre négatif indique qu'il est décroissant. Les colonnes qui ne sont pas triées ont un ordre de tri égal à 0. Les colonnes qui ne sont pas sélectionnées pour le tri sont automatiquement copiées dans la sortie de la transformation avec les colonnes triées.  
  
 La transformation de tri comprend un ensemble d'options de comparaison qui permettent de définir la façon dont la transformation gère les données de chaîne dans une colonne. Pour plus d'informations, voir [Comparing String Data](../comparing-string-data.md).  
  
> [!NOTE]  
>  La transformation de tri ne trie pas les GUID dans le même ordre que la clause ORDER BY dans Transact-SQL. Alors que la transformation de tri trie les GUID commençant par un numéro compris entre 0 et 9 avant les GUID commençant par une lettre comprise entre A et F, la clause ORDER BY, telle qu'elle est implémentée dans le [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)], les trie différemment. Pour plus d’informations, consultez [Clause ORDER BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql).  
  
 La transformation de tri peut également supprimer les doublons de lignes dans le cadre du tri. Les doublons de lignes sont des lignes possédant les mêmes valeurs de clé de tri. La valeur de clé de tri est générée en fonction des options de comparaison de chaînes en cours d'utilisation ; par conséquent, différentes chaînes littérales peuvent avoir les mêmes valeurs de clé de tri. Dans les colonnes d'entrée, la transformation identifie en tant que doublons les lignes qui ont des valeurs différentes mais la même clé de tri.  
  
 La transformation de tri inclut la propriété personnalisée `MaximumThreads`, qui peut être mise à jour par une expression de propriété lors du chargement du package. Pour plus d’informations, consultez [Expressions Integration Services &#40;SSIS&#41; ](../../expressions/integration-services-ssis-expressions.md), [Expressions de propriété dans des packages](../../expressions/use-property-expressions-in-packages.md) et [Propriétés personnalisées des transformations](transformation-custom-properties.md).  
  
 Cette transformation a une entrée et une sortie. Elle ne prend pas en charge les sorties d'erreur.  
  
## <a name="configuration-of-the-sort-transformation"></a>Configuration de la transformation de tri  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programme.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans la boîte de dialogue **Éditeur de transformation de tri** , consultez [Éditeur de transformation de tri](../../sort-transformation-editor.md).  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../../common-properties.md)  
  
-   [Propriétés personnalisées des transformations](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur la définition des propriétés du composant, consultez [Définir les propriétés d’un composant de flux de données](../set-the-properties-of-a-data-flow-component.md).  
  
## <a name="related-content"></a>Contenu associé  
 Exemple, [SortDeDuplicateDelimitedString Custom SSIS Component](https://go.microsoft.com/fwlink/?LinkId=220821), sur codeplex.com.  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de données](../data-flow.md)   
 [Transformations Integration Services](integration-services-transformations.md)  
  
  
