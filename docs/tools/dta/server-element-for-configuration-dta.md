---
title: "Élément de serveur de Configuration (DTA) | Documents Microsoft"
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
- Server element
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 548c08ab2bb5a12cade464305fa1ac0969c26bca
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="server-element-for-configuration-dta"></a>Server, élément pour les configurations (Assistant Paramétrage de base de données)
  Contient les informations d’identification du serveur sur lequel vous souhaitez que l’Assistant Paramétrage du moteur de base de données évalue la configuration hypothétique (spécifiée par l’élément **Configuration** ).  
  
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
|**Occurrence**|Obligatoire une fois par élément **Configuration** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Élément de configuration &#40; DTA &#41;](../../tools/dta/configuration-element-dta.md)|  
|**Éléments enfants**|[Name, élément pour les serveurs &#40; DTA &#41;](../../tools/dta/name-element-for-server-dta.md)<br /><br /> [Élément de base de données Configuration &#40; DTA &#41;](../../tools/dta/database-element-for-configuration-dta.md)|  
  
## <a name="remarks"></a>Notes  
 Vous ne pouvez spécifier qu’un seul élément **Server** pour l’élément **Configuration** . Cet élément porte le nom **ServerTypecomplexType** dans le [schéma XML de l’Assistant Paramétrage du moteur de base de données](http://go.microsoft.com/fwlink/?linkid=43100). Ne confondez pas cet élément **Server** avec l’élément enfant de l’élément **DTAInput**. Pour plus d’informations, consultez [Server, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/server-element-dta.md).  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation, consultez l’[Exemple de fichier d’entrée XML avec une configuration spécifiée par l’utilisateur &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  

