---
title: "Assistant D&#233;ploiement d&#39;Integration Services | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.deploymentwizard.f1"
ms.assetid: f3d93e13-2d85-47ff-a913-cda4046491c4
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 14
---
# Assistant D&#233;ploiement d&#39;Integration Services
  L’**Assistant Déploiement d’Integration Services** prend en charge deux modèles de déploiement :
   - Le modèle de déploiement de projet
   - le modèle de déploiement de package 
   
 Le **modèle de déploiement de projet** vous permet de déployer un projet SQL Server Integration Services (SSIS) comme une seule unité dans le catalogue SSIS.
 
 Le **modèle de déploiement de package** vous permet de déployer des packages que vous avez mis à jour dans le catalogue SSIS sans avoir besoin de déployer l’ensemble du projet. 
 
 > **REMARQUE :** le déploiement de l’Assistant par défaut est le modèle de déploiement de projet.  
  
## Lancer l'Assistant
Lancer l’Assistant en :

 - En tapant **« Assistant déploiement SQL Server »** dans Windows Search 

**- ou -**

 - En recherchant le fichier exécutable **ISDeploymentWizard.exe** sous le dossier d’installation de SQL Server, par exemple : « C:\Program Files (x86)\Microsoft SQL Server\130\DTS\Binn». 
 
 > **REMARQUE :** cliquez sur **Suivant** sur la page **Introduction** pour afficher la page **Sélectionner une source**. 
 
 Les paramètres de cette page sont différents pour chaque modèle de déploiement. Suivez les étapes de la section [Project Deployment Model](../../integration-services/packages/integration-services-deployment-wizard.md#ProjectModel) ou de la section [Package Deployment Model](../../integration-services/packages/integration-services-deployment-wizard.md#PackageModel) en fonction du modèle que vous avez sélectionné sur cette page.  
  
##  <a name="ProjectModel"></a> Modèle de déploiement de projet  
  
### Sélectionner une source  
 Pour déployer un fichier de déploiement de projet que vous avez créé, sélectionnez **Fichier de déploiement de projet** , puis entrez le chemin d’accès du fichier .ispac. Pour déployer un projet qui réside dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , sélectionnez **Catalogue Integration Services**, puis entrez le nom du serveur et le chemin d'accès au projet au sein du catalogue. Cliquez sur **Suivant** pour afficher la page **Sélectionner la destination** .  
  
### Sélectionner la destination  
 Pour sélectionner le dossier de destination du projet dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , entrez l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou cliquez sur **Parcourir** pour sélectionner un serveur dans une liste de serveurs. Entrez le chemin d'accès au projet dans SSISDB ou cliquez sur **Parcourir** pour le sélectionner. Cliquez sur **Suivant** pour afficher la page **Vérifier** .  
  
### Vérifier (et déployer)  
 La page vous permet de vérifier les paramètres que vous avez sélectionnés. Vous pouvez modifier vos sélections en cliquant sur **Précédent**ou en cliquant sur l'une des étapes dans le volet gauche. Cliquez sur **Déployer** pour démarrer le processus de déploiement.  
  
### Résultats  
 Une fois le processus de déploiement terminé, la page **Résultats** doit s’afficher. Cette page indique la réussite ou l’échec de chaque action. Si l'action échoue, cliquez sur **Échec** dans la colonne **Résultat** pour afficher une explication de l'erreur. Cliquez sur **Enregistrer le rapport** pour enregistrer les résultats dans un fichier XML ou cliquez sur **Fermer** pour quitter l’Assistant.  
  
##  <a name="PackageModel"></a> Modèle de déploiement de package  
  
### Sélectionner une source  
 La page **Sélectionner une source** dans l’ **Assistant Déploiement d’Integration Services** affiche les paramètres spécifiques au modèle de déploiement de package si vous avez sélectionné l’option **Déploiement de package** comme **modèle de déploiement**.  
  
 Pour sélectionner les packages source, cliquez sur **Parcourir...** pour sélectionner le **dossier** that contains the packages or type the dossier path in the **Packages dossier path** et cliquez sur le bouton **Actualiser** au bas de la page. Tous les packages contenus dans le dossier spécifié doivent s’afficher dans la zone de liste. Par défaut, tous les packages sont sélectionnés. Cliquez sur la **case à cocher** dans la première colonne pour choisir les packages à déployer sur le serveur.  
  
 Consultez les colonnes **État** et **Message** pour vérifier l’état du package. Si l’état est défini sur **Prêt** ou **Avertissement**, l’Assistant Déploiement ne bloquera pas le processus de déploiement. Si l’état est défini sur **Erreur**, l’Assistant ne procédera pas au déploiement des packages sélectionnés. Pour afficher les messages d’avertissement/d’erreur détaillés, cliquez sur le lien dans la colonne **Message**.  
  
 Si les données sensibles ou les données de package sont chiffrées avec un mot de passe, tapez le mot de passe dans la colonne **Mot de passe** et cliquez sur le bouton **Actualiser** pour vérifier si le mot de passe est accepté. Si le mot de passe est correct, l’état passe à **Prêt** et le message d’avertissement disparaît. S’il existe plusieurs packages avec le même mot de passe, sélectionnez les packages avec le même mot de passe de chiffrement, tapez le mot de passe dans la zone de texte **Mot de passe** et cliquez sur le bouton **Appliquer** . Le mot de passe est appliqué aux packages sélectionnés.  
  
 Si l’état de tous les packages sélectionnés n’est pas défini sur **Erreur**, le bouton **Suivant** est activé pour vous permettre de poursuivre le processus de déploiement de package.  
  
### Sélectionner la destination  
 Après avoir sélectionné les sources de package, cliquez sur le bouton **Suivant** pour afficher la page **Sélectionner la destination** . Les packages doivent être déployés dans un projet dans le catalogue SSIS (SSISDB). Par conséquent, avant de déployer des packages, vérifiez que le projet de destination existe déjà dans le catalogue SSIS. Dans le cas contraire, créez un projet vide. Sur la page **Sélectionner la destination** , tapez le nom du serveur dans la zone de texte **Nom du serveur** ou cliquez sur le bouton **Parcourir...** pour sélectionner une instance de serveur. Cliquez ensuite sur le bouton **Parcourir...** en regard de la zone de texte **Chemin d’accès** pour spécifier le projet de destination. Si le projet n’existe pas, cliquez sur **Nouveau projet...** pour créer un projet vide comme projet de destination. Le projet **DOIT** être créé dans un dossier.  
  
### Vérifier et déployer  
 Cliquez sur **Suivant** sur la page **Sélectionner la destination** pour afficher la page **Vérifier** dans l’ **Assistant Déploiement d’Integration Services**. Sur la page de vérification, passez en revue le rapport de synthèse sur l’action de déploiement. Après la vérification, cliquez sur le bouton **Déployer** pour exécuter le déploiement.  
  
### Résultats  
 Une fois le déploiement terminé, la page **Résultats** doit s’afficher. Sur la page **Résultats** , passez en revue les résultats de chaque étape du processus de déploiement. Sur la page **Résultats** , cliquez sur **Enregistrer le rapport** pour enregistrer le rapport de déploiement ou cliquez sur **Fermer** pour fermer l’Assistant.  
  
## Voir aussi  
 [Déployer des projets sur le serveur Integration Services](../../integration-services/packages/deploy-projects-to-integration-services-server.md)   
 [Déploiement de projets et de packages](https://msdn.microsoft.com/library/hh213290.aspx)  
  
  