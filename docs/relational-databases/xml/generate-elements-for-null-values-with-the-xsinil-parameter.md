---
title: Générer des éléments pour des valeurs NULL avec XSINIL | Microsoft Docs
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
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
ms.custom: seo-lt-2019
ms.openlocfilehash: 13451c2f9cfa87c1ceb83956e9ebe6056b74b6ad
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665304"
---
# <a name="generate-elements-for-null-values-with-the-xsinil-parameter"></a>Générer des éléments pour des valeurs NULL avec le paramètre XSINIL

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

La directive **ELEMENTS** construit du code XML dans lequel chaque valeur de colonne est mappée à un élément du code XML. Par défaut, si la valeur de colonne est NULL, aucun élément n’est ajouté. Mais en spécifiant le paramètre facultatif **XSINIL** sur la directive ELEMENTS, vous pouvez demander qu’un élément soit également créé pour la valeur NULL. Dans ce cas, un élément dont l’attribut **xsi:nil** a la valeur TRUE est retourné pour chaque valeur de colonne NULL.  
  
## <a name="see-also"></a>Voir aussi

[Utiliser le mode RAW avec FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)

[SELECT - Clause FOR](../../t-sql/queries/select-for-clause-transact-sql.md)
