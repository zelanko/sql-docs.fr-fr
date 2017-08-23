---
title: "Télécharger SQL Server Management Studio (SSMS) | Microsoft Docs"
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "installer ssms, télécharger ssms, dernière version de ssms"
- SQL Server Management Studio
- ssms.exe
- sql man studio
- sql management studio
- installation de sql management studio
- "télécharger sql management studio"
- ms sql management studio
- installer sql management studio
- ssms download
- sql server ssms
- ssms express
ms.assetid: adafeeef-4255-4924-8042-02f503d599ca
caps.latest.revision: 145
author: stevestein
ms.author: sstein
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 3f12671ace99d5fefc199c7b1c2db31e5b3cfade
ms.openlocfilehash: a689293fadb1a442f94d88cc06a9e7a4ef06650f
ms.contentlocale: fr-fr
ms.lasthandoff: 08/08/2017

---
# <a name="download-sql-server-management-studio-ssms"></a>Télécharger SQL Server Management Studio (SSMS)

SSMS est un environnement intégré pour la gestion des infrastructures SQL, de SQL Server à SQL Database. SSMS fournit des outils pour configurer, surveiller et administrer les instances de SQL. Utilisez SSMS pour déployer, surveiller et mettre à niveau les composants de la couche Données utilisés par vos applications, mais aussi pour créer des requêtes et des scripts.

Utilisez SQL Server Management Studio (SSMS) pour interroger, concevoir et gérer vos bases de données et entrepôts de données, où qu’ils se trouvent (sur votre ordinateur local ou dans le cloud).

**SSMS est gratuit !**

SSMS 17.x est la dernière génération de *SQL Server Management Studio* et fournit la prise en charge de SQL Server 2017.

