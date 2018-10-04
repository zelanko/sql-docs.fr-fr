---
title: SQL Server 2014 Express LocalDB | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- user instances
- LocalDB, described
- local database runtime
- file database
- LocalDB
ms.assetid: 5a641a46-7cfb-4d7b-a90d-6e4625719d74
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 676bc7adc3debb0beaee10d09d6fbe8018d42c2c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48158949"
---
# <a name="sql-server-2014-express-localdb"></a>SQL Server 2014 Express LocalDB
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] `LocalDB` est un mode d’exécution de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] destiné aux développeurs de programme. `LocalDB` installation copie l’ensemble minimal de fichiers nécessaires pour démarrer le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Une fois `LocalDB` est installé, les développeurs initialisent une connexion à l’aide d’une chaîne de connexion particulière. Lors de la connexion, nécessaires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] infrastructure est automatiquement créée et démarrée, l’activation de l’application pour utiliser la base de données sans tâches de configuration complexes ou longues. Les outils de développement incluent un [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui permet aux développeurs d'écrire et de tester le code [!INCLUDE[tsql](../../includes/tsql-md.md)] sans devoir gérer une instance de serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]complète. Une instance de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] `LocalDB` est géré à l’aide de la `SqlLocalDB.exe` utilitaire. [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]`LocalDB` doit être utilisé à la place de la [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] fonctionnalité d’instance utilisateur qui est déconseillée.  
  
## <a name="installing-localdb"></a>Installation de LocalDB  
 La méthode d’installation principale `LocalDB` est à l’aide du programme SqlLocalDB.msi. `LocalDB` est une option lors de l’installation d’une référence de [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)]. Sélectionnez `LocalDB` sur le **sélection des fonctionnalités** page lors de l’installation de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. Il peut y avoir qu’une seule installation de la `LocalDB` des fichiers binaires pour chaque version majeure [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] version. Plusieurs processus [!INCLUDE[ssDE](../../includes/ssde-md.md)] peuvent être démarrés et utiliseront tous les mêmes fichiers binaires. Une instance de la [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] a été lancé sous la `LocalDB` a les mêmes limitations que [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]  
  
