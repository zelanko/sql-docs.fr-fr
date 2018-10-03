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
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3fc54d5b287cd71ba303d34693e815c07b9cc3b4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48068073"
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
  
 **Rubriques connexes :** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md)  
  
 **Index**  
 Si vous utilisez l'énumérateur Foreach Item, indiquez l'index de la colonne de la valeur de la collection à mapper à la variable. Pour les autres types d'énumérateur, l'index est en lecture seule.  
  
> [!NOTE]  
>  L'index commence à 0.  
  
 **Rubriques connexes**: [parcourir les fichiers Excel et des Tables à l’aide d’un conteneur de boucles Foreach](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
 **Supprimer**  
 Sélectionnez une variable, puis cliquez sur **Supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de boucle foreach &#40;Page Général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur de boucle foreach &#40;Page de Collection&#41;](../../2014/integration-services/foreach-loop-editor-collection-page.md)   
 [Page expressions](expressions/expressions-page.md)   
 [Conteneur de boucles For](control-flow/for-loop-container.md)  
  
  
