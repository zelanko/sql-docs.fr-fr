---
title: Éditeur de boucle foreach (page mappage de variables) | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.mapping.f1
ms.assetid: aa847b87-f391-48a5-9849-eeda2d6b00b9
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 03488e4cfd3a0cc905a58166f381f68eb3292c49
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66058527"
---
# <a name="foreach-loop-editor-variable-mappings-page"></a>Éditeur de boucle Foreach (page Mappage de variables)
  Utilisez la page **Mappage de variables** de la boîte de dialogue **Éditeur de boucle Foreach** pour mapper les variables à la valeur de la collection. La valeur de cette variable est mise à jour avec les valeurs de la collection à chaque itération de la boucle.  
  
 Pour en savoir plus sur l’utilisation du conteneur de boucles Foreach dans un package Integration Services, consultez [Conteneur de boucles Foreach](control-flow/foreach-loop-container.md) . Pour en savoir plus sur la façon de le configurer, consultez [Configurer un conteneur de boucles Foreach](../../2014/integration-services/configure-a-foreach-loop-container.md).  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Le [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] didacticiel Création d’un package ETL simple, comprend une leçon qui vous apprend à ajouter et configurer une boucle foreach.  
  
## <a name="options"></a>Options  
 **Variable**  
 Sélectionnez une variable existante ou cliquez sur \< **nouvelle variable...**> pour créer une variable.  
  
> [!NOTE]  
>  Après avoir mappé une variable, une nouvelle ligne s’ajoute automatiquement à la liste **Variable**.  
  
 **Rubriques connexes**: [Integration Services &#40;les variables de&#41; SSIS](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md)  
  
 **Évaluer**  
 Si vous utilisez l'énumérateur Foreach Item, indiquez l'index de la colonne de la valeur de la collection à mapper à la variable. Pour les autres types d'énumérateur, l'index est en lecture seule.  
  
> [!NOTE]  
>  L'index commence à 0.  
  
 **Rubriques connexes**: parcourir [les fichiers et les tables Excel en utilisant un conteneur de boucles Foreach](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
 **Supprimer**  
 Sélectionnez une variable, puis cliquez sur **Supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de boucle foreach &#40;page général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur de boucle foreach &#40;page de collection&#41;](../../2014/integration-services/foreach-loop-editor-collection-page.md)   
 [Page Expressions](expressions/expressions-page.md)   
 [Conteneur de boucles For](control-flow/for-loop-container.md)  
  
  
