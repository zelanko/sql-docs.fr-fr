---
title: Gestion des erreurs dans les données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- truncating data
- data conversion errors [Integration Services]
- errors [Integration Services], data flow components
- lookups [Integration Services]
- errors [Integration Services]
- errors [Integration Services], data flow outputs
- error outputs [Integration Services]
- data flow [Integration Services], errors
- expressions [Integration Services], errors
ms.assetid: c61667b4-25cb-4d45-a52f-a733e32863f4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8b5a98877e04a077bf1bb1c0c527500f3102b862
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62827143"
---
# <a name="error-handling-in-data"></a>Gestion des erreurs dans les données
  Lorsqu'un composant de flux de données applique une transformation à des données de colonne, extrait des données à partir de sources ou charge des données dans des destinations, des erreurs peuvent se produire. Les erreurs sont fréquemment dues à des valeurs de données inattendues. Par exemple, une conversion de données échoue car une colonne contient une chaîne au lieu d'un nombre, une insertion dans une colonne de base de données échoue car les données sont une date et que la colonne a un type de données numérique, ou l'évaluation d'une expression échoue car la valeur d'une colonne est nulle, ce qui engendre une opération mathématique non valide.  
  
 Les erreurs appartiennent en général à l'une des catégories suivantes :  
  
-   Erreurs de conversion de données, qui se produisent si une conversion provoque la perte de chiffres significatifs, la perte de chiffres non significatifs et la troncation de chaînes. Les erreurs de conversion de données se produisent également si la conversion demandée n'est pas prise en charge.  
  
-   Erreurs d'évaluation d'expression, qui se produisent si des expressions évaluées au moment de l'exécution effectuent des opérations non valides ou deviennent syntaxiquement incorrectes à cause de valeurs de données manquantes ou incorrectes.  
  
-   Erreurs de recherche, qui se produisent si une opération de recherche ne trouve pas de correspondance dans la table de recherche.  
  
 De nombreux composants de flux de données prennent en charge les sorties d'erreur, qui vous permettent de contrôler la manière dont le composant gère les erreurs de lignes dans les données entrantes et sortantes. Vous pouvez spécifier le comportement du composant lorsqu'une troncation ou une erreur se produit en définissant des options sur des colonnes dans l'entrée ou la sortie. Par exemple, vous pouvez faire en sorte que le composant échoue si les données de noms des clients sont tronquées, mais qu'il ignore les erreurs sur une autre colonne qui contient des données moins importantes.  
  
 La sortie d'erreur peut être connectée à l'entrée d'une autre transformation ou chargée dans une destination différente de la sortie sans erreur. Par exemple, la sortie d'erreur peut être connectée à une transformation de colonne dérivée qui fournit une chaîne pour une colonne vide.  
  
 Le schéma suivant illustre un flux de données simple incluant une sortie d'erreur.  
  
 ![Flux de données avec affichage des erreurs](../media/mw-dts-11.gif "Flux de données avec affichage des erreurs")  
  
 Outre les colonnes de données, la sortie d'erreur contient les colonnes **ErrorCode** et **ErrorColumn** . La colonne **ErrorCode** identifie l'erreur, tandis que la colonne **ErrorColumn** contient l'identificateur de lignage de la colonne d'erreur. Pour afficher les métadonnées de ces colonnes, cliquez sur le chemin d'accès qui connecte la sortie d'erreur au composant suivant dans le flux de données. Dans certaines circonstances, la colonne **ErrorColumn** prend la valeur zéro. Cela se produit lorsque la condition d'erreur affecte toute la ligne et non une seule colonne. Par exemple, lorsqu'une recherche échoue dans la transformation de recherche.  
  
 Pour plus d’informations, consultez [Flux de données](data-flow.md) et [Chemins d’accès d’Integration Services](integration-services-paths.md).  
  
 Pour obtenir une liste d'erreurs, d'avertissements et d'autres messages Integration Services, consultez [Integration Services Error and Message Reference](../integration-services-error-and-message-reference.md).  
  
## <a name="error-and-truncation-options"></a>Options d'erreur et de troncation  
 Les erreurs appartiennent à l'une des deux catégories suivantes : erreurs ou troncations. Une erreur indique un échec non équivoque et génère un résultat NULL. Il peut s'agir par exemple d'erreurs de conversion de données ou d'évaluation d'expression, telles qu'une tentative de conversion d'une chaîne contenant des caractères alphabétiques en nombre. Les conversions de données, les évaluations d'expression et les affectations de résultats d'expression aux variables, propriétés et colonnes de données peuvent échouer en raison de casts non conformes et de types de données incompatibles. Pour plus d’informations, consultez [Cast &#40;expression SSIS&#41;](../expressions/cast-ssis-expression.md), [Types de données Integration Services dans les expressions](../expressions/integration-services-data-types-in-expressions.md) et [Types de données Integration Services](integration-services-data-types.md).  
  
 Une troncation est une erreur moins grave. Elle génère des résultats qui peuvent être utilisables, voire même souhaitables. Vous pouvez faire en sorte de traiter les troncations comme des erreurs ou comme des conditions acceptables. Par exemple, si vous insérez une chaîne de 15 caractères dans une colonne qui ne fait qu'un seul caractère de large, vous pouvez choisir de tronquer la chaîne.  
  
 Vous pouvez configurer la manière dont les sources, les  transformations et les destinations gèrent les erreurs et les troncations. Le tableau ci-dessous décrit les options disponibles.  
  
|Option|Description|  
|------------|-----------------|  
|Composant défaillant|La tâche de flux de données échoue lorsqu'une erreur ou une troncation a lieu. L'échec est l'option par défaut pour une erreur et une troncation.|  
|Ignorer l'échec|L'erreur ou la troncation est ignorée et la ligne de données est dirigée vers la sortie de la transformation ou de la source.|  
|Réacheminer la ligne|La ligne de données d'erreur ou de troncation est dirigée vers la sortie d'erreur de la source, de la transformation ou de la destination.|  
  
## <a name="adding-the-error-description"></a>Ajout de la description de l'erreur  
 Par défaut, une sortie d'erreur fournit le code d'erreur numérique et contient généralement l'identificateur de la colonne dans laquelle l'erreur s'est produite. Vous pouvez utiliser le composant Script pour inclure la description de l'erreur dans une colonne supplémentaire en utilisant une ligne unique de script pour appeler la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> de l'interface <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>.  
  
 Le composant Script peut être ajouté au segment d'erreur du flux de données n'importe où en aval des composants de flux de données dont vous souhaitez capturer les erreurs, mais est généralement placé immédiatement avant l'écriture des lignes en erreur vers une destination. De cette manière, le script recherche uniquement les descriptions des lignes d'erreurs écrites. Par exemple, le segment d'erreur du flux de données peut corriger certaines erreurs sans écrire ces lignes dans une destination d'erreur. Pour plus d’informations, consultez [amélioration d’une sortie d’erreur avec le composant script](../extending-packages-scripting-data-flow-script-component-examples/enhancing-an-error-output-with-the-script-component.md).  
  
### <a name="to-configure-an-error-output"></a>Pour configurer un affichage des erreurs  
  
-   [Configurer une sortie d'erreur dans un composant de flux de données](../configure-an-error-output-in-a-data-flow-component.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de données](data-flow.md)   
 [Transformer des données avec des transformations](transformations/transform-data-with-transformations.md)   
 [Connecter des composants avec des chemins d’accès](../connect-components-with-paths.md)   
 [Tâche de flux de données](../control-flow/data-flow-task.md)   
 [Flux de données](data-flow.md)  
  
  
