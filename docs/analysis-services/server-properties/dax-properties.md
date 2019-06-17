---
title: Propriétés DAX Analysis Services | Microsoft Docs
ms.date: 10/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 20a6df833f8c525c24abdf3bb51278d0067db951
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62509649"
---
# <a name="dax-properties"></a>Propriétés DAX
[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

   La section DAX de msmdsrv.ini contient les paramètres utilisés pour contrôler certains comportements de requête dans Analysis Services, telles que la limite supérieure sur le nombre de lignes retournées dans un jeu de résultats de requête DAX.

  Pour les ensembles de lignes volumineux, tels que ceux retournés dans les modèles DirectQuery, la valeur par défaut d’un million de lignes peut être insuffisante. Vous saurez que si la limite doit ajuster si vous obtenez cette erreur : « Le jeu de résultats d’une requête pour la source de données externe a dépassé la taille maximale autorisée de « 1000000 » lignes. »

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

Paramètre |Value |Description
--------|-------|-----------
MaxIntermediateRowsetSize | 1000000 | Nombre maximal de lignes retournées dans une requête DAX. Ajoutez cette entrée manuellement au fichier msmdsrv.ini et augmentez cette valeur si la valeur par défaut est trop faible.
PredicateCheckSpoolCardinalityThreshold| 5000 | Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l’assistance du support technique Microsoft.

Pour plus d’informations sur les autres propriétés de serveur et sur la façon de les configurer, consultez [Propriétés du serveur dans Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).
