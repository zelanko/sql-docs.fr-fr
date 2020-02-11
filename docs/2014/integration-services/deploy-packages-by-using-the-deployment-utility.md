---
title: Déployer des packages à l’aide de l’utilitaire de déploiement | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], installing
- installing packages
- dependencies [Integration Services]
- deploying packages [Integration Services], installing
ms.assetid: eaf4b56e-2023-4d17-971c-703031da758c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 73b71e83f3b0f0f895b2cc5b8fd3495fb4893a32
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66059621"
---
# <a name="deploy-packages-by-using-the-deployment-utility"></a>Déployer des packages à l’aide de l’utilitaire de déploiement
  Après avoir créé un utilitaire de déploiement pour installer les packages d’un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur un ordinateur différent de celui sur lequel cet utilitaire a été créé, vous devez d’abord copier le dossier de déploiement vers l’ordinateur de destination.  
  
 Le chemin du dossier de déploiement est spécifié dans la propriété DeploymentOutputPath du projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] pour lequel vous avez créé l’utilitaire de déploiement. Le chemin d’accès par défaut est bin\Deployment, lié au projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Pour plus d’informations, consultez [Créer un utilitaire de déploiement](../../2014/integration-services/create-a-deployment-utility.md).  
  
 Vous utilisez l'Assistant Installation de package pour installer les packages. Pour lancer l'Assistant, double-cliquez sur l'utilitaire de déploiement après avoir copié le dossier de déploiement sur le serveur. Le fichier est nommé \<nom_projet>.SSISDeploymentManifest et se trouve dans le dossier de déploiement sur l’ordinateur de destination.  
  
> [!NOTE]  
>  En fonction de la version du package que vous déployez, une erreur risque de se produire si différentes version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sont installées côte à côte. Cette erreur vient du fait que l'extension de nom de fichier .SSISDeploymentManifest est la même pour toutes les versions d' [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Si vous double-cliquez sur le fichier, cela entraîne l’appel du programme d’installation (dtsinstall.exe) correspondant à la version installée en dernier d’ [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], laquelle risque d’être différente de la version du fichier de l’utilitaire de déploiement. Pour contourner ce problème, exécutez la version appropriée de dtsinstall.exe à partir de la ligne de commande, puis indiquez le chemin d'accès du fichier de l'utilitaire de déploiement.  
  
 L'Assistant Installation de package vous accompagne dans le processus d'installation des packages sur le système de fichiers et sur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Vous pouvez configurer l'installation de plusieurs manières :  
  
-   Choix du type d'emplacement et emplacement d'installation des packages.  
  
-   Choix de l'emplacement d'installation des dépendances de package.  
  
-   Validation des packages après leur installation sur le serveur cible.  
  
 Les dépendances basées sur les fichiers pour les packages sont toujours installées sur le système de fichiers. Si vous installez un package sur le système de fichiers, les dépendances sont installées dans le même dossier que celui indiqué pour le package. Si vous installez un package sur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], vous pouvez spécifier le dossier dans lequel les dépendances basées sur les fichiers seront stockées.  
  
 Si le package comprend des configurations que vous voulez modifier pour qu'elles soient utilisées sur l'ordinateur de destination, vous pouvez mettre à jour les valeurs des propriétés à l'aide de l'Assistant.  
  
 Outre l’installation des packages à l’aide de l’Assistant Installation de package, vous pouvez copier et déplacer des packages à l’aide de l’utilitaire d’invite de commandes **dtutil** . Pour plus d’informations, consultez [dtutil Utility](dtutil-utility.md).  
  
### <a name="to-deploy-packages-to-an-instance-of-sql-server"></a>Pour déployer des packages sur une instance de SQL Server  
  
1.  Ouvrez le dossier de déploiement sur l'ordinateur cible.  
  
2.  Double-cliquez sur le fichier manifeste, \<nom_projet>.SSISDeploymentManifest, pour démarrer l’Assistant Installation de package.  
  
3.  Dans la page **Déployer les packages SSIS** , sélectionnez l’option **Déploiement sur SQL Server** .  
  
4.  Vous pouvez, si vous le souhaitez, sélectionner **Valider les packages après l’installation** pour valider les packages après qu’ils ont été installés sur le serveur cible.  
  
5.  Dans la page **Spécifier le serveur SQL cible** , spécifiez l’instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur laquelle les packages doivent être installés et sélectionnez un mode d’authentification. Si vous sélectionnez l’authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , vous devez fournir un nom d’utilisateur et un mot de passe.  
  
6.  Dans la page **Sélectionner le dossier d’installation** , spécifiez le dossier du système de fichiers dans lequel installer les dépendances du package.  
  
7.  Si le package comprend des configurations, vous pouvez les modifier en mettant à jour des valeurs dans la liste **Valeur** dans la page Configurer les packages.  
  
8.  Si vous avez choisi de valider les packages après l'installation, affichez les résultats de validation des packages déployés.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement de packages &#40;&#41;SSIS](packages/legacy-package-deployment-ssis.md)  
  
  
