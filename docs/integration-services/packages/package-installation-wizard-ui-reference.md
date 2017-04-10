---
title: "R&#233;f&#233;rence de l&#39;interface utilisateur de l&#39;Assistant Installation de package | Microsoft Docs"
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
  - "sql13.dts.deploymentwizard.welcome.f1"
  - "sql13.dts.deploymentwizard.confirminstallation.f1"
  - "sql13.dts.deploymentwizard.deploydtspackages.f1"
  - "sql13.dts.deploymentwizard.finish.f1"
  - "sql13.dts.deploymentwizard.configurepackages.f1"
  - "sql13.dts.deploymentwizard.selectinstfolder.f1"
  - "sql13.dts.deploymentwizard.packagevalidation.f1"
  - "sql13.dts.deploymentwizard.specifytargetsqlserver.f1"
helpviewer_keywords: 
  - "Assistant Installation de package"
ms.assetid: 6fca44d9-5001-4644-bcf3-c2d10a674b97
caps.latest.revision: 24
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 24
---
# R&#233;f&#233;rence de l&#39;interface utilisateur de l&#39;Assistant Installation de package
  **L’Assistant Installation de package** permet de déployer un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], dont les packages et les divers fichiers qu’il contient, ainsi que les dépendances de package éventuelles.  
  
 Avant de déployer des packages, vous pouvez créer des configurations, puis déployer ces dernières avec les packages. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise les configurations pour mettre à jour dynamiquement les propriétés des packages et les objets de package au moment de l’exécution. Par exemple, il est possible de définir dynamiquement à l'exécution la chaîne de connexion d'une connexion OLE DB en fournissant une configuration qui mappe une valeur avec la propriété contenant la chaîne de connexion.  
  
 Vous ne pouvez pas exécuter l'Assistant Installation de package tant que vous n'avez pas généré un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et créé un utilitaire de déploiement. Pour plus d’informations, consultez [Déployer des packages à l’aide de l’utilitaire de déploiement](../../integration-services/packages/deploy-packages-by-using-the-deployment-utility.md).  
  
 Les sections suivantes décrivent les pages de l’Assistant.  
  
## Page Assistant Installation de package  
 **L’Assistant Installation de package** vous permet de déployer un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour lequel vous avez créé un utilitaire de déploiement de package.  
  
 **Ne plus afficher cette page de démarrage**  
 Ignorer la page de démarrage à la prochaine exécution de l'Assistant.  
  
 **Suivant**  
 Permet de passer à la page suivante de l'Assistant.  
  
 **Terminer**  
 Passez directement à la page Fin de l'Assistant Installation de package. Utilisez cette option si vous êtes revenu en arrière dans les pages de l'Assistant pour examiner vos choix et si vous avez spécifié toutes les options obligatoires.  
  
## Page Configurer les packages  
 Utilisez la page **Configurer les packages** pour modifier la configuration des packages.  
  
### Options  
 **Fichier de configuration**  
 Modifie le contenu d'un fichier de configuration sélectionné dans la liste.  
  
 **Rubriques connexes :** [Créer des configurations de package](../../integration-services/packages/create-package-configurations.md)  
  
 **Chemin d'accès**  
 Affiche le chemin d'accès de la propriété à configurer.  
  
 **Type**  
 Affiche le type des données de la propriété.  
  
 **Value**  
 Spécifiez la valeur de la configuration.  
  
 **Suivant**  
 Permet de passer à la page suivante de l'Assistant.  
  
 **Terminer**  
 Passez directement à la page Fin de l'Assistant Installation de package. Utilisez cette option si vous êtes revenu en arrière dans les pages de l'Assistant pour examiner vos choix et si vous avez spécifié toutes les options obligatoires.  
  
## Page Confirmer l'installation  
 La page **Confirmer l’installation** permet de lancer l’installation de packages, de visualiser l’état et les informations que l’Assistant utilise pour installer les fichiers du projet spécifié.  
  
 **Suivant**  
 Installe les packages et leurs dépendances et passe à la page suivante de l'Assistant une fois l'installation terminée.  
  
 **État**  
 Affiche la progression de l'installation du package.  
  
 **Terminer**  
 Accédez à la page Fin de l'Assistant Installation de package. Utilisez cette option si vous êtes revenu en arrière dans les pages de l'Assistant pour revoir vos choix et si vous avez spécifié toutes les options indispensables.  
  
## Page Déployer les packages SSIS  
 La page **Déployer les packages SSIS** permet d’indiquer à quel emplacement les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et leurs dépendances doivent être installés.  
  
