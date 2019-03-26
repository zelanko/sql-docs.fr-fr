---
title: Échantillonnage de lignes, transformation | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.rowsamplingtrans.f1
- sql13.DTS.DESIGNER.ROWSAMPLINGTRANSFORMATION.COLUMNS.F1
- sql13.dts.designer.rowsamplingtransformation.f1
helpviewer_keywords:
- sampling seeds [Integration Services]
- random seeds
- random sampling
- sample data sets [Integration Services]
- Row Sampling transformation
- packages [Integration Services], samples
- datasets [Integration Services], sample
ms.assetid: b6caafd3-30b2-4368-82af-a44611d4cd39
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e2964300e2990721afe920c0e418a220fe0b1a22
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58271943"
---
# <a name="row-sampling-transformation"></a>transformation d'échantillonnage de lignes
  La transformation d'échantillonnage de lignes permet d'obtenir un sous-ensemble sélectionné aléatoirement d'un ensemble de données d'entrée. Vous pouvez spécifier la taille exacte de l'échantillon de sortie ainsi que la valeur de départ du générateur de nombres aléatoires.  
  
 Il existe de nombreuses applications de l'échantillonnage aléatoire. Par exemple, une entreprise souhaitant sélectionner aléatoirement 50 employés pour l'attribution de prix dans une loterie peut utiliser la transformation d'échantillonnage de lignes dans la base de données des employés afin de générer le nombre exact de gagnants.  
  
 La transformation d'échantillonnage de lignes permet également de créer, lors du développement des packages, un ensemble de données réduit mais représentatif. Vous pouvez tester l'exécution des packages et la transformation des données avec des données très représentatives, mais plus rapidement car c'est un échantillon aléatoire qui est utilisé, au lieu de l'ensemble complet des données. Étant donné que l'échantillon de dataset utilisé par le package de test a toujours la même taille, le recours à l'échantillon de sous-ensemble facilite également l'identification des problèmes de performances dans le package.  
  
 Cette transformation est similaire à la transformation de l'échantillonnage par pourcentage, qui crée un échantillon de dataset en sélectionnant un pourcentage de lignes d'entrée. Consultez [Transformation de l’échantillonnage du pourcentage](../../../integration-services/data-flow/transformations/percentage-sampling-transformation.md).  
  
## <a name="configuring-the-row-sampling-transformation"></a>Configuration de la transformation d'échantillonnage de lignes  
 La transformation d'échantillonnage de lignes crée un échantillon de dataset en sélectionnant un nombre spécifié de lignes de l'entrée de transformation. La sélection de lignes de l'entrée de transformation étant aléatoire, l'échantillon obtenu est représentatif de l'entrée. Vous pouvez également spécifier la valeur de départ utilisée par le générateur de nombres aléatoires afin de définir la façon dont la transformation sélectionne les lignes.  
  
 L'utilisation de la même valeur aléatoire de départ sur la même entrée de transformation crée toujours le même échantillon en sortie. Si aucune valeur de départ n'est spécifiée, la transformation utilise le nombre de cycles du système d'exploitation pour créer le nombre aléatoire. Par conséquent, vous pouvez utiliser la même valeur de départ pendant le test, pour vérifier les résultats de la transformation durant le développement et le test du package, puis adopter une valeur aléatoire de départ lorsque le package passe en production.  
  
 La transformation d’échantillonnage de lignes inclut la propriété personnalisée **SamplingValue** . La propriété peut être mise à jour par une expression de propriété lors du chargement du package. Pour plus d’informations, consultez [Expressions Integration Services &#40;SSIS&#41;](../../../integration-services/expressions/integration-services-ssis-expressions.md), [Utiliser des expressions de propriété dans les packages](../../../integration-services/expressions/use-property-expressions-in-packages.md) et [Propriétés personnalisées des transformations](../../../integration-services/data-flow/transformations/transformation-custom-properties.md).  
  
 Cette transformation a une entrée et deux sorties. Elle ne possède aucune sortie d'erreur.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Propriétés personnalisées des transformations](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 Pour plus d'informations sur la définition des propriétés, consultez.  
  
## <a name="row-sampling-transformation-editor-sampling-page"></a>Éditeur de transformation d'échantillonnage de ligne (page Échantillonnage)
  Utilisez la boîte de dialogue **Éditeur de transformation d'échantillonnage de ligne** pour échantillonner une partie d'une entrée à l'aide d'un nombre de lignes spécifié. Cette transformation divise l'entrée en deux sorties distinctes.  
  
### <a name="options"></a>Options  
 **Nombre de lignes**  
 Définissez le nombre de lignes de l'entrée à utiliser comme échantillon.  
  
 Il est possible de spécifier la valeur de cette propriété en utilisant l'expression d'une propriété.  
  
 **Nom de sortie de l'exemple**  
 Fournissez un nom unique pour la sortie qui contiendra les lignes échantillonnées. Le nom fourni sera affiché dans le concepteur SSIS.  
  
 **Nom de sortie non sélectionnée**  
 Fournissez un nom unique pour la sortie qui contiendra les lignes exclues de l'échantillonnage. Le nom fourni sera affiché dans le concepteur SSIS.  
  
 **Utiliser la valeur de départ aléatoire suivante**  
 Définissez la valeur de départ d'échantillonnage du générateur de nombres aléatoires qu'utilise la transformation pour créer un échantillon. Ceci est recommandé uniquement pour le développement et les tests. La transformation utilise le nombre de cycles Microsoft Windows comme valeur de départ si une valeur de départ aléatoire n'est pas définie.  
  
## <a name="related-tasks"></a>Tâches associées  
 [Définir les propriétés d’un composant de flux de données](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
  
