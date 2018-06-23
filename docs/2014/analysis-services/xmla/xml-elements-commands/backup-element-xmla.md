---
title: Élément (XMLA) de sauvegarde | Documents Microsoft
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
- Backup Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Backup
- http://schemas.microsoft.com/analysisservices/2003/engine#Backup
- microsoft.xml.analysis.backup
helpviewer_keywords:
- Backup command
ms.assetid: 5bcbc14c-9db9-45b2-99de-f3a265bcb0c4
caps.latest.revision: 19
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: bd1f2317c28acd2e6037520334168491ec0bbcbe
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155110"
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
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Commandee](../xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[AllowOverwrite](../xml-elements-properties/allowoverwrite-element-xmla.md), [ApplyCompression](../xml-elements-properties/applycompression-element-xmla.md), [BackupRemotePartitions](../xml-elements-properties/backupremotepartitions-element-xmla.md), [fichier](../xml-elements-properties/file-element-xmla.md), [emplacements](../xml-elements-properties/locations-element-xmla.md), [ Objet](../xml-elements-properties/object-element-xmla.md), [mot de passe](../xml-elements-properties/password-element-xmla.md), [sécurité](../xml-elements-properties/security-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Le `Backup` commande sauvegarde le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de données spécifiée dans le [objet](../xml-elements-properties/object-element-xmla.md) élément à un fichier de sauvegarde et sauvegarde éventuellement les partitions distantes pour les fichiers de sauvegarde distants. Si l'élément `Object` fait référence à un objet autre qu'une base de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], une erreur se produit.  
  
 Les informations de la `Backup` commande sauvegarde varie selon le mode de stockage utilisé par les objets dans la base de données. Le tableau suivant répertorie les informations sauvegardées selon le mode de stockage utilisé.  
  
|Mode de stockage|Informations sauvegardées|  
|------------------|-----------------------------------|  
|OLAP multidimensionnel (MOLAP)|Données sources, agrégations et métadonnées|  
|Hybrid OLAP (HOLAP)|Agrégations et métadonnées|  
|OLAP relationnel (ROLAP)|Métadonnées|  
  
 Pendant un `Backup` de commande, un verrou partagé est placé sur le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de données spécifiée dans le `Object` élément. Le verrou partagé est libéré lorsque la `Backup` commande est terminée.  
  
 Plusieurs `Backup` commandes peuvent être exécutées en parallèle, si les commandes sont inclus dans le [parallèles](../xml-elements-properties/parallel-element-xmla.md) collection d’un [lot](batch-element-xmla.md) commande. La collection `Parallel` permet de sauvegarder une base de données dans plusieurs fichiers de sauvegarde simultanément.  
  
 Pour plus d’informations sur la sauvegarde et restauration des bases de données, consultez [sauvegarde, restauration et synchronisation de bases de données de &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
> [!IMPORTANT]  
>  Pour chaque fichier de sauvegarde, l'utilisateur qui exécute la commande de sauvegarde doit avoir l'autorisation d'écrire dans l'emplacement de sauvegarde spécifié pour chaque fichier. L’utilisateur doit aussi avoir l’un des rôles suivants : membre d’un rôle serveur pour l’instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ou membre d’un rôle de base de données avec les autorisations de contrôle total (Administrateur) sur la base de données à sauvegarder.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Restore &#40;XMLA&#41;](restore-element-xmla.md)   
 [Élément Synchronize &#40;XMLA&#41;](synchronize-element-xmla.md)   
 [Commandes &#40;XMLA&#41;](xml-elements-commands.md)  
  
  