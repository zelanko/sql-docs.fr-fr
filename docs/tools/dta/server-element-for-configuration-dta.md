---
title: Élément de serveur de Configuration (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
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
ms.openlocfilehash: 3fee3915760241c294042fd24489a6c493a34a6f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47660439"
---
# <a name="server-element-for-configuration-dta"></a>Server, élément pour les configurations (Assistant Paramétrage de base de données)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
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
|**Élément parent**|[Configuration, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/configuration-element-dta.md)|  
|**Éléments enfants**|[Name, élément pour les serveurs &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/name-element-for-server-dta.md)<br /><br /> [Database, élément pour les configurations &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/database-element-for-configuration-dta.md)|  
  
## <a name="remarks"></a>Notes   
 Vous ne pouvez spécifier qu’un seul élément **Server** pour l’élément **Configuration** . Cet élément porte le nom **ServerTypecomplexType** dans le [schéma XML de l’Assistant Paramétrage du moteur de base de données](http://go.microsoft.com/fwlink/?linkid=43100). Ne confondez pas cet élément **Server** avec l’élément enfant de l’élément **DTAInput**. Pour plus d’informations, consultez [Server, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/server-element-dta.md).  
  
## <a name="example"></a> Exemple  
 Pour obtenir un exemple d’utilisation, consultez l’[Exemple de fichier d’entrée XML avec une configuration spécifiée par l’utilisateur &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a> Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
