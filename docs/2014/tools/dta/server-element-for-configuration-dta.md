---
title: Élément de serveur de Configuration (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2bc763d621d15f982a2670483683d3862e678c98
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63283677"
---
# <a name="server-element-for-configuration-dta"></a>Server, élément pour les configurations (Assistant Paramétrage de base de données)
  Contient les informations d'identification du serveur sur lequel vous souhaitez que l'Assistant Paramétrage du moteur de base de données évalue la configuration hypothétique (spécifiée par l'élément `Configuration`).  
  
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
|**Occurrence**|Obligatoire une fois par élément `Configuration`.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Configuration, élément &#40;Assistant Paramétrage de base de données&#41;](configuration-element-dta.md)|  
|**Éléments enfants**|[Name, élément pour les serveurs &#40;Assistant Paramétrage de base de données&#41;](name-element-for-server-dta.md)<br /><br /> [Database, élément pour les configurations &#40;Assistant Paramétrage de base de données&#41;](database-element-for-configuration-dta.md)|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez spécifier qu’un seul `Server` élément pour le `Configuration` élément. Cet élément porte le nom **ServerTypecomplexType** dans le [schéma XML de l’Assistant Paramétrage du moteur de base de données](https://go.microsoft.com/fwlink/?linkid=43100). Ne confondez pas cet élément `Server` avec l'élément enfant de l'élément `DTAInput`. Pour plus d’informations, consultez [Server, élément &#40;Assistant Paramétrage de base de données&#41;](server-element-dta.md).  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation, consultez l’[Exemple de fichier d’entrée XML avec une configuration spécifiée par l’utilisateur &#40;Assistant Paramétrage de base de données&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
