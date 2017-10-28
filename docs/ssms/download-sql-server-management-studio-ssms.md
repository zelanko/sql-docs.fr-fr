---
title: "Télécharger SQL Server Management Studio (SSMS) | Microsoft Docs"
ms.custom: 
ms.date: 10/09/2017
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
ms.workload: Active
ms.translationtype: HT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: be3d22491e1cf5e6446f9ac597d613e1d203a28e
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="download-sql-server-management-studio-ssms"></a>Télécharger SQL Server Management Studio (SSMS)

SSMS est un environnement intégré pour la gestion des infrastructures SQL, de SQL Server à SQL Database. SSMS fournit des outils pour configurer, surveiller et administrer les instances de SQL. Utilisez SSMS pour déployer, surveiller et mettre à niveau les composants de la couche Données utilisés par vos applications, mais aussi pour créer des requêtes et des scripts.

Utilisez SQL Server Management Studio (SSMS) pour interroger, concevoir et gérer vos bases de données et entrepôts de données, où qu’ils se trouvent (sur votre ordinateur local ou dans le cloud).

**SSMS est gratuit !**

SSMS 17.x est la dernière génération de *SQL Server Management Studio* et fournit la prise en charge de SQL Server 2017.

**[![télécharger](../ssdt/media/download.png) Télécharger SQL Server Management Studio 17.3](https://go.microsoft.com/fwlink/?linkid=858904)**

**[![télécharger](../ssdt/media/download.png) Télécharger le package de mise à niveau de SQL Server Management Studio 17.3 (mises à niveau 17.x à 17.3)](https://go.microsoft.com/fwlink/?linkid=858906)**

L’installation de SSMS 17.x ne met pas à niveau ni ne remplace les versions 16.x ou antérieures de SSMS. SSMS 17.x s’installe côte à côte avec les versions précédentes pour que vous puissiez utiliser les deux versions.
Si un ordinateur contient des installations côte à côte de SSMS, vérifiez que vous démarrez la version adaptée à vos besoins spécifiques. La version la plus récente est étiquetée *Microsoft SQL Server Management Studio 17* et a une nouvelle icône : 
 
   ![SSMS 17.x](media/download-sql-server-management-studio-ssms/version-icons.png)


> [!NOTE]
> Le module PowerShell de SQL Server est désormais une installation distincte que vous pouvez effectuer par l’intermédiaire de la galerie PowerShell.  Pour plus d'informations, consultez les [instructions de téléchargement](download-sql-server-ps-module.md).

## <a name="sql-server-management-studio"></a>SQL Server Management Studio

**Informations sur la version**

Numéro de version : 17.3

Numéro de build de cette version : 14.0.17199.0

## <a name="new-in-this-release"></a>Nouveautés de cette version

SSMS 17.3 est la nouvelle version de SQL Server Management Studio. La génération 17.x de SSMS prend en charge presque tous les composants de SQL Server 2008 à SQL Server 2017. La version 17.x prend également en charge la PaaS SQL Analysis Services.

Contenu de la version 17.3 :

- Ajout du nouvel Assistant « Importer un fichier plat » pour simplifier l’importation des fichiers CSV avec une infrastructure intelligente, nécessitant une intervention de l’utilisateur ou des connaissances techniques minimes. Pour plus d’informations, consultez [Assistant Importer un fichier plat dans SQL](../relational-databases/import-export/import-flat-file-wizard.md).
- Ajout du nœud « XEvent Profiler » à l’Explorateur d’objets. Pour plus d’informations, consultez [Utiliser SSMS XEvent Profiler](../relational-databases/extended-events/use-the-ssms-xe-profiler.md).
- Mise à jour du filtrage et de la catégorisation des attentes dans le rapport des attentes historiques du Tableau de bord Performances.
- Ajout de la vérification syntaxique de la fonction « Predict ».
- Ajout de la vérification syntaxique des requêtes External Library Management.
- Ajout de la prise en charge SMO pour External Library Management.
- Ajout de la prise en charge de « Démarrer PowerShell » dans la fenêtre « Serveurs inscrits » (nécessite un nouveau module SQL PowerShell).
- AlwaysOn : ajout de la [prise en charge du routage en lecture seule](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md) pour les groupes de disponibilité.
- Ajout d’une option pour envoyer les informations de trace dans la fenêtre Sortie pour les connexions « Active Directory - Authentification universelle avec prise en charge de MFA » (option désactivée par défaut ; doit être activée dans les paramètres utilisateur sous « Outils > Options > Services Azure > Azure Cloud > Niveau de trace dans la fenêtre Sortie ADAL »). 
- Magasin des requêtes : 
  - L’interface utilisateur Magasin des requêtes est maintenant accessible même quand QDS est désactivé, si QDS a enregistré des données.
  - L’interface utilisateur Magasin des requêtes expose maintenant les attentes par catégorie dans tous les rapports existants. Cela permet aux clients de gérer les scénarios avec des requêtes principales en attente, par exemple.
- Ajout des en-têtes de paramètres de script rendu facultatif (désactivé par défaut ; peut être activé dans les paramètres utilisateur sous « Outils > Options > Explorateur d’objets SQL Server > Scripts > Inclure l’en-tête des paramètres de script ») - [Article Connect 3139199](https://connect.microsoft.com/SQLServer/feedback/details/3139199).
- Suppression de la personnalisation « RC ».

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

SQL Server Management Studio 17.3 :<br>
[chinois (République populaire de Chine)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x804) | [chinois (Taïwan)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x404) | [anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x409) | [français](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40c) | [allemand](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x407) | [italien](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x410) | [japonais](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x411) | [coréen](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x412) | [portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x416) | [russe](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x419) | [espagnol](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40a)

Package de mise à niveau de SQL Server Management Studio 17.3 (mises à niveau 17.x à 17.3) :<br>
[chinois (République populaire de Chine)](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x804) | [chinois (Taïwan)](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x404) | [anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x409) | [français](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x40c) | [allemand](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x407) | [italien](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x410) | [japonais](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x411) | [coréen](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x412) | [portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x416) | [russe](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x419) | [espagnol](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x40a)

## <a name="release-notes"></a>Notes de publication

Voici les problèmes et limitations de cette version 17.3 :

**SSMS général**

- Les fonctionnalités SSMS suivantes ne sont pas prises en charge pour l’authentification Azure AD qui utilise l’agent utilisateur avec MFA :
   - L’Assistant Paramétrage du moteur de base de données n’est pas pris en charge pour l’authentification Azure AD. Il existe un problème connu où le message d’erreur présenté à l’utilisateur n’est pas très clair : « Impossible de charger le fichier ou l’assembly 'Microsoft.IdentityModel.Clients.ActiveDirectory,... » au lieu du message attendu : « L’Assistant Paramétrage du moteur de base de données ne prend pas en charge Microsoft Azure SQL Database. (DTAClient) ».
- La tentative d’analyse d’une requête dans les résultats DTA provoque une erreur : « L’objet doit implémenter IConvertible. mscorlib ».
- L’option *Requêtes régressées* ne figure pas dans la liste Magasin des requêtes des rapports affichés dans l’Explorateur d’objets.
   - Solution de contournement : cliquez avec le bouton droit sur le nœud **Magasin des requêtes** et sélectionnez **Afficher les requêtes régressées**.

**Integration Services (IS)**

- Le paramètre [execution_path] dans [catalog].[event_message] n’est pas correct pour les exécutions de package dans Scale Out. [execution_path] commence par « \Package » au lieu du nom d’objet du package exécutable. Quand vous affichez le rapport Vue d’ensemble des exécutions de package dans SSMS, le lien « Chemin d’accès de l’exécution » dans Vue d’ensemble de l’exécution ne fonctionne pas. Solution de contournement : cliquez sur « Afficher les messages » dans le rapport Vue d’ensemble pour vérifier tous les messages d’événement.



## <a name="previous-releases"></a>Versions antérieures

[Versions antérieures de SQL Server Management Studio](../ssms/sql-server-management-studio-changelog-ssms.md#previous-ssms-releases)

## <a name="feedback"></a>Commentaires

![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [Forum des outils clients SQL](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Signaler un problème ou faire une suggestion sur Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback)

## <a name="see-also"></a>Voir aussi

- [Didacticiel : SQL Server Management Studio](tutorials/tutorial-sql-server-management-studio.md)
- [Documentation de SQL Server Management Studio](sql-server-management-studio-ssms.md)
- [Service Packs et mises à jour supplémentaires](https://technet.microsoft.com/sqlserver/ff803383.aspx)
- [Télécharger SSDT (SQL Server Data Tools)](../ssdt/download-sql-server-data-tools-ssdt.md)

