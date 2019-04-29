---
title: Union totale, transformation | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unionalltrans.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- combining datasets
- Union All transformation
- datasets [Integration Services], merging
ms.assetid: 942e4b90-9c41-4e9c-a6f3-80b3afe57f2f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8cfbe5ab3a255367922195594063a1734b8c66b9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62899872"
---
# <a name="union-all-transformation"></a>transformation d'union totale
  La transformation d'union totale combine plusieurs entrées en une seule sortie. Par exemple, les sorties de cinq sources de fichier plat peuvent être des entrées de la transformation d'union totale et être combinées en une seule sortie.  
  
## <a name="inputs-and-outputs"></a>Entrées et sorties  
 Les entrées de transformation sont ajoutées à la sortie de transformation une par une ; aucune réorganisation de lignes n'intervient. Si le package nécessite une sortie triée, vous devez utiliser la transformation de fusion au lieu de la transformation d'union totale.  
  
 La première entrée que vous connectez à la transformation d'union totale est l'entrée à partir de laquelle la transformation crée la sortie de transformation. Les colonnes des entrées que vous connectez ensuite à la transformation sont mappées avec les colonnes de la sortie de transformation.  
  
 Pour fusionner les entrées, vous mappez les colonnes des entrées avec les colonnes de la sortie. Une colonne d'au moins une entrée doit être mappée avec chaque colonne de sortie. Vous ne pouvez mapper deux colonnes que si leurs métadonnées correspondent. Par exemple, les colonnes mappées doivent avoir le même type de données.  
  
 Si les colonnes mappées contiennent des données de chaîne et que la longueur de la colonne de sortie est plus courte que celle de la colonne d'entrée, la longueur de la colonne de sortie est automatiquement augmentée de manière à contenir la colonne d'entrée. Les colonnes d'entrée non mappées avec des colonnes de sortie ont la valeur NULL dans les colonnes de sortie.  
  
 Cette transformation a plusieurs entrées et une sortie. Elle ne prend pas en charge de sortie d'erreur.  
  
## <a name="configuration-of-the-union-all-transformation"></a>Configuration de la transformation d'union totale  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans la boîte de dialogue **Éditeur de transformation d’union totale** , consultez [Éditeur de transformation d’union totale](../../union-all-transformation-editor.md).  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir par programmation, consultez [Propriétés communes](../../common-properties.md).  
  
 Pour plus d'informations sur la définition des propriétés, cliquez sur l'une des rubriques suivantes :  
  
-   [Définir les propriétés d’un composant de flux de données](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a>Tâches associées  
 [Fusionner des données à l'aide de la transformation d'union totale](union-all-transformation.md)  
  
  
