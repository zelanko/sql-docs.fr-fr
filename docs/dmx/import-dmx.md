---
title: IMPORTATION (DMX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- IMPORT
dev_langs:
- DMX
helpviewer_keywords:
- IMPORT statement
- mining structures [DMX], importing
ms.assetid: c053bc88-2daf-4ebb-81d7-5a330250536d
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 162bc8fc7497d3e8b425e09b81c13a24adb75678
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="import-dmx"></a>IMPORT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Charge un modèle ou une structure d'exploration de données à partir d'un fichier de sauvegarde Analysis Services (.abf) sur le serveur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IMPORT FROM <filename>  
```  
  
## <a name="arguments"></a>Arguments  
 *filename*  
 Chaîne contenant le nom et l'emplacement du fichier à importer.  
  
## <a name="remarks"></a>Notes  
 Si aucun objet n'est spécifié, la totalité du contenu du fichier .dmb est chargée. Si le fichier .dmb comprend une base de données qui n'existe pas sur le serveur, la base de données est créée.  
  
 Pour exporter ou importer des objets, vous devez être administrateur de base de données ou de serveur.  
  
## <a name="import-from-file-example"></a>Exemple de l'importation à partir d'un fichier  
 L'exemple suivant importe la totalité du contenu du fichier contenant la structure et le modèle d'association sur le serveur actuel.  
  
```  
IMPORT FROM 'C:\TEMP\Association_NEW.dmb'  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Data Mining Extensions &#40;DMX&#41; instructions de définition de données](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;DMX&#41; instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Les Extensions d’exploration de données & #40 ; DMX & #41 ; Référence des instructions](../dmx/data-mining-extensions-dmx-statements.md)   
 [EXPORTER &AMP;#40;DMX&AMP;#41;](../dmx/export-dmx.md)   
 [Exporter et importer des objets d’exploration de données](../analysis-services/data-mining/export-and-import-data-mining-objects.md)  
  
  
