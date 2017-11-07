---
title: "Élément DbStorageLocation | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DbStorageLocation element
ms.assetid: 1f448249-103a-479f-ae86-b0017acd0436
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9267f5858eb837efdbcd84fb040934e767835d4f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

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
|Type de données et longueur|Chaîne|  
|Valeur par défaut|""|  
|Cardinalité|0-1 : Élément facultatif qui peut se produire une seule fois seulement.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Base de données](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La propriété de base de données **DbStorageLocation** doit être définie avec un chemin d'accès au dossier UNC existant ou avec une chaîne vide. Une chaîne vide est la valeur par défaut pour le dossier de données de serveur. Si le dossier n'existe pas, une erreur sera élevée lors de l'exécution d'un **Create**, **Attach**ou commande **Alter** .  
  
 En outre, la propriété de base de données **DbStorageLocation** ne peut pas être définie pour pointer sur le dossier de données de serveur ou sur l'un de ses sous-dossiers. Si l'emplacement pointe sur le dossier de données de serveur ou l'un de ses sous-dossiers, une erreur est déclenchée lorsque vous exécutez une commande **Create**, **Attach**ou **Alter** .  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Attacher et détacher des bases de données Analysis Services](../../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
  