**[![télécharger](../ssdt/media/download.png) Télécharger SQL Server Management Studio 17.2](https://go.microsoft.com/fwlink/?linkid=854085)**

**[![télécharger](../ssdt/media/download.png) Télécharger le package de mise à niveau de SQL Server Management Studio 17.2 (mises à niveau 17.x à 17.2)](https://go.microsoft.com/fwlink/?linkid=854087)**

L’installation de SSMS 17.x ne met pas à niveau ni ne remplace les versions 16.x ou antérieures de SSMS. SSMS 17.x s’installe côte à côte avec les versions précédentes pour que vous puissiez utiliser les deux versions.
Si un ordinateur contient des installations côte à côte de SSMS, vérifiez que vous démarrez la version adaptée à vos besoins spécifiques. La version la plus récente est étiquetée *Microsoft SQL Server Management Studio 17* et a une nouvelle icône : 
 
   ![SSMS 17.x](media/download-sql-server-management-studio-ssms/version-icons.png)


> [!NOTE]
> Le module PowerShell de SQL Server est désormais une installation distincte que vous pouvez effectuer par l’intermédiaire de la galerie PowerShell.  Pour plus d'informations, consultez les [instructions de téléchargement](download-sql-server-ps-module.md).

## <a name="sql-server-management-studio"></a>SQL Server Management Studio

**Informations sur la version**

Numéro de build : 17.2 Numéro de build de cette version : 14.0.17177.0

## <a name="new-in-this-release"></a>Nouveautés de cette version

SSMS 17.2 est la dernière version de SQL Server Management Studio. La génération 17.x de SSMS prend en charge presque tous les composants de SQL Server 2008 à SQL Server 2017. La version 17.x prend également en charge la PaaS SQL Analysis Services.

La version 17.2 inclut :

- L’authentification multifacteur (MFA)
  - L’authentification de plusieurs utilisateurs Azure AD pour une authentification universelle avec l’authentification multifacteur (agent utilisateur avec MFA)
  - Un nouveau champ d’entrée des informations d’identification de l’utilisateur a été ajouté pour l’authentification universelle avec MFA afin de prendre en charge l’authentification de plusieurs utilisateurs.
- La boîte de dialogue de connexion prend désormais en charge les 5 méthodes d’authentification suivantes :
  - Authentification Windows
  - Authentification SQL Server
  - Active Directory - Authentification universelle avec prise en charge de MFA
  - Active Directory - Authentification par mot de passe
  - Active Directory - Authentification intégrée

- L’Assistant Importation/exportation de base de données pour DacFx peut désormais utiliser l’authentification universelle avec MFA.
- Pour la prise en charge de l’API, consultez [IUniversalAuthProvider Interface](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.iuniversalauthprovider.aspx) (Interface IUniversalAuthProvider).
- La bibliothèque ADAL gérée utilisée par l’authentification universelle Azure AD avec MFA a été mise à niveau vers la version 3.13.9.
- Nouvelle interface CLI prenant en charge le paramètre d’administration Azure AD pour SQL Database et SQL Data Warehouse.

 Pour plus d’informations sur les méthodes d’authentification Active Directory, consultez [Authentification universelle avec SQL Database et SQL Data Warehouse (prise en charge de SSMS pour MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication) et [Configurer l’authentification multifacteur Azure SQL Database pour SQL Server Management Studio](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication-configure).

- La fenêtre Sortie a des entrées pour les requêtes exécutées pendant le développement des nœuds de l’Explorateur d’objets
- Concepteur de vues activé pour les bases de données Azure SQL Database
- Les options de script par défaut pour les objets de script dans l’Explorateur d’objets de SSMS ont changé :
  - Avant, la valeur par défaut pour une nouvelle installation spécifiait que le script généré devait cibler la dernière version de SQL Server (actuellement SQL Server 2017).
  - Dans SSMS 17.2, une nouvelle option a été ajoutée : *Faire correspondre les paramètres de script à la source*. Quand la valeur est définie sur *True*, le script généré cible les mêmes version, type de moteur et édition de moteur que le serveur à partir duquel l’objet est scripté.
  - Comme la valeur de *Faire correspondre les paramètres de script à la source* est définie sur *True* par défaut, les nouvelles installations de SSMS scriptent toujours automatiquement par défaut les objets sur la même cible que celle du serveur d’origine.
  - Quand la valeur de *Faire correspondre les paramètres de script à la source* est définie sur *False*, les options de cible de script normales sont activées et fonctionnent comme avant.
  - Par ailleurs, toutes les options de script ont été déplacées dans leur propre section - *Options de version*. Elles ne sont plus sous *Options de script générales*.

- Nouvelle prise en charge des clouds nationaux dans « Restaurer à partir de l’URL »
- Les rapports QueryStoreUI prennent désormais en charge des métriques supplémentaires (RowCount, DOP, CLR Time, etc.) de sys.query_store_runtime_stats.
- IntelliSense est maintenant pris en charge par Azure SQL Database
    - https://connect.microsoft.com/SQLServer/feedback/details/3100677/ssms-2016-would-be-nice-to-have-intellisense-on-azure-sql-databases
- Sécurité : par défaut, la boîte de dialogue de connexion ne fait pas confiance aux certificats de serveur et demande le chiffrement des connexions Azure SQL Database
- Améliorations générales de la prise en charge de SQL Server sur Linux :
 - Le nœud Messagerie de base de données est de retour
 - Différents problèmes concernant les chemins ont été traités
 - Améliorations de la stabilité du moniteur d’activité
 - La boîte de dialogue Propriétés de connexion affiche la plateforme appropriée
- Le rapport de serveur Tableau de bord des performances est désormais disponible comme rapport par défaut :
  - Peut se connecter à SQL Server 2008 et versions ultérieures.
  - Le sous-rapport Index manquants utilise la notation pour permettre d’identifier les index plus utiles.
  - Le sous-rapport Historique des statistiques d’attente regroupe maintenant les attentes par catégorie. Les attentes d’inactivité et de mise en veille sont filtrées par défaut.
  - Nouveau sous-rapport Historique des verrous.
- La recherche de nœuds de plan d’exécution de requêtes permet d’effectuer des recherches dans les propriétés de plan. Recherchez facilement n’importe quelle propriété d’opérateur, comme un nom de table. Pour utiliser cette option quand vous affichez un plan :
  - Cliquez avec le bouton droit sur le plan et, dans le menu contextuel, cliquez sur l’option Rechercher un nœud
  - Utiliser Ctrl+F

Pour obtenir la liste complète des modifications, consultez [SQL Server Management Studio - Journal des modifications (SSMS)](../ssms/sql-server-management-studio-changelog-ssms.md).

Pour plus d’informations sur la collecte de données utilisateur, consultez la [Déclaration de confidentialité de SQL Server](http://www.microsoft.com/privacystatement/en-us/SQLServer/Default.aspx).

## <a name="supported-sql-offerings"></a>Produits SQL pris en charge

* Cette version de SSMS fonctionne avec toutes les [versions prises en charge de SQL Server 2008 - SQL Server 2017](https://support.microsoft.com/lifecycle?C2=1044) et offre le meilleur niveau de prise en charge pour une utilisation des dernières fonctionnalités cloud dans Azure SQL Database et Azure SQL Data Warehouse.
* Il n’existe aucun bloc explicite pour SQL Server 2000 ni SQL Server 2005, mais certaines fonctionnalités peuvent ne pas fonctionner correctement.
* Par ailleurs, SSMS 17.x peut être installé côte à côte avec SSMS 16.x ou SQL Server 2014 SSMS et version antérieure.

## <a name="supported-operating-systems"></a>Systèmes d’exploitation pris en charge
  
Cette version de SSMS prend en charge les plateformes 64 bits suivantes quand elle est utilisée avec le dernier Service Pack :
- Windows 10 (64 bits)
- Windows 8.1 (64 bits)
- Windows 8 (64 bits)
- Windows 7 (SP1) (64 bits)
- Windows Server 2016 *
- Windows Server 2012 R2 (64 bits)
- Windows Server 2012 (64 bits)
- Windows Server 2008 R2 (64 bits)

\* SSMS 17.X est basé sur le shell isolé Visual Studio 2015, qui a été publié avant Windows Server 2016. Microsoft prend au sérieux la compatibilité des applications et vérifie que les applications déjà livrées continuent à s’exécuter sur les dernières versions de Windows. Pour réduire les problèmes liés à l’exécution de SSMS sur Windows Server 2016, vérifiez que vous avez appliqué toutes les mises à jour de SSMS. Si vous rencontrez des problèmes avec SSMS sur Windows Server 2016, contactez le support. L’équipe de support détermine si le problème est lié à SSMS, Visual Studio ou à la compatibilité de Windows. Puis, l’équipe de support achemine le problème vers l’équipe appropriée pour un examen approfondi.

## <a name="ssms-installation-tips-and-issues"></a>Problèmes et conseils pour l’installation de SSMS

### <a name="minimize-installation-reboots"></a>Réduire les redémarrages de l’installation

* Prenez les mesures suivantes pour réduire les possibilités que le programme d’installation de SSMS nécessite un redémarrage à la fin de l’installation :
  * Vérifiez que vous exécutez une version à jour de Visual C++ 2013 Redistributable Package. La version 12.00.40649.5 (ou version ultérieure) est nécessaire. Seule la version x64 est nécessaire.
  * Vérifiez que la version du .NET Framework sur l’ordinateur est 4.6.1 (ou version ultérieure).
  * Fermez toutes les autres instances de Visual Studio ouvertes sur l’ordinateur.
  * Vérifiez que toutes les dernières mises à jour du système d’exploitation sont installées sur l’ordinateur.
  * Les actions indiquées sont généralement nécessaires une seule fois. Dans certains cas, un redémarrage est nécessaire pendant les mises à niveau supplémentaires appliquées à la même version principale de SSMS. Pour les mises à niveau mineures, tous les prérequis de SSMS sont déjà installés sur l’ordinateur.

* Pour obtenir la liste des problèmes connus et des solutions de contournement, consultez [SQL Server Management Studio - Notes de publication](../ssms/sql-server-management-studio-release-notes.md)

## <a name="available-languages"></a>Langues disponibles

> [!NOTE]
> Les versions localisées dans des langues autres que l’anglais nécessitent la [mise à jour de sécurité KB 2862966](https://support.microsoft.com/en-us/kb/2862966) si l’installation est effectuée sur : Windows 8, Windows 7, Windows Server 2012 et Windows Server 2008 R2.

Cette version de SSMS peut être installée dans les langues suivantes :

SQL Server Management Studio 17.2 :<br>
[chinois (République populaire de Chine)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x804) | [chinois (Taïwan)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x404) | [anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x409) | [français](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40c) | [allemand](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x407) | [italien](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x410) | [japonais](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x411) | [coréen](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x412) | [portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x416) | [russe](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x419) | [espagnol](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40a)

Package de mise à niveau de SQL Server Management Studio 17.2 (mises à niveau 17.x à 17.2) :<br>
[chinois (République populaire de Chine)](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x804) | [chinois (Taïwan)](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x404) | [anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x409) | [français](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x40c) | [allemand](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x407) | [italien](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x410) | [japonais](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x411) | [coréen](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x412) | [portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x416) | [russe](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x419) | [espagnol](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x40a)

## <a name="release-notes"></a>Notes de publication

Voici les problèmes et limitations de cette version 17.2 :

- Les fenêtres de requête qui utilisent l’authentification « Active Directory – Authentification universelle avec prise en charge de MFA » peuvent rencontrer une erreur similaire à la suivante, quand vous tentez d’exécuter une requête ouverte depuis au moins une heure :

   `Msg 0, Level 11, State 0, Line 0
The connection is broken and recovery is not possible. The client driver attempted to recover the connection one or more times and all attempts failed. Increase the value of *ConnectRetryCount* to increase the number of recovery attempts.`

   La réexécution de la requête doit permettre de surmonter l’erreur.

- Les fonctionnalités SSMS suivantes ne sont pas prises en charge par Azure AD qui utilise l’authentification universelle avec MFA :
  - Le concepteur **Nouvelle table/vue** affiche l’ancienne invite de connexion et ne fonctionne pas pour l’authentification Azure AD.
  - La fonctionnalité **Modifier les 200 premières lignes** ne prend pas en charge l’authentification Azure AD.
  - Le composant **Serveur inscrit** ne prend pas en charge l’authentification Azure AD.
  - L’**Assistant Paramétrage du moteur de base de données** n’est pas pris en charge pour l’authentification Azure AD. Il existe un problème connu où le message d’erreur présenté à l’utilisateur est loin d’être utile : *Impossible de charger le fichier ou l’assembly ’Microsoft.IdentityModel.Clients.ActiveDirectory,...* au lieu du message attendu : *L’Assistant Paramétrage du moteur de base de données ne prend pas en charge Microsoft Azure SQL Database. (DTAClient)* .

**AS**

- L’Explorateur d’objets dans SSAS n’affiche pas le nom d’utilisateur de l’authentification Windows dans les propriétés de connexion d’Azure AS.
Pour plus d’informations, consultez le [Journal des modifications de SSMS](sql-server-management-studio-changelog-ssms.md).

## <a name="previous-releases"></a>Versions antérieures

[Versions antérieures de SQL Server Management Studio](../ssms/sql-server-management-studio-changelog-ssms.md#previous-ssms-releases)

## <a name="feedback"></a>Commentaires

![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [Forum des outils clients SQL](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Signaler un problème ou faire une suggestion sur Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback)

## <a name="see-also"></a>Voir aussi

- [Didacticiel : SQL Server Management Studio](tutorials/tutorial-sql-server-management-studio.md)
- [Documentation de SQL Server Management Studio](sql-server-management-studio-ssms.md)
- [Service Packs et mises à jour supplémentaires](https://technet.microsoft.com/sqlserver/ff803383.aspx)
- [Télécharger SSDT (SQL Server Data Tools)](../ssdt/download-sql-server-data-tools-ssdt.md)

