---
title: 'Étape 3 : Test des Packages déployés | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9159da3f-c9ca-4015-9e85-3bf4373a1349
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 92055ceb4226406fe26d7ce23491c81606f292c5
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58389907"
---
# <a name="step-3-testing-the-deployed-packages"></a>Étape 3 : Test des packages déployés
  Dans cette tâche, vous allez tester les packages que vous avez déployés vers une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Dans d'autres didacticiels [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , vous avez exécuté des packages dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], l'environnement de développement pour [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], à l'aide de l'option **Démarrer le débogage** du menu **Débogage** . Vous allez cette fois exécuter les packages différemment.  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] fournit plusieurs outils que vous pouvez utiliser pour exécuter des packages dans l'environnement de production et de test : l'utilitaire d'invite de commandes `dtexec` et l'utilitaire d'exécution de package. Cet utilitaire est un outil graphique qui repose sur `dtexec`. Ces deux outils exécutent le package immédiatement. De plus, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] fournit un sous-système de SQL Server Agent conçu spécifiquement pour planifier l'exécution de package comme une étape d'un travail de SQL Server Agent.  
  
 Vous allez utiliser l'utilitaire d'exécution de package pour exécuter les packages déployés. Les packages sont utilisés tel quel ; par conséquent, vous n'avez pas à mettre à jour les informations sur les pages de la boîte de dialogue. Vous allez exécuter les packages à partir de la page Général, la première page de l'utilitaire d'exécution de package. Si vous le souhaitez, vous pouvez cliquer sur les autres pages pour consulter les informations destinées à chaque package.  
  
> [!NOTE]  
>  Pour veiller à une bonne exécution des packages dans le contexte de ce didacticiel, vous ne devez modifier aucune option.  
  
 Avant d'exécuter des packages dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] à l'aide de l'utilitaire d'exécution de package, vérifiez que le service Integration Services est en cours d'exécution. Ce service fournit la prise en charge pour le stockage et l'exécution des packages. Si ce service est arrêté, vous ne pouvez pas vous connecter à [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] et [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] n'affiche pas les packages à exécuter. Vous devez aussi avoir les autorisations pour exécuter le package sur l'instance où celui-ci est déployé. Pour plus d’informations, consultez [Rôles Integration Services &#40;Service SSIS&#41;](security/integration-services-roles-ssis-service.md).  
  
 Les dossiers de niveau supérieur dans le dossier Packages stockés représentent les dossiers définis par l'utilisateur et que surveille le service Integration Services. Vous pouvez spécifier un grand nombre ou un petit nombre de dossiers dans le fichier MsDtsSrvr.ini.xml selon vos besoins. Ce didacticiel suppose que vous utilisez le fichier par défaut MsDtsSrvr.ini.xml, et que les noms des dossiers de niveau supérieur dans le dossier Packages stockés sont File System et MSDB.  
  
### <a name="to-connect-to-integration-services-in-sql-server-management-studio"></a>Pour vous connecter à Integration Services dans SQL Server Management Studio  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Microsoft SQL Server 2005**et cliquez sur **SQL Server Management Studio**.  
  
2.  Dans la boîte de dialogue **Se connecter au serveur** , dans la liste **Type de serveur** , sélectionnez **Integration Services** , entrez un nom de serveur dans la zone **Nom de serveur** , puis cliquez sur **Se connecter**.  
  
    > [!IMPORTANT]  
    >  Si vous ne pouvez pas vous connecter à [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], il est probable que le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ne soit pas en cours d'exécution. Pour connaître l'état du service, cliquez sur **Démarrer**, pointez sur **Tous les programmes**, sur **Microsoft SQL Server**, sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**. Dans le volet gauche, cliquez sur **Services SQL Server**. Dans le volet droit, recherchez le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Démarrez le service, il n'est pas déjà en cours d'exécution.  
  
     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] s'ouvre. Par défaut, la fenêtre de l'Explorateur d'objets est ouverte et placée dans le coin supérieur droit du studio. Si l'Explorateur d'objets n'est pas ouvert, dans le menu **Affichage** , cliquez sur **Explorateur d'objets** .  
  
### <a name="to-run-the-packages-using-the-execute-package-utility"></a>Pour exécuter les packages à l'aide de l'utilitaire d'exécution de package  
  
1.  Dans l'Explorateur d'objets, développez le dossier Packages stockés.  
  
