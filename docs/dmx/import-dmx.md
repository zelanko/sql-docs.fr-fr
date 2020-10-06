---
description: IMPORT (DMX)
title: IMPORTATION (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: fc96fb7dad5d7f6c4e555b133a0b3eaa02f91025
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726170"
---
# <a name="import-dmx"></a>IMPORT (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Charge un modèle ou une structure d'exploration de données à partir d'un fichier de sauvegarde Analysis Services (.abf) sur le serveur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IMPORT FROM <filename>  
```  
  
## <a name="arguments"></a>Arguments  
 *extension*  
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
 [Instructions de définition de données DMX&#41; Data Mining Extensions &#40;](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)   
 [EXPORTER &#40;&#41;DMX ](../dmx/export-dmx.md)   
 [Exporter et importer des objets d'exploration de données](/analysis-services/data-mining/export-and-import-data-mining-objects)  
  
