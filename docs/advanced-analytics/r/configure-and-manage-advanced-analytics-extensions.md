---
title: "Configuration des Options avancées pour Services de Machine Learning | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 11/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d73fd98-0c61-4a62-94bb-75658195f2a6
caps.latest.revision: 21
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 872acf107d72989b4623a9d5f4ccb85c44d1f2f9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="advanced-configuration-options-for-machine-learning-services"></a>Configuration des Options avancées pour les Services de Machine Learning

Cet article décrit les modifications que vous pouvez effectuer après l’installation, pour modifier la configuration du runtime R et d’autres services associés d’apprentissage dans SQL Server.

S’applique à : SQL Server 2016 R Services, SQL Server 2017 d’apprentissage automatique Services

##  <a name="bkmk_Provisioning"></a>Configurer des comptes d’utilisateurs pour l’ordinateur apprentissage

Processus de script externe dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécutent dans le contexte des comptes d’utilisateur local à faible privilège. Ces processus en cours d’exécution dans des comptes individuels à faible privilège présente les avantages suivants :

+ Réduit les privilèges des processus d’exécution de script externe sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ordinateur
+ Fournit une isolation entre les sessions d’un runtime externe tels que R ou Python.

Dans le cadre de l’installation, une nouvelle fenêtre *pool de comptes d’utilisateur* est créé qui contient les comptes d’utilisateur local requis pour l’exécution du processus d’exécution R. Vous pouvez si nécessaire modifier le nombre d’utilisateurs qui prendront en charge R. Votre administrateur de base de données doit également autoriser ce groupe à se connecter à toute instance où R Services a été activé. Pour plus d’informations, voir [Modify the User Account Pool for SQL Server R Services](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).

Toutefois, vous pouvez définir une listes de contrôle d’accès (ACL) pour des ressources sensibles sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin de refuser l’accès à ce groupe et d’empêcher le processus du runtime R d’obtenir l’accès aux ressources.

+ Le pool de comptes d’utilisateurs est lié à une instance particulière.  Pour chaque instance sur laquelle le script R a été activé, un pool distinct de comptes de travail est créé. Les comptes ne peuvent pas être partagés par plusieurs instances.

+ Les noms de comptes d’utilisateur dans le pool sont au format SQLInstanceName*nn*. Par exemple, si vous utilisez l’instance par défaut en tant que serveur R, le pool de comptes d’utilisateur prend en charge des noms de compte tels que MSSQLSERVER01, MSSQLSERVER02, et ainsi de suite.

+ La taille du pool de comptes d’utilisateur est statique et sa valeur par défaut est 20. Le nombre de sessions du runtime R qui peuvent s’exécuter simultanément est limité par la taille du pool de ce compte d’utilisateur. Toutefois, cette limite peut être modifiée par un administrateur à l’aide du Gestionnaire de configuration SQL Server.

Pour plus d’informations sur la modification du pool de comptes d’utilisateur, voir [Modify the User Account Pool for SQL Server R Services](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).

##  <a name="bkmk_ManagingMemory"></a>Gérer la mémoire utilisée par les processus de Script externe

Par défaut, les processus du runtime R associés à [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] sont limités à l’utilisation d’au maximum 20 % de la mémoire totale de l’ordinateur. Toutefois, l’administrateur peut augmenter être si nécessaire.

D’une manière générale, cette limite ne sera pas adaptée pour les tâches R importantes comme le modèle d’apprentissage ou la prévision sur plusieurs lignes de données. Vous devrez peut-être réduire la quantité de mémoire réservée à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (ou à d’autres services) et utiliser Resource Governor pour définir un ou plusieurs pools de ressources externes et les allouer. Pour plus d’informations, consultez [gouvernance des ressources pour R](../../advanced-analytics/r/resource-governance-for-r-services.md).

##  <a name="bkmk_ChangingConfig"></a>Modifier les Options de Service avancées à l’aide du fichier de Configuration

