---
title: "Droponlymode, élément (DTA) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: DropOnlyMode element
ms.assetid: 80960676-7581-4074-889b-80ee665963dd
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4ac3f3b750a5c2c5e9395900163a1db4e07c3691
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="droponlymode-element-dta"></a>DropOnlyMode, élément (Assistant Paramétrage de base de données)
  Spécifie que l'Assistant Paramétrage du moteur de base de données doit supprimer uniquement les index, les vues indexées ou les partitions existantes pendant la session de paramétrage. Aucune nouvelle structure PDS n'est pas prise en compte lorsque cette option de paramétrage est spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <DropOnlyMode>...</DropOnlyMode>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
 **Type de données et longueur**  
  
 **Valeur par défaut**  
  
 **Occurrence**: facultatif. Ne peut être utilisé qu’une seule fois pour chaque élément **TuningOptions** . Ne peut pas être utilisé si les éléments suivants sont spécifiés dans l'élément **TuningOptions** :  
  
-   [FeatureSet, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/featureset-element-dta.md)  
  
-   [Partitioning, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/partitioning-element-dta.md)  
  
-   [L’élément KeepExisting &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/keepexisting-element-dta.md) est défini sur **ALL**  
  
## <a name="element-relationships"></a>Relations entre les éléments  
 **Élément parent** : [TuningOptions, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/tuningoptions-element-dta.md)  
  
 **Éléments enfants**  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre la section **TuningOptions** d'un fichier d'entrée XML de l'Assistant Paramétrage du moteur de base de données dans lequel l'élément **DropOnlyMode** est spécifié. Dans cet exemple, la durée de paramétrage est limitée à 24 heures (1440 minutes) et tous les index cluster et non cluster existants sont pris en compte en vue de leur suppression :  
  
```xml  
<TuningOptions  
  <TuningTimeInMin>1440</Name>  
  <KeepExisting>ALIGNED</KeepExisting>  
  <DropOnlyMode />  
</TuningOptions>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
