---
title: EventString, élément (Assistant Paramétrage de base de données)
description: Dans l’utilitaire dta, l’élément EventString spécifie une charge de travail de script Transact-SQL directement dans le fichier d’entrée XML.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- EventString element
ms.assetid: f76c37b4-2f6e-4274-8ee2-87e89d98e8a2
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: f9944a2e9d9dc1ec8aad069aa74b90a6a420fad4
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826514"
---
# <a name="eventstring-element-dta"></a>EventString, élément (Assistant Paramétrage de base de données)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Spécifie une charge de travail de script [!INCLUDE[tsql](../../includes/tsql-md.md)] directement dans le fichier d'entrée XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Workload>  
    <EventString Weight="...">  
    ...code removed here...  
    </EventString>  
</Workload>  
```  
  
## <a name="element-attributes"></a>Attributs des éléments  
  
|Attribut|Description|  
|---------------|-----------------|  
|**Poids**|facultatif. Spécifie le facteur de pondération de la requête (facteur d'importance) pour l'événement spécifié. Utilisez un type de données **float** pour spécifier la pondération. Par exemple, **Weight**="100.01". La valeur minimale que vous pouvez spécifier pour **Weight** est « 0 ».|  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|**string**, longueur illimitée.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Obligatoire une fois si aucun autre type de charge de travail n'est spécifié. Vous devez spécifier un élément enfant **EventString**, **File**ou **Database** pour le parent **Workload** , mais un seul type peut être utilisé. Par exemple, si vous spécifiez une charge de travail avec l'élément **EventString** , vous ne pouvez pas spécifier une charge de travail avec l'élément **File** dans le même fichier d'entrée XML.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Workload, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/workload-element-dta.md)|  
|**Éléments enfants**|Aucun.|  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez [Exemple de fichier d’entrée XML avec une charge de travail Inline &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-inline-workload-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
