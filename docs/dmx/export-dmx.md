---
title: EXPORTATION (DMX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EXPORT
dev_langs:
- DMX
helpviewer_keywords:
- exporting mining models
- exporting mining structures
- mining structures [DMX], exporting
- EXPORT statement
ms.assetid: 97617071-e560-4080-81af-a80276fc0823
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: bfc3e8344d1c6967185979c0970be6d49b572500
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="export-dmx"></a>EXPORT (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Extrait un modèle ou une structure d'exploration de données du serveur vers un fichier Analysis Services Backup File (.abf).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
EXPORT <object type> <object name>[, <object name>] [<object type> <object name>[, <object name] ] TO <filename> [WITH DEPENDENCIES]  
```  
  
## <a name="arguments"></a>Arguments  
 *type d’objet*  
 Facultatif le type de l’objet à exporter (modèle d’exploration de données ou structure d’exploration de données).  
  
 *nom de l’objet*  
 Ce paramètre est facultatif. Nom de l'objet à exporter.  
  
 *nom de fichier*  
 Nom et emplacement du fichier à exporter en tant que chaîne.  
  
## <a name="remarks"></a>Notes  
 Si l'instruction spécifie un modèle d'exploration de données, le fichier obtenu contiendra également une structure d'exploration de données associée.  Si l’instruction spécifie **avec dépendances**, tous les objets requis pour traiter l’objet (par exemple, la source de données et la vue de source de données) sont inclus dans le fichier .abf.  
  
 Vous devez être une base de données ou administrateur de serveur pour exporter ou importer des objets d’un [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données.  
  
## <a name="export-mining-structure-example"></a>Exemple d'exportation d'une structure d'exploration de données  
 L'exemple suivant exporte les structures d'exploration de données Targeted Mailing (Publipostage ciblé) et Forecasting (Prévisions) et le modèle d'exploration de données Association vers un emplacement de fichier spécifique.  Dans la mesure où le modèle Association fait partie de la structure Market Basket (Panier de marchés), l'exemple exporte également la structure Market Basket. Tous les autres modèles d’exploration de données qui peuvent exister comme partie de la structure d’exploration de données de panier d’achat n’est pas exportée, car le modèle d’Association a été exporté à l’aide de **modèle d’exploration de**, et non **STRUCTURE d’exploration de**.  
  
```  
EXPORT MINING STRUCTURE [Targeted Mailing], [Forecasting] MINING MODEL Association TO 'C:\TM_NEW.abf'  
```  
  
## <a name="export-mining-model-example"></a>Exemple d'exportation d'un modèle d'exploration de données  
 L'exemple suivant exporte le modèle d'exploration de données Association vers un emplacement de fichier spécifié. Étant donné que l’instruction spécifie **avec dépendances**, la source de données et les objets de vue de source de données sont également inclus dans le fichier .abf.  
  
```  
EXPORT MINING MODEL [Association] TO 'C:\Association_NEW.abf' WITH DEPENDENCIES  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Les Extensions d’exploration de données &#40; DMX &#41; Instructions de définition de données](../dmx/dmx-statements-data-definition.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence des instructions](../dmx/data-mining-extensions-dmx-statements.md)   
 [IMPORTATION &#40; DMX &#41;](../dmx/import-dmx.md)   
 [Exporter et importer des objets d’exploration de données](../analysis-services/data-mining/export-and-import-data-mining-objects.md)  
  
  

