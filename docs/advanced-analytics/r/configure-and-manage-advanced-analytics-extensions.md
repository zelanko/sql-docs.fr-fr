---
title: Configuration avancée pour SQL Server Machine Learning Services | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8384773f6db4c0ced2fc68e52cd78100c98c52fd
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40392724"
---
# <a name="advanced-configuration-options-for-sql-server-machine-learning-services"></a>Options de configuration avancée pour SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit les modifications que vous pouvez effectuer après l’installation, pour modifier la configuration de l’exécution de script externe et d’autres services associés à machine learning dans SQL Server.

**S’applique à :** SQL Server 2016 R Services, SQL Server 2017 Machine Learning Services

##  <a name="bkmk_Provisioning"></a> Supplémentaire des comptes utilisateur pour machine learning

Processus de script externe dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] exécuter dans le contexte des comptes d’utilisateur local à faible privilège. Ces processus en cours d’exécution dans des comptes à faibles privilèges présente les avantages suivants :

+ Réduit les privilèges des processus d’exécution de script externe sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ordinateur
+ Fournit une isolation entre les sessions d’un runtime externe comme R ou Python.

Dans le cadre du programme d’installation, un nouveau Windows *pool de comptes d’utilisateur* est créé qui contient les comptes d’utilisateur locaux requis pour exécuter des processus externes runtime, tels que R ou Python. Vous pouvez modifier le nombre d’utilisateurs en fonction des besoins pour prendre en charge les tâches d’apprentissage automatique. 

En outre, votre administrateur de base de données doit accorder cette autorisation de groupe pour se connecter à n’importe quelle instance où l’apprentissage a été activé. Pour plus d’informations, consultez [modifier le pool de comptes d’utilisateur pour SQL Server Machine Learning Services](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).

À des ressources sensibles protext sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez définir une liste de contrôle d’accès (ACL) pour ce groupe. En spécifiant les ressources auxquelles l’accès est refusé par le groupe, vous pouvez empêcher l’accès par des processus externes, tels que les runtimes R ou Python.

+ Le pool de comptes d’utilisateurs est lié à une instance particulière. Un pool distinct de comptes de travail est nécessaire pour chaque instance sur lequel machine learning a été activée. Les comptes ne peuvent pas être partagés par plusieurs instances.

+ Les noms de comptes d’utilisateur dans le pool sont au format SQLInstanceName*nn*. Par exemple, si vous utilisez l’instance par défaut pour l’apprentissage automatique, le pool de comptes d’utilisateur prend en charge les noms de compte tels que MSSQLSERVER01, MSSQLSERVER02 et ainsi de suite.

+ La taille du pool de comptes d’utilisateur est statique et sa valeur par défaut est 20. Le nombre de sessions de runtime externes qui peuvent s’exécuter simultanément est limité par la taille de ce pool de comptes d’utilisateur. Pour modifier cette limite, un administrateur doit utiliser le Gestionnaire de Configuration SQL Server.

Pour plus d’informations sur comment apporter des modifications pour le pool de comptes d’utilisateur, consultez [modifier le pool de comptes d’utilisateur pour SQL Server Machine Learning Services](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).

##  <a name="bkmk_ManagingMemory"></a> Gérer la mémoire utilisée par les processus de script externe

Par défaut, les runtimes de script externe pour l’apprentissage sont limités à pas plus de 20 % de mémoire. Cela dépend de votre système, mais en général, vous pouvez trouver cette limite pas adaptée pour les tâches d’apprentissage automatique graves telles que l’apprentissage d’un modèle ou la prévision sur plusieurs lignes de données. 

Pour prendre en charge d’apprentissage automatique, un administrateur peut augmenter cette limite. Lorsque vous procédez ainsi, vous devrez peut-être réduire la quantité de mémoire réservée pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou pour d’autres services. Vous devez également envisager d’à l’aide de Resource Governor pour définir un pool de ressources externes ou des pools, afin que vous pouvez allouer des pools de ressources spécifiques aux travaux R ou Python.

Pour plus d’informations, consultez [gouvernance des ressources pour l’apprentissage](../../advanced-analytics/r/resource-governance-for-r-services.md).


