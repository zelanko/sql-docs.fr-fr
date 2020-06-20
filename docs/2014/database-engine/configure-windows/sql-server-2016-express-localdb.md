---
title: SQL Server 2014 Express-base de données locale | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
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
ms.openlocfilehash: f3c43604604580c5924be4daf4d473407564d247
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934878"
---
# <a name="sql-server-2014-express-localdb"></a>SQL Server 2014 Express LocalDB
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] `LocalDB` est un mode d’exécution de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] destiné aux développeurs de programmes. `LocalDB`l’installation de copie un ensemble minimal de fichiers nécessaires pour démarrer le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] . Une fois `LocalDB` installé, les développeurs établissent une connexion à l’aide d’une chaîne de connexion spéciale. Lors de la connexion, l'infrastructure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nécessaire est automatiquement créée et démarrée, ce qui permet à l'application d'utiliser la base de données sans tâches de configuration complexes ou longues. Les outils de développement incluent un [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui permet aux développeurs d'écrire et de tester le code [!INCLUDE[tsql](../../includes/tsql-md.md)] sans devoir gérer une instance de serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]complète. Une instance de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] `LocalDB` est gérée à l’aide de l' `SqlLocalDB.exe` utilitaire. [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]`LocalDB`doit être utilisé à la place de la [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] fonctionnalité d’instance utilisateur qui est déconseillée.  
  
## <a name="installing-localdb"></a>Installation de LocalDB  
 La méthode d’installation principale `LocalDB` consiste à utiliser le programme SqlLocalDB.msi. `LocalDB`est une option lors de l’installation d’une référence (SKU) de [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] . Sélectionnez `LocalDB` dans la page **sélection de fonctionnalités** pendant l’installation de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] . Il ne peut y avoir qu’une seule installation des `LocalDB` fichiers binaires pour chaque [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] version principale. Plusieurs processus [!INCLUDE[ssDE](../../includes/ssde-md.md)] peuvent être démarrés et utiliseront tous les mêmes fichiers binaires. Une instance de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] démarrée comme `LocalDB` a les mêmes limitations que[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]  
  
