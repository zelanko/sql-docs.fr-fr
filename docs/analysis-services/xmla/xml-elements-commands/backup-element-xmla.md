---
title: "Élément (XMLA) de sauvegarde | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Backup Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Backup
- http://schemas.microsoft.com/analysisservices/2003/engine#Backup
- microsoft.xml.analysis.backup
helpviewer_keywords:
- Backup command
ms.assetid: 5bcbc14c-9db9-45b2-99de-f3a265bcb0c4
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c5617d1b0b62eabb945881041a795a1a699b4c41
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="backup-element-xmla"></a>Élément Backup (XMLA)
  Sauvegarde une [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de données à un fichier de sauvegarde.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <Backup>  
      <Object>...</Object>  
      <File>...</File>  
      <Security>...</Security>  
      <ApplyCompression>...</ApplyCompression>  
      <AllowOverwrite>...</AllowOverwrite>  
      <Password>...</Password>  
      <BackupRemotePartitions>...</BackupRemotePartitions>  
      <Locations>...</Locations>  
   </Backup>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[AllowOverwrite](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md), [ApplyCompression](../../../analysis-services/xmla/xml-elements-properties/applycompression-element-xmla.md), [BackupRemotePartitions](../../../analysis-services/xmla/xml-elements-properties/backupremotepartitions-element-xmla.md), [fichier](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md), [emplacements](../../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md), [objet](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), [mot de passe](../../../analysis-services/xmla/xml-elements-properties/password-element-xmla.md), [sécurité](../../../analysis-services/xmla/xml-elements-properties/security-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Le **sauvegarde** commande sauvegarde le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de données spécifiée dans le [objet](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) élément à un fichier de sauvegarde et sauvegarde éventuellement les partitions distantes pour les fichiers de sauvegarde distants. Si le **objet** élément fait référence à un objet autre qu’un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] de base de données, une erreur se produit.  
  
 Les informations sauvegardées par la commande **Backup** dépendent du mode de stockage utilisé par les objets dans la base de données. Le tableau suivant répertorie les informations sauvegardées selon le mode de stockage utilisé.  
  
|Mode de stockage|Informations sauvegardées|  
|------------------|-----------------------------------|  
|OLAP multidimensionnel (MOLAP)|Données sources, agrégations et métadonnées|  
|Hybrid OLAP (HOLAP)|Agrégations et métadonnées|  
|OLAP relationnel (ROLAP)|Métadonnées|  
  
 Pendant un **sauvegarde** de commande, un verrou partagé est placé sur le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de données spécifiée dans le **objet** élément. Le verrou partagé est libéré lorsque la commande **Backup** est terminée.  
  
 Plusieurs **sauvegarde** commandes peuvent être exécutées en parallèle, si les commandes sont inclus dans le [parallèles](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md) collection d’un [lot](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) commande. La collection **Parallel** permet de sauvegarder une base de données dans plusieurs fichiers de sauvegarde simultanément.  
  
 Pour plus d’informations sur la sauvegarde et restauration des bases de données, consultez [sauvegarde, restauration et synchroniser les bases de données &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
> [!IMPORTANT]  
>  Pour chaque fichier de sauvegarde, l'utilisateur qui exécute la commande de sauvegarde doit avoir l'autorisation d'écrire dans l'emplacement de sauvegarde spécifié pour chaque fichier. L’utilisateur doit aussi avoir l’un des rôles suivants : membre d’un rôle serveur pour l’instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ou membre d’un rôle de base de données avec les autorisations de contrôle total (Administrateur) sur la base de données à sauvegarder.  
  
## <a name="see-also"></a>Voir aussi  
 [Restaurer l’élément &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Synchroniser, élément &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Commandes &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

