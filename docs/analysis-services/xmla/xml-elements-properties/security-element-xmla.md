---
title: "Élément Security (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Security Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.security
- urn:schemas-microsoft-com:xml-analysis#Security
- http://schemas.microsoft.com/analysisservices/2003/engine#Security
helpviewer_keywords: Security element
ms.assetid: 0b601f69-d16d-4d10-9361-b8afaa6ed357
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7e66c114446c44d52d535c27334bc3c5f996b4a2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="security-element-xmla"></a>Élément Security (XMLA)
  Spécifie la manière de sauvegarder ou restaurer des définitions de sécurité, telles que les rôles et les autorisations, pendant un [sauvegarde](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) ou [restaurer](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <Security>...</Security>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*SkipMembership*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Sauvegarde](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [restaurer](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **sécurité** élément détermine si les définitions de sécurité, notamment les rôles et autorisations, définies sur un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de données sont sauvegardées ou restaurées durant, un **sauvegarde** ou **restaurer** commande. Cet élément détermine également si les comptes d'utilisateur et les groupes Windows définis comme membres des définitions de sécurité sont inclus dans le cadre de la commande **Backup** ou **Restore** .  
  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*SkipMembership*|Inclut les définitions de sécurité, mais exclut les informations d'appartenance durant les commandes **Backup** ou **Restore** .|  
|*CopyAll*|Inclut les définitions de sécurité et les informations d'appartenance durant les commandes **Backup** ou **Restore** .|  
|*IgnoreSecurity*|Exclut les définitions de sécurité durant les commandes **Backup** ou **Restore** .|  
  
## <a name="see-also"></a>Voir aussi  
 [Élément SynchronizeSecurity &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/synchronizesecurity-element-xmla.md)   
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
