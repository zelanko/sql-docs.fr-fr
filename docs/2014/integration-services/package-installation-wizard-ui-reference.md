---
title: Référence de l’interface utilisateur Assistant Installation de package | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.deploymentwizard.confirminstallation.f1
- sql12.dts.deploymentwizard.deploydtspackages.f1
- sql12.dts.deploymentwizard.selectinstfolder.f1
- sql12.dts.deploymentwizard.specifytargetsqlserver.f1
- sql12.dts.deploymentwizard.welcome.f1
- sql12.dts.deploymentwizard.finish.f1
- sql12.dts.deploymentwizard.configurepackages.f1
- sql12.dts.deploymentwizard.packagevalidation.f1
helpviewer_keywords:
- Package Installer Wizard
ms.assetid: 6fca44d9-5001-4644-bcf3-c2d10a674b97
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2f907127ff9863b696843a7d17e8df9950cd99c7
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66056829"
---
# <a name="package-installation-wizard-ui-reference"></a>Référence de l'interface utilisateur de l'Assistant Installation de package
  **L’Assistant Installation de package** permet de déployer un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], dont les packages et les divers fichiers qu’il contient, ainsi que les dépendances de package éventuelles.  
  
 Avant de déployer des packages, vous pouvez créer des configurations, puis déployer ces dernières avec les packages. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] utilise les configurations pour mettre à jour dynamiquement les propriétés des packages et les objets de package au moment de l’exécution. Par exemple, il est possible de définir dynamiquement à l'exécution la chaîne de connexion d'une connexion OLE DB en fournissant une configuration qui mappe une valeur avec la propriété contenant la chaîne de connexion.  
  
 Vous ne pouvez pas exécuter l'Assistant Installation de package tant que vous n'avez pas généré un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] et créé un utilitaire de déploiement. Pour plus d’informations, consultez [Déployer des packages à l’aide de l’utilitaire de déploiement](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md).  
  
 Les sections suivantes décrivent les pages de l’Assistant.  
  
## <a name="welcome-to-the-package-installation-wizard-page"></a>Page Assistant Installation de package  
 **L’Assistant Installation de package** vous permet de déployer un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] pour lequel vous avez créé un utilitaire de déploiement de package.  
  
 **Ne plus afficher cette page de démarrage**  
 Ignorer la page de démarrage à la prochaine exécution de l'Assistant.  
  
 **Suivant**  
 Permet de passer à la page suivante de l'Assistant.  
  
 **Terminer**  
 Passez directement à la page Fin de l'Assistant Installation de package. Utilisez cette option si vous êtes revenu en arrière dans les pages de l'Assistant pour examiner vos choix et si vous avez spécifié toutes les options obligatoires.  
  
## <a name="configure-packages-page"></a>Page Configurer les packages  
 Utilisez la page **Configurer les packages** pour modifier la configuration des packages.  
  
### <a name="options"></a>Options  
 **Fichier de configuration**  
 Modifie le contenu d'un fichier de configuration sélectionné dans la liste.  
  
 **Rubriques connexes :** [Créer des configurations de package](../../2014/integration-services/create-package-configurations.md)  
  
 **Chemin d'accès**  
 Affiche le chemin d'accès de la propriété à configurer.  
  
 **Type**  
 Affiche le type des données de la propriété.  
  
 **Valeur**  
 Spécifiez la valeur de la configuration.  
  
 **Suivant**  
 Permet de passer à la page suivante de l'Assistant.  
  
 **Terminer**  
 Passez directement à la page Fin de l'Assistant Installation de package. Utilisez cette option si vous êtes revenu en arrière dans les pages de l'Assistant pour examiner vos choix et si vous avez spécifié toutes les options obligatoires.  
  
## <a name="confirm-installation-page"></a>Page Confirmer l'installation  
 La page **Confirmer l’installation** permet de lancer l’installation de packages, de visualiser l’état et les informations que l’Assistant utilise pour installer les fichiers du projet spécifié.  
  
 **Suivant**  
 Installe les packages et leurs dépendances et passe à la page suivante de l'Assistant une fois l'installation terminée.  
  
 **État**  
 Affiche la progression de l'installation du package.  
  
 **Terminer**  
 Accédez à la page Fin de l'Assistant Installation de package. Utilisez cette option si vous êtes revenu en arrière dans les pages de l'Assistant pour revoir vos choix et si vous avez spécifié toutes les options indispensables.  
  
## <a name="deploy-ssis-packages-page"></a>Page Déployer les packages SSIS  
 La page **Déployer les packages SSIS** permet d’indiquer à quel emplacement les packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] et leurs dépendances doivent être installés.  
  
