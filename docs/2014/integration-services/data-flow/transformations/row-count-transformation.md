---
title: Calcul du nombre de lignes, transformation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rowcounttrans.f1
helpviewer_keywords:
- updating variables
- Row Count transformation
- number of rows
- variables [Integration Services], updating
- counting rows
ms.assetid: b68293b9-a68c-40be-9d81-77342da1be29
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d991ee94e04be0ea72450b8e3e4649c339d1c2a4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62900209"
---
# <a name="row-count-transformation"></a>transformation de calcul du nombre de lignes
  La transformation de calcul du nombre de lignes compte les lignes à mesure qu'elles passent par un flux de données et stocke le nombre final dans une variable.  
  
 Un package [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] peut utiliser les nombres de lignes pour mettre à jour les variables utilisées dans des scripts, des expressions et des expressions de propriétés. (Par exemple, la variable qui stocke le nombre de lignes peut mettre à jour le texte d'un message électronique avec ce nombre.) La variable utilisée par la transformation de calcul du nombre de lignes doit déjà exister et figurer dans l'étendue de la tâche de flux de données à laquelle appartient le flux de données avec la transformation de calcul du nombre de lignes.  
  
 La transformation stocke la valeur de nombre de lignes dans la variable uniquement après que la dernière ligne est passée par la transformation. Par conséquent, la valeur de la variable n'est pas mise à jour à temps pour utiliser la valeur mise à jour dans le flux de données qui contient la transformation Nombre de lignes. Vous pouvez utiliser la variable mise à jour dans un flux de données distinct.  
  
 Cette transformation a une entrée et une sortie. Elle ne prend pas en charge de sortie d'erreur.  
  
## <a name="configuration-of-the-row-count-transformation"></a>Configuration de la transformation du calcul du nombre de lignes  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../../common-properties.md)  
  
-   [Propriétés personnalisées des transformations](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur la définition des propriétés de ce composant, consultez [Définir les propriétés d’un composant de flux de données](../set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Variables Integration Services &#40;SSIS&#41;](../../integration-services-ssis-variables.md)   
 [Flux de données](../data-flow.md)   
 [Transformations Integration Services](integration-services-transformations.md)  
  
  