## <a name="description"></a>Description  
 Le `LocalDB` programme d’installation utilise le programme SqlLocalDB.msi pour installer les fichiers nécessaires sur l’ordinateur. Une fois installée, `LocalDB` est une instance de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] qui peut créer et ouvrir des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données. Les fichiers de base de données système pour la base de données sont stockés dans le chemin d'accès AppData local de l'utilisateur, qui est normalement masqué. Par exemple, **C:\Users\\<utilisateur\>\AppData\Local\Microsoft\Microsoft SQL Server Local DB\Instances\LocalDBApp1\\**. Les fichiers de la base de données utilisateur sont stockés à l’emplacement indiqué par l’utilisateur, en général dans le dossier **C:\Users\\<utilisateur\>\Documents\\**.  
  
 Pour plus d’informations sur `LocalDB` l’inclusion dans une application, consultez la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] documentation [vue d’ensemble des données locales](https://msdn.microsoft.com/library/ms233817\(VS.110\).aspx), [procédure pas à pas : création d’une SQL Server base de données de base de données](https://msdn.microsoft.com/library/ms233763\(VS.110\).aspx)locale et [procédure pas à pas : connexion aux données d’une base de données de base de données locale SQL Server (Windows Forms)](https://msdn.microsoft.com/library/ms171890\(VS.110\).aspx)  
  
 Pour plus d’informations sur l' `LocalDB` API, consultez [SQL Server Express référence](https://msdn.microsoft.com/library/hh234692\(SQL.110\).aspx) de l’API de l’instance de base de données locale et [fonction LocalDBStartInstance](https://msdn.microsoft.com/library/hh217143\(SQL.110\).aspx).  
  
 L’utilitaire SqlLocalDb peut créer de nouvelles instances de `LocalDB` , démarrer et arrêter une instance de `LocalDB` , et comprend des options pour vous aider à gérer `LocalDB` .  Pour plus d’informations sur l’utilitaire SqlLocalDb, consultez [Utilitaire SqlLocalDB](../../tools/sqllocaldb-utility.md).  
  
 Le classement d’instance pour `LocalDB` est défini sur SQL_Latin1_General_CP1_CI_AS et ne peut pas être modifié. Les classements au niveau des bases de données, des colonnes ou des expressions sont pris en charge normalement. Les bases de données autonomes suivent les règles de classement des métadonnées et de tempdb définies par [Classements de base de données autonome](../../relational-databases/databases/contained-database-collations.md).  
  
### <a name="restrictions"></a>Restrictions  
 `LocalDB`ne peut pas être un abonné de réplication de fusion.  
  
 `LocalDB`ne prend pas en charge FILESTREAM.  
  
 `LocalDB`autorise uniquement les files d’attente locales pour Service Broker.  
  
 Une instance de `LocalDB` possédée par les comptes intégrés tels que NT AUTHORITY\SYSTEM peut présenter des problèmes de gestion dus à la redirection du système de fichiers Windows. Utilisez plutôt un compte Windows normal comme propriétaire.  
  
### <a name="automatic-and-named-instances"></a>Instances automatiques et nommées  
 `LocalDB`prend en charge deux types d’instances : les instances automatiques et les instances nommées.  
  
-   Les instances automatiques de `LocalDB` sont publiques. Elles sont créées et gérées automatiquement pour l'utilisateur et peuvent être utilisées par n'importe quelle application. Une instance automatique de `LocalDB` existe pour chaque version de `LocalDB` installée sur l’ordinateur de l’utilisateur. Les instances automatiques de `LocalDB` permettent une gestion transparente des instances. Il n'est pas nécessaire de créer l'instance ; elle fonctionne tout simplement. Cela permet une installation et une migration faciles de l'application vers un autre ordinateur. Si la version spécifiée de `LocalDB` est installée sur l'ordinateur cible, l'instance automatique de `LocalDB` pour cette version est disponible sur l'ordinateur cible. Les instances automatiques de `LocalDB` ont un modèle spécial pour le nom de l’instance qui appartient à un espace de noms réservé. Cela empêche les conflits de noms avec les instances nommées de `LocalDB` . Le nom de l'instance automatique est **MSSQLLocalDB**.  
  
-   Les instances nommées de `LocalDB` sont privées. Elles appartiennent à une seule application qui est chargée de créer et de gérer l'instance. Les instances nommées fournissent l'isolement d'autres instances et peuvent améliorer les performances en réduisant les contentions de ressources avec d'autres utilisateurs de base de données. Les instances nommées doivent être créées explicitement par l’utilisateur via l' `LocalDB` API de gestion ou implicitement via le fichier app.config pour une application managée (bien que l’application managée puisse également utiliser l’API, si vous le souhaitez). Chaque instance nommée de `LocalDB` a une `LocalDB` version associée qui pointe vers le jeu de `LocalDB` fichiers binaires respectif. Le nom d’instance d’un `LocalDB` est de `sysname` type de données et peut comporter jusqu’à 128 caractères. (Cela diffère des instances nommées normales de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , qui limitent les noms aux noms NetBIOS standard de 16 caractères ASCII.) Le nom d’une instance de `LocalDB` peut contenir tous les caractères Unicode qui sont valides dans un nom de fichier.  Une instance nommée qui utilise un nom d'instance automatique devient une instance automatique.  
  
 Les différents utilisateurs d'un ordinateur peuvent avoir des instances de même nom. Chaque instance correspond à différents processus qui s'exécutent sous un utilisateur différent.  
  
## <a name="shared-instances-of-localdb"></a>Instances partagées de LocalDB  
 Pour prendre en charge les scénarios dans lesquels plusieurs utilisateurs de l’ordinateur doivent se connecter à une instance unique de `LocalDB` , `LocalDB` prend en charge le partage d’instance. Un propriétaire d'instance peut choisir d'autoriser les autres utilisateurs sur l'ordinateur à se connecter à son instance. Les instances automatiques et nommées de `LocalDB` peuvent être partagées. Pour partager une instance de `LocalDB`, un utilisateur sélectionne un nom partagé (alias) pour celle-ci. Étant donné que le nom partagé est visible par tous les utilisateurs de l'ordinateur, ce nom partagé doit être unique sur l'ordinateur. Le nom partagé d’une instance de `LocalDB` a le même format que l’instance nommée de `LocalDB` .  
  
 Seul un administrateur sur l’ordinateur peut créer une instance partagée de `LocalDB` . Une instance partagée de `LocalDB` peut être partagée par un administrateur ou par le propriétaire de l’instance partagée de `LocalDB` . Pour partager et annuler le partage d’une instance de `LocalDB` , utilisez `LocalDBShareInstance` les `LocalDBUnShareInstance` méthodes et de l' `LocalDB` API, ou les options de partage et non partagées de l’utilitaire SqlLocalDb.  
  
## <a name="starting-localdb-and-connecting-to-localdb"></a>Démarrage de LocalDB et connexion à LocalDB  
  
### <a name="connecting-to-the-automatic-instance"></a>Se connecter à l'instance automatique  
 Le moyen le plus simple d’utiliser `LocalDB` est de se connecter à l’instance automatique détenue par l’utilisateur actuel à l’aide de la chaîne de connexion **« Server = (base de données locale) \MSSQLLocalDB ; Integrated Security = True »**. Pour vous connecter à une base de données spécifique en utilisant le nom de fichier, connectez-vous à l’aide d’une chaîne de connexion semblable à **"Server=(LocalDB)\MSSQLLocalDB; Integrated Security=true ;AttachDbFileName=D:\Data\MyDB1.mdf"**.  
  
> [!NOTE]  
>  La première fois qu’un utilisateur tente de se connecter à un ordinateur `LocalDB` , l’instance automatique doit être créée et démarrée. Le temps supplémentaire requis pour créer l'instance peut entraîner l'échec de la tentative de connexion et l'affichage d'un message de délai de connexion dépassé. Dans ce cas, attendez quelques secondes la fin du processus de création, puis connectez-vous à nouveau.  
  
### <a name="creating-and-connecting-to-a-named-instances"></a>Création et connexion à des instances nommées  
 En plus de l’instance automatique, `LocalDB` prend également en charge les instances nommées. Utilisez le programme SqlLocalDB.exe pour créer, démarrer et arrêter une instance nommée de `LocalDB` . Pour plus d’informations sur SqlLocalDB.exe, consultez [Utilitaire SqlLocalDB](../../tools/sqllocaldb-utility.md).  
  
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
|Nom|"LocalDBApp1"|  
|Version|\<Current Version>|  
|Nom partagé|""|  
|Propriétaire|"\<Your Windows User>"|  
|Création automatique|Non|  
|State|exécution en cours|  
|Dernière heure de début|\<Date and Time>|  
|Nom du canal de l'instance|np:\\\\.\pipe\LOCALDB#F365A78E\tsql\query|  
  
> [!NOTE]  
>  Si votre application utilise une version de .NET avant 4.0.2, vous devez vous connecter directement au canal nommé de `LocalDB` . La valeur du nom du canal d’instance est le canal nommé sur lequel l’instance de `LocalDB` écoute. La partie du nom du canal de l’instance après la base de données locale change chaque fois que l’instance de `LocalDB` est démarrée. Pour vous connecter à l’instance de à l' `LocalDB` aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , tapez le nom du canal de l’instance dans la zone **nom du serveur** de la boîte de dialogue **se connecter à [!INCLUDE[ssDE](../../includes/ssde-md.md)] ** . À partir de votre programme personnalisé, vous pouvez établir une connexion à l’instance de `LocalDB` à l’aide d’une chaîne de connexion similaire à`SqlConnection conn = new SqlConnection(@"Server=np:\\.\pipe\LOCALDB#F365A78E\tsql\query");`  
  
### <a name="connecting-to-a-shared-instance-of-localdb"></a>Connexion à une instance partagée de LocalDB  
 Pour vous connecter à une instance partagée `LocalDB` de **Add \\ .** (point + barre oblique inverse) à la chaîne de connexion pour faire référence à l’espace de noms réservé aux instances partagées. Par exemple, pour se connecter à une instance partagée de `LocalDB` nommée, `AppData` Utilisez une chaîne de connexion telle que dans `(localdb)\.\AppData` le cadre de la chaîne de connexion. Un utilisateur qui se connecte à une instance partagée de `LocalDB` dont il n’est pas propriétaire doit disposer d’une connexion d’authentification ou d' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentification Windows.  
  
## <a name="troubleshooting"></a>Résolution des problèmes  
 Pour plus d’informations sur la résolution des problèmes `LocalDB` , consultez [résolution des problèmes SQL Server 2012 Express](https://social.technet.microsoft.com/wiki/contents/articles/4609.aspx).  
  
## <a name="permissions"></a>Autorisations  
 Une instance de [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] `LocalDB` est une instance créée par un utilisateur pour son utilisation. Tout utilisateur sur l’ordinateur peut créer une base de données à l’aide d’une instance de `LocalDB` , en stockant les fichiers sous son profil utilisateur et en exécutant le processus sous ses informations d’identification. Par défaut, l’accès à l’instance de `LocalDB` est limité à son propriétaire. Les données contenues dans le `LocalDB` sont protégées par l’accès du système de fichiers aux fichiers de base de données. Si les fichiers de base de données utilisateur sont stockés dans un emplacement partagé, la base de données peut être ouverte par toute personne ayant accès au système de fichiers à cet emplacement à l’aide d’une instance de `LocalDB` son propriétaire. Si les fichiers de base de données sont dans un emplacement protégé, tel que le dossier des données d'utilisateurs, seul cet utilisateur, et tous les administrateurs ayant accès à ce dossier, peuvent ouvrir la base de données. Les `LocalDB` fichiers ne peuvent être ouverts que par une instance de `LocalDB` à la fois.  
  
> [!NOTE]  
>  `LocalDB`s’exécute toujours sous le contexte de sécurité des utilisateurs ; autrement dit, `LocalDB` ne s’exécute jamais avec les informations d’identification du groupe de l’administrateur local. Cela signifie que tous les fichiers de base de données utilisés par une `LocalDB` instance doivent être accessibles à l’aide du compte Windows de l’utilisateur propriétaire, sans prendre en compte l’appartenance au groupe Administrateurs local.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire SqlLocalDB](../../tools/sqllocaldb-utility.md)  
  
  
