---
title: Élément storagelocation | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- DbStorageLocation element
ms.assetid: 1f448249-103a-479f-ae86-b0017acd0436
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cdee1fc2d62f63eb70e5aecd47c32693a9fbd155
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48173919"
---
# <a name="dbstoragelocation-element"></a>Élément StorageLocation
  Spécifie le dossier où [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] crée et gère l'ensemble des données de base de données et des fichiers de métadonnées.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Database>  
...  
   <ddl100_100:DbStorageLocation>...</ddl100_100:DbStorageLocation>  
...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|""|  
|Cardinalité|0-1 : Élément facultatif qui peut se produire une seule fois seulement.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Base de données](database-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Le `DbStorageLocation` propriété de base de données doit être définie pour un chemin d’accès de dossier UNC existant ou une chaîne vide. Une chaîne vide est la valeur par défaut pour le dossier de données de serveur. Si le dossier n'existe pas, une erreur sera élevée lors de l'exécution d'un `Create`, `Attach`ou commande `Alter`.  
  
 En outre, le `DbStorageLocation` propriété de base de données ne peut pas être définie pour pointer vers le dossier de données de serveur ou un de ses sous-dossiers. Si l’emplacement pointe vers le dossier de données de serveur ou un de ses sous-dossiers, une erreur sera générée lors de l’exécution un `Create`, `Attach`, ou `Alter` commande.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Attacher et détacher des bases de données Analysis Services](../../multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
  
