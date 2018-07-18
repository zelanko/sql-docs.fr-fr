---
title: Colonne dérivée, transformation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.derivedcolumntrans.f1
helpviewer_keywords:
- multiple derived columns
- expressions [Integration Services], derived columns
- derived columns
- columns [Integration Services], derivations
- Derived Column transformation
ms.assetid: 8eba755e-8e48-4233-bd1e-09a46bf2692f
caps.latest.revision: 59
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 68dae5fdc6d4b35c4c4ef7633e29d22f8db25cb8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285595"
---
# <a name="derived-column-transformation"></a>Transformation de colonne dérivée
  La transformation de colonne dérivée crée de nouvelles valeurs de colonne en appliquant des expressions aux colonnes d'entrée de transformation. Une expression peut contenir toute combinaison de variables, de fonctions, d'opérateurs et de colonnes provenant de l'entrée de transformation. Le résultat peut être ajouté en tant que nouvelle colonne ou inséré dans une colonne existante en tant que valeur de remplacement. La transformation de colonne dérivée peut définir plusieurs colonnes dérivées, et toute variable ou colonne d'entrée peut apparaître dans plusieurs expressions.  
  
 Vous pouvez utiliser cette transformation pour réaliser les tâches suivantes :  
  
-   concaténer des données à partir de différentes colonnes en une colonne dérivée. Par exemple, vous pouvez combiner les valeurs des colonnes **FirstName** et **LastName** en une colonne dérivée unique nommée **FullName**à l’aide de l’expression `FirstName + " " + LastName`.  
  
-   extraire des caractères de données de chaîne à l'aide de fonctions telles que SUBSTRING, puis stocker le résultat dans une colonne dérivée. Par exemple, vous pouvez extraire de la colonne **FirstName** l’initiale d’une personne à l’aide de l’expression `SUBSTRING(FirstName,1,1)`.  
  
-   appliquer des fonctions mathématiques à des données numériques et stocker le résultat dans une colonne dérivée. Par exemple, vous pouvez modifier la longueur et la précision d’une colonne numérique, **SalesTax**, en un nombre à deux décimales à l’aide de l’expression `ROUND(SalesTax, 2)`.  
  
-   créer des expressions qui comparent les colonnes d'entrée et les variables. Par exemple, vous pouvez comparer la variable **Version** aux données de la colonne **ProductVersion**et, suivant le résultat de la comparaison, utiliser la valeur de **Version** ou de **ProductVersion**, à l’aide de l’expression `ProductVersion == @Version? ProductVersion : @Version`.  
  
-   extraire des parties d'une valeur de date et d'heure. Par exemple, vous pouvez utiliser les fonctions GETDATE et DATEPART pour extraire l’année actuelle à l’aide de l’expression `DATEPART("year",GETDATE())`.  
  
-   convertir des chaînes de date dans un format spécifique en utilisant une expression.  
  
## <a name="configuration-of-the-derived-column-transformation"></a>Configuration de la transformation de colonne dérivée  
 Vous pouvez configurer la transformation de colonne dérivée comme suit :  
  
-   Indiquez une expression pour chaque colonne d'entrée ou pour chaque nouvelle colonne à modifier. Pour plus d’informations, consultez [Expressions Integration Services &#40;SSIS&#41;](../../expressions/integration-services-ssis-expressions.md).  
  
    > [!NOTE]  
    >  Si une expression référence une colonne d'entrée remplacée par la transformation de colonne dérivée, cette expression utilise la valeur d'origine de la colonne au lieu de la valeur dérivée.  
  
-   Si les résultats sont insérés dans de nouvelles colonnes et que le type de données est `string`, spécifiez une page de codes. Pour plus d'informations, voir [Comparing String Data](../comparing-string-data.md).  
  
 La transformation de colonne dérivée inclut la propriété personnalisée FriendlyExpression. La propriété peut être mise à jour par une expression de propriété lors du chargement du package. Pour plus d’informations, consultez [Expressions de propriété dans des packages](../../expressions/use-property-expressions-in-packages.md)et [Propriétés personnalisées des transformation](transformation-custom-properties.md).  
  
 Cette transformation a une entrée, une sortie standard et une sortie d'erreur.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de transformation de colonne dérivée** , consultez [Éditeur de transformation de colonne dérivée](../../derived-column-transformation-editor.md).  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../../common-properties.md)  
  
-   [Propriétés personnalisées des transformations](transformation-custom-properties.md)  
  
 Pour plus d'informations sur la définition des propriétés, cliquez sur l'une des rubriques suivantes :  
  
-   [Définir les propriétés d’un composant de flux de données](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Dériver les valeurs de colonnes à l’aide de la transformation de colonne dérivée](derived-column-transformation.md)  
  
## <a name="related-content"></a>Contenu associé  
 Article technique, [SSIS Expression Examples](http://go.microsoft.com/fwlink/?LinkId=220761), sur social.technet.microsoft.com  
  
 Réponse organisée, [How to Split Column Data using SSIS](http://go.microsoft.com/fwlink/?LinkId=321995)(Comment fractionner des données de colonne à l’aide de SSIS), sur curatedviews.cloudapp.net.  
  
  
