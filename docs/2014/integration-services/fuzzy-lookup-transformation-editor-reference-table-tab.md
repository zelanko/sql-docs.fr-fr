---
title: Éditeur de Transformation de recherche floue (onglet Table de référence) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.referencetable.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: 451f4e7d-1c8e-4784-b540-df0806509bf1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4c9fb11308ae60cf061f184ade467d814d6a10fc
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66058305"
---
# <a name="fuzzy-lookup-transformation-editor-reference-table-tab"></a>Éditeur de transformation de recherche floue (onglet Table de référence)
  Utilisez l’onglet **Table de référence** de la boîte de dialogue **Éditeur de transformation de recherche floue** pour définir la table source et l’index à utiliser pour la recherche. La source de données de référence doit être une table d’une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  La transformation de recherche floue crée une copie de travail de la table de référence. Les index décrits ci-dessous sont créés dans cette table de travail en utilisant une table spéciale et non un index [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] standard. La transformation ne modifie pas les tables sources existantes si vous ne sélectionnez pas **Conserver l’index stocké**. Dans ce cas, elle crée un déclencheur dans la table de référence qui met à jour la table de travail et la table d'index de recherche en fonction des modifications apportées à la table de référence.  
  
> [!NOTE]  
>  Le `Exhaustive` et `MaxMemoryUsage` propriétés de la transformation de recherche floue ne sont pas disponibles dans le **éditeur de Transformation de recherche floue**, mais peut être définie à l’aide de la **éditeur avancé**. En outre, une valeur supérieure à 100 pour `MaxOutputMatchesPerInput` peut uniquement être spécifiée dans le **éditeur avancé**. Pour plus d’informations sur ces propriétés, consultez la section Transformation de recherche floue dans [Propriétés personnalisées des transformations](data-flow/transformations/transformation-custom-properties.md).  
  
 Pour en savoir plus sur la transformation de recherche floue, consultez [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Options  
 **Gestionnaire de connexions OLE DB**  
 Sélectionnez un gestionnaire de connexions OLE DB existant dans la liste ou créez une connexion en cliquant sur **Nouveau**.  
  
 **Nouveau**  
 Crée une connexion en utilisant la boîte de dialogue **Configurer le gestionnaire de connexions OLE DB** .  
  
 **Créer un nouvel index**  
 Indiquez que la transformation doit créer un nouvel index à utiliser pour la recherche.  
  
 **Nom de la table de référence**  
 Sélectionnez la table existante à utiliser comme table de référence (recherche).  
  
 **Stocker un nouvel index**  
 Sélectionnez cette option pour enregistrer le nouvel index de recherche.  
  
 **Nom du nouvel index**  
 Si vous avez décidé d'enregistrer le nouvel index de recherche, tapez un nom descriptif.  
  
 **Conserver l’index stocké**  
 Si vous avez décidé d'enregistrer le nouvel index de recherche, indiquez si vous voulez également que [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] conserve l'index.  
  
> [!NOTE]  
>  Quand vous sélectionnez **Conserver l’index stocké** sous l’onglet **Table de référence** de **l’Éditeur de transformation de recherche floue**, la transformation utilise des procédures stockées gérées pour tenir l’index à jour. Ces procédures stockées managées utilisent la fonctionnalité d’intégration du Common Language Runtime (CLR) dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Par défaut, l'intégration CLR dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est désactivée. Pour utiliser la fonctionnalité **Conserver l’index stocké** , vous devez activer l’intégration du CLR. Pour plus d’informations, consultez [Activation de l’intégration du CLR](../relational-databases/clr-integration/clr-integration-enabling.md).  
>   
>  L’option **Conserver l’index stocké** nécessitant l’intégration du CLR, cette fonctionnalité n’est effective que quand vous sélectionnez une table de référence dans une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour laquelle l’intégration du CLR est activée.  
  
 **Utiliser l'index existant**  
 Indiquez que la transformation doit utiliser un index de recherche existant.  
  
 **Nom d'un index existant**  
 Dans la liste, sélectionnez un index de recherche existant.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de transformation de recherche floue &#40;onglet Colonnes&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md)   
 [Éditeur de transformation de recherche floue &#40;onglet Avancé&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-advanced-tab.md)  
  
  
