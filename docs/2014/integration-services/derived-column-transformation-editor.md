---
title: Dérivé d’éditeur de Transformation de colonne | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.derivedcolumntransformation.f1
helpviewer_keywords:
- Derived Column Transformation Editor
ms.assetid: ff73923e-d245-43d8-bf24-af3bdc942e51
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 55260f465c69c69f3cdebca0f9e9eae048530376
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039762"
---
# <a name="derived-column-transformation-editor"></a>Éditeur de transformation de colonne dérivée
  Utilisez la boîte de dialogue **Éditeur de transformation de colonne dérivée** pour créer des expressions qui remplissent de nouvelles colonnes ou des colonnes de remplacement.  
  
 Pour en savoir plus sur la transformation de colonne dérivée, consultez [Transformation de colonne dérivée](data-flow/transformations/derived-column-transformation.md).  
  
## <a name="options"></a>Options  
 **Variables et colonnes**  
 Pour créer une expression qui utilise une variable ou une colonne d'entrée, faites glisser la variable ou la colonne à partir de la liste des variables et colonnes disponibles vers une ligne d'une table existante dans le volet inférieur ou vers une nouvelle ligne au bas de la liste.  
  
 **Fonctions et opérateurs**  
 Pour créer une expression qui utilise une fonction ou un opérateur dans le but d'évaluer des données d'entrée ou de diriger des données de sortie, faites-les glisser à partir de la liste dans le volet inférieur.  
  
 **Nom de la colonne dérivée**  
 Fournissez un nom pour la colonne dérivée. Par défaut, il s'agit d'une liste numérotée de colonnes dérivées ; vous pouvez néanmoins choisir un nom unique et descriptif.  
  
 **Colonne dérivée**  
 Sélectionnez une colonne dérivée dans la liste. Choisissez d'ajouter la colonne dérivée comme nouvelle colonne de sortie ou de remplacer les données d'une colonne existante.  
  
 **Expression**  
 Tapez une expression ou créez-en une en faisant glisser la liste précédente des colonnes, variables et fonctions disponibles.  
  
 Il est possible de spécifier la valeur de cette propriété en utilisant l'expression d'une propriété.  
  
 **Rubriques connexes :** [Expressions Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md), [Opérateurs &#40;expression SSIS&#41;](expressions/operators-ssis-expression.md) et [Fonctions &#40;expression SSIS&#41;](expressions/functions-ssis-expression.md)  
  
 **Type de données**  
 Si vous ajoutez des données à une nouvelle colonne, la boîte de dialogue **Éditeur de transformation de colonne dérivée** évalue automatiquement l’expression et définit correctement le type de données. La valeur de cette colonne est en lecture seule. Pour plus d’informations, consultez [Types de données Integration Services](data-flow/integration-services-data-types.md).  
  
 **Longueur**  
 Si vous ajoutez des données à une nouvelle colonne, la boîte de dialogue **Éditeur de transformation de colonne dérivée** évalue automatiquement l’expression et définit la longueur de colonne des données de chaînes. La valeur de cette colonne est en lecture seule.  
  
 **Précision**  
 Si vous ajoutez des données à une nouvelle colonne, la boîte de dialogue **Éditeur de transformation de colonne dérivée** définit automatiquement la précision des données numériques en fonction du type de données. La valeur de cette colonne est en lecture seule.  
  
 **Échelle**  
 Si vous ajoutez des données à une nouvelle colonne, la boîte de dialogue **Éditeur de transformation de colonne dérivée** définit automatiquement l’échelle des données numériques en fonction du type de données. La valeur de cette colonne est en lecture seule.  
  
 **Page de codes**  
 Si vous ajoutez des données à une nouvelle colonne, la boîte de dialogue **Éditeur de transformation de colonne dérivée** définit automatiquement la page de codes pour le type de données DT_STR. Vous pouvez mettre à jour **Page de codes**.  
  
 **Configurer l'affichage des erreurs**  
 Spécifiez comment gérer les erreurs dans la boîte de dialogue [Configurer la sortie d’erreur](../../2014/integration-services/configure-error-output.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Dériver les valeurs de colonnes à l’aide de la transformation de colonne dérivée](data-flow/transformations/derive-column-values-by-using-the-derived-column-transformation.md)  
  
  