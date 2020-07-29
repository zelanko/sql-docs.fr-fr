---
title: Name, élément pour les tables (Assistant Paramétrage de base de données)
description: Dans l’utilitaire dta, l’élément Name pour les tables spécifie un nom de table pour le paramétrage. Cet article décrit cet élément.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Name element
ms.assetid: 422a755f-ee52-4863-b1aa-f4ef1b8fd0bb
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: ad49751156f8ee4ad5eefaf8ad0cead9228bdcea
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775012"
---
# <a name="name-element-for-table-dta"></a>Name, élément pour les tables (Assistant Paramétrage de base de données)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Spécifie un nom de table pour le paramétrage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Schema>  
    <Table>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|**string**, entre 1 et 255 caractères.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Obligatoire. Une fois par élément **Table** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Table, élément pour les schémas &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/table-element-for-schema-dta.md)|  
|**Éléments enfants**|Aucun.|  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation, consultez [Server, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/server-element-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
