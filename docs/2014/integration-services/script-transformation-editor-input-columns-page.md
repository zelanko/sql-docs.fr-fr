---
title: Éditeur de transformation de script (page colonnes d’entrée) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.inputcolumn.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: d6e4ce84-3335-48e6-82d3-1c359ed87f63
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 5e5ce667a34bc9ebff01e97b31205f7a3629c147
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84963969"
---
# <a name="script-transformation-editor-input-columns-page"></a>Éditeur de transformation de script (page Colonnes d'entrée)
  Utilisez la page **Colonnes d’entrée** de la boîte de dialogue **Éditeur de transformation de script** pour définir les propriétés des colonnes d’entrée.  
  
> [!NOTE]  
>  La page **Colonnes d’entrée** ne s’affiche pas pour les composants source qui ont des sorties, mais pas d’entrées.  
  
 Pour en savoir plus sur le composant de script, consultez [Script Component](data-flow/transformations/script-component.md) et [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md). Pour en savoir plus sur la programmation du composant de script, consultez [Extension du flux de données avec le composant Script](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
## <a name="options"></a>Options  
 **Nom d’entrée**  
 Sélectionnez le nom d'une entrée dans la liste.  
  
 **Colonnes d’entrée disponibles**  
 Utilisez les cases à cocher pour spécifier les colonnes que la transformation de script utilisera.  
  
 **Colonne d'entrée**  
 Sélectionnez dans la liste le nom d'une colonne d'entrée pour chaque ligne. Vos sélections se reflètent dans les sélections des cases à cocher de la table **Colonnes d’entrée disponibles**.  
  
 **Alias de sortie**  
 Permet de saisir un alias pour chaque colonne de sortie. Par défaut, il s'agit du nom de la colonne d'entrée ; vous pouvez néanmoins choisir un nom unique et descriptif.  
  
 **Type d’utilisation**  
 Spécifiez si la transformation de script traite chaque colonne en `ReadOnly` ou en `ReadWrite`.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services de référence des erreurs et des messages](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Sélectionner un type de composant de script](../../2014/integration-services/select-script-component-type.md)   
 [Éditeur de transformation de script &#40;page entrées et sorties&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md)   
 [Éditeur de transformation de script &#40;page de script&#41;](../../2014/integration-services/script-transformation-editor-script-page.md)   
 [Éditeur de transformation de script &#40;page gestionnaires de connexions&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md)   
 [Exemples supplémentaires du composant Script](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
