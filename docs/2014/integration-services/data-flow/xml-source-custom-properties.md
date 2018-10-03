---
title: Propriétés personnalisées des sources XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: eb29b28c-3159-41ec-b3d7-fce5b2f2be55
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6843e2f2d818789a791ba12c78e5aa42a086a15d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224779"
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
  
  