## <a name="bkmk_Launchpad"></a>Modifier le compte de service Launchpad

Distinct [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] service est créé pour chaque instance sur laquelle vous avez configuré les services machine learning.

Par défaut, le service Launchpad est configuré pour s’exécuter avec le compte NT Service\MSSQLLaunchpad, qui dispose de toutes les autorisations nécessaires pour exécuter des scripts R. Toutefois, si vous modifiez ce compte, Launchpad peut-être pas en mesure de démarrer ou accéder à l’instance de SQL Server exécutant des scripts externes.

Si vous modifiez le compte de service, veillez à utiliser l’application de **stratégie de sécurité locale** et mettre à jour les autorisations sur chaque compte de service afin d’inclure ces autorisations :

+ Changer les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege)
+ Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)
+ Ouvrir une session en tant que service (SeServiceLogonRight)
+ Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)

Pour plus d’informations sur les autorisations requises pour exécuter les services SQL Server, consultez [Configurer les comptes de service Windows et les autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

##  <a name="bkmk_ChangingConfig"></a> Modifier les options de service avancées

Dans les premières versions de SQL Server 2016 R Services, vous pouvez modifier certaines propriétés du service en modifiant le [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] fichier de configuration. 

Toutefois, ce fichier est n’est plus utilisé pour la modification des configurations. Nous vous recommandons d’utiliser le Gestionnaire de Configuration SQL Server pour les modifications de configuration du service, telles que le compte de service et le nombre d’utilisateurs.

**Pour modifier la configuration de Launchpad**

1. Ouvrez le [Gestionnaire de configuration SQL Server](../../relational-databases/sql-server-configuration-manager.md). 
2. Cliquez sur le Launchpad de SQL Server et sélectionnez **propriétés**.

    + Pour modifier le compte de service, cliquez sur le **ouverture de session** onglet.

    + Pour augmenter le nombre d’utilisateurs, cliquez sur le **avancé** onglet.


**Pour modifier les paramètres de débogage**

Quelques propriétés peuvent uniquement être modifiées à l’aide du fichier de configuration de la zone de lancement qui peut-être être utile dans certains cas limités, telles que le débogage. Le fichier de configuration est créé au cours de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme d’installation et par défaut est enregistré comme un fichier texte brut à l’emplacement suivant : `<instance path>\binn\rlauncher.config`

Pour pouvoir apporter des modifications à ce fichier, vous devez être administrateur sur l’ordinateur exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si vous modifiez le fichier, nous vous recommandons de faire une copie de sauvegarde avant d’enregistrer les modifications.

Le tableau suivant répertorie les paramètres avancés de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], avec les valeurs autorisées. 

|**Nom du paramètre**|**Type**|**Description**|
|----|----|----|
|TRAVAIL\_NETTOYAGE\_ON\_QUITTER|Entier |Il s’agit d’un paramètre exclusivement interne : ne modifiez pas cette valeur. </br></br>Spécifie si le dossier de travail temporaire créé pour chaque session de runtime externe doit être nettoyé après que la session est terminée. Ce paramètre est utile pour le débogage. </br></br>Valeurs prises en charge sont **0** (désactivé) ou **1** (activé). </br></br>La valeur par défaut est 1, les fichiers journaux de signification sont supprimés à la sortie.|
|TRACE\_NIVEAU|Entier |Configure le niveau de détail de trace de MSSQLLAUNCHPAD pour le débogage. Cela affecte les fichiers de trace dans le chemin d’accès spécifié par le paramètre LOG_DIRECTORY. </br></br>Valeurs prises en charge sont : **1** (erreur), **2** (Performance), **3** (avertissement), **4** (informations). </br></br>La valeur par défaut est 1, ce qui signifie seulement les avertissements de sortie.|

Tous les paramètres prennent la forme d’une paire clé-valeur, chaque paramètre figurant sur une ligne distincte. Par exemple, pour modifier le niveau de trace, vous ajoutez la ligne `Default: TRACE_LEVEL=4`.

## <a name="see-also"></a>Voir aussi

[Considérations sur la sécurité](security-considerations-for-the-r-runtime-in-sql-server.md)
