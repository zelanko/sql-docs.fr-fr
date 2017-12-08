---
title: "Problèmes connus dans Machine Learning Services | Documents Microsoft"
ms.date: 11/16/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b37a63a-5ff5-478e-bcc2-d13da3ac241c
caps.latest.revision: "53"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: d5835b1c79ec1ce26e200b02fa9ba6e03378187b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="known-issues-in-machine-learning-services"></a>Problèmes connus dans les Services de Machine Learning

Cet article décrit les limitations ou des problèmes connus avec les composants qui sont fournies en tant qu’option dans SQL Server 2016 et SQL Server 2017 d’apprentissage.

Les informations ici s’applique à tous les éléments suivants, sauf indication contraire :

* SQL Server 2016

  - R Services (dans la base de données)
  - Microsoft R Server (autonome)

* SQL Server 2017

  - Apprentissage des Services pour R (de-de base de données)
  - Apprentissage des Services pour Python (de-de base de données)
  - Machine Learning Server (autonome)

## <a name="setup-and-configuration-issues"></a>Problèmes d’installation et configuration

Pour obtenir une description des processus et des questions courantes liées à la configuration initiale et la configuration, consultez [FAQ d’installation et de mise à niveau](r/upgrade-and-installation-faq-sql-server-r-services.md). Il contient des informations sur les mises à niveau, installation de côte-à-côte et l’installation de nouveaux composants de R ou Python.

### <a name="unable-to-install-sql-server-machine-learning-features-on-a-domain-controller"></a>Impossible d’installer des fonctionnalités de formation l’ordinateur SQL Server sur un contrôleur de domaine

Si vous essayez d’installer SQL Server 2016 R Services ou SQL Server 2017 Machine Learning Services sur un contrôleur de domaine, le programme d’installation échoue, ces erreurs :

>*« Une erreur s’est produite pendant le processus d’installation de la fonctionnalité ».*
> 
>*« Impossible de trouver le groupe avec l’identité... »*
> 
>*« Code d’erreur de composant : est 0 x 80131509 »*

