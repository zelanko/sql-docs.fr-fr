---
title: "Télécharger SQL Server Management Studio (SSMS) | Microsoft Docs"
ms.custom: 
ms.date: 06/27/2017
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
ms.translationtype: Human Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 60bdb820d74be98dd051d4729463d375d2a5202a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/03/2017

---
<a id="download-sql-server-management-studio-ssms" class="xliff"></a>

# Télécharger SQL Server Management Studio (SSMS)
SQL Server Management Studio (SSMS) est un environnement intégré pour la gestion des infrastructures SQL, de SQL Server à SQL Database. SSMS fournit des outils permettant de configurer, de surveiller et d’administrer les instances de SQL Server, quel que soit l’endroit d’où vous les déployez. Avec SSMS, vous pouvez déployer, surveiller et mettre à niveau les composants de la couche Données utilisés par vos applications, mais aussi créer des requêtes et des scripts. 

Cette version présente une meilleure compatibilité avec les versions précédentes de SQL Server, un programme d’installation web autonome, ainsi que des notifications toast dans SSMS quand de nouvelles versions deviennent disponibles.  
  
Le ![téléchargement](../ssdt/media/download.png) de SSMS est gratuit ! **[Télécharger SQL Server Management Studio 17.1](https://go.microsoft.com/fwlink/?linkid=849819)**  SSMS 17.X est la dernière génération de SQL Server Management Studio et fournit la prise en charge de SQL Server 2017. 

![télécharger](../ssdt/media/download.png) **[Télécharger le package de mise à niveau de SQL Server Management Studio 17.1 (mises à niveau de 17.0 vers 17.1)](https://go.microsoft.com/fwlink/?linkid=849821)**

> [!NOTE]
> Le module PowerShell de SQL Server est désormais une installation distincte que vous pouvez effectuer par l’intermédiaire de la galerie PowerShell.  Pour plus d'informations, consultez les [instructions de téléchargement](download-sql-server-ps-module.md).

<a id="sql-server-management-studio" class="xliff"></a>

## SQL Server Management Studio   
**Informations sur la version**  
  
Numéro de la version : 17.1  
Numéro de build de cette version : 14.0.17119.0

<a id="new-in-this-release" class="xliff"></a>

## Nouveautés de cette version  

SSMS 17.1 est la première mise à jour de la génération 17.X de SQL Server Management Studio.  La génération 17.X prend en charge presque toutes les fonctionnalités de SQL Server 2008 à SQL Server 2017.  La version 17.X est également la génération de SSMS qui prend en charge SQL Analysis Service PaaS.

La version 17.1 inclut :

* Des correctifs pour plusieurs problèmes signalés par les utilisateurs 
* Un nouvel outil de gestion de scale-out Integration Services

Pour obtenir la liste complète des modifications, consultez   
                [SQL Server Management Studio : journal des modifications (SSMS)](../ssms/sql-server-management-studio-changelog-ssms.md)  
   
Pour plus d’informations sur la collecte de données utilisateur, consultez   
                [Déclaration de confidentialité de SQL Server](http://www.microsoft.com/privacystatement/en-us/SQLServer/Default.aspx) 
  
<a id="supported-sql-offerings" class="xliff"></a>

## Produits SQL pris en charge
  
* Cette version de SSMS fonctionne avec toutes les [versions prises en charge de SQL Server 2008 - SQL Server 2017](https://support.microsoft.com/en-us/lifecycle?C2=1044) et offre le meilleur niveau de prise en charge pour une utilisation des dernières fonctionnalités cloud dans Azure SQL Database et Azure SQL Data Warehouse.  
* Il n’existe aucun bloc explicite pour SQL Server 2000 ni SQL Server 2005, mais certaines fonctionnalités peuvent ne pas fonctionner correctement.  
* Par ailleurs, SSMS 17.X peut être installé côte à côte avec SSMS 16.X ou SQL Server 2014 SSMS et versions antérieures. 
  
<a id="supported-operating-systems" class="xliff"></a>

## Systèmes d’exploitation pris en charge
  
Cette version de SSMS prend en charge les plateformes suivantes quand elle est utilisée avec le dernier Service Pack :   
- Windows 10
- Windows 8.1
- Windows 8
- Windows 7 (SP1)
- Windows Server 2016
- Windows Server 2012 (64 bits) 
- Windows Server 2012 R2 (64 bits) 
- Windows Server 2008 R2 (64 bits)  

>[!NOTE]
>SSMS 17.X est basé sur le shell isolé Visual Studio 2015, qui a été publié avant Windows Server 2016. Microsoft prend au sérieux la compatibilité des applications et vérifie que les applications déjà livrées continuent à s’exécuter sur les dernières versions de Windows. Pour réduire les problèmes liés à l’exécution de SSMS sur Windows Server 2016, vérifiez que vous avez appliqué toutes les mises à jour de SSMS. Si vous rencontrez des problèmes avec SSMS sur Windows Server 2016, contactez le support. La prise en charge détermine si le problème est lié à SSMS, Visual Studio ou à la compatibilité de Windows, et si le problème est adressé à la bonne équipe.

<a id="ssms-installation-tips-and-issues" class="xliff"></a>

## Problèmes et conseils pour l’installation de SSMS
**Réduire les redémarrages de l’installation**

- Prenez les mesures suivantes pour réduire les possibilités que le programme d’installation de SSMS nécessite un redémarrage à la fin de l’installation :
  - Vérifiez que vous exécutez une version à jour de Visual C++ 2013 Redistributable Package. La version 12.00.40649.5 (ou version ultérieure) est nécessaire. Seule la version x64 est nécessaire.
  - Vérifiez que la version du .NET Framework sur l’ordinateur est 4.6.1 (ou version ultérieure).
  - Fermez toutes les autres instances de Visual Studio ouvertes sur l’ordinateur.
  - Vérifiez que toutes les dernières mises à jour du système d’exploitation sont installées sur l’ordinateur.
  - Les actions indiquées sont généralement nécessaires une seule fois. Dans certains cas, un redémarrage est nécessaire pendant les mises à niveau supplémentaires appliquées à la même version principale de SSMS. Pour les mises à niveau mineures, tous les prérequis de SSMS sont déjà installés sur l’ordinateur.

- Pour obtenir la liste des problèmes connus et des solutions de contournement, consultez [SQL Server Management Studio - Notes de publication](../ssms/sql-server-management-studio-release-notes.md)

<a id="available-languages" class="xliff"></a>

## Langues disponibles  
> Les versions localisées dans des langues autres que l’anglais nécessitent la [mise à jour de sécurité KB 2862966](https://support.microsoft.com/en-us/kb/2862966) si l’installation est effectuée sur : Windows 8, Windows 7, Windows Server 2012 et Windows Server 2008 R2. 
  
Cette version de SSMS peut être installée dans les langues suivantes :

SQL Server Management Studio 17.1 :<br>
[Chinois (République populaire de Chine)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x804) | [Chinois (Taïwan)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x40a)

Package de mise à niveau de SQL Server Management Studio 17.1 (mises à niveau de 17.0 vers 17.1) :<br>
[chinois (République populaire de Chine)](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x804) | [chinois (Taïwan)](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x404) | [anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x409) | [français](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x40c) | [allemand](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x407) | [italien](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x410) | [japonais](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x411) | [coréen](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x412) | [portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x416) | [russe](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x419) | [espagnol](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x40a)

<a id="previous-releases" class="xliff"></a>

## Versions antérieures  
[Versions antérieures de SQL Server Management Studio](../ssms/previous-sql-server-management-studio-releases.md)  
  
<a id="feedback" class="xliff"></a>

## Commentaires  
  
![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [Forum des outils clients SQL](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Signaler un problème ou faire une suggestion sur Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback)  
  
<a id="see-also" class="xliff"></a>

## Voir aussi  
[Didacticiel : SQL Server Management Studio](http://msdn.microsoft.com/en-us/d2bade70-07cf-4d94-b5d2-88aecb538ed1)  
[Documentation de SQL Server Management Studio](https://msdn.microsoft.com/library/hh213248(v=sql.130).aspx)  
[Microsoft SQL Server](https://msdn.microsoft.com/library/bb545450.aspx)  
[Service Packs et mises à jour supplémentaires](https://technet.microsoft.com/sqlserver/ff803383.aspx)  
[Télécharger SSDT (SQL Server Data Tools)](../ssdt/download-sql-server-data-tools-ssdt.md)  



