---
title: Éditeur de boucle foreach (Page mappage de variables) | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.mapping.f1
ms.assetid: aa847b87-f391-48a5-9849-eeda2d6b00b9
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f2d95909e76c6b5c3665926783fb42ff247d1ba9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894057"
---
# <a name="foreach-loop-editor-variable-mappings-page"></a>Éditeur de boucle Foreach (page Mappage de variables)
  Utilisez la page **Mappage de variables** de la boîte de dialogue **Éditeur de boucle Foreach** pour mapper les variables à la valeur de la collection. La valeur de cette variable est mise à jour avec les valeurs de la collection à chaque itération de la boucle.  
  
 Pour en savoir plus sur l’utilisation du conteneur de boucles Foreach dans un package Integration Services, consultez [Conteneur de boucles Foreach](control-flow/foreach-loop-container.md) . Pour en savoir plus sur la façon de le configurer, consultez [Configurer un conteneur de boucles Foreach](../../2014/integration-services/configure-a-foreach-loop-container.md).  
  
 Le didacticiel « Création d’un package ETL simple » de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] inclut une leçon sur l’ajout et la configuration d’une boucle Foreach.  
  
## <a name="options"></a>Options  
 **Variable**  
 Sélectionnez une variable existante ou cliquez sur \<**Nouvelle variable...**> pour en créer une.  
  
> [!NOTE]  
>  Après avoir mappé une variable, une nouvelle ligne s’ajoute automatiquement à la liste **Variable**.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md)  
  
 **Index**  
 Si vous utilisez l'énumérateur Foreach Item, indiquez l'index de la colonne de la valeur de la collection à mapper à la variable. Pour les autres types d'énumérateur, l'index est en lecture seule.  
  
> [!NOTE]  
>  L'index commence à 0.  
  
 **Rubriques connexes :** [Effectuer une boucle dans des fichiers et des tables Excel en utilisant un conteneur de boucles Foreach](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
 **Supprimer**  
 Sélectionnez une variable, puis cliquez sur **Supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de boucle foreach &#40;Page Général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur de boucle foreach &#40;Page de Collection&#41;](../../2014/integration-services/foreach-loop-editor-collection-page.md)   
 [Page Expressions](expressions/expressions-page.md)   
 [Conteneur de boucles For](control-flow/for-loop-container.md)  
  
  
