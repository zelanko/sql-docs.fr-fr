---
title: Élément Password (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Password Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Password
- urn:schemas-microsoft-com:xml-analysis#Password
- microsoft.xml.analysis.password
helpviewer_keywords:
- Password element
ms.assetid: 8a0603bd-f6a1-4b86-84f1-c83d0b03951b
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: cfc62de4ad73888fb95fe179efd0fdaeabbc9dc9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052708"
---
# <a name="password-element-xmla"></a>Élément Password (XMLA)
  Détermine le mot de passe à utiliser par le parent [sauvegarde](../xml-elements-commands/backup-element-xmla.md) ou [restaurer](../xml-elements-commands/restore-element-xmla.md) commande pour chiffrer ou déchiffrer un fichier de sauvegarde.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <Password>...</Password>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Sauvegarde](../xml-elements-commands/backup-element-xmla.md), [restaurer](../xml-elements-commands/restore-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Pour les commandes `Backup`, si l'élément `Password` n'est pas inclus ou contient une chaîne vide, le fichier de sauvegarde n'est pas chiffré.  
  
 Pour les commandes `Restore`, si l'élément `Password` n'est pas inclus ou contient une chaîne vide en tentant de restaurer un fichier de sauvegarde chiffré, une erreur survient.  
  
 Si des éléments `Location` sont inclus dans une commande `Backup` ou `Restore`, le même élément `Password` est utilisé pour les fichiers de sauvegarde et les fichiers de sauvegarde distants. Pour plus d’informations sur les fichiers de sauvegarde à distance, consultez [sauvegarde, restauration et synchronisation de bases de données de &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément location &#40;XMLA&#41;](location-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  