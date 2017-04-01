---
title: "&#201;diteur de transformation de recherche floue (onglet Table de r&#233;f&#233;rence) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.fuzzylookuptransformation.referencetable.f1"
helpviewer_keywords: 
  - "Éditeur de transformation de recherche floue"
ms.assetid: 451f4e7d-1c8e-4784-b540-df0806509bf1
caps.latest.revision: 35
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 35
---
# &#201;diteur de transformation de recherche floue (onglet Table de r&#233;f&#233;rence)
  Utilisez l’onglet **Table de référence** de la boîte de dialogue **Éditeur de transformation de recherche floue** pour définir la table source et l’index à utiliser pour la recherche. La source de données de référence doit être une table d’une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  La transformation de recherche floue crée une copie de travail de la table de référence. Les index décrits ci-dessous sont créés dans cette table de travail en utilisant une table spéciale et non un index [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] standard. La transformation ne modifie pas les tables sources existantes si vous ne sélectionnez pas **Conserver l’index stocké**. Dans ce cas, elle crée un déclencheur dans la table de référence qui met à jour la table de travail et la table d'index de recherche en fonction des modifications apportées à la table de référence.  
  
> [!NOTE]  
>  Les propriétés **Exhaustive** et **MaxMemoryUsage** de la transformation de recherche floue ne sont pas disponibles dans **l’Éditeur de transformation de recherche floue**, mais elles peuvent être définies à l’aide de **l’Éditeur avancé**. De plus, une valeur supérieure à 100 pour **MaxOutputMatchesPerInput** peut uniquement être spécifiée dans **l’Éditeur avancé**. Pour plus d’informations sur ces propriétés, consultez la section Transformation de recherche floue dans [Propriétés personnalisées des transformations](../../../integration-services/data-flow/transformations/transformation-custom-properties.md).  
  
 Pour en savoir plus sur la transformation de recherche floue, consultez [Fuzzy Lookup Transformation](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation.md).  
  
## Options  
 **Gestionnaire de connexions OLE DB**  
 Sélectionnez un gestionnaire de connexions OLE DB existant dans la liste ou créez une connexion en cliquant sur **Nouvelle**.  
  
 **Nouveau**  
 Crée une connexion en utilisant la boîte de dialogue **Configurer le gestionnaire de connexions OLE DB**.  
  
 **Créer un nouvel index**  
 Indiquez que la transformation doit créer un nouvel index à utiliser pour la recherche.  
  
 **Nom de la table de référence**  
 Sélectionnez la table existante à utiliser comme table de référence (recherche).  
  
 **Stocker un nouvel index**  
 Sélectionnez cette option pour enregistrer le nouvel index de recherche.  
  
 **Nom du nouvel index**  
 Si vous avez décidé d'enregistrer le nouvel index de recherche, tapez un nom descriptif.  
  
 **Conserver l'index stocké**  
 Si vous avez décidé d'enregistrer le nouvel index de recherche, indiquez si vous voulez également que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] conserve l'index.  
  
> [!NOTE]  
>  Quand vous sélectionnez **Conserver l’index stocké** sous l’onglet **Table de référence** de **l’Éditeur de transformation de recherche floue**, la transformation utilise des procédures stockées gérées pour tenir l’index à jour. Ces procédures stockées managées utilisent la fonctionnalité d’intégration du Common Language Runtime (CLR) dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Par défaut, l'intégration CLR dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est désactivée. Pour utiliser la fonctionnalité **Conserver l’index stocké**, vous devez activer l’intégration du CLR. Pour plus d’informations, consultez [Activation de l’intégration du CLR](../Topic/Enabling%20CLR%20Integration.md).  
>   
>  L’option **Conserver l’index stocké** nécessitant l’intégration du CLR, cette fonctionnalité n’est effective que quand vous sélectionnez une table de référence dans une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour laquelle l’intégration du CLR est activée.  
  
 **Utiliser l'index existant**  
 Indiquez que la transformation doit utiliser un index de recherche existant.  
  
 **Nom d'un index existant**  
 Dans la liste, sélectionnez un index de recherche existant.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de transformation de recherche floue &#40;onglet Colonnes&#41;](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-columns-tab.md)   
 [Éditeur de transformation de recherche floue &#40;onglet Avancé&#41;](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-advanced-tab.md)  
  
  