---
title: Grant autorisations Lire la définition des métadonnées d’objet (Analysis Services) | Microsoft Docs
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
- metadata [Analysis Services]
- permissions [Analysis Services], read metadata
- read metadata permissions
ms.assetid: c857e48e-64b0-4ffe-900d-a0a3ddafcefb
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f87b088072350e58aa00d7c0063a2aa2378346cb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241729"
---
# <a name="grant-read-definition-permissions-on-object-metadata-analysis-services"></a>Octroyer des autorisations Lire la définition sur des métadonnées d'objets (Analysis Services)
  L'autorisation de lire une définition d'objets ou des métadonnées sur des objets sélectionnés permet à un administrateur d'accorder l'autorisation d'afficher des informations sur les objets sans accorder l'autoriser de modifier les définitions des objets, modifier la structure des objets ou afficher les données des objets. `Read Definition` autorisations peuvent être accordées à la base de données source de données, dimension, structure d’exploration de données et les niveaux de modèle d’exploration de données. Si vous avez besoin `Read Definition` autorisations pour un cube, vous devez activer `Read Definition` pour la base de données. N’oubliez pas que les autorisations sont additives. Par exemple, imaginez qu'un rôle accorde l'autorisation de lire les métadonnées d'un cube tandis qu'un second rôle accorde au même utilisateur l'autorisation de lire les métadonnées d'une dimension. Les autorisations des deux rôles se combinent et permettent à l'utilisateur de lire les métadonnées du cube et celles de la dimension dans cette base de données.  
  
> [!NOTE]  
>  L'autorisation de lire les métadonnées d'une base de données est l'autorisation minimale nécessaire pour se connecter à une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en utilisant [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ou [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Un utilisateur autorisé à lire les métadonnées peut également utiliser l’ensemble de lignes de schéma DISCOVER_XML_METADATA pour exécuter une requête sur l’objet et afficher ses métadonnées. Pour plus d’informations, consultez [Ensemble de lignes DISCOVER_XML_METADATA](../schema-rowsets/xml/discover-xml-metadata-rowset.md).  
  
## <a name="set-read-definition-permissions-on-a-database"></a>Définir des autorisations Lire la définition sur une base de données  
 Le fait d'accorder l'autorisation de lire des métadonnées de base de données accorde également l'autorisation de lire les métadonnées de tous les objets dans la base de données.  
  
 Nous vous suggérons d’inclure le `Read Definition` autorisation au niveau de la base de données chaque fois que vous configurez des rôles pour le traitement dédié. Avoir `Read Definition` permet des non-administrateurs à afficher la hiérarchie des objets d’un modèle dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et accéder à des objets pour un traitement ultérieur.  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à l’instance d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], développez **Rôles** pour la base de données appropriée dans l’Explorateur d’objets, puis cliquez sur un rôle de base de données (ou créez un rôle de base de données).  
  
2.  Sur le **général** onglet, sélectionnez le `Read Definition` option.  
  
3.  Dans le volet **Appartenance** , entrez les comptes d'utilisateurs et de groupes Windows qui se connectent à Analysis Services à l'aide de ce rôle.  
  
4.  Cliquez sur **OK** pour terminer la création du rôle.  
  
## <a name="set-read-definition-permissions-on-individual-objects"></a>Définir des autorisations Lire la définition sur des objets spécifiques  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à l’instance d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], ouvrez le dossier **Bases de données** , sélectionnez une base de données, développez **Rôles** pour la base de données appropriée dans l’Explorateur d’objets, puis cliquez sur un rôle de base de données (ou créez-en un).  
  
2.  Dans le **général** volet, désactivez l’autorisation de base de données pour `Read Definition`. Cette étape permet de supprimer l'héritage des autorisations afin que vous puissiez définir des autorisations sur des objets spécifiques.  
  
3.  Sélectionnez l’objet pour lequel vous spécifiez `Read Definition` propriétés :  
  
    -   Dans le **des Sources de données** volet, cliquez sur le `Read Definition` case à cocher pour cette source de données. Les membres du rôle peuvent afficher la chaîne de connexion à la source de données, y compris le nom du serveur et éventuellement le nom d'utilisateur. Cette autorisation est disponible pour le cas où vous souhaiteriez fournir des informations sur la chaîne de connexion sans accorder également l'autorisation de modifier la chaîne de connexion ou d'afficher les définitions d'autres objets.  
  
    -   Dans le **Dimensions** volet, cliquez sur le `Read Definition` case à cocher pour cette dimension. Les analystes et développeurs expérimentés devront peut-être afficher la définition sans être autorisé à la modifier ou afficher les définitions d'autres objets (tels que d'autres dimensions, objets de cube ou modèles et structures d'exploration de données).  
  
    -   Dans le volet des Structures d’exploration de données, cliquez sur le `Read Definition` case à cocher pour les modèles ou structures d’exploration de données. `Read Definition` est requis pour parcourir le modèle de données. Pour plus d’informations, consultez [Octroyer des autorisations sur des modèles et des structures d’exploration de données &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md).  
  
4.  Dans le volet **Appartenance** , entrez les comptes d'utilisateurs et de groupes Windows qui se connectent à Analysis Services à l'aide de ce rôle.  
  
5.  Cliquez sur **OK** pour terminer la création du rôle.  
  
## <a name="see-also"></a>Voir aussi  
 [Accorder des autorisations de base de données &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md)   
 [Accorder des autorisations de processus &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md)  
  
  
