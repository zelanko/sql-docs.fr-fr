---
title: Créer une Dimension à l’aide d’une Table existante | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], dimensions
- main dimension tables
- dimensions [Analysis Services], standard
- standard dimensions [Analysis Services]
ms.assetid: edd96fbe-1b1c-445a-95d6-7a025e0ee868
caps.latest.revision: 52
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9ff912d4c828efec8bacd163ae6b47f980a94beb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37319249"
---
# <a name="create-a-dimension-by-using-an-existing-table"></a>Créer une dimension à l'aide d'une table existante
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous pouvez utiliser l'Assistant Dimension de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] pour créer une dimension à partir d'une table existante. Pour cela, sélectionnez l’option **Utiliser une table existante** de la page **Sélectionner la méthode de création** de l’Assistant. Si vous sélectionnez cette option, l'Assistant base la structure de la dimension sur les tables de dimension, leurs colonnes et toutes les relations entre ces colonnes d'une vue de source de données existante. L'Assistant échantillonne des données dans la table source et les tables associées. Il utilise ces données pour définir des colonnes d’attributs basées sur les colonnes dans les tables de dimension et pour définir des hiérarchies d’attributs (nommées hiérarchies *définies par l’utilisateur* ). Une fois que vous avez utilisé l'Assistant Dimension pour créer votre dimension, vous pouvez utiliser le Concepteur de dimensions pour ajouter, supprimer et configurer des attributs et des hiérarchies dans la dimension.  
  
 Lorsque vous utilisez une table existante pour créer une dimension, l'Assistant Dimension vous guide à travers les étapes suivantes :  
  
-   Spécification des informations sur la source  
  
-   Sélection de tables associées  
  
-   Sélection des attributs de dimension  
  
-   Définition de l’intelligence comptable  
  
> [!NOTE]  
>  Pour les instructions détaillées qui correspondent aux informations présentées dans cette rubrique, consultez [Créer une dimension à l’aide de l’Assistant Dimension](create-a-dimension-using-the-dimension-wizard.md).  
  
## <a name="specifying-the-source-information"></a>Spécification des informations sur la source  
 Vous spécifiez les informations de source dans la page **Spécifier des informations sur la source** . Vous commencez ce processus en sélectionnant la vue de source de données qui contient la table sur laquelle vous souhaitez baser la dimension. Vous spécifiez ensuite la table de dimension principale pour la dimension que vous définissez. La table de dimension principale est la table qui est directement liée à la table de faits. Par exemple, spécifiez une table Product comme table principale pour une dimension Products ou une table Employee pour une dimension Employees. L'Assistant sélectionne automatiquement une colonne clé qui est basée sur la clé primaire dans la vue de source de données. Toutefois, vous pouvez modifier la colonne clé si nécessaire. La colonne clé détermine les membres de la dimension. Par exemple, spécifiez ProductKey comme colonne clé d'une dimension Product.  
  
 Vous pouvez éventuellement définir une colonne qui contient le nom du membre. Par défaut, le nom de membre qui s'affiche est la valeur de la colonne clé. Les valeurs d'une colonne clé (comme ProductID ou EmployeeID) sont souvent des clés uniques générées par le système qui ne signifient rien pour l'utilisateur. Vous pouvez souvent fournir des informations plus explicites à l'utilisateur si vous modifiez le nom que les utilisateurs peuvent voir en une valeur correspondante dans une autre colonne de la dimension. Par exemple, vous pouvez définir une colonne des noms de membre qui contient des noms de produits ou d'employés. Si vous modifiez le nom de membre, les utilisateurs voient un plus nom descriptif, mais les requêtes utilisent toujours les valeurs de colonne clé pour faire correctement la distinction entre les membres qui partagent le même nom. Si vous spécifiez une clé composite pour la colonne clé, vous devez également spécifier la colonne qui fournit les valeurs de membre pour l'attribut de clé. Pour plus d’informations sur la configuration des propriétés d’attributs, consultez [Référence des propriétés d’attribut de dimension](dimension-attribute-properties-reference.md).  
  
## <a name="selecting-related-tables"></a>Sélection de tables associées  
  
> [!NOTE]  
>  L'Assistant ignore cette étape s'il n'existe aucune relation entre la table principale de la dimension dans la vue de source de données et les autres tables de la dimension.  
  
 Si vous générez une dimension en flocon, spécifiez les tables associées à partir desquelles des attributs supplémentaires seront définis dans la page **Sélectionner les tables associées** . Par exemple, si vous générez une dimension de clients dans laquelle vous souhaitez définir une table de zone géographique du client, vous pouvez définir une table de géographie en tant que table associée.  
  