L’échec se produit parce que, sur un contrôleur de domaine, le service ne peut pas créer les comptes locaux 20 requis pour exécuter l’apprentissage. En règle générale, nous déconseillons l’installation de SQL Server sur un contrôleur de domaine. Pour plus d’informations, consultez [bulletin de prise en charge 2032911](https://support.microsoft.com/en-us/help/2032911/you-may-encounter-problems-when-installing-sql-server-on-a-domain-cont).

### <a name="install-the-latest-service-release-to-ensure-compatibility-with-microsoft-r-client"></a>Installer la dernière version de service pour garantir la compatibilité avec le Client de Microsoft R

Si vous installez la dernière version du Client de Microsoft R et l’utiliser pour exécuter R sur SQL Server dans un contexte de calcul à distance, vous pouvez obtenir une erreur semblable à celui-ci :

>*9.x.x de version du Client de Microsoft R sont en cours d’exécution sur votre ordinateur, ce qui est incompatible avec Microsoft R Server version 8.x.x. Téléchargez et installez une version compatible.*

SQL Server 2016 nécessite que les bibliothèques R sur le client correspondent exactement aux bibliothèques R sur le serveur. La restriction a été supprimée pour les versions R Server 9.0.1 plus tard. Toutefois, si vous rencontrez cette erreur, vérifiez la version des bibliothèques R qui est utilisée par votre client et le serveur et, si nécessaire, mettez à jour le client pour faire correspondre la version du serveur.

La version de R est installé avec SQL Server R Services est mise à jour chaque fois qu’une version de service SQL Server est installée. Pour vous assurer que vous disposez toujours les versions plus récentes des composants R, veillez à installer tous les service packs.

Pour garantir la compatibilité avec le Client Microsoft R 9.0.0, installer les mises à jour qui sont décrites dans cette [article du support technique](https://support.microsoft.com/kb/3210262).

Pour éviter des problèmes avec les packages R, vous pouvez également mettre à niveau la version des bibliothèques R qui sont installés sur le serveur, en remplaçant par la stratégie de cycle de vie moderne qui est décrit dans [la section suivante](#bkmk_sqlbindr). Lorsque vous procédez ainsi, la version de R est installé avec SQL Server est mis à jour en même temps que les mises à jour sont publiées pour Microsoft R Server, ce qui garantit que serveur et client ont toujours les dernières versions de Microsoft R.

**S’applique à :** SQL Server 2016 R Services, avec R Server version9.0.0 ou une version antérieure

### <a name="unable-to-install-python-components-in-offline-installations-of-sql-server-2017-ctp-20-or-later"></a>Impossible d’installer les composants de Python dans les installations en mode hors connexion de SQL Server 2017 CTP 2.0 ou version ultérieure

Si vous installez une version préliminaire de SQL Server 2017 sur un ordinateur sans accès à internet, le programme d’installation peut échouer afficher la page qui vous invite à spécifier l’emplacement des composants téléchargés Python. Dans ce cas, vous pouvez installer la fonctionnalité Services de Machine Learning, mais pas les composants de Python.

Ce problème est résolu dans la version release. Si vous rencontrez ce problème, comme une solution de contournement, vous pouvez activer temporairement les accès à internet pour la durée de l’installation. Cette limitation ne s’applique pas à R.

**S’applique à :** 2017 du serveur SQL avec Python ### <a name="bkmk_sqlbindr"> </a> de version non compatible d’avertissement lorsque vous vous connectez à une version antérieure de SQL Server R Services à partir d’un client à l’aide de[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]

Lorsque vous exécutez le code R dans un contexte de calcul de SQL Server 2016, et une des deux instructions suivantes est true, vous pouvez rencontrer une erreur semblable à la suivante :
* Vous avez installé R Server (autonome) sur un ordinateur client à l’aide de l’Assistant Installation de [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].
* Vous avez installé Microsoft R Server à l’aide de la [séparer le programme d’installation de Windows](https://docs.microsoft.com/r-server/install/r-server-install-windows).

>*Vous exécutez la version 9.0.0 de Microsoft R Client sur votre ordinateur, ce qui est incompatible avec la version 8.0.3 de Microsoft R Server. Téléchargez et installez une version compatible.*

Vous pouvez utiliser _liaison_ dans Microsoft R Server 9.0 et versions ultérieures, pour mettre à niveau les composants de R dans les instances de SQL Server 2016. Pour déterminer si prise en charge des mises à niveau est disponible pour votre version de R Services, consultez [mettre à niveau une instance de R Services à l’aide de SqlBindR.exe](/r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

**S’applique à :** SQL Server 2016 R Services, avec R Server version9.0.0 ou une version antérieure

### <a name="setup-for-sql-server-2016-service-releases-might-fail-to-install-newer-versions-of-r-components"></a>La configuration des versions de services de SQL Server 2016 peut échouer à installer de nouvelles versions des composants R

Lorsque vous installez une mise à jour cumulative ou que vous installez un service pack pour SQL Server 2016 sur un ordinateur qui n’est pas connecté à internet, l’Assistant installation peut échouer afficher l’invite qui vous permet de mettre à jour les composants R à l’aide des fichiers CAB téléchargés. Cette erreur se produit généralement lorsque plusieurs composants ont été installés avec le moteur de base de données.

Pour résoudre ce problème, vous pouvez installer la version de service à l’aide de la ligne de commande et en spécifiant le */MRCACHEDIRECTORY* argument, comme illustré dans cet exemple, qui installe les mises à jour CU1 :

`C:\<path to installation media>\SQLServer2016-KB3164674-x64.exe /Action=Patch /IACCEPTROPENLICENSETERMS /MRCACHEDIRECTORY=<path to CU1 CAB files>`

Pour obtenir les programmes d’installation les plus récentes, consultez [installer les composants d’apprentissage ordinateur sans accès à internet](r/installing-ml-components-without-internet-access.md).

**S’applique à :** SQL Server 2016 R Services, avec R Server version9.0.0 ou une version antérieure

### <a name="launchpad-services-fails-to-start-if-the-version-is-different-from-the-r-version"></a>LaunchPad services ne démarre pas si la version est différente de la version de R

Si vous installez SQL Server R Services séparément à partir du moteur de base de données, et les versions de build sont différentes, vous pouvez voir l’erreur suivante dans le journal des événements système :

>_Le service Launchpad de SQL Server a échoué en raison de l’erreur suivante : le service n’a pas répondu à la demande de démarrage ou de contrôle en temps voulu._

Par exemple, cette erreur peut se produire si vous installez le moteur de base de données à l’aide de la version release, appliquer un correctif pour mettre à niveau le moteur de base de données, puis ajouter la fonctionnalité de R Services à l’aide de la version release.

Pour éviter ce problème, assurez-vous que tous les composants ont le même numéro de version. Si vous mettez à niveau un composant, veillez à appliquer la même mise à niveau à tous les autres composants installés.

Pour afficher une liste des numéros de version de R sont requises pour chaque version de SQL Server 2016, consultez [composants d’installation de R sans accès à internet](r/installing-ml-components-without-internet-access.md).

### <a name="remote-compute-contexts-are-blocked-by-a-firewall-in-sql-server-instances-that-are-running-on-azure-virtual-machines"></a>Contextes de calcul à distance sont bloqués par un pare-feu dans les instances de SQL Server qui s’exécutent sur des machines virtuelles

Si vous avez installé [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] sur un ordinateur virtuel Windows Azure, vous ne pourrez pas être en mesure d’utiliser les contextes de calcul qui nécessitent l’utilisation de l’espace de travail de l’ordinateur virtuel. La raison est que, par défaut, le pare-feu sur les machines virtuelles comprend une règle qui bloque accès pour les comptes d’utilisateur locaux R l'réseau.

Pour résoudre ce problème, sur la machine virtuelle Azure, ouvrez **pare-feu Windows avec fonctions avancées de sécurité**, sélectionnez **règles de trafic sortant**et désactivez la règle suivante : **bloquer l’accès réseau pour les comptes d’utilisateur locaux R dans Instance de SQL Server MSSQLSERVER**. Vous pouvez également laisser la règle activée, mais affectez à la propriété de sécurité **Autoriser si paramètres sécurisés**.

### <a name="implied-authentication-in-sqlexpress"></a>Authentification implicite dans SQLEXPRESS

Lorsque vous exécutez les travaux R à partir d’une station de travail de science des données à distance à l’aide de l’authentification Windows intégrée, SQL Server utilise *l’authentification implicite* pour générer tous les appels ODBC locales qui peuvent être requis par le script. Toutefois, cette fonctionnalité ne marchait pas dans la version RTM de SQL Server Express Edition.

Pour résoudre ce problème, nous vous recommandons d’effectuer la mise à niveau vers une version ultérieure du service.

Si vous ne pouvez pas effectuer la mise à niveau, vous pouvez utiliser une connexion SQL pour exécuter des tâches R à distance qui peuvent nécessiter des appels ODBC incorporés.

**S’applique à :** SQL Server 2016 R Services Express Edition

### <a name="performance-limits-when-libraries-used-by-sql-server-are-called-from-other-tools"></a>Limites de performances lorsque les bibliothèques utilisées par SQL Server sont appelées à partir d’autres outils

Il est possible d’appeler les bibliothèques qui sont installés pour SQL Server à partir d’une application externe, telles que RGui d’apprentissage automatique. Cela peut être le meilleur moyen pour effectuer certaines tâches, telles que l’installation de nouveaux packages, ou en cours d’exécution des tests ad hoc sur les exemples de code très courte. Toutefois, en dehors de SQL Server, les performances peuvent être limitées. 

Par exemple, même si vous utilisez l’édition Enterprise de SQL Server, R s’exécute en mode de thread unique lorsque vous exécutez votre code R à l’aide des outils externes. Pour obtenir les avantages de performances dans SQL Server, établir une connexion SQL Server et utiliser [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) pour appeler le runtime de script externe.

+ En règle générale, évitez d’appeler les bibliothèques qui sont utilisées par SQL Server à partir d’outils externes d’apprentissage automatique.
+ Si vous avez besoin pour le débogage R ou code Python, il est généralement plus facile de le faire en dehors de SQL Server. Pour obtenir les mêmes bibliothèques qui se trouvent dans SQL Server, vous pouvez installer le Client Microsoft R ou [Machine Learning Server](r/create-a-standalone-r-server.md).

### <a name="external-script-execution-is-throttled-due-to-resource-governance-default-values"></a>L’exécution du script externe est limitée en raison de valeurs par défaut de gouvernance des ressources

Dans Enterprise Edition, vous pouvez utiliser des pools de ressources pour gérer les processus de script externe. Dans certaines versions release anticipée, la mémoire maximale qui peut être allouée, pour les processus R était 20 pour cent. Par conséquent, si le serveur dispose de 32 Go de RAM, les exécutables de R (RTerm.exe et BxlServer.exe) peuvent utiliser un maximum de 6,4 Go dans une demande unique.

Si vous rencontrez des limitations de ressources, vérifiez la valeur par défaut en cours. Si 20 pour cent n’est pas suffisant, consultez la documentation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur la façon de modifier cette valeur.

**S’applique à :** SQL Server 2016 R Services, Enterprise Edition

## <a name="r-issues"></a>Problèmes liés à R

Cette section contient des problèmes connus qui sont spécifiques à l’exécution de code R sur SQL Server, ainsi que certains problèmes liés aux bibliothèques R et outils publiés par Microsoft, y compris RevoScaleR.

Pour les autres problèmes connus qui peuvent affecter des solutions R, accédez à la [site Microsoft R Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues).

### <a name="limitations-on-processor-affinity-for-r-jobs"></a>Limitations sur l’affinité du processeur pour les tâches R

Dans la génération de la version initiale de SQL Server 2016, vous pouvez définir l’affinité du processeur uniquement pour les processeurs dans le premier groupe de k. Par exemple, si le serveur est un ordinateur 2 sockets avec deux k-groups, processeurs uniquement à partir du premier groupe de k sont utilisés pour les processus R. La même restriction s’applique lorsque vous configurez la gouvernance de ressources pour les travaux de script R.

Ce problème est résolu dans le Service Pack 1 de SQL Server 2016. Nous vous recommandons de mettre à niveau vers la dernière version de service.

**S’applique à :** version RTM de SQL Server 2016 R Services

### <a name="changes-to-column-types-cannot-be-performed-when-reading-data-in-a-sql-server-compute-context"></a>Les modifications des types de colonne ne peuvent pas être effectuées lors de la lecture de données dans un contexte de calcul SQL Server

Si votre contexte de calcul est défini sur l’instance SQL Server, vous ne pouvez pas utiliser l’argument _colClasses_ (ou d’autres arguments similaires) pour modifier le type de données des colonnes dans votre code R.

Par exemple, l’instruction suivante génère une erreur si la colonne CRSDepTimeStr n’est pas déjà un entier :

```r
data <- RxSqlServerData(sqlQuery = "SELECT CRSDepTimeStr, ArrDelay  FROM AirlineDemoSmall",
                                connectionString = connectionString,
                                colClasses = c(CRSDepTimeStr = "integer"))
```

Pour résoudre ce problème, vous pouvez réécrire la requête SQL pour l’utilisation de CAST ou convertir et présenter les données à R en utilisant le type de données correct. En général, performance est meilleure lorsque vous travaillez avec des données à l’aide de SQL plutôt que par la modification de données dans le code R.

**S’applique à :** SQL Server 2016 R Services

### <a name="limits-on-size-of-serialized-models"></a>Limite la taille des modèles sérialisés

Lorsque vous enregistrez un modèle dans une table SQL Server, vous devez sérialiser le modèle et enregistrez-le dans un format binaire. En théorie, la taille maximale d’un modèle qui peut être stocké avec cette méthode est 2 Go, ce qui est la taille maximale des colonnes varbinary dans SQL Server.

Si vous avez besoin d’utiliser des modèles plus volumineux, les solutions de contournement suivantes sont disponibles :

+ Prendre des mesures pour réduire la taille de votre modèle. Certains packages R open source incluent une grande quantité d’informations dans l’objet de modèle, et une grande partie de ces informations peut être supprimée pour le déploiement. 
+ Sélection de fonctionnalités permet de supprimer des colonnes superflues.
+ Si vous utilisez un algorithme open source, envisagez une implémentation similaire à l’aide de l’algorithme correspondant dans MicrosoftML ou RevoScaleR. Ces packages ont été optimisées pour les scénarios de déploiement.
+ Une fois le modèle a été gérée, et la taille réduite à l’aide de la procédure précédente, voir si le [memCompress](https://www.rdocumentation.org/packages/base/versions/3.4.1/topics/memCompress) fonction dans R de base peut être utilisée pour réduire la taille du modèle avant de le transmettre à SQL Server. Cette option est préférable lorsque le modèle est proche de la limite de 2 Go.
+ Pour les modèles plus volumineux, vous pouvez utiliser le serveur SQL Server [FileTable](..\relational-databases\blob\filetables-sql-server.md) pour stocker les modèles de fonctionnalités, plutôt que d’utiliser une colonne varbinary.

    Pour utiliser les FileTables, vous devez ajouter une exception de pare-feu, car les données stockées dans les FileTables sont gérées par le pilote de système de fichiers Filestream dans SQL Server, et les règles de pare-feu par défaut bloquent l’accès aux fichiers réseau. Pour plus d’informations, consultez [activer les conditions préalables pour FileTable](../relational-databases/blob/enable-the-prerequisites-for-filetable.md). 

    Une fois que vous avez activé le FileTable, pour écrire le modèle, vous obtenez un chemin d’accès à partir de SQL à l’aide de l’API FileTable et écrivez puis le modèle à cet emplacement à partir de votre code. Lorsque vous avez besoin lire le modèle, vous obtenez le chemin d’accès à partir de SQL, puis appelez le modèle en utilisant le chemin d’accès de votre script de. Pour plus d’informations, consultez [accéder aux FileTables avec les API de fichier d’entrée-sortie](../relational-databases/blob/access-filetables-with-file-input-output-apis.md).

### <a name="avoid-clearing-workspaces-when-you-execute-r-code-in-a-includessnoversionincludesssnoversion-mdmd-compute-context"></a>Éviter la suppression des espaces de travail lorsque vous exécutez le code R dans un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contexte de calcul

Si vous utilisez la commande R pour effacer votre espace de travail d’objets lors de l’exécution de code R un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contexte, de calcul ou si vous désactivez l’espace de travail dans le cadre d’un script R appelée à l’aide de [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), vous pouvez obtenir cela Erreur : 

>*objet de l’espace de travail 'revoScriptConnection' introuvable*

`revoScriptConnection` est un objet dans l’espace de travail R qui contient des informations sur une session R appelée à partir de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Toutefois, si votre code R inclut une commande pour effacer l’espace de travail (comme `rm(list=ls()))`) toutes les informations sur la session et les autres objets dans l’espace de travail R sont également effacés.

Pour résoudre ce problème, évitez d’effacement manque de discernement dans des variables et autres objets en cours d’exécution R [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Bien qu’il soit courant d’effacement de l’espace de travail lorsque vous travaillez dans la console R, il peut avoir des conséquences inattendues.

* Pour supprimer des variables spécifiques, utilisent le R *supprimer* fonction : `remove('name1', 'name2', ...)`.
* Si plusieurs variables sont à supprimer, enregistrez les noms des variables temporaires dans une liste et effectuez un nettoyage périodique.

### <a name="restrictions-on-data-that-can-be-provided-as-input-to-an-r-script"></a>Restrictions sur les données qui peuvent être fournies comme entrée à un script R

Dans un script R, vous ne pouvez pas utiliser les types de résultats de requête suivants :

- Données issues d’une requête [!INCLUDE[tsql](../includes/tsql-md.md)] qui référence des colonnes à chiffrement intégral.
  
- Données issues d’une requête [!INCLUDE[tsql](../includes/tsql-md.md)] qui référence des colonnes masquées.
  
     Si vous avez besoin d’utiliser des données masquées dans un script R, une solution de contournement possible consiste à effectuer une copie des données dans une table temporaire et à utiliser ces données à la place.

### <a name="use-of-strings-as-factors-can-lead-to-performance-degradation"></a>Utiliser des chaînes comme facteurs peuvent entraîner une dégradation des performances

À l’aide de variables de type chaîne comme facteurs peuvent augmenter considérablement la quantité de mémoire utilisée pour les opérations de R. Il s’agit en général d’un problème connu avec R, et il existe de nombreux articles sur le sujet. Par exemple, consultez [facteurs ne sont pas des citoyens dans R, par John monter, dans R-bloggers)](https://www.r-bloggers.com/factors-are-not-first-class-citizens-in-r/) ou [stringsAsFactors : une biographie non autorisée, par Roger Peng](https://simplystatistics.org/2015/07/24/stringsasfactors-an-unauthorized-biography/). 

Bien que le problème n’est pas spécifique à SQL Server, peuvent affecter considérablement les performances du code R exécuté dans SQl Server. Les chaînes sont généralement stockés en tant que varchar ou nvarchar et si une colonne de données de la chaîne possède de valeurs uniques, processus de conversion d’en interne à des entiers et à des chaînes par R même peut entraîner des erreurs d’allocation de mémoire.

Si vous n'avez pas absolument besoin un type de données de chaîne pour d’autres opérations, les valeurs de chaîne de mappage en une valeur numérique (entier) de type de données comme partie de la préparation des données peut être avantageuse en termes de performances et l’échelle.

Pour en savoir plus sur ce problème et d’autres conseils, consultez [performances pour R Services - optimisation des données](r/r-and-data-optimization-r-services.md).

### <a name="arguments-varstokeep-and-varstodrop-are-not-supported-for-sql-server-data-sources"></a>Arguments *varsToKeep* et *varsToDrop* ne sont pas pris en charge pour les sources de données SQL Server

Lorsque vous utilisez la fonction rxDataStep pour écrire les résultats dans une table, à l’aide du *varsToKeep* et *varsToDrop* est un moyen pratique de définir les colonnes à inclure ou exclure dans le cadre de l’opération. Toutefois, ces arguments ne sont pas pris en charge pour les sources de données SQL Server.

### <a name="limited-support-for-sql-data-types-in-spexecuteexternalscript"></a>Prise en charge limitée pour les types de données SQL dans`sp_execute_external_script`

Tous les types de données pris en charge dans SQL ne peuvent pas être utilisés dans R. Pour résoudre ce problème, envisagez de convertir le type de données non pris en charge pour un type de données pris en charge avant de transmettre les données à sp_execute_external_script.

Pour plus d’informations, consultez [R bibliothèques et types de données](r/r-libraries-and-data-types.md).

### <a name="possible-string-corruption"></a>Corruption de chaîne possible

Tout aller-retour des données de chaîne à partir de [!INCLUDE[tsql](../includes/tsql-md.md)] sur R, puis sur [!INCLUDE[tsql](../includes/tsql-md.md)] nouveau peuvent provoquer une corruption. Cela est dû aux différents codages utilisés dans R et dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], ainsi que les différents classements et langues prises en charge dans R et [!INCLUDE[tsql](../includes/tsql-md.md)]. Toute chaîne dans un codage non-ASCII risque d’être gérée de façon incorrecte.

Lorsque vous envoyez des données de type chaîne vers R, convertissez-les en une représentation ASCII, si possible.

Cette limitation s’applique aux données passées entre SQL Server et Python également. Caractères multioctets doivent être passés en tant que UTF-8 et stockées au format Unicode.

### <a name="only-one-value-of-type-raw-can-be-returned-from-spexecuteexternalscript"></a>Une seule valeur de type `raw` peuvent être retournées à partir de`sp_execute_external_script`

Lorsqu’un type de données binaires (R **brutes** type de données) est retournée à partir de R, la valeur doit être envoyée dans la trame de données de sortie.

Avec les données les types autres que **brutes**, vous pouvez retourner des valeurs de paramètre, ainsi que les résultats de la procédure stockée en ajoutant le mot clé OUTPUT. Pour plus d’informations, consultez [paramètres](https://docs.microsoft.com/sql/relational-databases/stored-procedures/parameters).

Si vous souhaitez utiliser plusieurs jeux de sortie qui incluent des valeurs de type **brutes**, une solution de contournement possible consiste à effectuer plusieurs appels de la procédure stockée, ou pour envoyer le résultat jeux à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l’aide de ODBC.

### <a name="loss-of-precision"></a>Perte de précision

Étant donné que [!INCLUDE[tsql](../includes/tsql-md.md)] et R prennent en charge différents types de données, les types de données numériques peuvent subir une perte de précision lors de la conversion.

Pour plus d’informations sur la conversion de type de données implicite, consultez [R bibliothèques et types de données](r/r-libraries-and-data-types.md).

### <a name="variable-scoping-error-when-you-use-the-transformfunc-parameter-the-sample-data-set-for-the-analysis-has-no-variables"></a>Erreur de portée lorsque vous utilisez le paramètre transformfunc est utilisé de variable : *l’exemple de jeu de données pour l’analyse ne comporte aucune variable*

Pour transformer des données pendant que vous modélisez, vous pouvez passer un *transformfunc est utilisé* argument dans une fonction telle que `rxLinmod` ou `rxLogit`. Toutefois, les appels de fonction imbriqués risque d’erreurs de portée dans le contexte de calcul de SQL Server, même si les appels fonctionnent correctement dans le contexte de calcul local.

Par exemple, supposons que vous avez défini deux fonctions, `f` et `g`, dans votre environnement global local, et `g` appelle `f`. Dans les appels distribués ou distants impliquant `g`, l’appel à `g` risque d’échouer car `f` est introuvable, même si vous avez transmis à la fois `f` et `g` à l’appel distant.

Si vous rencontrez ce problème, vous pouvez le résoudre en incorporant la définition de `f` dans votre définition de `g`, n’importe où avant l’appel habituel de `g` par `f`.

Exemple :

```r
f <- function(x) { 2*x * 3 }
g <- function(y) {
              a <- 10 * y
               f(a)
}
```

Pour éviter cette erreur, réécrivez la définition comme suit :

```r
g <- function(y){
              f <- function(x) { 2*x +3}
              a <- 10 * y
              f(a)
}
```

### <a name="data-import-and-manipulation-using-revoscaler"></a>Importation et manipulation de données à l’aide de RevoScaleR

Lorsque **varchar** colonnes sont lues à partir d’une base de données, un espace blanc est tronqué. Pour éviter cela, placez les chaînes entre caractères autres qu’un espace.

Lorsque les fonctions telles que `rxDataStep` sont utilisées pour créer des tables de base de données qui ont **varchar** colonnes, la largeur de colonne est estimée en fonction d’un échantillon des données. Si la largeur peut varier, il peut être nécessaire compléter toutes les chaînes en une longueur commune.

L’utilisation d’une transformation pour modifier le type de données d’une variable n’est pas prise en charge quand des appels répétés à `rxImport` ou `rxTextToXdf` sont effectués pour importer et ajouter des lignes, combinant plusieurs fichiers d’entrée dans un fichier .xdf unique.

### <a name="limited-support-for-rxexec"></a>Prise en charge limitée de rxExec

Dans SQL Server 2016, le `rxExec` fonction qui est fournie par le RevoScaleR package peut être utilisé uniquement en mode de thread unique.

Parallélisme pour `rxExec` entre plusieurs processus est prévue pour une version ultérieure.

### <a name="increase-the-maximum-parameter-size-to-support-rxgetvarinfo"></a>Augmentez la taille de paramètre maximale pour prendre en charge rxGetVarInfo

Si vous utilisez des jeux de données avec un grand nombre de variables (par exemple, plus de 40 000), définissez la `max-ppsize` indicateur lorsque vous démarrez R pour utiliser des fonctions telles que `rxGetVarInfo`. L’indicateur `max-ppsize` spécifie la taille maximale de la pile de protection du pointeur.

Si vous utilisez la console R (par exemple, dans rgui.exe ou rterm.exe), vous pouvez définir la valeur de max-ppsize sur 500000 en tapant :

```r
R --max-ppsize=500000
```

Si vous utilisez la [!INCLUDE[rsql_developr](../includes/rsql-developr-md.md)] environnement, vous pouvez définir le `max-ppsize` indicateur en effectuant l’appel suivant à l’exécutable revoide comme suit :

```
RevoIDE.exe /RCommandLine --max-ppsize=500000  
```

### <a name="issues-with-the-rxdtree-function"></a>Problèmes liés à la fonction rxDTree

La fonction `rxDTree` ne prend pas en charge actuellement les transformations dans les formules. En particulier, l’utilisation de la syntaxe `F()` pour créer des facteurs à la volée n’est pas prise en charge. Toutefois, les données numériques sont automatiquement placées.

Les facteurs ordonnés sont traités de la même façon que les facteurs dans toutes les fonctions d’analyse RevoScaleR, sauf `rxDTree`.

## <a name="python-code-execution-or-python-package-issues"></a>L’exécution du code Python ou de problèmes liés à des packages Python

Cette section contient des problèmes connus qui sont spécifiques à l’exécution de Python sur SQL Server, ainsi que des problèmes liés aux packages Python publiés par Microsoft, y compris [revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) et [microsoftml](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package).

### <a name="call-to-pretrained-model-fails-if-path-to-model-is-too-long"></a>Appel au modèle préformé échoue si le chemin d’accès au modèle est trop long

Si vous installez les modèles préformés dans une installation par défaut, en fonction de votre nom de l’ordinateur et le nom de l’instance, le chemin d’accès complet obtenu dans le fichier de modèle formé peut être trop long pour Python à lire. Cette limitation sera résolue dans une version de service à venir.

Il existe plusieurs solutions possibles : 

+ Lorsque vous installez les modèles préformés, choisissez un emplacement personnalisé.
+ Si possible, installez l’instance de SQL Server sous un chemin d’installation personnalisé, tel que C:\SQL\MSSQL14. MSSQLSERVER.
+ Utilisez l’utilitaire Windows [Fsutil](https://technet.microsoft.com/library/cc788097(v=ws.11).aspx) pour créer un lien réel qui mappe le fichier de modèle sur un chemin plus court. 

### <a name="failure-to-initialize-a-varbinary-variable-causes-an-error-in-bxlserver"></a>Impossible d’initialiser une variable varbinary provoque une erreur dans BxlServer

Si vous exécutez le code Python à l’aide de SQL Server `sp_execute_external_script`et le code possède des variables de type varbinary (max), varchar (max) ou des types semblables de sortie, la variable doit être initialisée ou définie dans le cadre de votre script. Sinon, le composant d’échange de données, BxlServer, déclenche une erreur et s’arrête de fonctionner.

Cette limitation sera résolue dans une version de service à venir. Pour résoudre ce problème, assurez-vous que la variable est initialisée dans le script Python. N’importe quelle valeur peut être utilisé, comme dans les exemples suivants :

```sql
declare @b varbinary(max);
exec sp_execute_external_script
  @language = N'Python'
  , @script = N'b = 0x0'
  , @params = N'@b varbinary(max) OUTPUT'
  , @b = @b OUTPUT;
go
```

```sql
declare @b varchar(30);
exec sp_execute_external_script
  @language = N'Python'
  , @script = N' b = ""  '
  , @params = N'@b varchar(30) OUTPUT'
  , @b = @b OUTPUT;
go
```

## <a name="revolution-r-enterprise-and-microsoft-r-open"></a>Revolution R Enterprise et Microsoft R Open

Cette section répertorie les problèmes propres à la connectivité, de développement et outils de performance fournis par Revolution Analytique R. Ces outils ont été fournis dans les versions préliminaires antérieures de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].

En général, nous recommandons que vous désinstallez les versions précédentes et installez la dernière version de SQL Server ou Microsoft R Server.

### <a name="running-side-by-side-versions-of-revolution-r-enterprise"></a>Versions en cours d’exécution côte à côte de Revolution R Enterprise

L’installation côte à côte de Revolution R Enterprise avec n’importe quelle version de [!INCLUDE[rsql_productname_md](../includes/rsql-productname-md.md)] n’est pas pris en charge.

Si vous avez une licence pour utiliser une version différente de Revolution R Enterprise, vous devez la placer sur un ordinateur autre que celui de l’instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et que toute station de travail que vous souhaitez utiliser pour vous connecter à l’instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .

### <a name="the-use-of-an-r-productivity-environment-is-not-supported"></a>L’utilisation d’un environnement de productivité R n’est pas pris en charge.

Certaines versions préliminaires de [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)] inclus un environnement de développement R pour Windows qui a été créé par Revolution Analytique. Cet outil n’est plus disponible, et il n’est pas pris en charge.

Pour la compatibilité avec [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)], nous recommandons fortement d’installer Microsoft R Client ou Microsoft R Server au lieu des outils Revolution Analytique. [R Tools pour Visual Studio](https://www.visualstudio.com/vs/rtvs/) et [Visual Studio Code](https://code.visualstudio.com/) prend également en charge les solutions de Microsoft R.

### <a name="compatibility-issues-with-sqlite-odbc-driver-and-revoscaler"></a>Problèmes de compatibilité avec le pilote ODBC de SQLite et RevoScaleR

Révision 0.92 du pilote ODBC de SQLite est incompatible avec RevoScaleR. Révisions 0.88 à 0.91, 0.93 et ultérieur sont connues pour être compatibles.


## <a name="see-also"></a>Voir aussi

[Nouveautés de SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md)

[Résolution des problèmes d’apprentissage dans SQL Server](machine-learning-troubleshooting-faq.md)
