---
title: Propriétés personnalisées des sources XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb29b28c-3159-41ec-b3d7-fce5b2f2be55
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 6cda524adafb4202f324246b1a4bd94495ebdf48
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142848"
---
# <a name="xml-source-custom-properties"></a>Propriétés personnalisées des sources XML
  La source XML comporte des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la source XML. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Entier|Mode utilisé pour accéder aux données XML.|  
|UseInlineSchema|Booléen|Valeur qui indique si une définition de schéma inséré doit être utilisée dans la source XML. La valeur par défaut de cette propriété est `False`.|  
|XMLData|String|Fichier ou variables à partir desquels les données XML sont extraites.<br /><br /> Il est possible de spécifier la valeur de cette propriété en utilisant l'expression d'une propriété.|  
|XMLSchemaDefinition|String|Chemin d'accès et nom de fichier du fichier de définition de schéma (.xsd).<br /><br /> Il est possible de spécifier la valeur de cette propriété en utilisant l'expression d'une propriété.|  
  
 Le tableau suivant décrit les propriétés personnalisées de la sortie de la source XML. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|RowsetID|String|Valeur qui identifie l'ensemble de lignes associé à la sortie.|  
  
 Les colonnes de sortie de la source XML ne possèdent pas de propriétés personnalisées.  
  
 Pour plus d'informations, consultez [XML Source](xml-source.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés communes](../common-properties.md)  
  
  