---
title: Élément Restore (XMLA) | Microsoft Docs
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
- Restore Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Restore
- urn:schemas-microsoft-com:xml-analysis#Restore
- microsoft.xml.analysis.restore
helpviewer_keywords:
- Restore command
ms.assetid: bb5a0c92-3927-4fa4-975b-6e4d79e0a912
caps.latest.revision: 26
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 682806680604606d54c133617b2150b975cf8c03
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37275655"
---
# <a name="restore-element-xmla"></a>Élément Restore (XMLA)
  Restaure un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de données à partir d’un fichier de sauvegarde.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <Restore>  
      <DatabaseName>...</DatabaseName>  
      <DatabaseID>...</DatabaseID>  
      <File>...</File>  
      <Security>...</Security>  
      <AllowOverwrite>...</AllowOverwrite>  
      <Password>...</Password>  
      <Locations>...</Locations>  
      <DbStorageLocation>...</DbStorageLocation>  
   </Restore>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Commandee](../xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[AllowOverwrite](../xml-elements-properties/allowoverwrite-element-xmla.md), [DatabaseName](../xml-elements-properties/name-element-xmla.md), [DatabaseID](../xml-elements-properties/id-element-xmla.md), [fichier](../xml-elements-properties/file-element-xmla.md), [emplacements](../xml-elements-properties/locations-element-xmla.md), [mot de passe](../xml-elements-properties/password-element-xmla.md), [Sécurité](../xml-elements-properties/security-element-xmla.md), [DbStorageLocation](../xml-elements-properties/dbstoragelocation-element.md)|  
  
## <a name="remarks"></a>Notes  
 Le `Restore` commande restaure un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de données spécifiée dans le `DatabaseName` élément à partir d’un fichier de sauvegarde et, éventuellement, les restaurations des partitions distantes à partir de fichiers de sauvegarde distants.  
  
 Selon le mode de stockage utilisé par les objets stockés dans le fichier de sauvegarde, le `Restore` commande restaure les informations répertoriées dans le tableau suivant.  
  
|Mode de stockage|Informations|  
|------------------|-----------------|  
|OLAP multidimensionnel (MOLAP)|Données sources, agrégations et métadonnées|  
|Hybrid OLAP (HOLAP)|Agrégations et métadonnées|  
|OLAP relationnel (ROLAP)|Métadonnées|  
  
 Pendant un `Restore` commande, un verrou exclusif est placé sur le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de données spécifiée dans le `DatabaseName` élément. Le verrou est libéré lorsque la `Restore` commande est terminée.  
  
 Pour plus d’informations sur la sauvegarde et restauration des bases de données, consultez [sauvegarde, restauration et synchronisation de bases de données de &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
> [!IMPORTANT]  
>  Pour chaque fichier de sauvegarde, l'utilisateur qui exécute la commande de restauration doit avoir l'autorisation de lire à partir de l'emplacement de sauvegarde spécifié pour chaque fichier. Pour restaurer une base de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] qui n'est pas installée sur le serveur, l'utilisateur doit également être un membre du rôle serveur pour cette instance d' [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . Pour remplacer une base de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , l’utilisateur doit avoir l’un des rôles suivants : membre du rôle serveur pour l’instance d’ [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ou membre d’un rôle de base de données avec les autorisations de contrôle total (Administrateur) sur la base de données à restaurer.  
  
> [!NOTE]  
>  Après la restauration d'une base de données existante, l'utilisateur qui a restauré la base de données peut perdre l'accès à la base de données restaurée. Cette perte d'accès peut se produire si, au moment de la sauvegarde, l'utilisateur n'était pas un membre du rôle de serveur ou un membre du rôle de base de données avec les autorisations de contrôle total (Administrateur).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément de sauvegarde &#40;XMLA&#41;](backup-element-xmla.md)   
 [Élément du lot &#40;XMLA&#41;](batch-element-xmla.md)   
 [Élément en parallèle &#40;XMLA&#41;](../xml-elements-properties/parallel-element-xmla.md)   
 [Élément Synchronize &#40;XMLA&#41;](synchronize-element-xmla.md)   
 [Commandes &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
