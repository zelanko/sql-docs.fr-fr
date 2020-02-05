---
title: Propriétés personnalisées des sources XML | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: eb29b28c-3159-41ec-b3d7-fce5b2f2be55
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 52ce0e96ce131b1ea1a69f2ba9f7466850cbf4cf
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "71290942"
---
# <a name="xml-source-custom-properties"></a>Propriétés personnalisées des sources XML

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  La source XML comporte des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la source XML. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer|Mode utilisé pour accéder aux données XML.|  
|UseInlineSchema|Boolean|Valeur qui indique si une définition de schéma inséré doit être utilisée dans la source XML. La valeur par défaut de cette propriété est **False**.|  
|XMLData|String|Fichier ou variables à partir desquels les données XML sont extraites.<br /><br /> Il est possible de spécifier la valeur de cette propriété en utilisant l'expression d'une propriété.|  
|XMLSchemaDefinition|String|Chemin d'accès et nom de fichier du fichier de définition de schéma (.xsd).<br /><br /> Il est possible de spécifier la valeur de cette propriété en utilisant l'expression d'une propriété.|  
  
 Le tableau suivant décrit les propriétés personnalisées de la sortie de la source XML. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|RowsetID|String|Valeur qui identifie l'ensemble de lignes associé à la sortie.|  
  
 Les colonnes de sortie de la source XML ne possèdent pas de propriétés personnalisées.  
  
 Pour plus d'informations, consultez [XML Source](../../integration-services/data-flow/xml-source.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés communes](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
