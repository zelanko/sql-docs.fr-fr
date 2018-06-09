---
title: Propriétés DAX | Documents Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9150eb13b6c39f74f1e65743b6a79aca0a07676a
ms.sourcegitcommit: 6e55a0a7b7eb6d455006916bc63f93ed2218eae1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35238839"
---
# <a name="dax-properties"></a>Propriétés DAX
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

   La section DAX de msmdsrv.ini contient les paramètres utilisés pour contrôler certains comportements de requête dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], tels que la limite supérieure du nombre de lignes retournées dans un jeu de résultats de requête DAX.

  Pour les ensembles de lignes volumineux, tels que ceux retournés dans les modèles DirectQuery, la valeur par défaut d’un million de lignes peut être insuffisante. Vous devez ajuster la limite si vous obtenez une erreur indiquant que le jeu de résultats d’une requête pour la source de données externe a dépassé la taille maximale autorisée d’un million de lignes.

Pour augmenter la limite supérieure, spécifiez le paramètre de configuration **MaxIntermediateRowSize** . Vous devez ajouter manuellement la totalité de l’élément dans la section DAX du fichier de configuration. Le paramètre n’est pas présent dans le fichier tant que vous ne l’y avez pas ajouté.

## <a name="configuration-snippet"></a>Extrait de la configuration

```
<ConfigurationSettings>
. . .
<DAX>
  <PredicateCheckSpoolCardinalityThreshold>5000
  </PredicateCheckSpoolCardinalityThreshold>
  <DQ>
     <MaxIntermediateRowsetSize>1000000
     </MaxIntermediateRowsetSize>
  </DQ>
</DAX>
. . .
```

## <a name="property-descriptions"></a>Description des propriétés

Paramètre |Valeur |Description
--------|-------|-----------
MaxIntermediateRowsetSize | 1000000 | Nombre maximal de lignes retournées dans une requête DAX. Ajoutez cette entrée manuellement au fichier msmdsrv.ini et augmentez cette valeur si la valeur par défaut est trop faible.
PredicateCheckSpoolCardinalityThreshold| 5000 | Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l’assistance du support technique Microsoft.

Pour plus d’informations sur les autres propriétés de serveur et sur la façon de les configurer, consultez [Propriétés du serveur dans Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).