## <a name="selecting-dimension-attributes"></a>Sélection des attributs de dimension  
 Après avoir sélectionné les tables de dimension, utilisez la page **Sélectionner les attributs de la dimension** pour sélectionner les attributs que vous souhaitez inclure dans la dimension à partir de ces tables. Toutes les colonnes sous-jacentes de toutes ces tables sont disponibles comme attributs de dimension potentiels. L'attribut de clé de la dimension doit être sélectionné et activé pour l'exploration.  
  
 Par défaut, l'Assistant affecte la valeur `Regular` au type d'un attribut. Toutefois, vous souhaiterez peut-être mapper des attributs spécifiques sur un autre type d'attribut qui représente mieux les données. Par exemple, la table dbo.DimAccount dans l'exemple de base de données DW [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] contient une colonne AccountCodeAlternateKey qui fournit le numéro de compte. Au lieu de définir le type `Regular` pour cet attribut, vous pouvez souhaiter mapper cet attribut à la `Account Number` type.  
  
> [!NOTE]  
>  Si le type de dimension et les types d'attribut standard ne sont pas définis lorsque vous créez la dimension, utilisez l'Assistant Business Intelligence pour définir ces valeurs après avoir créé la dimension. Pour plus d’informations, consultez [Ajouter de l’intelligence de dimensions à une dimension](bi-wizard-add-dimension-intelligence-to-a-dimension.md) ou (pour une dimension de type Comptes) [Ajouter de l’intelligence comptable à une dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
 L'Assistant définit automatiquement le type de dimension en fonction des types d'attribut spécifiés. Les types d’attributs spécifiés dans l’Assistant définissent la `Type` propriété pour les attributs. Les paramètres de la propriété `Type` pour la dimension et ses attributs fournissent des informations sur le contenu d'une dimension aux applications serveur et clientes. Dans certains cas, ces `Type` uniquement, les paramètres de propriété fournissent des conseils pour les applications clientes et sont facultatifs. Dans les autres cas, comme pour les comptes, d’heure ou de devise dimensions, ces `Type` les paramètres de propriété déterminent un comportement serveur spécifique et peuvent être nécessaires pour implémenter certains comportements du cube.  
  
 Pour plus d’informations sur les types de dimensions et d’attributs, consultez [Types de dimension](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md), [Configurer des types d’attributs](attribute-properties-configure-attribute-types.md).  
  
## <a name="defining-account-intelligence"></a>Définition de l’intelligence comptable  
  
> [!NOTE]  
>  L’Assistant Dimension affiche cette étape uniquement si vous avez défini un attribut de dimension **Type de compte** dans la page **Sélectionner les attributs de la dimension** de l’Assistant.  
  
 La page **Définir l’intelligence comptable** permet de créer une dimension de type Compte. Si vous créez une dimension de type Compte, vous devez mapper les types de compte standard pris en charge par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] aux membres de l’attribut de type compte de la dimension. Le serveur utilise ces mappages pour fournir des fonctions d'agrégation et des alias différents pour chaque type de données de compte.  
  
 Pour mapper ces types de compte, l'Assistant fournit une table avec les colonnes suivantes :  
  
-   La colonne **Types de comptes de la table source** répertorie les types de comptes à partir de la table de source de données.  
  
-   La colonne **Types de comptes intégrés** répertorie les types de compte standard correspondant pris en charge par le serveur. Si les données sources utilisent des noms standard, l’Assistant mappe automatiquement le type de source sur le type de serveur et remplit la colonne **Types de comptes intégrés** avec ces informations. Si le serveur ne mappe pas les types de compte ou que vous souhaitez modifier le mappage, sélectionnez un autre type dans la liste de la colonne **Types de comptes intégrés** .  
  
> [!NOTE]  
>  Si les types de compte ne sont pas mappés lorsque l'Assistant crée une dimension de comptes, utilisez l'Assistant Business Intelligence pour configurer ces mappages après avoir créé la dimension. Pour plus d’informations, consultez [Ajouter de l’intelligence comptable à une dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
## <a name="completing-the-wizard"></a>Fin de l'Assistant  
 L'Assistant analyse les tables de dimension pour détecter les relations. L'Assistant créera automatiquement des relations d'attributs entre les attributs de clé dans les dimensions en flocon.  
  
 L'Assistant détecte également automatiquement si une relation parent-enfant existe dans la dimension. Une relation parent-enfant existe lorsqu'un attribut parent fait référence à des membres de l'attribut clé de la dimension. Cette relation définit les relations hiérarchiques ainsi que les chemins d'agrégation entre les membres de nœud terminal de la dimension. Pour plus d’informations sur les hiérarchies parent-enfant, consultez [Attributs dans des hiérarchies de type parent-enfant](parent-child-dimension-attributes.md).  
  
 Dans la page **Fin de l’Assistant** , vous terminez l’Assistant en tapant un nom pour la nouvelle dimension et en examinant la structure de la dimension.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une Dimension en générant une Table Non temporelle dans la Source de données](create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md)   
 [Créer une Dimension de temps en générant une Table temporelle](create-a-time-dimension-by-generating-a-time-table.md)   
 [Dimension Attribute Properties Reference](dimension-attribute-properties-reference.md)   
 [Créer une Dimension de temps en générant une Table temporelle](create-a-time-dimension-by-generating-a-time-table.md)   
 [Créer une dimension en générant une table non temporelle dans la source de données](create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md)  
  
  
