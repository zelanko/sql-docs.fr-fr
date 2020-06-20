---
title: Élément Database pour la charge de travail (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: 112fca2a-37e5-4162-b2e7-b56eb8ab0c6f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 48f9202483bcb2cf8e06b6e0d14834753cc666b8
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85000393"
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
|**Occurrence**|Obligatoire une fois si aucun autre type de charge de travail n'est spécifié. Vous devez spécifier un élément enfant `EventString`, `File` ou `Database` pour le parent `Workload`, mais un seul type peut être utilisé. Par exemple, si vous spécifiez une charge de travail avec l' `Database` élément, vous ne pouvez pas spécifier une charge de travail avec l' `File` élément dans le même fichier d’entrée XML.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Workload, élément &#40;Assistant Paramétrage de base de données&#41;](workload-element-dta.md)|  
|**Éléments enfants**|[Name, élément pour les bases de données &#40;Assistant Paramétrage de base de données&#41;](name-element-for-database-dta.md)<br /><br /> [Schema, élément pour les bases de données &#40;Assistant Paramétrage de base de données&#41;](schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a>Notes  
 Cet élément porte le nom **DatabaseDetailsTypecomplexType** dans le schéma XML de l’Assistant Paramétrage du moteur de base de données. Ne confondez pas cet élément `Database` avec celui dont le parent racine est l'élément `Configuration`. (Consultez [Database, élément pour les configurations &#40;Assistant Paramétrage de base de données&#41;](database-element-for-configuration-dta.md).)  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de cet `Database` élément, consultez l’exemple de code dans [élément de charge de travail &#40;DTA&#41;](workload-element-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
