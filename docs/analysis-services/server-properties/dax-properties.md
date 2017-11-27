---
title: "Propriétés DAX | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: server-properties
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: aa928dc5-d00d-4f8a-80b9-7e6973d2196c
caps.latest.revision: "6"
author: HeidiSteen
ms.author: heidist
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a48b3f89da00437cec8781e1ea35b6ea87f0c300
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="dax-properties"></a>Propriétés DAX
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

Pour plus d’informations sur les autres propriétés de serveur et la façon de les configurer, consultez [Propriétés du serveur dans Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md). 
