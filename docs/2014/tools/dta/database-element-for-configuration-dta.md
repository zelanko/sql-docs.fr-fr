---
title: Élément de base de données de Configuration (DTA) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: e91ba243-6cc9-457a-8f5a-134f3c71ae69
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 6afd8b418cd00c2ec89430e4c82613ea1af285d6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040990"
---
# <a name="database-element-for-configuration-dta"></a>Database, élément pour les configurations (Assistant Paramétrage de base de données)
  Spécifie la base de données dans laquelle vous souhaitez que l’Assistant Paramétrage du moteur de base de données pour évaluer la configuration hypothétique (spécifiée par la `Configuration` élément).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Obligatoire une ou plusieurs fois par `Server` élément.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Élément de serveur de Configuration &#40;DTA&#41;](server-element-for-configuration-dta.md)|  
|**Éléments enfants**|[Nom d’élément de base de données &#40;DTA&#41;](name-element-for-database-dta.md)<br /><br /> [Élément de schéma pour la base de données &#40;DTA&#41;](schema-element-for-database-dta.md)<br /><br /> [Recommendation, élément &#40;DTA&#41;](recommendation-element-dta.md)|  
  
## <a name="remarks"></a>Notes  
 Cet élément porte le nom **DatabaseTypecomplexType** dans le schéma XML de l’Assistant Paramétrage du moteur de base de données. Ne confondez pas cet élément `Database` avec celui dont le parent racine est l'élément `Server`, qui se trouve en haut du fichier d'entrée XML. Pour plus d’informations, consultez [Database, élément pour les serveurs &#40;Assistant Paramétrage de base de données&#41;](database-element-for-server-dta.md).  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de ce `Database` élément, consultez la [exemple de fichier d’entrée XML avec la Configuration spécifiée par l’utilisateur &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  