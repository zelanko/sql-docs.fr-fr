---
title: Accorder des autorisations de base de données (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Analysis Services], full control
- full control permissions [Analysis Services]
ms.assetid: be7e5f64-af43-47d6-84a5-c5c1c277d644
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6bac9958c7b906a52b5b0d9d28a37c31d280b836
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62726059"
---
# <a name="grant-database-permissions-analysis-services"></a>Octroyer des autorisations de base de données (Analysis Services)
  Si vous débutez dans l'administration des bases de données Analysis Services avec une expérience des bases de données relationnelles, la première chose que vous devez comprendre est qu'en termes d'accès aux données, la base de données n'est pas l'objet sécurisable principal dans Analysis Services.  
  
 La principale structure de requête dans Analysis Services est un cube (ou modèle tabulaire), avec des autorisations utilisateur définies sur ces objets spécifiques. Si on la compare au moteur de base de données relationnelle (dans lequel les connexions de base de données et les autorisations utilisateur, souvent `db_datareader`, sont définies sur la base de données proprement dite), une base de données Analysis Services est principalement un conteneur pour les principaux objets de requête dans un modèle de données. Si votre objectif immédiat consiste à activer l’accès aux données pour un cube ou modèle tabulaire, vous pouvez ignorer les autorisations de base de données pour l’instant et passer directement à cette rubrique : [Accorder des autorisations de cube ou modèle &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md).  
  
 Les autorisations de base de données dans Analysis Services activent des fonctions d'administration, soit d'un point de vue global (comme c'est le cas avec l'autorisation de base de données Contrôle total), soit de nature plus granulaire si vous déléguez des opérations de traitement. La définition des niveaux d’autorisation pour une base de données Analysis Services s’effectue dans le volet **Général** de la boîte de dialogue **Créer un rôle** , illustrée et décrite ci-dessous.  
  
 Il n'existe aucune connexion dans Analysis Services. Vous créez simplement des rôles et assignez des comptes Windows dans le volet **Appartenance** . Tous les utilisateurs, y compris les administrateurs, se connectent à Analysis Services à l'aide d'un compte Windows.  
  
 ![Rôle de boîte de dialogue affichant les autorisations CREATE database](../media/ssas-permsdbrole.png "rôle boîte de dialogue affichant les autorisations Create database")  
  
 Trois types d'autorisations sont spécifiés au niveau de la base de données.  
  
 **Contrôle total (Administrateur)** : Contrôle total est une autorisation complète qui permet de disposer de capacités étendues sur une base de données Analysis Services, telles que la capacité à interroger ou à traiter tout objet de la base de données et à gérer la sécurité des rôles. Contrôle total est synonyme de statut d'administrateur de base de données. Lorsque vous sélectionnez `Full Control`, les autorisations `Process Database` et `Read Definition` sont également sélectionnées et ne peuvent pas être supprimées.  
  
> [!NOTE]  
>  Les administrateurs de serveur (membres du rôle Administrateur du serveur) disposent également d'un Contrôle total implicite sur chaque base de données du serveur.  
  
 `Process Database` Obtenir cette autorisation permet de déléguer le traitement au niveau de la base de données. En tant qu'administrateur, vous pouvez vous décharger de cette tâche en créant un rôle qui permet à une autre personne ou à un autre service d'exécuter des opérations de traitement pour tout objet de la base de données. En guise d'alternative, vous pouvez créer des rôles qui autorisent le traitement d'objets spécifiques. Pour plus d’informations, consultez [Octroyer des autorisations de traitement &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md) .  
  
 `Read Definition` Obtenir cette autorisation donne la possibilité de lire les métadonnées d’objet, sans toutefois pouvoir afficher les données associées. En général, on l'utilise dans les rôles créés pour le traitement dédié, en ajoutant la capacité à utiliser des outils tels que [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] ou [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] pour traiter une base de données de manière interactive. Sans `Read Definition`, l'autorisation `Process Database` est efficace uniquement dans les scénarios scriptés. Si vous prévoyez d'automatiser le traitement, par exemple grâce à SSIS ou un autre planificateur, vous souhaiterez probablement créer un rôle qui a `Process Database` sans `Read Definition`. Sinon, vous pouvez combiner les deux propriétés dans le même rôle pour prendre en charge le traitement interactif et sans assistance via les outils SQL Server qui visualisent le modèle de données dans une interface utilisateur.  
  
