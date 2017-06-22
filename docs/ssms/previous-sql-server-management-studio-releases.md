---
title: "Versions antérieures de SQL Server Management Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87f593c3-8b76-4c12-963a-31d35f2fb294
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 0927784589c1f7227b432ff49f81f29de20083ec
ms.openlocfilehash: 200753bf64d92043171788852227c6199b64711d
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="previous-sql-server-management-studio-releases"></a>Versions antérieures de SQL Server Management Studio
  
Les versions antérieures suivantes de SQL Server Management Studio sont disponibles.
   
## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-1653-releasehttpgomicrosoftcomfwlinklinkid840946"></a>![télécharger](../ssdt/media/download.png) [version de SQL Server Management Studio 16.5.3](http://go.microsoft.com/fwlink/?LinkID=840946)

**Informations sur la version**  
  
*Cette version de SSMS utilise le shell isolé Visual Studio 2015.*  
Numéro de la version : 16.5.3  
Numéro de build de cette version : 13.0.16106.4

## <a name="changelog"></a>Journal des modifications  

16.5.3

Les problèmes suivants ont été résolus dans cette version :

* Résolution du problème introduit dans SSMS 16.5.2 qui provoquait l’expansion du nœud « Table » quand la table comportait plusieurs colonnes éparses.

* Les utilisateurs peuvent déployer des packages SSIS contenant le Gestionnaire de connexions OData qui connectent une ressource Microsoft Dynamics AX/CRM Online au catalogue SSIS. Pour plus d’informations, consultez [Gestionnaire de connexions OData](https://msdn.microsoft.com/library/dn584133.aspx).

* La configuration d’Always Encrypted sur une table existante échoue avec des erreurs sur des objets non associés. [Microsoft Connect - ID 3103181](https://connect.microsoft.com/SQLServer/feedback/details/3103181/setting-up-always-encrypted-on-an-existing-table-fails-with-errors-on-unrelated-objects)

* La configuration d’Always Encrypted pour une base de données existante avec plusieurs schémas ne fonctionne pas. [Microsoft Connect - ID 3109591](https://connect.microsoft.com/SQLServer/feedback/details/3109591/sql-server-2016-always-encrypted-against-existing-database-with-multiple-schemas-doesnt-work)

* L’Assistant Colonne chiffrée d’Always Encrypted échoue parce que la base de données contient des vues qui référencent des vues système. [Microsoft Connect - ID 3111925](https://connect.microsoft.com/SQLServer/feedback/details/3111925/sql-server-2016-always-encrypted-encrypted-column-wizard-failed-task-failed-due-to-following-error-cannot-save-package-to-file-the-model-has-build-blocking-errors)

* Lors du chiffrement à l’aide d’Always Encrypted, les erreurs provenant de l’actualisation des modules après le chiffrement ne sont pas gérées correctement.

* Le menu *Ouvrir un fichier récent* n’affiche pas les fichiers récemment enregistrés. [Microsoft Connect - ID 3113288](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files)

* SSMS est lent quand l’utilisateur clique avec le bouton droit sur un index pour une table (via une connexion (Internet) à distance). [Microsoft Connect - ID 3114074](https://connect.microsoft.com/SQLServer/feedback/details/3114074/ssms-slow-when-right-clicking-an-index-for-a-table-over-a-remote-internet-connection)
 
* Correction d’un problème avec la barre de défilement de SQL Designer. [Microsoft Connect - ID 3114856](http://connect.microsoft.com/SQLServer/feedback/details/3114856/bug-in-scrollbar-on-sql-desginer-in-ssms-2016)

* Le menu contextuel pour les tables se bloque momentanément 
 
* Il peut arriver que SSMS lève des exceptions dans le moniteur d’activité et se bloque. [Microsoft Connect - ID 697527](https://connect.microsoft.com/SQLServer/feedback/details/697527/)

* SSMS 2016 se bloque avec l’erreur « Le processus a été arrêté en raison d’une erreur interne dans le runtime .NET à l’adresse IP 71AF8579 (71AE0000) avec le code de sortie 80131506 »



## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-165-releasehttpgomicrosoftcomfwlinklinkid832812"></a>![télécharger](../ssdt/media/download.png) [SQL Server Management Studio 16.5](http://go.microsoft.com/fwlink/?LinkID=832812)

**Informations sur la version**  
  
*Cette version de SSMS utilise le shell isolé Visual Studio 2015.*  
Numéro de la version : 16.5  
Numéro de build de cette version : 13.0.16000.28

**Problèmes connus de cette version**  

1. Invoke-Sqlcmd insère par erreur plusieurs lignes lors d’une contrainte de validation. [Article Microsoft Connect n°811560](https://connect.microsoft.com/SQLServer/feedback/details/811560)

2. Les versions qui ne sont pas en langue anglaise ne fonctionnent pas complètement lors de la création de groupes de disponibilité.

3. Un clic sur le fichier XML du plan de requête n’ouvre pas l’interface utilisateur SSMS appropriée.

**Journal des modifications**

* Résolution d’un problème : un blocage peut se produire quand une base de données avec un nom de la table contenant « ;: » a été activée.
* Résolution d’un problème : les modifications apportées à la page Modèle dans la fenêtre des propriétés de base de données tabulaire AS génèrent un script de la définition d’origine. 
[Élément Microsoft Connect : 3080744](https://connect.microsoft.com/SQLServer/feedback/details/3080744) 
* Correction du problème lié à l’ajout de fichiers temporaires à la liste « Fichiers récents ».  
[Élément Microsoft Connect : 2558789](https://connect.microsoft.com/SQLServer/feedback/details/2558789)
* Résolution du problème : l’élément de menu « Gérer la Compression » est désactivé pour les nœuds de la table utilisateur dans l’arborescence de l’Explorateur d’objets.  
[Élément Microsoft Connect : 3104616](https://connect.microsoft.com/SQLServer/feedback/details/3104616)

* Résolution du problème : l’utilisateur ne peut pas définir la taille de police pour l’Explorateur d’objets, l’Explorateur de serveurs inscrits, l’Explorateur de modèle ainsi que pour les détails de l’Explorateur d’objets. La police pour les explorateurs utilise la police de l’environnement.  
[Élément Microsoft Connect : 691432](https://connect.microsoft.com/SQLServer/feedback/details/691432)

* Résolution du problème : SSMS se reconnecte toujours à la base de données par défaut quand la connexion est perdue.  
[Élément Microsoft Connect Item : 3102337](https://connect.microsoft.com/SQLServer/feedback/details/3102337)

* Résolution d’un grand nombre de problèmes liés à la haute résolution dans la fenêtre de gestion des stratégies et de l’Éditeur de requête, notamment les icônes de plan d’exécution.

* Résolution du problème : l’option de configuration des polices et des couleurs pour les événements étendus est manquante.

* Résolution du problème : blocage de SSMS se produisant lors de la fermeture de l’application ou lors de la tentative d’affichage de la boîte de dialogue d’erreur.


   
## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-1641-september-2016-releasehttpgomicrosoftcomfwlinklinkid828615"></a>![télécharger](../ssdt/media/download.png) [SQL Server Management Studio version 16.4.1 (septembre 2016)](http://go.microsoft.com/fwlink/?LinkID=828615)

**Informations sur la version**  
  
*Cette version de SSMS utilise le shell isolé Visual Studio 2015.*  
Numéro de la version : 16.4.1  
Numéro de build de cette version : 13.0.15900.1
  
**Problèmes connus de cette version**  

1. **Un seul compte Azure Active Directory peut se connecter à une instance SSMS en utilisant l’authentification Active Directory universelle.**  
    Cette restriction est limitée à l’authentification Active Directory universelle : vous pouvez vous connecter à différents serveurs en utilisant l’authentification Active Directory par mot de passe, l’authentification Active Directory intégrée ou l’authentification SQL Server.
    
    Une solution de contournement consiste à utiliser une autre instance de SSMS pour se connecter sous un autre compte Azure Active Directory. 
    
2. **Les commandes de Data-Tier Application Framework (DACFx) et le Concepteur de schémas dans SSMS ne prennent pas en charge l’authentification Active Directory universelle.**  
    Les commandes qui utilisent DACFx (par exemple, l’importation et l’exportation) et le Concepteur de schémas dans SSMS ne prennent pas actuellement en charge l’authentification Active Directory universelle.
    
    Une solution de contournement consiste à utiliser les autres formes d’authentification fournies dans SSMS : authentification Active Directory par mot de passe, authentification Active Directory intégrée ou authentification SQL Server.

3. **SSMS peut se connecter uniquement à des instances de SQL Server Integrated Services 2016 (SSIS 2016).**  
    Il existe une limitation de compatibilité connue avec SQL Server Integration Services, qui empêche la connexion aux versions précédentes.
    
    Une solution de contournement de ce problème consiste à vous connecter à votre instance SQL Server Integration Services à l’aide de la [version de SSMS correspondant à votre instance SSIS.](../ssms/previous-sql-server-management-studio-releases.md) 
  
4. **SSMS n’enregistre pas les plans de maintenance de SQL Server 2008 R2 et versions antérieures de SQL Server.**  
    Il s’agit d’une limitation connue que nous espérons pouvoir résoudre à l’avenir. En attendant, vous pouvez utiliser la [version SSMS 2014](../ssms/previous-sql-server-management-studio-releases.md) pour enregistrer les plans de maintenance.  
    
5. **Les installations non anglaises de SSMS peuvent nécessiter l’installation d’un package de sécurité supplémentaire.**  
Les versions localisées dans des langues autres que l’anglais nécessitent la [mise à jour de sécurité KB 2862966](https://support.microsoft.com/en-us/kb/2862966) si l’installation est effectuée sous Windows 8, Windows 7, Windows Server 2012 et Windows Server 2008 R2.
  
6. **Le démarrage du module Gestionnaire de configuration SQL Server échoue si aucun serveur SQL Server n’est installé sur l’ordinateur client**  
    Si SQL Server n’est pas installé sur votre ordinateur client, lorsque vous démarrez le module Gestionnaire de configuration SQL Server, le message d’erreur suivant s’affiche :   
     `Cannot connect to WMI provider. You do not have permission or the server is unreachable. Note that you can only manage SQL Server 2005 and later servers with SQL Server Configuration Manager. Invalid namespace \[0x8004100e]`,   
   
     * Si vous avez ajouté vos instances SQL Server à la liste « Serveurs inscrits » dans SSMS :  
        1. Accédez à la vue « Serveurs inscrits » dans SSMS.  
        2. Cliquez avec le bouton droit sur l’instance SQL Server que vous souhaitez configurer.  
        3. Sélectionnez « Gestionnaire de configuration SQL Server... » dans le menu contextuel.    
          
      * Si vous n’avez pas ajouté d’instance SQL Server à la liste « Serveurs inscrits » dans SSMS :  
        1. Ouvrez une invite de commandes en tant qu’administrateur.  
        2. Exécutez l’outil Mofcomp à l’aide de la commande suivante :  
    `mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"`  
        3. Après avoir exécuté l’outil Mofcomp, pour que les modifications prennent effet, redémarrez le service WMI à l’aide de la commande suivante :  
        `net stop "Windows Management Instrumentation"`  
        `net start “Windows Management Instrumentation”`  

 
**Journal des modifications** 

*  Correction d’un problème selon lequel la tentative de modification (ALTER) d’une procédure stockée échoue :  
[Article Microsoft Connect n°3103831](https://connect.microsoft.com/SQLServer/feedback/details/3103831)

* Nouvelles applets de commande « Read-SqlTableData », « Read-SqlViewData » et « Write-SqlTableData » pour afficher et écrire des données à l’aide de PowerShell.  
[Trello Read-SqlTableData Card](https://trello.com/c/FXVUNJ8x/131-read-sqltabledata)  
[Article Microsoft Connect n° 2685363](https://connect.microsoft.com/SQLServer/feedback/details/2685363)
    
* Nouvelle applet de commande « Add-SqlLogin » pour permettre de nouveaux scénarios de gestion de connexion à l’aide de PowerShell.  
[Article Microsoft Connect n° 2588952](https://connect.microsoft.com/SQLServer/feedback/details/2588952)
    
*  Prise en charge et utilisation améliorées pour les utilisateurs qui se connectent à plusieurs clouds nationaux.
    
*  Correction d’un problème où des exceptions Mémoire insuffisante étaient levées.  
[Article Microsoft Connect n° 3062914](https://connect.microsoft.com/SQLServer/feedback/details/3062914)  
[Article Microsoft Connect n° 3074856](https://connect.microsoft.com/SQLServer/feedback/details/3074856)
    
*  Correction d’un problème où le filtrage par schéma n’était pas une option de filtre valide.  
[Article Microsoft Connect n° 3058105](https://connect.microsoft.com/SQLServer/feedback/details/3058105)  
[Article Microsoft Connect n° 3101136](https://connect.microsoft.com/SQLServer/feedback/details/3101136)
    
*  Correction d’un problème où la fenêtre de surveillance d’une base de données étendue n’était pas accessible.
    
*  Correction d’un problème où la touche F1 (Aide) ouvrait toujours le contenu en ligne. Les utilisateurs peuvent désormais choisir s’ils préfèrent une aide en ligne ou hors connexion dans « Définir les préférences pour l’aide » du menu Aide.   
[Article Microsoft Connect n° 2826366](https://connect.microsoft.com/SQLServer/feedback/details/2826366)
    
*  Correction d’un problème où l’écriture du script d’un modèle tabulaire Analysis Services de niveau 1200 ne supprimait pas le mot de passe pour l’écriture du script, même si la version du serveur indiquait [l’objet de modèle de client est maintenant synchronisé avant l’écriture du script].
    
*  Correction d’un problème où l’option « Sélectionner les n premières lignes » générait une syntaxe déconseillée pour l’opérateur TOP.  
[Article Microsoft Connect n° 3065435](https://connect.microsoft.com/SQLServer/feedback/details/3065435)
    
*  Correction de divers problèmes de mise en page dans SSMS, notamment la page Propriétés de la connexion et les options d’exécution de requête avancée.   
[Article Microsoft Connect n° 3058199](https://connect.microsoft.com/SQLServer/feedback/details/3058199)  
[Article Microsoft Connect n° 3079122](https://connect.microsoft.com/SQLServer/feedback/details/3058199)  
[Article Microsoft Connect n° 3071384](https://connect.microsoft.com/SQLServer/feedback/details/3071384)
    
*  Correction d’un problème où une solution était créée automatiquement chaque fois qu’un utilisateur ouvrait une nouvelle fenêtre de requête.   
[Article Microsoft Connect n° 2924667](https://connect.microsoft.com/SQLServer/feedback/details/2924667)    
[Article Microsoft Connect n° 2917742](https://connect.microsoft.com/SQLServer/feedback/details/2917742)   
[Article Microsoft Connect n° 2612635](https://connect.microsoft.com/SQLServer/feedback/details/2612635)
    
*  Correction d’un problème où les tables temporelles ne pouvaient pas être développées dans l’Explorateur d’objets quand elles se trouvaient dans des bases de données système.  
[Article Microsoft Connect n° 2551649](https://connect.microsoft.com/SQLServer/feedback/details/2551649)
    
*  Correction d’un problème où SSMS exécute une requête SELECT @@trancount après l’exécution d’un lot.    
[Article Microsoft Connect n° 3042364](https://connect.microsoft.com/SQLServer/feedback/details/3042364)
    
*  Correction d’un problème dans Analysis Services où la création d’un script à partir de la page de propriétés d’un serveur masquait une boîte de dialogue de connexion.
    
*  Correction d’un problème où Ctrl + Q ne sélectionnait pas la barre d’outils Lancement rapide.
    
*  Correction d’un problème où la modification du paramètre MaxSize d’une base de données à l’aide de la boîte de dialogue Propriétés du serveur ne fonctionnait pas pour les bases de données > 2 To.  
[Article Microsoft Connect n°1231091](https://connect.microsoft.com/SQLServer/feedback/details/1231091)
    
*  Correction d’un problème où l’Assistant Restauration de la base de données n’acceptait pas les noms de fichiers avec des espaces de début :   
[Article Microsoft Connect n° 2395147](https://connect.microsoft.com/SQLServer/feedback/details/2395147)

*  Correction d’un problème où l’Assistant Restauration de la base de données n’acceptait pas les noms de fichiers avec des espaces de début :   
[Article Microsoft Connect n° 2395147](https://connect.microsoft.com/SQLServer/feedback/details/2395147)



## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-163-august-2016-releasehttpgomicrosoftcomfwlinklinkid824938"></a>![télécharger](../ssdt/media/download.png) [Version de SQL Server Management Studio 16.3 (août 2016)](http://go.microsoft.com/fwlink/?LinkID=824938)
 15 Août 2016 | Numéro de version : 13.0.15700.28

**Fonctionnalités**  
1. Nouvelle option d’authentification « Authentification Active Directory universelle »
2. Nouvelles applets de commande pour le module SQL Server PowerShell
3. Améliorations apportées à l’Assistant Paramétrage du moteur de base de données et aux modèles d’événements étendus
4. Prise en charge bêta de [l’affichage « Haute résolution » dans SSMS](https://blogs.msdn.microsoft.com/sqlreleaseservices/ssms-highdpi-support/)

[Informations supplémentaires sur les fonctionnalités disponibles dans le journal des modifications de SSMS.](../ssms/sql-server-management-studio-changelog-ssms.md)

**Problèmes connus**

Les problèmes et limitations constatés dans cette version de SQL Server Management Studio sont les suivants :  

1. **Un seul compte Azure Active Directory peut se connecter à une instance SSMS en utilisant l’authentification Active Directory universelle.**  
    Cette restriction est limitée à l’authentification Active Directory universelle : vous pouvez vous connecter à différents serveurs en utilisant l’authentification Active Directory par mot de passe, l’authentification Active Directory intégrée ou l’authentification SQL Server.
    
    Une solution de contournement consiste à utiliser une autre instance de SSMS pour se connecter sous un autre compte Azure Active Directory. 
    
2. **Les commandes de Data-Tier Application Framework (DACFx) et le Concepteur de schémas dans SSMS ne prennent pas en charge l’authentification Active Directory universelle.**  
    Les commandes qui utilisent DACFx (par exemple, l’importation et l’exportation) et le Concepteur de schémas dans SSMS ne prennent pas actuellement en charge l’authentification Active Directory universelle.
    
    Une solution de contournement consiste à utiliser les autres formes d’authentification fournies dans SSMS : authentification Active Directory par mot de passe, authentification Active Directory intégrée ou authentification SQL Server.

3. **SSMS peut se connecter uniquement à des instances de SQL Server Integrated Services 2016 (SSIS 2016).**  
    Il existe une limitation de compatibilité connue avec SQL Server Integration Services, qui empêche la connexion aux versions précédentes.
    
    Une solution de contournement de ce problème consiste à vous connecter à votre instance SQL Server Integration Services à l’aide de la [version de SSMS correspondant à votre instance SSIS.](../ssms/previous-sql-server-management-studio-releases.md) 
  
4. **SSMS n’enregistre pas les plans de maintenance de SQL Server 2008 R2 et versions antérieures de SQL Server.**  
    Il s’agit d’une limitation connue que nous espérons pouvoir résoudre à l’avenir. En attendant, vous pouvez utiliser la [version SSMS 2014](../ssms/previous-sql-server-management-studio-releases.md) pour enregistrer les plans de maintenance.  
    
5. **Les installations non anglaises de SSMS peuvent nécessiter l’installation d’un package de sécurité supplémentaire.**  
Les versions localisées dans des langues autres que l’anglais nécessitent la [mise à jour de sécurité KB 2862966](https://support.microsoft.com/en-us/kb/2862966) si l’installation est effectuée sous Windows 8, Windows 7, Windows Server 2012 et Windows Server 2008 R2.
  
6. **Le démarrage du module Gestionnaire de configuration SQL Server échoue si aucun serveur SQL Server n’est installé sur l’ordinateur client**  
    Si SQL Server n’est pas installé sur votre ordinateur client, lorsque vous démarrez le module Gestionnaire de configuration SQL Server, le message d’erreur suivant s’affiche :   
     `Cannot connect to WMI provider. You do not have permission or the server is unreachable. Note that you can only manage SQL Server 2005 and later servers with SQL Server Configuration Manager. Invalid namespace \[0x8004100e]`,   
   
     * Si vous avez ajouté vos instances SQL Server à la liste « Serveurs inscrits » dans SSMS :  
        1. Accédez à la vue « Serveurs inscrits » dans SSMS.  
        2. Cliquez avec le bouton droit sur l’instance SQL Server que vous souhaitez configurer.  
        3. Sélectionnez « Gestionnaire de configuration SQL Server... » dans le menu contextuel.    
          
      * Si vous n’avez pas ajouté d’instance SQL Server à la liste « Serveurs inscrits » dans SSMS :  
        1. Ouvrez une invite de commandes en tant qu’administrateur.  
        2. Exécutez l’outil Mofcomp à l’aide de la commande suivante :  
    `mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"`  
        3. Après avoir exécuté l’outil Mofcomp, pour que les modifications prennent effet, redémarrez le service WMI à l’aide de la commande suivante :  
        `net stop "Windows Management Instrumentation"`  
        `net start “Windows Management Instrumentation”`  


**Correctifs**
1. Résolution de bogue pour afficher le texte en clair de colonnes d’objet volumineux (LOB) AlwaysEncrypted déchiffrées dans SSMS (article Microsoft Connect n° 2413024).
2. Résolution de bogue dans la boîte de dialogue Chiffrement intégral pour corriger l’incident qui se produit quand les styles visuels Windows ne sont pas activés (par exemple, l’activation de l’affichage à contraste élevé).
3. Résolution de bogue pour l’erreur « Méthode introuvable » qui empêche la connexion à des instances SQL Server.
4. Résolution de bogue pour l’incident SSMS qui se produit lors de la création d’une fonction de partition avec décalage de date/heure.
5. Résolution de bogue pour supprimer l’exigence de disposer de Microsoft .NET 3.5 pour démarrer l’outil d’administration Distributed Replay (DReplay.exe).
6. Résolution de bogue dans l’Assistant Déploiement d’Analysis Services pour prendre en charge les noms de serveur complets.
7. Résolution de bogue dans SSMS pour afficher les partitions dans les modèles tabulaires Analysis Services avec un modèle de compatibilité 2016 (article Microsoft Connect n° 2845053).

[Informations supplémentaires sur les fonctionnalités disponibles dans le journal des modifications de SSMS.](../ssms/sql-server-management-studio-changelog-ssms.md)
 
---
## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-july-2016-hotfix-update-releasehttpgomicrosoftcomfwlinklinkid822301"></a>![télécharger](../ssdt/media/download.png) [correctif logiciel de juillet 2016 de SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkID=822301)

13 juillet 2016 | Numéro de version : 13.0.15600.2

**Fonctionnalités**  
1. Prise en charge d’Azure SQL Data Warehouse dans SSMS.   
2. Mises à jour importantes apportées au module SQL Server PowerShell.   
3. Délais de connexion aux bases de données SQL Azure considérablement améliorés.  
4. Prise en charge améliorée des bases de données tabulaires SQL Server 2016 (niveau de compatibilité de 1200) dans la fenêtre de traitement d’Analysis Services, et bien plus encore.   

[Informations supplémentaires et fonctionnalités disponibles dans le journal des modifications de SSMS.](../ssms/sql-server-management-studio-changelog-ssms.md)

**Problèmes connus** 
1. **Le programme d’installation du correctif logiciel de SSMS de juillet apparaît en tant que version d’août de SSMS.**
La page de configuration du correctif logiciel de mise à jour de juillet indique Août en raison d’un paramètre de build interne. Ce package est en fait un correctif logiciel pour la version de juillet de SSMS. 
2. **SSMS ne peut pas se connecter aux instances SQL Server après installation de la version « correctif logiciel de juillet 2016 ».**
Nous sommes conscients d’un problème lié à la dernière mise à jour de SSMS qui, en cas de tentative de connexion à un serveur, entraîne l’affichage du message d’erreur suivant : 
   ```
    "Method not found: 'Void Microsoft.SqlServer.Management.Common.SqlConnectionInfo.set_ApplicationIntent(System.String)'"
    ```
  
    Le correctif de ce problème sera disponible dans la prochaine version de SSMS. Une solution de contournement de ce problème consiste à désinstaller, puis réinstaller SSMS. Pour plus d’informations, [voir ce fil de discussion Microsoft Connect concernant le problème](https://connect.microsoft.com/SQLServer/feedback/details/2925257/not-able-to-connect-to-sql-server-instances-after-installing-ssms-2016-july-update).
    
3. **SSMS se bloque lors d’une tentative de sélection d’un compte de stockage Azure.**
Les versions de SSMS et du correctif logiciel de juillet se bloquent lorsque vous tentez de sélectionner un compte de stockage Azure alors que vous n’avez pas de compte de stockage « classique ».
Le correctif de ce problème sera disponible dans une prochaine version SSMS. Une solution de contournement de ce problème consiste à sauvegarder et restaurer vos bases de données à l’aide d’un compte de stockage Azure en créant un compte de stockage classique, ou à [utiliser T-SQL pour sauvegarder ou restaurer](https://msdn.microsoft.com/library/jj720552(v=sql.120).aspx).

4. **SSMS affiche les comptes de stockage Azure « classiques » uniquement dans les Assistants Sauvegarde et Restauration.**
Les versions de SSMS et du correctif logiciel de juillet affichent les comptes de stockage Azure « classiques » pour la création d’informations d’identification uniquement si vous tentez de sauvegarder ou de restaurer à l’aide des Assistants Sauvegarde et Restauration.
Le correctif de ce problème sera disponible dans une prochaine version SSMS. Une solution de contournement de ce problème consiste à sauvegarder et restaurer vos bases de données à l’aide du compte de stockage Azure « classiques » disponible, ou à sauvegarder sur des comptes de stockage de « type ARM » [en utilisant T-SQL pour sauvegarder ou restaurer](https://msdn.microsoft.com/library/jj720552(v=sql.120).aspx). 

5. **Les installations non anglaises de SSMS peuvent nécessiter l’installation d’un package de sécurité supplémentaire.**
Les versions localisées dans des langues autres que l’anglais nécessitent la [mise à jour de sécurité KB 2862966](https://support.microsoft.com/en-us/kb/2862966) si l’installation est effectuée sur : Windows 8, Windows 7, Windows Server 2012 et Windows Server 2008 R2.
6. **SSMS peut se connecter uniquement à des instances de SQL Server Integrated Services 2016 (SSIS 2016).** Il existe une limitation de compatibilité connue avec SQL Server Integration Services, qui empêche la connexion aux versions précédentes.
Une solution de contournement de ce problème consiste à vous connecter à votre instance de SQL Server Integration Services à l’aide de la version de SSMS correspondant à votre instance SSIS.
7. **SSMS n’enregistre pas les plans de maintenance de SQL Server 2008 R2 et versions antérieures de SQL Server.** Nous développons un correctif pour résoudre ce problème. En attendant, vous pouvez utiliser la version de SSMS 2014 ci-dessous pour enregistrer les plans de maintenance.
8. **Le démarrage du module Gestionnaire de configuration SQL Server échoue si aucun serveur SQL Server n’est installé sur l’ordinateur client.** Si SQL Server n’est pas installé sur votre ordinateur client, lorsque vous démarrez le module Gestionnaire de configuration SQL Server, le message d’erreur « Impossible de se connecter au fournisseur WMI » s’affiche. Solution de contournement :
    * Ouvrez une invite de commandes en tant qu'administrateur.
    * Exécutez l’outil Mofcomp à l’aide de la commande suivante :  
      mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"
    * Après avoir exécuté l’outil Mofcomp, pour que les modifications prennent effet, redémarrez le service WMI à l’aide de la commande suivante :  
       net stop "Windows Management Instrumentation"  
       net start "Windows Management Instrumentation"

**Correctifs**  
1. Résolution de bogue dans le concepteur de requêtes de SSMS pour permettre l’ajout de tables au concepteur si un utilisateur ne dispose pas d’autorisations SELECT sur celles-ci.
2. Résolution de bogue pour ajouter la prise en charge IntelliSense pour les fonctions TRY_CAST() et TRY_CONVERT() [(article Microsoft Connect numéro 2453461)](https://connect.microsoft.com/SQLServer/feedback/details/2453461/sql-server-2012-issue-with-try-cast).
3. Résolution de bogue dans la fenêtre de l’éditeur SSMS pour autoriser l’ouverture par glisser-déplacer de fichiers Sql [(article Microsoft Connect numéro 2690658)](https://connect.microsoft.com/SQLServer/feedback/details/2690658/cannot-drag-sql-files-into-management-studios).
4. Résolution de bogue dans Analysis Services pour afficher correctement le fournisseur de flux de données pour les modèles Analysis Services multidimensionnels.
5. Résolution de bogue dans SSMS pour éviter tout incident lors d’une tentative de modification d’un lien de jointure dans le Concepteur de tables SSMS [(article Microsoft Connect numéro 2721052)](https://connect.microsoft.com/SQLServer/feedback/details/2721052/ssms-view-design-mode-right-click-on-join-crashes-ssms).  

[Informations supplémentaires et résolutions de bogues disponibles dans le journal des modifications de SSMS.](../ssms/sql-server-management-studio-changelog-ssms.md)

---
## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-june-2016-releasehttpgomicrosoftcomfwlinklinkid799832"></a>![télécharger](../ssdt/media/download.png) [version de juillet 2016 de SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkID=799832)

1er juin 2016 | Numéro de version : 13.0.15000.23

**Fonctionnalités**  
Nouveau programme d’installation de SSMS simplifié. Versions de SSMS autonomes. Recherche automatique des mises à jour. Nouvelle boîte de dialogue Recherche rapide. SSMS basé sur le shell Visual Studio 2015, et bien plus encore.   
[Informations supplémentaires disponibles dans le journal des modifications de SSMS.](../ssms/sql-server-management-studio-changelog-ssms.md)

**Problèmes connus** 
1. **La génération de scripts PowerShell à partir de l’Assistant Chiffrement intégral est actuellement désactivée.**
Un correctif de ce problème sera disponible dans une prochaine mise à jour mensuelle de SSMS.
2. **L’option de menu contextuel « Chiffrer les colonnes » dans l’Explorateur d’objets est désactivée pour les tables et les colonnes lorsque vous êtes connecté à Base de données SQL Azure.** Un correctif de ce problème sera disponible dans une prochaine mise à jour mensuelle de SSMS. Une solution de contournement consiste à cliquer avec le bouton droit sur votre base de données dans l’Explorateur d’objets, à sélectionner « Tâches », puis à choisir «Chiffrer les colonnes» afin de chiffrer les tables et les colonnes dans Base de données SQL Azure.
3. **SSMS peut se connecter uniquement à des instances de SQL Server Integrated Services 2016 (SSIS 2016).** Il existe une limitation de compatibilité connue avec SQL Server Integration Services, qui empêche la connexion aux versions précédentes.
Une solution de contournement de ce problème consiste à vous connecter à votre instance de SQL Server Integration Services à l’aide de la version de SSMS correspondant à votre instance SSIS.
4. **SSMS n’enregistre pas les plans de maintenance de SQL Server 2008 R2 et versions antérieures de SQL Server.** Nous développons un correctif pour résoudre ce problème. En attendant, vous pouvez utiliser la version de SSMS 2014 ci-dessous pour enregistrer les plans de maintenance.
5. **Le démarrage du module Gestionnaire de configuration SQL Server échoue si aucun serveur SQL Server n’est installé sur l’ordinateur client.** Si SQL Server n’est pas installé sur votre ordinateur client, lorsque vous démarrez le module Gestionnaire de configuration SQL Server, le message d’erreur « Impossible de se connecter au fournisseur WMI » s’affiche. Solution de contournement :
    * Ouvrez une invite de commandes en tant qu'administrateur.
    * Exécutez l’outil Mofcomp à l’aide de la commande suivante :  
      mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"
    * Après avoir exécuté l’outil Mofcomp, pour que les modifications prennent effet, redémarrez le service WMI à l’aide de la commande suivante :  
       net stop "Windows Management Instrumentation"  
       net start "Windows Management Instrumentation"

**Correctifs**  
1. Boîte de dialogue Recherche rapide dans SSMS, mieux intégrée dans le document actif, et permettant de rechercher des expressions régulières ([article Microsoft Connect n°2735513](https://connect.microsoft.com/SQLServer/feedback/details/2735513/quick-find-replace-in-ssms-2016-rc3/)).
2. Résolution de bogue dans l’aide contextuelle (accessible via la touche F1) de SSMS afin d’afficher correctement les documents et articles d’aide.
3. Résolution de bogue dans la vue « Requêtes régressées » du Magasin de données de requête, qui entraînait le blocage de SSMS lors du défilement.
4. Résolution de bogue dans le connecteur Analysis Services OLEDB d’Excel pour autoriser les connexions d’Excel 2016 à SQL Server Analysis Services.
5. Résolution de bogue dans la boîte de dialogue de connexion de SSMS pour afficher la boîte de dialogue de connexion sur le même moniteur que la fenêtre principale de SSMS dans les systèmes d’écrans multiples ([article Microsoft Connect n°724909)](https://connect.microsoft.com/SQLServer/feedback/details/724909/connection-dialog-appears-off-screen/).
6. Résolution de bogue dans l’expérience de Chiffrement intégral. Résolution du bogue où l’option de menu Chiffrement intégral n’était pas activée correctement pour les bases de données Stretch. Également résolution du bogue de l’Assistant Chiffrement intégral qui n’utilisait pas correctement le fournisseur HSM SafeNet (Luna SA).

---
## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-2014-sp1httpdownloadmicrosoftcomdownload156156992e6-f7c7-4e55-833d-249bd2348138enux86sqlmanagementstudiox86enuexe"></a>![télécharger](../ssdt/media/download.png) [SQL Server Management Studio 2014 SP1](http://download.microsoft.com/download/1/5/6/156992E6-F7C7-4E55-833D-249BD2348138/ENU/x86/SQLManagementStudio_x86_ENU.exe)

14 mai 2015 | Numéro de version : 12.0.4100.1

**Fonctionnalités**  
Prise en charge améliorée d’Azure SQL Database avec nouveau menu Ouvrir dans le portail de gestion, intégration du Concepteur de tables, et bien plus encore.   
[Informations supplémentaires disponibles dans les notes de publication](https://support.microsoft.com/en-us/kb/3058865).

**Problèmes connus**  
Néant

**Correctifs**
1. SSMS se bloque lors de l’exécution de tâches de déplacement du Plan de maintenance si le nom du Plan de maintenance et le premier nom SUB_PLAN sont identiques.
2. Vous ne pouvez pas déboguer une procédure stockée qui appelle sp_executesql dans SQL Server Management Studio (SSMS). Lorsque vous appuyez sur F11, le message d’erreur « Référence d’objet non définie sur une instance de l’objet » s’affiche ([article Microsoft Connect n°736509](https://connect.microsoft.com/SQLServer/feedback/details/736509/sql-server-2012-rtm-management-studio-cannot-debug-sp-executesql)).
3. SSMS ne gère pas complètement le Texte intégral dans SQL Server Express ([article Microsoft Connect n°740181](https://connect.microsoft.com/SQLServer/feedback/details/740181/management-studio-does-not-fully-manage-full-text-in-sql-server-express)).
4. SSMS gère les procédures stockées numérotées de façon incohérente [(article Microsoft Connect n°764197](https://connect.microsoft.com/SQLServer/feedback/details/764197/ssms-2012-inconsistently-handles-numbered-procedures)).
5. SSMS se bloque occasionnellement lors de la fermeture, ce qui entraîne automatiquement son redémarrage ([article Microsoft Connect n°774317](https://connect.microsoft.com/SQLServer/feedback/details/774317/sql-server-management-studio-2012-2014-crashes-when-closing)).
6. Créer un script a pour effet de dupliquer les instructions lorsque le script a trait aux autorisations au niveau des colonnes dans SSMS ([article Microsoft Connect n°797967](https://connect.microsoft.com/SQLServer/feedback/details/797967/ssms-create-script-duplicates-the-statements-for-grant-or-deny-column-permissions)).
7. SSMS peut se bloquer lorsque vous tentez d’actualiser l’icône de la fenêtre de SSMS dans la barre des tâches ([article Microsoft Connect n°799430](https://connect.microsoft.com/SQLServer/feedback/details/799430/ssms-2012-sp-1-cu-5-installed-crash-when-enforce-refresh-on-connect)).

---
## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-2012-sp3httpdownloadmicrosoftcomdownloadf67f673709c-d371-4a64-8bf9-c1dd73f60990enux86sqlmanagementstudiox86enuexe"></a>![télécharger](../ssdt/media/download.png) [SQL Server Management Studio 2012 SP3](http://download.microsoft.com/download/F/6/7/F673709C-D371-4A64-8BF9-C1DD73F60990/ENU/x86/SQLManagementStudio_x86_ENU.exe)  
  
21 novembre 2015 | Numéro de version : 11.0.6020.0

**Fonctionnalités**  
Éditions SSMS Express complètes. Extraits de code. Index de magasins de colonnes, et bien plus encore.  
[Informations supplémentaires disponibles dans les notes de publication.](https://support.microsoft.com/en-us/kb/3072779)
 
**Problèmes connus**  
Néant

**Correctifs**
1. Les colonnes manquantes ne peuvent pas être indiquées dans le message d’erreur lorsque vous importez des données à l’aide de l’Assistant d’importation et d’exportation.
2. Message d’erreur « Impossible de créer un plan de restauration en raison d’arrêt dans la chaîne de NSE » lorsque vous restaurez une sauvegarde différentielle dans SSMS

---
## <a name="additional-downloads"></a>Téléchargements supplémentaires  
Pour obtenir la liste de tous les téléchargements de SQL Server Management Studio, rechercher dans le [Centre de téléchargement Microsoft](https://www.microsoft.com/en-us/download/search.aspx?q=sql%20server%20management%20studio&p=0&r=10&t=&s=Relevancy~Descending).  
  
Pour obtenir la dernière version de SQL Server Management Studio, voir [Télécharger SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md).  

---  
## <a name="related-resources"></a>Ressources connexes
[Update Center pour Microsoft SQL Server](https://technet.microsoft.com/sqlserver/ff803383.aspx)   
[Démarrage rapide de SQL Server Management Studio](http://msdn.microsoft.com/en-us/d2bade70-07cf-4d94-b5d2-88aecb538ed1)  
[Forum sur SQL Server Management Studio](https://social.msdn.microsoft.com/forums/en-us/home?forum=sqltools)  

  