### <a name="options"></a>Options  
 **Déploiement sur le système de fichiers**  
 Déploie les packages et leurs dépendances dans un dossier du système de fichiers.  
  
 **Déploiement sur SQL Server**  
 Déploie les packages et leurs dépendances dans une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Utilisez cette option si [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] partage des packages entre serveurs. Toutes les dépendances de package sont installées dans le dossier spécifié du système de fichiers.  
  
 **Valider les packages après l'installation**  
 Indique si les packages doivent être validés après installation.  
  
 **Suivant**  
 Permet de passer à la page suivante de l'Assistant.  
  
 **Terminer**  
 Passez directement à la page Fin de l'Assistant Installation de package. Utilisez cette option si vous êtes revenu en arrière dans les pages de l'Assistant pour examiner vos choix et si vous avez spécifié toutes les options obligatoires.  
  
## <a name="packages-validation-page"></a>Page Validation des packages  
 La page **Validation des packages** permet d’afficher et de suivre la progression de la validation des packages et les résultats de cette validation.  
  
 **Suivant**  
 Permet de passer à la page suivante de l'Assistant.  
  
## <a name="select-installation-folder-page"></a>Page Sélectionner le dossier d'installation  
 La page **Sélectionner le dossier d’installation** permet de définir le dossier du système de fichiers dans lequel les packages et leurs dépendances sont installés.  
  
### <a name="options"></a>Options  
 **Dossier**  
 Définissez le chemin d'accès et le dossier de copie du package et de ses dépendances.  
  
 **Parcourir**  
 Accédez au dossier cible via la boîte de dialogue **Rechercher un dossier** .  
  
 **Suivant**  
 Permet de passer à la page suivante de l'Assistant.  
  
 **Terminer**  
 Passez directement à la page Fin de l'Assistant Installation de package. Utilisez cette option si vous voulez revenir dans les pages de l'Assistant pour vérifier vos choix et si vous avez défini toutes les options nécessaires.  
  
## <a name="specify-target-sql-server-page"></a>Page Spécifier le serveur SQL cible  
 La page **Spécifier le serveur SQL cible** permet de spécifier les options de déploiement du package dans une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
### <a name="options"></a>Options  
 **Nom du serveur**  
 Permet de spécifier le nom du serveur pour lequel doit s'effectuer le déploiement des packages.  
  
 **Utiliser l'authentification Windows**  
 Permet d'indiquer si la méthode d'authentification Windows doit être utilisée pour ouvrir une session sur le serveur. L'authentification Windows est recommandée pour renforcer la sécurité.  
  
 **Utiliser l'authentification SQL Server**  
 Permet d'indiquer si la méthode d'authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] doit être utilisée pour ouvrir une session sur le serveur. Si vous utilisez l’authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , vous devez fournir un nom d’utilisateur et un mot de passe.  
  
 **Nom d'utilisateur**  
 Indique un nom d'utilisateur.  
  
 **Mot de passe**  
 Permet de spécifier un mot de passe.  
  
 **Chemin d'accès au package**  
 Spécifiez le nom du dossier logique ou entrez « / » pour le dossier par défaut.  
  
 Pour sélectionner le dossier dans la boîte de dialogue **Package SSIS** , cliquez sur Parcourir (...). La boîte de dialogue ne fournit toutefois pas de moyen de sélectionner le dossier par défaut. Si vous souhaitez utiliser le dossier par défaut, vous devez entrer « / » dans la zone de texte.  
  
> [!NOTE]  
>  Si vous n’entrez pas de chemin de package valide, le message d’erreur suivant apparaît : « Un ou plusieurs arguments ne sont pas valides ».  
  
 **Se fier au serveur pour le chiffrement**  
 Permet d’utiliser les fonctionnalités de sécurité du [!INCLUDE[ssDE](../includes/ssde-md.md)] pour sécuriser les packages.  
  
 **Suivant**  
 Permet de passer à la page suivante de l'Assistant.  
  
 **Terminer**  
 Passez directement à la page Fin de l'Assistant Installation de package. Utilisez cette option si vous êtes revenu en arrière dans les pages de l'Assistant pour examiner vos choix et si vous avez spécifié toutes les options obligatoires.  
  
## <a name="finish-the-package-installation-page"></a>Page Fin de l'Assistant Installation de package  
 La page **Fin de l’Assistant Installation de package** permet d’obtenir un résumé des résultats de l’installation des packages. Cette page fournit des détails comme le nom du projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] déployé, les packages installés, les fichiers de configuration et l’emplacement de l’installation.  
  
 **Terminer**  
 Pour quitter l’Assistant, cliquez sur **Terminer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement du package &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md)  
  
  