## <a name="full-control-administrator-permissions"></a>Autorisations Contrôle total (Administrateur)  
 Dans [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], un administrateur de base de données est toute identité utilisateur Windows assignée à un rôle qui comprend des autorisations Contrôle total (Administrateur). Un administrateur de base de données peut effectuer toute tâche dans la base de données, y compris les suivantes :  
  
-   traiter des objets ;  
  
-   lire des données et des métadonnées pour tous les objets de la base de données, y compris les cubes, dimensions, groupes de mesures, perspectives et modèles d'exploration de données ;  
  
-   créer ou modifier des rôles de base de données en ajoutant des utilisateurs ou des autorisations, y compris en ajoutant des utilisateurs à des rôles qui disposent également d'autorisations Contrôle total ;  
  
-   supprimer des rôles de base de données ou des appartenances aux rôles ;  
  
-   enregistrer des assemblys (ou procédures stockées) pour la base de données.  
  
 Notez qu'un administrateur de base de données ne peut pas ajouter ou supprimer de bases de données sur le serveur, ni accorder de droits d'administrateur à d'autres bases de données sur le même serveur. Ce privilège appartient uniquement aux administrateurs du serveur. Consultez [accorder des autorisations administrateur du serveur &#40;Analysis Services&#41; ](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md) pour plus d’informations sur ce niveau d’autorisation.  
  
 Tous les rôles étant définis par l'utilisateur, nous vous recommandons de créer un rôle dédié à cette fin (par exemple un rôle nommé « adminbd »), puis d'assigner des comptes d'utilisateurs et de groupes Windows en conséquence.  
  
#### <a name="create-roles-in-ssms"></a>Créer des rôles dans SSMS  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connectez-vous à l’instance d’ [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], ouvrez le dossier **Bases de données** , sélectionnez une base de données, puis cliquez avec le bouton droit sur **Rôles** | **Nouveau rôle**.  
  
2.  Dans le volet **Général** , entrez un nom tel que DBAdmin.  
  
3.  Cochez la case **Contrôle total (Administrateur)** pour le cube. Notez que `Process Database` et `Read Definition` sont sélectionnées automatiquement. Ces deux autorisations sont toujours incluses dans les rôles qui comprennent `Full Control`.  
  
4.  Dans le volet **Appartenance** , entrez les comptes d'utilisateurs et de groupes Windows qui se connectent à Analysis Services à l'aide de ce rôle.  
  
5.  Cliquez sur **OK** pour terminer la création du rôle.  
  
## <a name="process-database"></a>Traiter la base de données  
 Lorsque vous définissez un rôle qui accorde des autorisations de base de données, vous pouvez ignorer `Full Control` et choisir simplement `Process Database`. Cette autorisation, définie au niveau de la base de données, permet de traiter tous les objets dans la base de données. Pour plus d’informations, consultez [Grant process permissions &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md)  
  
## <a name="read-definition"></a>Lire la définition  
 Comme `Process Database`, la définition `Read Definition` autorisations au niveau de la base de données a un effet en cascade sur d’autres objets dans la base de données. Si vous souhaitez définir des autorisations Lire la définition à un niveau plus granulaire, vous devez effacer Lire la définition comme propriété de base de données dans le volet Général. Pour plus d’informations, consultez [Octroyer des autorisations Lire la définition sur des métadonnées d’objets &#40;Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Accorder des autorisations administrateur du serveur &#40;Analysis Services&#41;](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md)   
 [Octroyer des autorisations de traitement &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md)  
  
  
