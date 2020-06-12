---
title: EXPORTER (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 59e4a78c9432c5ba8f75eb7bfaa6ab46a0b052cf
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83670272"
---
# <a name="export-dmx"></a>EXPORT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Extrait un modèle ou une structure d'exploration de données du serveur vers un fichier Analysis Services Backup File (.abf).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
EXPORT <object type> <object name>[, <object name>] [<object type> <object name>[, <object name] ] TO <filename> [WITH DEPENDENCIES]  
```  
  
## <a name="arguments"></a>Arguments  
 *type d’objet*  
 Facultatif. type de l’objet à exporter (modèle d’exploration de données ou structure d’exploration de données).  
  
 *nom de l’objet*  
 facultatif. Nom de l'objet à exporter.  
  
 *extension*  
 Nom et emplacement du fichier à exporter en tant que chaîne.  
  
## <a name="remarks"></a>Notes  
 Si l'instruction spécifie un modèle d'exploration de données, le fichier obtenu contiendra également une structure d'exploration de données associée.  Si l’instruction spécifie **des dépendances**, tous les objets requis pour traiter l’objet (par exemple, la source de données et la vue de source de données) sont inclus dans le fichier. ABF.  
  
 Vous devez être un administrateur de base de données ou de serveur pour exporter ou importer des objets à partir d’une [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données.  
  
## <a name="export-mining-structure-example"></a>Exemple d'exportation d'une structure d'exploration de données  
 L'exemple suivant exporte les structures d'exploration de données Targeted Mailing (Publipostage ciblé) et Forecasting (Prévisions) et le modèle d'exploration de données Association vers un emplacement de fichier spécifique.  Dans la mesure où le modèle Association fait partie de la structure Market Basket (Panier de marchés), l'exemple exporte également la structure Market Basket. Tous les autres modèles d’exploration de données qui peuvent exister dans le cadre de la structure d’exploration de données du panier d’exploitation ne seront pas exportés, car le modèle d’association a été exporté à l’aide du **modèle d’exploration** **de données, et non**  
  
```  
EXPORT MINING STRUCTURE [Targeted Mailing], [Forecasting] MINING MODEL Association TO 'C:\TM_NEW.abf'  
```  
  
## <a name="export-mining-model-example"></a>Exemple d'exportation d'un modèle d'exploration de données  
 L'exemple suivant exporte le modèle d'exploration de données Association vers un emplacement de fichier spécifié. Étant donné que l’instruction spécifie **des dépendances**, les objets de source de données et de vue de source de données sont également inclus dans le fichier. ABF.  
  
```  
EXPORT MINING MODEL [Association] TO 'C:\Association_NEW.abf' WITH DEPENDENCIES  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de définition de données DMX&#41; Data Mining Extensions &#40;](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)   
 [IMPORTER &#40;&#41;DMX](../dmx/import-dmx.md)   
 [Exporter et importer des objets d'exploration de données](https://docs.microsoft.com/analysis-services/data-mining/export-and-import-data-mining-objects)  
  
  
