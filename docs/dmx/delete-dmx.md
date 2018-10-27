---
title: DELETE (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bc78718c813ef1aa599c1ab299c634d018bc88d6
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50144545"
---
# <a name="delete-dmx"></a>DELETE (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Supprime un modèle d'exploration de données, une structure d'exploration de données ou une structure d'exploration de données et tous ses modèles d'exploration de données associés selon les clauses DMX (Data Mining Extensions) que vous utilisez.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DELETE FROM [MINING MODEL] <model>[.CONTENT]  
DELETE FROM [MINING STRUCTURE] <structure>[.CONTENT]|[.CASES]  
```  
  
## <a name="arguments"></a>Arguments  
 *model*  
 Identificateur du modèle  
  
 *structure*  
 Identificateur de la structure  
  
## <a name="remarks"></a>Notes  
 Si vous ne spécifiez pas **MINING MODEL** ou **STRUCTURE d’exploration de données**, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] recherche le type d’objet en fonction du nom et traite l’objet correct. Si le serveur contient une structure d'exploration de données et un modèle d'exploration de données portant le même nom, une erreur est retournée.  
  
 Le tableau ci-dessous décrit le résultat obtenu en utilisant différentes formes de la syntaxe.  
  
|.|Résultats|  
|---------------|------------|  
|SUPPRIMER à partir de la STRUCTURE d’exploration de données*\<structure >*<br /><br /> ou Gestionnaire de configuration<br /><br /> SUPPRIMER à partir de la STRUCTURE d’exploration de données*\<structure >*. CONTENU|Effectue ProcessClear sur la structure d’exploration de données. Tout le contenu est supprimé de la structure d'exploration de données et de ses modèles d'exploration de données associés.|  
|SUPPRIMER à partir de la STRUCTURE d’exploration de données*\<structure >*. CAS|Effectue ProcessClearStructureOnly sur la structure d’exploration de données. Tout le contenu est supprimé de la structure d'exploration de données, en laissant ses modèles d'exploration de données associés intacts. Une fois la structure d'exploration de données supprimée, l'extraction dans les modèles d'exploration de données associés échoue.|  
|SUPPRIMER à partir de modèle d’exploration de données*\<modèle >*<br /><br /> ou Gestionnaire de configuration<br /><br /> SUPPRIMER à partir de modèle d’exploration de données*\<modèle >*. CONTENU|Exécute ProcessClear sur le modèle d’exploration de données, mais laisse les valeurs d’état intactes. Les valeurs d'état correspondent aux états possibles d'une colonne. Par exemple, les valeurs d'état d'une colonne Gender seraient Male ou Female.|  
  
 Pour plus d’informations sur les types de traitement, consultez [élément Type &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime tout le contenu du modèle NB_Sample.  
  
```  
DELETE FROM NB_Sample.CONTENT  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Data Mining Extensions &#40;DMX&#41; les instructions de définition de données](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;DMX&#41; les instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
