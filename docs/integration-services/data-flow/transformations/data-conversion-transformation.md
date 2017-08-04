---
title: "Transformation de Conversion de données | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.dataconversiontrans.f1
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: fd515bbc-6f49-4d0c-ae7f-6ea3c3f24a1c
caps.latest.revision: 53
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 897651a9257aadeac68a392eeae8b51d0c87de8d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="data-conversion-transformation"></a>transformation de conversion de données
  La transformation de conversion de données convertit les données d'une colonne d'entrée en un type de données différent, puis les copie dans une nouvelle colonne de sortie. Par exemple, un package peut extraire des données de plusieurs sources, puis utiliser cette transformation pour convertir des colonnes vers le type de données requis par la banque de données de destination. Vous pouvez appliquer plusieurs conversions à une même colonne d'entrée.  
  
 Cette transformation permet à un package de réaliser les types de conversions de données suivants :  
  
-   Modifier le type de données. Pour plus d’informations, consultez [Integration Services Data Types](../../../integration-services/data-flow/integration-services-data-types.md).  
  
    > [!NOTE]  
    >  Si vous convertissez des données en un type de données date ou datetime, la date de la colonne de sortie est exprimée dans le format ISO, bien que la préférence des paramètres régionaux puisse spécifier un format différent.  
  
-   Définir la longueur de colonne des données de chaîne ainsi que la précision et l'échelle des données numériques. Pour plus d’informations, consultez [Précision, échelle et longueur &#40;Transact-SQL&#41;](../../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
-   Spécifier une page de codes. Pour plus d'informations, voir [Comparing String Data](../../../integration-services/data-flow/comparing-string-data.md).  
  
    > [!NOTE]  
    >  Lors d'une copie entre deux colonnes de type de données chaîne, celles-ci doivent utiliser la même page de codes.  
  
 Si une colonne de sortie de données de type chaîne est plus courte que la colonne d'entrée correspondante, les données de sortie sont tronquées. Pour plus d’informations, consultez [Gestion des erreurs dans les données](../../../integration-services/data-flow/error-handling-in-data.md).  
  
 Cette transformation a une entrée, une sortie et une sortie d'erreur.  
  
## <a name="related-tasks"></a>Tâches associées  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation. Pour plus d’informations sur l’utilisation de la transformation de conversion de données dans le Concepteur SSIS, consultez [Convertir des données en un type différent à l’aide de la transformation de conversion de données](../../../integration-services/data-flow/transformations/convert-data-type-by-using-data-conversion-transformation.md) et [Éditeur de transformation de conversion de données](../../../integration-services/data-flow/transformations/data-conversion-transformation-editor.md). Pour plus d’informations sur la définition des propriétés de cette transformation par programmation, consultez [Propriétés courantes](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796) et [Propriétés personnalisées des transformations](../../../integration-services/data-flow/transformations/transformation-custom-properties.md).  
  
## <a name="related-content"></a>Contenu connexe  
 Entrée de blog, [Performance Comparison between Data Type Conversion Techniques in SSIS 2008](http://go.microsoft.com/fwlink/?LinkId=220823), sur blogs.msdn.com.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse rapide](http://msdn.microsoft.com/library/6688707d-3c5b-404e-aa2f-e13092ac8d95)   
 [Flux de données](../../../integration-services/data-flow/data-flow.md)   
 [Transformations Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  
