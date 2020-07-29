---
title: DropOnlyMode, élément (Assistant Paramétrage de base de données)
description: Dans l’utilitaire dta, l’élément DropOnlyMode spécifie que l’Assistant Paramétrage du moteur de base de données doit considérer uniquement la suppression des index, des vues indexées ou des partitions existants.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DropOnlyMode element
ms.assetid: 80960676-7581-4074-889b-80ee665963dd
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 0f0115e5f657ccf7976d3a407239ff1e0616c03f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85732098"
---
# <a name="droponlymode-element-dta"></a>DropOnlyMode, élément (Assistant Paramétrage de base de données)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
  
 **Occurrence** : facultatif. Ne peut être utilisé qu’une seule fois pour chaque élément **TuningOptions** . Ne peut pas être utilisé si les éléments suivants sont spécifiés dans l'élément **TuningOptions** :  
  
-   [FeatureSet, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/featureset-element-dta.md)  
  
-   [Partitioning, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/partitioning-element-dta.md)  
  
-   [L’élément KeepExisting &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/keepexisting-element-dta.md) est défini sur **ALL**  
  
## <a name="element-relationships"></a>Relations entre les éléments  
 **Élément parent** : [Élément TuningOptions &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)  
  
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
  
  
