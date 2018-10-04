---
title: Élément de base de données pour le serveur (DTA) | Microsoft Docs
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
- Database element
ms.assetid: 5cd9a87a-af4b-45f3-8c18-f7fd7e7d3064
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 341c267b686a56a37390e0ee774df0aa20e73fd8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48049819"
---
# <a name="database-element-for-server-dta"></a>Élément Database pour les serveurs (Assistant Paramétrage de base de données)
  Spécifie la base de données que vous souhaitez paramétrer sur un serveur spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucun.|  
|Valeur par défaut|Aucun.|  
|Occurrence|Obligatoire une ou plusieurs fois par `Server` élément.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|Élément parent|[Élément de serveur &#40;DTA&#41;](server-element-dta.md)|  
|Éléments enfants|[Nom d’élément de base de données &#40;DTA&#41;](name-element-for-database-dta.md)<br /><br /> [Élément de schéma pour la base de données &#40;DTA&#41;](schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a>Notes  
 Cet élément porte le nom **DatabaseDetailsTypecomplexType** dans le schéma XML de l’Assistant Paramétrage du moteur de base de données. Ne confondez pas cet élément `Database` avec celui dont le parent racine est l'élément `Configuration`. Pour plus d’informations, consultez [Database, élément pour les configurations &#40;Assistant Paramétrage de base de données&#41;](database-element-for-configuration-dta.md).  
  
## <a name="example"></a>Exemple  
 Pour un exemple d’utilisation de la `Database` élément, consultez [Server, élément &#40;DTA&#41;](server-element-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