## <a name="description"></a>Description  
 Le `LocalDB` programme d’installation utilise le programme SqlLocalDB.msi pour installer les fichiers nécessaires sur l’ordinateur. Une fois installé, `LocalDB` est une instance de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] qui peut créer et ouvrir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données. Les fichiers de base de données système pour la base de données sont stockés dans le chemin d'accès AppData local de l'utilisateur, qui est normalement masqué. Par exemple, **C:\Users\\<utilisateur\>\AppData\Local\Microsoft\Microsoft SQL Server Local DB\Instances\LocalDBApp1\\**. Les fichiers de la base de données utilisateur sont stockés à l’emplacement indiqué par l’utilisateur, en général dans le dossier **C:\Users\\<utilisateur\>\Documents\\**.  
  
 Pour plus d’informations sur l’inclusion de `LocalDB` dans une application, consultez le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] documentation [vue d’ensemble des données locales](http://msdn.microsoft.com/library/ms233817\(VS.110\).aspx), [procédure pas à pas : création d’une base de données SQL Server LocalDB](http://msdn.microsoft.com/library/ms233763\(VS.110\).aspx), et [Procédure pas à pas : connexion aux données dans une base de données SQL Server LocalDB (Windows Forms)](http://msdn.microsoft.com/library/ms171890\(VS.110\).aspx).  
  
 Pour plus d’informations sur la `LocalDB` API, consultez [SQL Server Express LocalDB Instance référence de l’API](http://msdn.microsoft.com/library/hh234692\(SQL.110\).aspx) et [fonction LocalDBStartInstance](http://msdn.microsoft.com/library/hh217143\(SQL.110\).aspx).  
  
 L’utilitaire SqlLocalDb peut créer des instances de `LocalDB`, démarrer et arrêter une instance de `LocalDB`et inclut des options pour vous aider à gérer `LocalDB`.  Pour plus d’informations sur l’utilitaire SqlLocalDb, consultez [Utilitaire SqlLocalDB](../../tools/sqllocaldb-utility.md).  
  
 Le classement d’instance pour `LocalDB` a la valeur SQL_Latin1_General_CP1_CI_AS et ne peut pas être modifié. Les classements au niveau des bases de données, des colonnes ou des expressions sont pris en charge normalement. Les bases de données autonomes suivent les règles de classement des métadonnées et de tempdb définies par [Classements de base de données autonome](../../relational-databases/databases/contained-database-collations.md).  
  
### <a name="restrictions"></a>Restrictions  
 `LocalDB` ne peut pas être un abonné de réplication de fusion.  
  
 `LocalDB` ne prend pas en charge FILESTREAM.  
  
 `LocalDB` autorise uniquement les files d’attente locales pour Service Broker.  
  
 Une instance de `LocalDB` détenus par les comptes intégrés tels que NT AUTHORITY\SYSTEM peut présenter des problèmes de facilité de gestion en raison de la redirection du système de fichiers windows ; Au lieu de cela, utilisez un compte windows normal comme propriétaire.  
  
### <a name="automatic-and-named-instances"></a>Instances automatiques et nommées  
 `LocalDB` prend en charge deux types d’instances : les instances automatiques et les instances nommées.  
  
-   Instances automatiques de `LocalDB` sont publics. Elles sont créées et gérées automatiquement pour l'utilisateur et peuvent être utilisées par n'importe quelle application. Une instance automatique de `LocalDB` existe pour chaque version de `LocalDB` installé sur l’ordinateur de l’utilisateur. Instances automatiques de `LocalDB` fournir une gestion transparente d’instances. Il n'est pas nécessaire de créer l'instance ; elle fonctionne tout simplement. Cela permet une installation et une migration faciles de l'application vers un autre ordinateur. Si l’ordinateur cible dispose de la version spécifiée de `LocalDB` installé, l’instance automatique de `LocalDB` pour cette version est disponible sur l’ordinateur cible. Instances automatiques de `LocalDB` ont un modèle particulier pour le nom d’instance qui appartient à un espace de noms réservé. Cela empêche les conflits de nom avec les instances nommées de `LocalDB`. Le nom de l'instance automatique est **MSSQLLocalDB**.  
  
-   Instances nommées de `LocalDB` sont privés. Elles appartiennent à une seule application qui est chargée de créer et de gérer l'instance. Les instances nommées fournissent l'isolement d'autres instances et peuvent améliorer les performances en réduisant les contentions de ressources avec d'autres utilisateurs de base de données. Instances nommées doivent être créées explicitement par l’utilisateur via le `LocalDB` API de gestion ou implicitement via le fichier app.config de fichiers pour une application managée (bien que l’application managée peut également utiliser l’API, si vous le souhaitez). Chaque instance nommée de `LocalDB` est associé à un `LocalDB` version qui pointe vers le jeu respectif de `LocalDB` les fichiers binaires. Le nom d’instance d’un `LocalDB` est `sysname` data type et peut comporter jusqu'à 128 caractères. (Ceci diffère des instances nommées normales de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], qui limitent les noms aux noms NetBIOS standard de 16 caractères ASCII.) Le nom d’une instance de `LocalDB` peut contenir des caractères Unicode qui sont valides dans un nom de fichier.  Une instance nommée qui utilise un nom d'instance automatique devient une instance automatique.  
  
 Les différents utilisateurs d'un ordinateur peuvent avoir des instances de même nom. Chaque instance correspond à différents processus qui s'exécutent sous un utilisateur différent.  
  
## <a name="shared-instances-of-localdb"></a>Instances partagées de LocalDB  
 Pour prendre en charge les scénarios où plusieurs utilisateurs de l’ordinateur doivent se connecter à une instance unique de `LocalDB`, `LocalDB` prend en charge le partage d’instance. Un propriétaire d'instance peut choisir d'autoriser les autres utilisateurs sur l'ordinateur à se connecter à son instance. Les instances automatiques et nommées de `LocalDB` peuvent être partagées. Pour partager une instance de `LocalDB` un utilisateur sélectionne un nom partagé (alias) pour celle-ci. Étant donné que le nom partagé est visible par tous les utilisateurs de l'ordinateur, ce nom partagé doit être unique sur l'ordinateur. Le nom partagé pour une instance de `LocalDB` a le même format que l’instance nommée de `LocalDB`.  
  
 Seul un administrateur sur l’ordinateur peut créer une instance partagée de `LocalDB`. Une instance partagée de `LocalDB` peut être annulé par un administrateur ou par le propriétaire de l’instance partagée de `LocalDB`. Pour partager et annuler le partage d’une instance de `LocalDB`, utilisez le `LocalDBShareInstance` et `LocalDBUnShareInstance` méthodes de la `LocalDB` API, ou le partage et les options non partagées de l’utilitaire SqlLocalDb.  
  
## <a name="starting-localdb-and-connecting-to-localdb"></a>Démarrage de LocalDB et connexion à LocalDB  
  
### <a name="connecting-to-the-automatic-instance"></a>Se connecter à l'instance automatique  
 Le moyen le plus simple d’utiliser `LocalDB` consiste à se connecter à l’instance automatique détenue par l’utilisateur actuel à l’aide de la chaîne de connexion **« Server = (localdb) \MSSQLLocalDB;Integrated Security = true »**. Pour vous connecter à une base de données spécifique en utilisant le nom de fichier, connectez-vous à l’aide d’une chaîne de connexion semblable à **"Server=(LocalDB)\MSSQLLocalDB; Integrated Security=true ;AttachDbFileName=D:\Data\MyDB1.mdf"**.  
  
> [!NOTE]  
>  La première fois qu’un utilisateur sur un ordinateur tente de se connecter à `LocalDB`, l’instance automatique doit être créée et démarrée. Le temps supplémentaire requis pour créer l'instance peut entraîner l'échec de la tentative de connexion et l'affichage d'un message de délai de connexion dépassé. Dans ce cas, attendez quelques secondes la fin du processus de création, puis connectez-vous à nouveau.  
  
### <a name="creating-and-connecting-to-a-named-instances"></a>Création et connexion à des instances nommées  
 En plus de l’instance automatique, `LocalDB` également prend en charge les instances nommées. Utilisez le programme SqlLocalDB.exe pour créer, démarrer et arrêter une instance nommée de `LocalDB`. Pour plus d’informations sur SqlLocalDB.exe, consultez [Utilitaire SqlLocalDB](../../tools/sqllocaldb-utility.md).  
  
```ms-dos  
REM Create an instance of LocalDB  
"C:\Program Files\Microsoft SQL Server\120\Tools\Binn\SqlLocalDB.exe" create LocalDBApp1  
REM Start the instance of LocalDB  
"C:\Program Files\Microsoft SQL Server\120\Tools\Binn\SqlLocalDB.exe" start LocalDBApp1  
REM Gather information about the instance of LocalDB  
"C:\Program Files\Microsoft SQL Server\120\Tools\Binn\SqlLocalDB.exe" info LocalDBApp1  
```  
  
 La dernière ligne ci-dessus retourne des informations semblables aux suivantes.  
  
|||  
|-|-|  
|Nom   |"LocalDBApp1"|  
|Version|\<Version actuelle>|  
|Nom partagé|""|  
|Propriétaire|"\<votre utilisateur Windows>"|  
|Création automatique|non|  
|État|en cours d'exécution|  
|Dernière heure de début|\<Date et heure>|  
|Nom du canal de l'instance|np:\\\\.\pipe\LOCALDB#F365A78E\tsql\query|  
  
> [!NOTE]  
>  Si votre application utilise une version de .NET antérieure à 4.0.2, vous devez vous connecter directement au canal nommé de la `LocalDB`. La valeur de nom du canal de l’Instance est le canal nommé que l’instance de `LocalDB` écoute. La partie du nom de canal d’Instance après LOCALDB # change chaque fois que l’instance de `LocalDB` est démarré. Pour vous connecter à l’instance de `LocalDB` à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], tapez le nom de canal d’Instance dans le **nom du serveur** boîte de le **se connecter à [!INCLUDE[ssDE](../../includes/ssde-md.md)]**  boîte de dialogue. À partir de votre programme personnalisé, vous pouvez établir la connexion à l’instance de `LocalDB` à l’aide d’une chaîne de connexion semblable à `SqlConnection conn = new SqlConnection(@"Server=np:\\.\pipe\LOCALDB#F365A78E\tsql\query");`  
  
### <a name="connecting-to-a-shared-instance-of-localdb"></a>Connexion à une instance partagée de LocalDB  
 Pour vous connecter à une instance partagée de `LocalDB` ajouter **.\\**  (point + barre oblique inverse) à la chaîne de connexion pour référencer l’espace de noms réservé aux instances partagées. Par exemple, pour se connecter à une instance partagée de `LocalDB` nommé `AppData` utiliser une chaîne de connexion comme `(localdb)\.\AppData` dans le cadre de la chaîne de connexion. Un utilisateur se connectant à une instance partagée de `LocalDB` dont ils n’est pas propriétaire doit avoir une authentification Windows ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion d’authentification.  
  
## <a name="troubleshooting"></a>Dépannage  
 Pour plus d’informations sur le dépannage `LocalDB`, consultez [dépannage de SQL Server 2012 Express LocalDB](http://social.technet.microsoft.com/wiki/contents/articles/4609.aspx).  
  
## <a name="permissions"></a>Permissions  
 Une instance de [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] `LocalDB` est une instance créée par un utilisateur pour leur utilisation. Tout utilisateur sur l’ordinateur peut créer une base de données à l’aide d’une instance de `LocalDB`, stockant les fichiers sous son profil utilisateur et le processus sous leurs informations d’identification en cours d’exécution. Par défaut, l’accès à l’instance de `LocalDB` est limitée à son propriétaire. Les données contenues dans le `LocalDB` est protégé par l’accès au système de fichiers pour les fichiers de base de données. Si les fichiers de base de données utilisateur sont stockés dans un emplacement partagé, la base de données peut être ouverte par toute personne ayant accès au système de fichiers à cet emplacement à l’aide d’une instance de `LocalDB` qu’ils sont propriétaires. Si les fichiers de base de données sont dans un emplacement protégé, tel que le dossier des données d'utilisateurs, seul cet utilisateur, et tous les administrateurs ayant accès à ce dossier, peuvent ouvrir la base de données. Le `LocalDB` fichiers peuvent uniquement être ouverts par une instance de `LocalDB` à la fois.  
  
> [!NOTE]  
>  `LocalDB` s’exécute toujours dans le contexte de sécurité utilisateurs ; Autrement dit, `LocalDB` ne s’exécute jamais avec les informations d’identification à partir du groupe Administrateurs local. Cela signifie que tous les fichiers de la base utilisés par un `LocalDB` instance doit être accessible à l’aide de compte Windows de l’utilisateur propriétaire, sans tenir compte de l’appartenance au groupe Administrateurs local.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire SqlLocalDB](../../tools/sqllocaldb-utility.md)  
  
  
