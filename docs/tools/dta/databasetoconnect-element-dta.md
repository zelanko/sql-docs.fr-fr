---
title: Élément DatabaseToConnect, (DTA) | Microsoft Docs
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
- DatabaseToConnect element
ms.assetid: 65153a66-3aee-4429-99b7-0816ac23c285
author: markingmyname
ms.author: maghan
ms.openlocfilehash: e37bef50b77ded9d41fde856cbe4beebdf05cb9f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68119792"
---
# <a name="databasetoconnect-element-dta"></a>DatabaseToConnect, élément (Assistant Paramétrage de base de données)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Spécifie la première base de données à laquelle l'Assistant Paramétrage du moteur de base de données se connecte lors du paramétrage d'une charge de travail.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
    <TuningOptions>  
...code removed here...  
      <DatabaseToConnect>...</DatabaseToConnect>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|**string**, longueur illimitée.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Facultatif. Peut être utilisé une seule fois pour chaque élément **TuningOptions** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Élément TuningOptions &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Éléments enfants**|None|  
  
## <a name="remarks"></a>Notes  
 Utilisez **DatabaseToConnect** pour spécifier le nom de la première base de données à laquelle vous souhaitez que l'Assistant Paramétrage du moteur de base de données se connecte lorsqu'il démarre une session de paramétrage. Vous ne pouvez spécifier qu'une seule base de données avec cet élément. Si plusieurs noms de bases de données sont spécifiées, l'Assistant Paramétrage du moteur de base de données renvoie une erreur.  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation, consultez [Exemple de fichier d’entrée XML avec une charge de travail Inline &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-inline-workload-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
