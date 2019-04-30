---
title: Générer des éléments pour des valeurs NULL avec le paramètre XSINIL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, null values
- null values [SQL Server], XML
- ELEMENTS directive
- XSINIL parameter
ms.assetid: 2dbc4e48-1cae-4d83-b371-3265da9687cc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d056959f5e05d3de79fa81d33331390f4decb49a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63205608"
---
# <a name="generate-elements-for-null-values-with-the-xsinil-parameter"></a>Générer des éléments pour des valeurs NULL avec le paramètre XSINIL
  La directive **ELEMENTS** construit du code XML dans lequel chaque valeur de colonne est mappée à un élément du code XML. Si la valeur de colonne est NULL, aucun élément n'est ajouté. En spécifiant le paramètre facultatif **XSINIL** sur la directive ELEMENTS, vous pouvez demander qu’un élément soit également créé pour la valeur NULL. Dans ce cas, un élément dont l’attribut **xsi:nil** a la valeur TRUE est retourné pour chaque valeur de colonne NULL.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le mode RAW avec FOR XML](use-raw-mode-with-for-xml.md)  
  
  
