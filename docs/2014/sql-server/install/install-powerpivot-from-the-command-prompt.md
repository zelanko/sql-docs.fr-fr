---
title: Installer PowerPivot à partir de l’invite de commandes | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 7f1f2b28-c9f5-49ad-934b-02f2fa6b9328
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 8959b1ca4ea719ce571cb8609b817bba965185bd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "72798332"
---
# <a name="install-powerpivot-from-the-command-prompt"></a>Installer PowerPivot à partir de l'invite de commandes
  Vous pouvez exécuter le programme d'installation depuis la ligne de commande pour installer SQL Server PowerPivot pour SharePoint. Vous devez inclure le paramètre de `/ROLE` dans votre commande et exclure le paramètre `/FEATURES`.  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 L'édition entreprise SharePoint Server 2010 Enterprise Edition dotée du Service Pack 1 (SP1) doit être installée.  
  
 Vous devez utiliser des comptes de domaine pour configurer Analysis Services.  
  
 L'ordinateur doit être joint au même domaine que la batterie de serveurs SharePoint.  
  
##  <a name="Commands"></a>Options d’installation basées sur/ROLE  
 Dans les déploiements PowerPivot pour SharePoint, le paramètre `/ROLE` est utilisé à la place du paramètre `/FEATURES`. Les valeurs valides sont les suivantes :  
  
-   `SPI_AS_ExistingFarm`  
  
-   `SPI_AS_NewFarm`  
  
 Ces deux rôles installent les fichiers d'application, de configuration et de déploiement qui permettent à un PowerPivot pour SharePoint de s'exécuter dans une batterie de serveurs SharePoint. La spécification de l'un ou l'autre rôle forcera le programme d'installation à vérifier les configurations matérielle et logicielle requises pour l'intégration SharePoint.  
  
 L'option batterie de serveurs existante suppose qu'une batterie de serveurs SharePoint est déjà en place. L’option nouvelle batterie de serveurs part du principe que vous allez créer une batterie de serveurs ; Il prend en charge l’ajout d’une instance de Moteur de base de données dans la syntaxe de la ligne de commande afin que vous puissiez utiliser l’instance Moteur de base de données en tant que serveur de base de données de la batterie de serveurs.  
  
 Contrairement aux versions précédentes, toutes les tâches de configuration du serveur sont effectuées comme après l'installation. Si vous automatisez les étapes d'installation et de configuration, vous pouvez utiliser PowerShell pour configurer le serveur. Pour plus d’informations, consultez [configuration de PowerPivot à l’aide de Windows PowerShell](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell).  
  
## <a name="example-commands"></a>Exemple de commandes  
 Les exemples suivants illustrent l'utilisation de chaque option. Le premier exemple montre `SPI_AS_ExistingFarm`.  
  
```cmd
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_ExistingFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 Le deuxième exemple montre `SPI_AS_NewFarm`. Notez qu'il inclut des paramètres de configuration du moteur de base de données.  
  
```cmd
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_NewFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/SQLSVCACCOUNT=<DomainName\UserName> /SQLSVCPASSWORD=<StrongPassword> /SQLSYSADMINACCOUNTS=<DomainName\UserName> /AGTSVCACCOUNT=<DomainName\UserName> /AGTSVCPASSWORD=<StrongPassword> /ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
##  <a name="Join"></a>Modification de la syntaxe de la commande  
 Utilisez la procédure suivante pour modifier la syntaxe de commande de l'exemple.  
  
1.  Copiez la commande suivante dans le Bloc-notes :  
  
    ```cmd
    Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_ExistingFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
    ```  
  
     Le paramètre `/q` exécute le programme d'installation en mode silencieux, ce qui supprime l'interface utilisateur.  
  
     Le paramètre `/IAcceptSQLServerLicenseTerms` est indispensable lorsque le paramètre `/q` ou `/qs` est spécifié pour les installations sans assistance.  
  
     Le paramètre `/action` indique au programme d'installation d'effectuer une installation.  
  
     Le paramètre `/role` indique au programme d'installation d'installer le programme et les fichiers de configuration Analysis Services nécessaires pour PowerPivot for SharePoint. Ce rôle détecte et utilise également les informations de connectivité de la batterie existante pour accéder à la base de données de configuration SharePoint. Ce paramètre est obligatoire. Utilisez-le à la place du paramètre `/features` pour spécifier les composants à installer.  
  
     Le paramètre `/instancename` spécifie 'PowerPivot' comme une instance nommée. Cette valeur est codée en dur et ne peut pas être modifiée. Elle est spécifiée dans la commande à titre éducatif, pour que vous sachiez comment le service est installé.  
  
     Le paramètre `/indicateprogress` vous permet de surveiller la progression dans la fenêtre d'invite de commandes.  
  
2.  Le paramètre `PID` est omis de la commande, ce qui entraîne l'installation d'Evaluation edition. Si vous souhaitez installer Enterprise Edition, ajoutez le paramètre PID à votre commande d'installation et fournissez une clé de produit valide.  
  
    ```  
    /PID=<product key for an Enterprise installation>  
    ```  
  
3.  Remplacez les espaces réservés pour \<domaine\nom_utilisateur> et \<StrongPassword>par des comptes d’utilisateur et des mots de passe valides.  
  
     Les `/assvaccount` paramètres et **/ASSVCPASSWORD** sont utilisés pour configurer l' [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] instance sur le serveur d’applications. Remplacez ces espaces réservés par des informations de compte valides.  
  
     Le paramètre **/ASSYSADMINACCOUNTS** doit être défini sur l’identité de l’utilisateur qui exécute SQL Server installation. Vous devez spécifier au moins un administrateur système. Notez que le programme d'installation de SQL Server n'accorde plus d'autorisations sysadmin automatiques aux membres du groupe intégré Administrateurs.  
  
4.  Supprimez les sauts de ligne.  
  
5.  Sélectionnez l’intégralité de la commande, puis cliquez sur **copier** dans le menu Edition.  
  
6.  Ouvrez une invite de commandes d'administrateur. Pour ce faire, cliquez sur **Démarrer**, cliquez avec le bouton droit sur l’invite de commandes, puis sélectionnez **exécuter en tant qu’administrateur**.  
  
7.  Accédez au lecteur ou au dossier partagé qui contient le support d'installation de SQL Server.  
  
8.  Collez la commande modifiée dans la ligne de commande. Pour ce faire, cliquez sur l’icône dans le coin supérieur gauche de la fenêtre d’invite de commandes, pointez sur **modifier**, puis cliquez sur **coller**.  
  
9. Appuyez sur **entrée** pour exécuter la commande. Attendez que l'installation soit terminée. Vous pouvez surveiller la progression de l'installation dans la fenêtre d'invite de commandes.  
  
10. Pour vérifier l'installation, vérifiez le fichier summary.txt dans \Program Files\SQL Server\120\Setup Bootstrap\Log. Le résultat final doit indiquer « Réussite » si le serveur a été installé sans erreurs.  
  
11. Configurez le serveur. Vous devez au minimum déployer des solution, créer une application de service et activer la fonction pour chaque collection de sites. Pour plus d’informations, consultez [configurer ou réparer PowerPivot pour SharePoint 2010 &#40;outil de configuration powerpivot&#41;](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md) ou [administration et configuration du serveur PowerPivot dans l’administration centrale](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration).  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer des comptes de service PowerPivot](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts)   
 [PowerPivot for SharePoint 2010 Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
