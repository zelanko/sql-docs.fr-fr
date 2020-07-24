---
title: SUPPRIMER (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1ce350c4d99fec986d8df06c364e6f6adac94324
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86969870"
---
# <a name="delete-dmx"></a>DELETE (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Supprime un modèle d'exploration de données, une structure d'exploration de données ou une structure d'exploration de données et tous ses modèles d'exploration de données associés selon les clauses DMX (Data Mining Extensions) que vous utilisez.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DELETE FROM [MINING MODEL] <model>[.CONTENT]  
DELETE FROM [MINING STRUCTURE] <structure>[.CONTENT]|[.CASES]  
```  
  
## <a name="arguments"></a>Arguments  
 *model*  
 Identificateur du modèle  
  
 *arborescence*  
 Identificateur de la structure  
  
## <a name="remarks"></a>Notes  
 Si vous ne spécifiez pas de **modèle** d’exploration de données ou de **structure d’exploration de données**, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] recherche le type d’objet en fonction du nom et traite l’objet correct. Si le serveur contient une structure d'exploration de données et un modèle d'exploration de données portant le même nom, une erreur est retournée.  
  
 Le tableau ci-dessous décrit le résultat obtenu en utilisant différentes formes de la syntaxe.  
  
|.|Résultats|  
|---------------|------------|  
|SUPPRIMER DE LA STRUCTURE D’EXPLORATION DE DONNÉES*\<structure>*<br /><br /> ou<br /><br /> SUPPRIMER de la STRUCTURE d’exploration de données *\<structure>* . HUMIDITÉ|Exécute ProcessClear sur la structure d’exploration de données. Tout le contenu est supprimé de la structure d'exploration de données et de ses modèles d'exploration de données associés.|  
|SUPPRIMER de la STRUCTURE d’exploration de données *\<structure>* . PARFOIS|Exécute ProcessClearStructureOnly sur la structure d’exploration de données. Tout le contenu est supprimé de la structure d'exploration de données, en laissant ses modèles d'exploration de données associés intacts. Une fois la structure d'exploration de données supprimée, l'extraction dans les modèles d'exploration de données associés échoue.|  
|SUPPRIMER DU MODÈLE D’EXPLORATION DE DONNÉES*\<model>*<br /><br /> ou<br /><br /> SUPPRIMER du modèle d’exploration de données *\<model>* . HUMIDITÉ|Exécute ProcessClear sur le modèle d’exploration de données, mais laisse les valeurs d’État intactes. Les valeurs d'état correspondent aux états possibles d'une colonne. Par exemple, les valeurs d'état d'une colonne Gender seraient Male ou Female.|  
  
 Pour plus d’informations sur les types de traitement, consultez [élément Type &#40;&#41;XMLA ](https://docs.microsoft.com/analysis-services/xmla/xml-elements-properties/type-element-xmla).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime tout le contenu du modèle NB_Sample.  
  
```  
DELETE FROM NB_Sample.CONTENT  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de définition de données DMX&#41; Data Mining Extensions &#40;](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
