---
title: Assistant Conversion de projet de Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.migrationwizard.f1
ms.assetid: a192b094-4d0f-4c21-b911-460ec844a49f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9c077fdb85612c5e3f574d9d0236b07f149b9c3a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66057977"
---
# <a name="integration-services-project-conversion-wizard"></a>Assistant Conversion de projet Integration Services
  
  **L’Assistant Conversion de projet Integration Services** convertit un projet en modèle de déploiement de projet.  
  
> [!NOTE]  
>  Si le projet contient une ou plusieurs sources de données, les sources de données sont supprimées à l’issue de la conversion du projet. Pour créer une connexion à une source de données pouvant être partagée par les packages du projet, ajoutez un gestionnaire de connexions au niveau du projet. Pour plus d’informations, consultez [Ajouter, supprimer ou partager un gestionnaire de connexions dans un package](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md).  
  
 **Que voulez-vous faire ?**  
  
-   [Ouvrir l’Assistant Conversion de projet Integration Services](#open_dialog)  
  
-   [Définir les options sur la page localiser les packages](#locate)  
  
-   [Définir les options sur la page Sélectionner les packages](#selectPackages)  
  
-   [Définir les options sur la page Sélectionner la destination](#destination)  
  
-   [Définir les options sur la page spécifier les propriétés du projet](#projectProperties)  
  
-   [Définir les options sur la page mettre à jour la tâche d’exécution de package](#executePackage)  
  
-   [Définir les options sur la page Sélectionner les configurations](#configurations)  
  
-   [Définir les options sur la page créer des paramètres](#createParameters)  
  
-   [Définir les options sur la page Configurer les paramètres](#configureParameters)  
  
-   [Définir les options de la page vérifier](#review)  
  
-   [Définir les options de l’option effectuer la conversion](#conversion)  
  
##  <a name="open_dialog"></a>Ouvrir l’Assistant Conversion de projet Integration Services  
 Pour ouvrir l’Assistant **Conversion de projet Integration Services** , effectuez l’une des opérations suivantes.  
  
-   Ouvrez le projet dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puis dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et sélectionnez **Convertir en modèle de déploiement de projet**.  
  
-   Depuis l’Explorateur d’objets dans [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], cliquez avec le bouton droit sur le nœud **Projets** et sélectionnez **Importer les packages**.  
  
 Selon que vous exécutez **l’Assistant Conversion de projet Integration Services** à partir de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], l’Assistant effectue différentes tâches de conversion. Pour plus d’informations, consultez [Déployer des projets sur le serveur Integration Services](../../2014/integration-services/deploy-projects-to-integration-services-server.md).  
  
##  <a name="locate"></a>Définir les options sur la page localiser les packages  
  
> [!NOTE]  
>  La page **Localiser les packages** est disponible uniquement quand vous exécutez l’Assistant à partir de [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
 L’option suivante s’affiche dans la page quand vous sélectionnez **Système de fichiers** dans la liste déroulante **Source** . Sélectionnez cette option quand le package se trouve dans le système de fichiers.  
  
 **Folder**  
 Tapez le chemin d’accès du package ou accédez au package en cliquant sur **Parcourir**.  
  
 Les options suivantes s’affichent dans la page quand vous sélectionnez **Magasin de packages SSIS** dans la liste déroulante **Source**. Pour plus d’informations sur le magasin de packages, consultez [Gestion de packages &#40;Service SSIS&#41;](service/package-management-ssis-service.md).  
  
 **Serveur**  
 Tapez le nom du serveur ou sélectionnez ce dernier.  
  
 **Folder**  
 Tapez le chemin d’accès du package ou accédez au package en cliquant sur **Parcourir**.  
  
 Les options suivantes s’affichent dans la page quand vous sélectionnez **Microsoft SQL Server** dans la liste déroulante **Source** . Sélectionnez cette option quand le package se trouve dans Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 **Serveur**  
 Tapez le nom du serveur ou sélectionnez ce dernier.  
  
 **Utiliser l’authentification Windows**  
 Le mode d'authentification Microsoft Windows permet à l'utilisateur de se connecter au moyen d'un compte d'utilisateur Windows. Si vous utilisez l'authentification Windows, vous n'avez pas besoin de fournir un nom d'utilisateur ou un mot de passe.  
  
 **Utiliser l’authentification SQL Server**  
 Quand un utilisateur se connecte avec un nom d’accès et un mot de passe spécifiés à partir d’une connexion non autorisée, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] authentifie la connexion en vérifiant si un compte de connexion [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a été défini et si le mot de passe spécifié correspond à celui enregistré. Si [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne possède pas de compte de connexion, l'authentification échoue et un message d'erreur est envoyé à l'utilisateur.  
  
 **Nom d'utilisateur**  
 Spécifiez un nom d'utilisateur lorsque vous utilisez l'authentification SQL Server.  
  
 **Mot de passe**  
 Tapez le mot de passe lorsque vous utilisez l'authentification SQL Server.  
  
 **Folder**  
 Tapez le chemin d’accès du package ou accédez au package en cliquant sur **Parcourir**.  
  
##  <a name="selectPackages"></a>Définir les options sur la page Sélectionner les packages  
 **Nom du package**  
 Indique le fichier de package.  
  
 **État**  
 Indique si un package est prêt à être converti en modèle de déploiement de projet.  
  
 **Message**  
 Affiche un message associé au package.  
  
 **Mot de passe**  
 Affiche un mot de passe associé au package. Le texte du mot de passe est masqué.  
  
 **Appliquer à la sélection**  
 Cliquez pour appliquer le mot de passe de la zone de texte **Mot de passe** au(x) package(s) sélectionné(s).  
  
 **Actualiser**  
 Actualise la liste des packages.  
  
##  <a name="destination"></a>Définir les options sur la page Sélectionner la destination  
 Dans cette page, spécifiez le nom et le chemin d'accès d'un nouveau fichier de déploiement de projet (.ispac) ou sélectionnez un fichier existant.  
  
> [!NOTE]  
>  La page **Sélectionner la destination** est disponible uniquement quand vous exécutez l’Assistant à partir de [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
 **Chemin de sortie**  
 Tapez le chemin d’accès du fichier de déploiement ou accédez à ce dernier en cliquant sur **Parcourir**.  
  
 **Nom du projet**  
 Tapez le nom du projet.  
  
 **Niveau de protection**  
 Sélectionnez le niveau de protection. Pour plus d'informations, consultez [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md).  
  
 **Description du projet**  
 Tapez une description facultative du projet.  
  
##  <a name="projectProperties"></a>Définir les options sur la page spécifier les propriétés du projet  
  
> [!NOTE]  
>  La page **Spécifier les propriétés du projet** est disponible uniquement quand vous exécutez l’Assistant à partir de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 **Nom du projet**  
 Indique le nom du projet.  
  
 **Niveau de protection**  
 Sélectionnez le niveau de protection des packages contenus dans le projet. Pour plus d’informations sur les niveaux de protection, consultez [Contrôle d’accès pour les données sensibles présentes dans les packages](security/access-control-for-sensitive-data-in-packages.md).  
  
 **Description du projet**  
 Si vous le souhaitez, tapez une description du projet.  
  
##  <a name="executePackage"></a>Définir les options sur la page mettre à jour la tâche d’exécution de package  
 Mettez à jour les tâches d'exécution de package contenues dans les packages pour utiliser une référence basée sur un projet. Pour plus d'informations, consultez [Execute Package Task Editor](../../2014/integration-services/execute-package-task-editor.md).  
  
 **Package parent**  
 Indique le nom du package qui exécute le package enfant à l'aide de la tâche d'exécution de package.  
  
 **Nom de la tâche**  
 Indique le nom de la tâche d'exécution de package.  
  
 **Référence d’origine**  
 Indique le chemin d'accès actuel du package enfant.  
  
 **Affecter une référence**  
 Sélectionnez un package enfant stocké dans le projet.  
  
##  <a name="configurations"></a>Définir les options sur la page Sélectionner les configurations  
 Sélectionnez les configurations de package que vous souhaitez remplacer par des paramètres.  
  
 **Package**  
 Indique le fichier de package.  
  
 **Type**  
 Indique le type de configuration, par exemple un fichier de configuration XML.  
  
 **Chaîne de configuration**  
 Indique le chemin d'accès du fichier de configuration.  
  
 **État**  
 Affiche un message d'état pour la configuration. Cliquez sur le message pour afficher l'intégralité du texte du message.  
  
 **Ajouter des configurations**  
 Ajoutez les configurations de package contenues dans d'autres projets à la liste des configurations disponibles que vous souhaitez remplacer à l'aide de paramètres. Vous pouvez sélectionner des configurations stockées dans un système de fichiers ou dans SQL Server.  
  
 **Actualiser**  
 Cliquez pour actualiser la liste des configurations.  
  
 **Supprimer les configurations de tous les packages après la conversion**  
 Il est recommandé de supprimer toutes les configurations de projet en sélectionnant cette option.  
  
 Si vous ne sélectionnez pas cette option, seules les configurations que vous avez sélectionnées pour remplacement à l’aide de paramètres sont supprimées.  
  
##  <a name="createParameters"></a>Définir les options sur la page créer des paramètres  
 Sélectionnez le nom et l'étendue du paramètre pour chaque propriété de configuration.  
  
 **Package**  
 Indique le fichier de package.  
  
 **Nom du paramètre**  
 Indique le nom du paramètre.  
  
 **Étendue**  
 Sélectionnez l'étendue du paramètre, package ou projet.  
  
##  <a name="configureParameters"></a>Définir les options sur la page Configurer les paramètres  
 **Nom**  
 Indique le nom du paramètre.  
  
 **Étendue**  
 Indique l'étendue du paramètre.  
  
 **Valeur**  
 Indique la valeur du paramètre.  
  
 Cliquez sur le bouton de sélection en regard du champ de valeur pour configurer les propriétés du paramètre.  
  
 Dans la boîte de dialogue **Définir les détails du paramètre** , vous pouvez modifier la valeur de paramètre. Vous pouvez également spécifier si la valeur de paramètre doit être fournie lorsque vous exécutez le package.  
  
 Vous pouvez modifier la valeur dans la page **Paramètres** de la boîte de dialogue **Configurer** de [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]en cliquant sur le bouton Parcourir en regard du paramètre. La boîte de dialogue **Définir la valeur du paramètre** s’affiche.  
  
 La boîte de dialogue **Définir les détails du paramètre** indique également le type de données de la valeur de paramètre et l’origine du paramètre.  
  
##  <a name="review"></a>Définir les options de la page vérifier  
 Utilisez la page **Vérifier** pour confirmer l’exactitude des options sélectionnées pour la conversion du projet.  
  
 **Premier**  
 Cliquez pour modifier une option.  
  
 **Passer**  
 Cliquez pour convertir le projet en modèle de déploiement de projet.  
  
##  <a name="conversion"></a>Définir les options de l’option effectuer la conversion  
 La page Effectuer la conversion indique l'état de la conversion du projet.  
  
 **Action**  
 Indique une étape de conversion spécifique.  
  
 **Résultat**  
 Indique l'état de chaque étape de conversion. Pour plus d'informations, cliquez sur le message d'état.  
  
 La conversion de projet n'est pas enregistrée tant que le projet n'est pas enregistré dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 **Enregistrer le rapport**  
 Cliquez pour enregistrer un résumé de la conversion du projet dans un fichier .xml.  
  
## <a name="see-also"></a>Voir aussi  
 [Déployer des projets sur le serveur Integration Services](../../2014/integration-services/deploy-projects-to-integration-services-server.md)  
  
  
