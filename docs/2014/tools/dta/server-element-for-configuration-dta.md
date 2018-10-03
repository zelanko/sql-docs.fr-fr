---
title: Élément de serveur de Configuration (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 10a8fa9eed7f89d9706ab3388eccc881b165ef74
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48206909"
---
# <a name="server-element-for-configuration-dta"></a>Server, élément pour les configurations (Assistant Paramétrage de base de données)
  Contient les informations d’identification pour le serveur où vous souhaitez l’Assistant de paramétrage du moteur de base de données pour évaluer la configuration hypothétique (spécifiée par la `Configuration` élément).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Configuration>  
    <Server>  
...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Obligatoire une fois par `Configuration` élément.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Élément de configuration &#40;DTA&#41;](configuration-element-dta.md)|  
|**Éléments enfants**|[Élément nom serveur &#40;DTA&#41;](name-element-for-server-dta.md)<br /><br /> [Élément de base de données pour la Configuration &#40;DTA&#41;](database-element-for-configuration-dta.md)|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez spécifier qu’un seul `Server` élément pour le `Configuration` élément. Cet élément porte le nom **ServerTypecomplexType** dans le [schéma XML de l’Assistant Paramétrage du moteur de base de données](http://go.microsoft.com/fwlink/?linkid=43100). Ne confondez pas cet `Server` élément avec celui qui est l’enfant de le `DTAInput` élément. Pour plus d’informations, consultez [Server, élément &#40;Assistant Paramétrage de base de données&#41;](server-element-dta.md).  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation, consultez l’[Exemple de fichier d’entrée XML avec une configuration spécifiée par l’utilisateur &#40;Assistant Paramétrage de base de données&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