Vous pouvez contrôler certaines propriétés avancées de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] en modifiant le fichier de configuration de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Ce fichier est créé au cours de l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Par défaut, il est enregistré au format de fichier texte brut à l’emplacement suivant :

`<instance path>\binn\rlauncher.config`

Pour pouvoir apporter des modifications à ce fichier, vous devez être administrateur sur l’ordinateur exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si vous modifiez le fichier, nous vous recommandons de faire une copie de sauvegarde avant d’enregistrer les modifications.

Par exemple, pour utiliser le bloc-notes pour ouvrir le fichier de configuration pour l’instance par défaut, vous serez ouvrir une invite de commandes en tant qu’administrateur et tapez la commande suivante :

```
C:\>Notepad.exe "%programfiles%\Microsoft SQL Server\MSSQL13.MSSQLSERVER\mssql\binn\rlauncher.config"  
```

##  <a name="bkmk_properties"></a>Modifier les propriétés de Configuration

Le tableau suivant répertorie les paramètres pris en charge pour [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], avec les valeurs autorisées.

Tous les paramètres prennent la forme d’une paire clé-valeur, chaque paramètre figurant sur une ligne distincte. Par exemple, cette propriété spécifie le niveau de trace pour RLauncher :

Par défaut : TRACE_LEVEL = 4


|**Nom du paramètre**|**Type de valeur**|**Par défaut**|**Description**|
|------------------|----------------|-------------|-----------------|
|JOB_CLEANUP_ON_EXIT|Entier<br /><br /> 0 = Désactivé<br /><br /> 1 = Activé|1<br /><br /> Les fichiers journaux sont supprimés à la sortie|Spécifie si le dossier de travail temporaire créé pour chaque session R doit être nettoyé une fois la session R terminée. Ce paramètre est utile pour le débogage.<br /><br /> Remarque : il s’agit d’un paramètre exclusivement interne ; ne modifiez pas cette valeur.|
|TRACE_LEVEL|Entier<br /><br /> 1 = Erreur<br /><br /> 2 = Performance<br /><br /> 3 = Avertissement<br /><br /> 4 = Informations| 1<br /><br /> Sortir les avertissements uniquement|Configure le niveau de détail de trace du lanceur R (MSSQLLAUNCHPAD) aux fins de débogage. Ce paramètre affecte le niveau de détail des traces stockées dans les fichiers de trace suivants, tous deux situés dans le chemin d’accès spécifié par le paramètre LOG_DIRECTORY :<br /><br /> **rlauncher.log**: fichier de trace généré pour les sessions R déclenchées par des requêtes T-SQL.<br /><br /> |

## <a name="bkmk_Launchpad"></a>Modifier le compte de Service Launchpad

Distinct [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] service est créé pour chaque instance sur laquelle vous avez configuré les services d’apprentissage automatique.

Par défaut, le service Launchpad est configuré pour s’exécuter avec le compte NT Service\MSSQLLaunchpad, qui dispose de toutes les autorisations nécessaires pour exécuter des scripts R. Toutefois, si vous modifiez ce compte, la zone de lancement peut ne pas pouvoir démarrer ou accéder à l’instance de SQL Server où les scripts externes doivent être exécutés.

Si vous modifiez le compte de service, veillez à utiliser l’application de **stratégie de sécurité locale** et mettre à jour les autorisations sur chaque compte de service afin d’inclure ces autorisations :

+ Changer les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege)
+ Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)
+ Ouvrir une session en tant que service (SeServiceLogonRight)
+ Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)

Pour plus d’informations sur les autorisations requises pour exécuter les services SQL Server, consultez [Configurer les comptes de service Windows et les autorisations](https://msdn.microsoft.com/library/ms143504.aspx#Windows).

## <a name="see-also"></a>Voir aussi

[Considérations sur la sécurité](security-considerations-for-the-r-runtime-in-sql-server.md)

