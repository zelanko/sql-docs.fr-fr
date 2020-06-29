---
title: Unpivot, transformation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unpivottrans.f1
helpviewer_keywords:
- Unpivot transformation
- more normalized data set [Integration Services]
- normalized data [Integration Services]
- datasets [Integration Services], normalized data
ms.assetid: f635c64b-a9c5-4f11-9c40-9cd9d5298c5d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 795be32ef9f30912ecc0d2e8795ff5faa284a572
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85429976"
---
# <a name="unpivot-transformation"></a>Transformation Unpivot
  La transformation Unpivot convertit un dataset non normalisé en version plus normalisée en étendant les valeurs de plusieurs colonnes d'un enregistrement dans plusieurs enregistrements avec les mêmes valeurs dans une colonne unique. Par exemple, un dataset qui répertorie des noms de clients possède une ligne pour chaque client, avec les produits et la quantité achetée mentionnés dans les colonnes sur la ligne. Après que la transformation Unpivot a normalisé le dataset, celui-ci contient une ligne différente pour chaque produit que le client a acheté.  
  
 Le schéma suivant illustre un dataset avant que les données n'aient été transformées dans la colonne Product.  
  
 ![Dataset après la suppression du tableau croisé dynamique](../../media/mw-dts-18.gif "Dataset après la suppression du tableau croisé dynamique")  
  
 Le schéma suivant illustre un dataset après transformation de la colonne Product.  
  
 ![Dataset avant la suppression du tableau croisé dynamique](../../media/mw-dts-17.gif "Dataset avant la suppression du tableau croisé dynamique")  
  
 Dans certaines circonstances, les résultats de la suppression du tableau croisé dynamique peuvent contenir des lignes aux valeurs inattendues. Par exemple, si les exemples de données du diagramme qui doivent être supprimées du tableau croisé dynamique possèdent des valeurs Null dans toutes les colonnes Qty pour Fred, la sortie ne comprend qu'une ligne pour Fred, au lieu de cinq. La colonne Qty contient Null ou zéro, suivant le type de données de la colonne.  
  
## <a name="configuration-of-the-unpivot-transformation"></a>Configuration de la transformation Unpivot  
 La transformation Unpivot inclut la propriété personnalisée `PivotKeyValue`. La propriété peut être mise à jour par une expression de propriété lors du chargement du package. Pour plus d’informations, consultez [Expressions Integration Services &#40;SSIS&#41; ](../../expressions/integration-services-ssis-expressions.md), [Expressions de propriété dans des packages](../../expressions/use-property-expressions-in-packages.md) et [Propriétés personnalisées des transformations](transformation-custom-properties.md).  
  
 Cette transformation a une entrée et une sortie. Elle ne possède aucune sortie d'erreur.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de transformation UnPivot** , cliquez sur l’une des rubriques suivantes :  
  
-   [Éditeur de transformation UnPivot](../../unpivot-transformation-editor.md)  
  
 Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../../common-properties.md)  
  
-   [Propriétés personnalisées des transformations](transformation-custom-properties.md)  
  
 Pour plus d’informations sur la façon de définir des propriétés, consultez [Définir les propriétés d’un composant de flux de données](../set-the-properties-of-a-data-flow-component.md).  
  
  