2.  Développez le dossier MSDB. Dans la mesure où vous déployez les packages vers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], tous les packages déployés sont stockés dans la base de données msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ; par ailleurs, tous les packages déployés apparaissent dans le dossier MSDB. Le dossier File System est vide sauf si vous avez déployé des packages vers le système de fichiers à l'extérieur du didacticiel de déploiement.  
  
3.  En commençant par le haut de la liste des packages, cliquez avec le bouton droit sur DataTransfer et cliquez sur **Exécuter le package**.  
  
4.  Dans la boîte de dialogue **Utilitaire d'exécution de package** , cliquez sur **Exécuter**.  
  
5.  Consultez les résultats de la progression et de l'exécution du package dans la boîte de dialogue **Utilitaire d'exécution de package** . Lorsque le bouton **Arrêter** n'est plus disponible, ce qui indique la fin de l'exécution du package, cliquez sur **Fermer**.  
  
    > [!IMPORTANT]  
    >  Si vous cliquez sur **Arrêter** au cours de l’exécution du package, le package ne se termine pas.  
  
6.  Dans la boîte de dialogue **Utilitaire d'exécution de package** , cliquez sur **Fermer**.  
  
7.  Répétez les étapes 3 à 6 pour le package LoadXML.  
  
8.  Dans le menu **Fichier** , cliquez sur **Quitter**.  
  
### <a name="to-verify-the-results-of-the-datatransfer-package"></a>Pour vérifier les résultats du package DataTransfer  
  
1.  Dans la barre d'outils dans le [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], cliquez sur **Nouvelle requête**.  
  
2.  Dans la boîte de dialogue **Se connecter au serveur** , sélectionnez **Moteur de base de données** dans la liste **Type du serveur** , fournissez le nom du serveur sur lequel vous avez installé les packages du didacticiel ou tapez (local) dans la zone **Nom du serveur** , et sélectionnez un mode d’authentification. Si vous utilisez l'authentification SQL Server, vous devez fournir un nom d'utilisateur et un mot de passe.  
  
3.  Cliquer sur **Se connecter**.  
  
4.  Dans la fenêtre de requêtes, tapez ou collez l'instruction SQL suivante :  
  
     `USE AdventureWorks`  
  
     `SELECT * FROM HighIncomeCustomers`  
  
5.  Appuyez sur **F5** ou cliquez sur l'icône Exécuter dans la barre d'outils.  
  
     La requête retourne 31 lignes de données. Le résultat retourné contient les lignes du fichier texte, Customers.txt, dont les valeurs sont supérieures à 100000 dans la colonne YearlyIncome.  
  
6.  Accédez au dossier DeploymentTutorial, cliquez avec le bouton droit sur le fichier journal XML, sur le Journal Didacticiel de déploiement, puis cliquez sur **Ouvrir**. Vous pouvez ouvrir ce fichier dans le Bloc-notes ou à l'aide de l'éditeur de texte/XML de votre choix.  
  
### <a name="to-verify-the-results-of-the-loadxmldata-package"></a>Pour vérifier les résultats du package LoadXMLData  
  
1.  Dans la barre d'outils dans le [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], cliquez sur **Nouvelle requête**.  
  
2.  Si vous êtes invité à vous reconnecter, dans la boîte de dialogue **Se connecter au serveur** , sélectionnez **Moteur de base de données** dans la liste **Type du serveur** , fournissez le nom du serveur sur lequel vous avez installé les packages du didacticiel ou tapez (local) dans la zone **Nom du serveur** , et sélectionnez un mode d’authentification. Si vous utilisez l'authentification SQL Server, vous devez fournir un nom d'utilisateur et un mot de passe.  
  
3.  Cliquer sur **Se connecter**.  
  
4.  Dans la fenêtre de requêtes, tapez ou collez l'instruction SQL suivante :  
  
     `USE AdventureWorks`  
  
     `SELECT * FROM OrderDatesByCountryRegion`  
  
5.  Appuyez sur **F5** ou cliquez sur l'icône Exécuter dans la barre d'outils.  
  
     La requête retourne 21 lignes de données. Le résultat retourné comprend les lignes provenant du fichier de données XML, orders.xml. Chaque ligne est une synthèse par pays/région ; la ligne répertorie le nom d'un pays/d'une région, le nombre de commandes par pays/région, ainsi que les dates des commandes les plus récentes et les plus anciennes.  
  
![Icône Integration Services (petite)](media/dts-16.gif "icône Integration Services (petite)")**rester jusqu'à la Date avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire dtexec](packages/dtexec-utility.md)  
  
  
