---
title: "Télécharger SQL Server Management Studio (SSMS) | Microsoft Docs"
ms.custom: 
ms.date: 04/03/2017
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
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: cc827737cec19c11d2102f968dc2b8bc638bda86
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="download-sql-server-management-studio-ssms"></a>Télécharger SQL Server Management Studio (SSMS)
SQL Server Management Studio (SSMS) est un environnement intégré d’accès, de configuration, de gestion, d’administration et de développement de tous les composants de SQL Server. SSMS associe un groupe d’outils graphiques à des éditeurs de script performants pour permettre aux développeurs et aux administrateurs de tous niveaux d’avoir accès à SQL Server. Cette version présente une meilleure compatibilité avec les versions précédentes de SQL Server, un programme d’installation web autonome, ainsi que des notifications toast dans SSMS quand de nouvelles versions deviennent disponibles.  

    
| ![téléchargement](../ssdt/media/download.png) Télécharger SQL Server Management Studio (SSMS)  |  |
|:---|:---|
|**[Télécharger SQL Server Management Studio (16.5.3)](https://go.microsoft.com/fwlink/?LinkID=840946)**|Version actuelle pour l’utilisation en production.|
|**[Télécharger SQL Server Management Studio - Release Candidate (17.0 RC3)](../ssms/sql-server-management-studio-ssms-release-candidate.md)**|Prend en charge SQL Server vNext CTP1.3 et fonctionne côte à côte avec la version 16.x, mais non recommandé pour la production.| 


> [!NOTE]
> Les versions de SSMS sont désormais étiquetées numériquement, pas par mois. SSMS est gratuit ! Aucune licence n’est exigée pour l’installer et l’utiliser.  


## <a name="sql-server-management-studio"></a>SQL Server Management Studio   
**Informations sur la version**  
  
Numéro de la version : 16.5.3  
Numéro de build de cette version : 13.0.16106.4
  
**Versions de SQL Server prises en charge**  
  
* Cette version de SSMS fonctionne avec toutes les [versions prises en charge de SQL Server (SQL Server 2008 à SQL Server 2016)](https://support.microsoft.com/en-us/lifecycle?C2=1044) , et offre le meilleur niveau de prise en charge pour une utilisation avec les dernières fonctionnalités de cloud dans Azure SQL Database et Azure SQL Data Warehouse.  
* Il n’existe aucun bloc explicite pour SQL Server 2000 ni SQL Server 2005, mais certaines fonctionnalités peuvent ne pas fonctionner correctement.  
* En outre, une version de SSMS 16.x ou SSMS 2016 peut être installée côte à côte avec les versions précédentes de SSMS 2014 et antérieur. 
  
**Systèmes d’exploitation pris en charge**  
  
Cette version de SSMS prend en charge les plateformes suivantes quand elle est utilisée avec le dernier Service Pack :   
 Windows 10, Windows 8, Windows 8.1, Windows 7 (SP1), Windows Server 2012 (64 bits), Windows Server 2012 R2 (64 bits), Windows Server 2008 R2 (64 bits)  
   
 **Langues disponibles**  
> [!NOTE]  
> Les versions localisées dans des langues autres que l’anglais nécessitent la [mise à jour de sécurité KB 2862966](https://support.microsoft.com/en-us/kb/2862966) si l’installation est effectuée sur : Windows 8, Windows 7, Windows Server 2012 et Windows Server 2008 R2. 
  
 Cette version de SSMS peut être installée dans les langues suivantes :  
[chinois (République populaire de Chine)](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x804) | [chinois (Taïwan)](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x404) | [anglais (États-Unis)](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x409) | [français](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40c)  
[allemand](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x407) | [italien](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x410) | [japonais](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x411) | [coréen](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x412) | [portugais (Brésil)](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x416) | [russe](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x419) | [espagnol](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40a)  

 
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





Pour obtenir la liste complète des fonctionnalités, consultez   
                [SQL Server Management Studio : journal des modifications (SSMS)](../ssms/sql-server-management-studio-changelog-ssms.md)  
  
Pour afficher la liste des problèmes connus et des solutions de contournement, consultez   
                [SQL Server Management Studio : notes de publication](../ssms/sql-server-management-studio-release-notes.md)  
  
Pour plus d’informations sur la collecte de données utilisateur, consultez   
                [Déclaration de confidentialité de SQL Server](http://www.microsoft.com/privacystatement/en-us/SQLServer/Default.aspx).  
  
## <a name="previous-releases"></a>Versions antérieures  
[Versions antérieures de SQL Server Management Studio](../ssms/previous-sql-server-management-studio-releases.md)  
  
## <a name="feedback"></a>Commentaires  
  
![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [Forum des outils clients SQL](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Signaler un problème ou faire une suggestion sur Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback).  
  
## <a name="see-also"></a>Voir aussi  
[Didacticiel : SQL Server Management Studio](http://msdn.microsoft.com/en-us/d2bade70-07cf-4d94-b5d2-88aecb538ed1)  
[Documentation de SQL Server Management Studio](https://msdn.microsoft.com/library/hh213248(v=sql.130).aspx)  
[Microsoft SQL Server](https://msdn.microsoft.com/library/bb545450.aspx)  
[Service Packs et mises à jour supplémentaires](https://technet.microsoft.com/sqlserver/ff803383.aspx)  
[Télécharger SSDT (SQL Server Data Tools)](../ssdt/download-sql-server-data-tools-ssdt.md)  



