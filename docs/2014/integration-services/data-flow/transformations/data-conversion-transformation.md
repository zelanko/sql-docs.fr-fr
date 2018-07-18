---
title: Conversion de données, transformation | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataconversiontrans.f1
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: fd515bbc-6f49-4d0c-ae7f-6ea3c3f24a1c
caps.latest.revision: 52
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5b9bc5c7e4845adbc15d2e73d45ea85ff851084d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37207539"
---
# <a name="data-conversion-transformation"></a>transformation de conversion de données
  La transformation de conversion de données convertit les données d'une colonne d'entrée en un type de données différent, puis les copie dans une nouvelle colonne de sortie. Par exemple, un package peut extraire des données de plusieurs sources, puis utiliser cette transformation pour convertir des colonnes vers le type de données requis par la banque de données de destination. Vous pouvez appliquer plusieurs conversions à une même colonne d'entrée.  
  
 Cette transformation permet à un package de réaliser les types de conversions de données suivants :  
  
-   Modifier le type de données. Pour plus d’informations, consultez [Types de données Integration Services](../integration-services-data-types.md).  
  
    > [!NOTE]  
    >  Si vous convertissez des données en un type de données date ou datetime, la date de la colonne de sortie est exprimée dans le format ISO, bien que la préférence des paramètres régionaux puisse spécifier un format différent.  
  
-   Définir la longueur de colonne des données de chaîne ainsi que la précision et l'échelle des données numériques. Pour plus d’informations, consultez [Précision, échelle et longueur &#40;Transact-SQL&#41;](/sql/t-sql/data-types/precision-scale-and-length-transact-sql).  
  
-   Spécifier une page de codes. Pour plus d'informations, voir [Comparing String Data](../comparing-string-data.md).  
  
    > [!NOTE]  
    >  Lors d'une copie entre deux colonnes de type de données chaîne, celles-ci doivent utiliser la même page de codes.  
  
 Si une colonne de sortie de données de type chaîne est plus courte que la colonne d'entrée correspondante, les données de sortie sont tronquées. Pour plus d’informations, consultez [Gestion des erreurs dans les données](../error-handling-in-data.md).  
  
 Cette transformation a une entrée, une sortie et une sortie d'erreur.  
  
## <a name="related-tasks"></a>Related Tasks  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programme. Pour plus d’informations sur l’utilisation de la transformation de conversion de données dans le Concepteur SSIS, consultez [Convertir des données en un type différent à l’aide de la transformation de conversion de données](data-conversion-transformation.md) et [Éditeur de transformation de conversion de données](../../data-conversion-transformation-editor.md). Pour plus d’informations sur la définition des propriétés de cette transformation par programmation, consultez [Propriétés courantes](../../common-properties.md) et [Propriétés personnalisées des transformations](transformation-custom-properties.md).  
  
## <a name="related-content"></a>Contenu associé  
 Entrée de blog, [Performance Comparison between Data Type Conversion Techniques in SSIS 2008](http://go.microsoft.com/fwlink/?LinkId=220823), sur blogs.msdn.com.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse rapide](../../fast-parse.md)   
 [Flux de données](../data-flow.md)   
 [Transformations Integration Services](integration-services-transformations.md)  
  
  
