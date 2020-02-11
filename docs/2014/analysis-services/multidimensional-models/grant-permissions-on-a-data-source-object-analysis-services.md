---
title: Accorder des autorisations sur un objet de source de données (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.roledesignerdialog.datasources.f1
helpviewer_keywords:
- read/write permissions
- user access rights [Analysis Services], data sources
- security [Analysis Services], data sources
- connection strings [Analysis Services]
- data sources [Analysis Services], security
ms.assetid: b4e302d3-c93b-4383-aa4a-37d15c129830
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4a869d2033adaa57be0ace522787332c03a69bcb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66075000"
---
# <a name="grant-permissions-on-a-data-source-object-analysis-services"></a>Octroyer des autorisations sur un objet de source de données (Analysis Services)
  Généralement, la plupart des utilisateurs d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] n'ont pas besoin d'accéder aux sources de données d'un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . D'ordinaire, les utilisateurs interrogent simplement les données d'une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Toutefois, dans le contexte de l'exploration de données, lors de l'exécution de prévisions en fonction d'un modèle d'exploration, par exemple, l'utilisateur doit joindre les données connues d'un modèle d'exploration de données avec les données fournies par l'utilisateur. Pour se connecter à la source de données qui contient les données fournies par l’utilisateur, celui-ci doit utiliser une requête DMX (Data Mining Extensions) qui contient la clause [OPENQUERY &#40;DMX&#41;](/sql/dmx/source-data-query-openquery) ou la clause [OPENROWSET &#40;DMX&#41;](/sql/dmx/source-data-query-openrowset).  
  
 Pour exécuter une requête DMX qui se connecte à une source de données, l’utilisateur doit avoir accès à l’objet de source de données dans la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Par défaut, seuls les administrateurs du serveur et les administrateurs de base de données ont accès aux objets source de données. Cela signifie qu'un utilisateur ne peut pas accéder à un objet source de données à moins que l'administrateur ne lui en accorde l'autorisation.  
  
> [!IMPORTANT]  
>  Pour des raisons de sécurité, la soumission de requêtes DMX à l’aide d’une chaîne de connexion ouverte dans la clause OPENROWSET est désactivée.  
  
## <a name="set-read-permissions-to-a-data-source"></a>Définir des autorisations de lecture sur une source de données  
 Un rôle de base de données peut ne pas être autorisé à accéder à un objet source de données ou peut bénéficier d'autorisations de lecture.  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à l' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]instance de, développez **rôles** pour la base de données appropriée dans l’Explorateur d’objets, puis cliquez sur un rôle de base de données (ou créez un rôle de base de données).  
  
2.  Dans le volet **Accès à la source de données** , recherchez l’objet source de données dans la liste **Source de données** , puis sélectionnez **Lecture** dans la liste **Accès** de la source de données. Si cette option n’est pas disponible, consultez le volet **Général** pour savoir si Contrôle total est sélectionné. Contrôle total fournit déjà cette autorisation ; vous ne pouvez pas remplacer les autorisations sur la source de données.  
  
## <a name="working-with-the-connection-string-used-by-a-data-source-object"></a>Utilisation de la chaîne de connexion utilisée par un objet de source de données  
 L'objet de source de données contient la chaîne de connexion utilisée pour se connecter à la source de données sous-jacente. Cette chaîne de connexion peut spécifier l'un des éléments suivants :  
  
-   **Spécifier un nom d’utilisateur et un mot de passe**  
  
     Si la chaîne de connexion qu'utilise un objet de source de données définit un nom d'utilisateur et un mot de passe, vous pouvez créer plusieurs objets de source de données ayant chacun un compte d'utilisateur différent. La création de plusieurs objets de source de données permet aux utilisateurs d'accéder à certains objets de source de données et d'empêcher ces utilisateurs d'accéder à d'autres objets de source de données. Ces derniers peuvent être utilisés par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour traiter des objets, tels que des cubes et des modèles d’exploration.  
  
-   **Spécifier l’authentification Windows**  
  
     Si la chaîne de connexion qu'utilise un objet source de données spécifie l'authentification Windows, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] doit pouvoir emprunter l'identité du client. Si la source de données se trouve sur un ordinateur distant, les deux ordinateurs doivent être approuvés pour l'emprunt d'identité en utilisant l'authentification Kerberos, sinon la requête échoue. Pour plus d’informations, consultez [Configurer Analysis Services pour la délégation contrainte Kerberos](../instances/configure-analysis-services-for-kerberos-constrained-delegation.md) .  
  
     Si le client n’autorise pas l’emprunt d’identité (via la propriété Impersonation Level dans OLE DB et d’autres composants du client), [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tente de se connecter de manière anonyme à la source de données sous-jacente. Les connexions anonymes aux sources de données distantes réussissent rarement, car la plupart des sources de données n'acceptent pas les connexions anonymes.  
  
## <a name="see-also"></a>Voir aussi  
 [Sources de données dans les modèles multidimensionnels](data-sources-in-multidimensional-models.md)   
 [Propriétés de la chaîne de connexion &#40;Analysis Services&#41;](../instances/connection-string-properties-analysis-services.md)   
 [Méthodologies d’authentification prises en charge par Analysis Services](../instances/authentication-methodologies-supported-by-analysis-services.md)   
 [Accorder un accès personnalisé à des données de dimension &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md)   
 [Octroi d’autorisations de cube ou de modèle &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md)   
 [Accorder un accès personnalisé à des données de cellule &#40;Analysis Services&#41;](grant-custom-access-to-cell-data-analysis-services.md)  
  
  
