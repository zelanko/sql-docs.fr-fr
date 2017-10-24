---
title: "Élément de base de données pour la charge de travail (DTA) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: 112fca2a-37e5-4162-b2e7-b56eb8ab0c6f
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e71d9a3077821fc4b34ee5cebac5441065ddf013
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="database-element-for-workload-dta"></a>Database, élément pour les charges de travail (Assistant Paramétrage de base de données)
  Spécifie la base de données où se trouve la table de trace de charge de travail.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Workload>  
  <Database>  
   ...code removed here...  
  </Database>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Obligatoire une fois si aucun autre type de charge de travail n'est spécifié. Vous devez spécifier un élément enfant **EventString**, **File**ou **Database** pour le parent **Workload** , mais un seul type peut être utilisé. Par exemple, si vous spécifiez une charge de travail avec l’élément **Database** , vous ne pouvez pas spécifier une charge de travail avec l’élément **File** dans le même fichier d’entrée XML.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Workload, élément &#40; DTA &#41;](../../tools/dta/workload-element-dta.md)|  
|**Éléments enfants**|[Name, élément pour la base de données &#40; DTA &#41;](../../tools/dta/name-element-for-database-dta.md)<br /><br /> [Schema, élément pour les bases de données &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a>Notes  
 Cet élément porte le nom **DatabaseDetailsTypecomplexType** dans le schéma XML de l’Assistant Paramétrage du moteur de base de données. Ne confondez pas cet élément **Database** avec celui dont le parent racine est l’élément **Configuration**. (Consultez [Database, élément pour les configurations &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/database-element-for-configuration-dta.md).)  
  
## <a name="example"></a>Exemple  
 Pour voir un exemple d’utilisation de cet élément **Database** , consultez l’exemple de code dans [Workload, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/workload-element-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  

