---
title: Élément DropOnlyMode, (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DropOnlyMode element
ms.assetid: 80960676-7581-4074-889b-80ee665963dd
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8e7c6648cdc3257b0fecef77ed4c09b27a52f2c6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68132784"
---
# <a name="droponlymode-element-dta"></a>DropOnlyMode, élément (Assistant Paramétrage de base de données)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
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
  
  