### Options  
 **Déploiement sur le système de fichiers**  
 Déploie les packages et leurs dépendances dans un dossier du système de fichiers.  
  
 **Déploiement sur SQL Server**  
 Déploie les packages et leurs dépendances dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Utilisez cette option si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] partage des packages entre serveurs. Toutes les dépendances de package sont installées dans le dossier spécifié du système de fichiers.  
  
 **Valider les packages après l'installation**  
 Indique si les packages doivent être validés après installation.  
  
 **Suivant**  
 Permet de passer à la page suivante de l'Assistant.  
  
 **Terminer**  
 Passez directement à la page Fin de l'Assistant Installation de package. Utilisez cette option si vous êtes revenu en arrière dans les pages de l'Assistant pour examiner vos choix et si vous avez spécifié toutes les options obligatoires.  
  
## Page Validation des packages  
 La page **Validation des packages** permet d’afficher et de suivre la progression de la validation des packages et les résultats de cette validation.  
  
 **Suivant**  
 Permet de passer à la page suivante de l'Assistant.  
  
## Page Sélectionner le dossier d'installation  
 La page **Sélectionner le dossier d’installation** permet de définir le dossier du système de fichiers dans lequel les packages et leurs dépendances sont installés.  
  
### Options  
 **Dossier**  
 Définissez le chemin d'accès et le dossier de copie du package et de ses dépendances.  
  
 **Parcourir**  
 Accédez au dossier cible via la boîte de dialogue **Rechercher un dossier**.  
  
 **Suivant**  
 Permet de passer à la page suivante de l'Assistant.  
  
 **Terminer**  
 Passez directement à la page Fin de l'Assistant Installation de package. Utilisez cette option si vous voulez revenir dans les pages de l'Assistant pour vérifier vos choix et si vous avez défini toutes les options nécessaires.  
  
## Page Spécifier le serveur SQL cible  
 La page **Spécifier le serveur SQL cible** permet de spécifier les options de déploiement du package dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### Options  
 **Nom du serveur**  
 Permet de spécifier le nom du serveur pour lequel doit s'effectuer le déploiement des packages.  
  
 **Utiliser l'authentification Windows**  
 Permet d'indiquer si la méthode d'authentification Windows doit être utilisée pour ouvrir une session sur le serveur. L'authentification Windows est recommandée pour renforcer la sécurité.  
  
 **Utiliser l'authentification SQL Server**  
 Permet d'indiquer si la méthode d'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être utilisée pour ouvrir une session sur le serveur. Si vous utilisez l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous devez fournir un nom d’utilisateur et un mot de passe.  
  
 **Nom d'utilisateur**  
 Indique un nom d'utilisateur.  
  
 **Mot de passe**  
 Permet de spécifier un mot de passe.  
  
 **Chemin d'accès au package**  
 Spécifiez le nom du dossier logique ou entrez « / » pour le dossier par défaut.  
  
 Pour sélectionner le dossier dans la boîte de dialogue **Package SSIS**, cliquez sur Parcourir (...). La boîte de dialogue ne fournit toutefois pas de moyen de sélectionner le dossier par défaut. Si vous souhaitez utiliser le dossier par défaut, vous devez entrer « / » dans la zone de texte.  
  
> [!NOTE]  
>  Si vous n'entrez pas de chemin d'accès de package valide, le message d'erreur suivant apparaît : « Un ou plusieurs arguments ne sont pas valides ».  
  
 **Se fier au serveur pour le chiffrement**  
 Permet d’utiliser les fonctionnalités de sécurité du [!INCLUDE[ssDE](../../includes/ssde-md.md)] pour sécuriser les packages.  
  
 **Suivant**  
 Permet de passer à la page suivante de l'Assistant.  
  
 **Terminer**  
 Passez directement à la page Fin de l'Assistant Installation de package. Utilisez cette option si vous êtes revenu en arrière dans les pages de l'Assistant pour examiner vos choix et si vous avez spécifié toutes les options obligatoires.  
  
## Page Fin de l'Assistant Installation de package  
 La page **Fin de l’Assistant Installation de package** permet d’obtenir un résumé des résultats de l’installation des packages. Cette page fournit des détails comme le nom du projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] déployé, les packages installés, les fichiers de configuration et l’emplacement de l’installation.  
  
 **Terminer**  
 Pour quitter l’Assistant, cliquez sur **Terminer**.  
  
## Voir aussi  
 [Déploiement de packages hérités &#40;SSIS&#41;](../../integration-services/packages/legacy-package-deployment-ssis.md)  
  
  