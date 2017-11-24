---
title: "DTAXML, élément (DTA) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: DTAXML element
ms.assetid: 3d9942ed-8a27-40db-a7c9-808984d914a2
caps.latest.revision: "18"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cfbd14f4f2fb602111c72e82ddf71503a751cead
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="dtaxml-element-dta"></a>DTAXML, élément (Assistant Paramétrage de base de données)
  Élément racine d'un fichier d'entrée ou de sortie de l'Assistant Paramétrage du moteur de base de données, **DTAXML** contient tous les éléments qui décrivent les entrées et les sorties de paramétrage générées par l'Assistant Paramétrage du moteur de base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<DTAXML   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
    xmlns="http://schemas.microsoft.com/sqlserver/2004/07/dta">  
    ...code removed here...  
</DTAXML>  
```  
  
## <a name="element-attributes"></a>Attributs des éléments  
  
|Attribut|Description|  
|---------------|-----------------|  
|**xmlns:xsi**|Obligatoire. Identifie l'espace de noms de l'instance du schéma XML. Les attributs de cet espace de noms servent à référencer le schéma qui est utilisé pour valider le fichier XML de l'Assistant Paramétrage du moteur de base de données.<br /><br /> Valeur obligatoire : [http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)|  
|**xmlns**|Obligatoire. Identifie l'espace de noms de l'Assistant Paramétrage du moteur de base de données.<br /><br /> Si vous modifiez le fichier XML de l'Assistant Paramétrage du moteur de base de données à l'aide de l'éditeur XML dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cette valeur est utilisée par l'aide obtenue par la touche F1 et l'aide dynamique pour rechercher les rubriques de référence dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Valeur obligatoire :<br /><br /> [Database Engine Tuning Advisor XML Schema](http://go.microsoft.com/fwlink/?LinkId=43100) Namespace|  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Obligatoire une fois par fichier XML de l'Assistant Paramétrage du moteur de base de données.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|Aucune|  
|**Éléments enfants**|[DTAInput, élément &#40;DTA&#41;](../../tools/dta/dtainput-element-dta.md)<br /><br /> **DTAOutput** , élément (consultez l’article [Database Engine Tuning Advisor XML schema](http://schemas.microsoft.com/sqlserver/) pour plus d’informations)|  
  
## <a name="remarks"></a>Notes  
 Pour plus d'informations sur les espaces de noms XML, consultez l'article [Namespaces in an XML Document](http://go.microsoft.com/fwlink/?LinkId=7341) dans la bibliothèque [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN.  
  
## <a name="example"></a>Exemple  
 Pour obtenir des exemples d’éléments **DTAXML** caractéristiques, consultez [Exemples de fichiers d’entrée XML &#40;DTA&#41;](../../tools/dta/xml-input-file-samples-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)   
 [Démarrer et utiliser l’Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)  
  
  
