---
title: Problèmes connus pour le langage R et l’intégration de Python - SQL Server Machine Learning Services
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/29/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 2b9ed73b2b4cb65696f9809d757eb901367dde63
ms.sourcegitcommit: b6ca8596c040fa731efd397e683226516c9f8359
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64906163"
---
# <a name="known-issues-in-machine-learning-services"></a>Problèmes connus dans Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit les problèmes connus ou limitations avec les composants d’apprentissage automatique qui sont fournies en tant qu’option dans [SQL Server 2016 R Services](install/sql-r-services-windows-install.md) et [SQL Server 2017 Machine Learning Services avec R et Python](install/sql-machine-learning-services-windows-install.md).

## <a name="setup-and-configuration-issues"></a>Problèmes d’installation et configuration

Pour obtenir une description des processus et des questions courantes liées à la configuration initiale et la configuration, consultez [FAQ d’installation et de mise à niveau](r/upgrade-and-installation-faq-sql-server-r-services.md). Il contient des informations sur les mises à niveau, l’installation de la côte à côte et installation de nouveaux composants de R ou Python.

### <a name="1-inconsistent-results-in-mkl-computations-due-to-missing-environment-variable"></a>1. Résultats incohérents dans les calculs MKL due à l’absence de variable d’environnement

**S’applique à :** Fichiers binaires R_SERVER 9.0, 9.1, 9.2 ou 9.3.

R_SERVER utilise Intel Math Kernel Library (MKL). Pour effectuer des calculs impliquant MKL, des résultats incohérents peuvent se produire si votre système n’a pas une variable d’environnement. 

Définissez la variable d’environnement `'MKL_CBWR'=AUTO` pour garantir la reproductibilité de numérique conditionnelle dans R_SERVER. Pour plus d’informations, consultez [Introduction à conditionnel numérique reproductibilité (CNR)](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr).

**Solution de contournement**

1. Dans le panneau de configuration, cliquez sur **système et sécurité** > **système** > **paramètres système avancés**  >   **Variables d’environnement**.

2. Créer une nouvelle variable utilisateur ou système. 

  + Définissez le nom de variable 'MKL_CBWR'.
  + La valeur ' Variable' à 'AUTO'.

3. Redémarrez R_SERVER. Sur le serveur SQL Server, vous pouvez redémarrer le Launchpad Service de SQL Server.

> [!NOTE]
> Si vous exécutez la version préliminaire de SQL Server 2019 sur Linux, modifiez ou créez *.bash_profile* dans votre répertoire de base de l’utilisateur, ajoutez la ligne `export MKL_CBWR="AUTO"`. Exécutez ce fichier en tapant `source .bash_profile` à une invite de commandes bash. Redémarrez R_SERVER en tapant `Sys.getenv()` à l’invite de commande R.

### <a name="2-r-script-runtime-error-sql-server-2017-cu5-cu7-regression"></a>2. Erreur d’exécution de Script R (SQL Server 2017 CU5-CU7 régression)

Pour SQL Server 2017, les mises à jour cumulative 5 à 7, il existe une régression dans le **rlauncher.config** où le chemin d’accès de répertoire temporaire inclut un espace de fichier. Cette régression est corrigée dans CU8.

L’erreur que s’affiche lors de l’exécution du script R inclut les messages suivants :

> *Impossible de communiquer avec le runtime de script « R ». Vérifiez la configuration requise du runtime « R ».*
>
> Message (s) STDERR à partir du script externe : 
>
> *Erreur irrécupérable : Impossible de créer 'R_TempDir'*

**Solution de contournement**

Appliquer CU8 lorsqu’elle est disponible. Vous pouvez également recréer **rlauncher.config** en exécutant **registerrext** avec désinstallez/installez sur une invite de commandes avec élévation de privilèges. 

```cmd
<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExt.exe /uninstall /sqlbinnpath:<SQLInstanceBinnPath> /userpoolsize:0 /instance:<SQLInstanceName>

<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExt.exe /install /sqlbinnpath:<SQLInstanceBinnPath> /userpoolsize:0 /instance:<SQLInstanceName>
```

L’exemple suivant montre les commandes avec l’instance par défaut « MSSQL14. MSSQLSERVER » installé dans « C:\Program Files\Microsoft SQL Server\":

```cmd
"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRext.exe" /uninstall /sqlbinnpath:"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\Binn" /userpoolsize:0 /instance:MSSQLSERVER

"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRext.exe" /install /sqlbinnpath:"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\Binn" /userpoolsize:0 /instance:MSSQLSERVER
```

### <a name="3-unable-to-install-sql-server-machine-learning-features-on-a-domain-controller"></a>3. Impossible d’installer des fonctionnalités de SQL Server machine learning sur un contrôleur de domaine

Si vous essayez d’installer SQL Server 2016 R Services ou SQL Server 2017 Machine Learning Services sur un contrôleur de domaine, le programme d’installation échoue, avec ces erreurs :

> *Une erreur s’est produite pendant le processus d’installation de la fonctionnalité*
> 
> *Impossible de trouver le groupe avec l’identité*
> 
> *Code d’erreur de composant : 0x80131509*

L’échec se produit parce que, sur un contrôleur de domaine, le service ne peut pas créer les comptes locaux 20 requis pour exécuter l’apprentissage. En règle générale, nous recommandons l’installation de SQL Server sur un contrôleur de domaine. Pour plus d’informations, consultez [bulletin de prise en charge 2032911](https://support.microsoft.com/help/2032911/you-may-encounter-problems-when-installing-sql-server-on-a-domain-cont).

### <a name="4-install-the-latest-service-release-to-ensure-compatibility-with-microsoft-r-client"></a>4. Installer la dernière version de service pour garantir la compatibilité avec Microsoft R Client

Si vous installez la dernière version de Microsoft R Client et l’utiliser pour exécuter R sur SQL Server dans un contexte de calcul à distance, vous pouvez obtenir une erreur semblable à celui-ci :

> *9.x.x de version de Microsoft R Client sont en cours d’exécution sur votre ordinateur, ce qui n’est pas compatible avec Microsoft R Server version 8.x.x. Téléchargez et installez une version compatible.*

SQL Server 2016 nécessite que les bibliothèques R sur le client correspondent exactement les bibliothèques R sur le serveur. La restriction a été supprimée pour les versions R Server 9.0.1 au plus tard. Toutefois, si vous rencontrez cette erreur, vérifiez la version des bibliothèques R qui est utilisée par votre client et le serveur et, si nécessaire, mettre à jour le client pour faire correspondre la version du serveur.

La version de R est installé avec SQL Server R Services est mis à jour chaque fois qu’une version de service SQL Server est installée. Pour vous assurer que vous disposez toujours des versions les plus récentes des composants R, veillez à installer tous les service packs.

Pour garantir la compatibilité avec la version 9.0.0 de Microsoft R Client, installez les mises à jour qui sont décrites dans ce [article du support technique](https://support.microsoft.com/kb/3210262).

Pour éviter tout problème avec les packages R, vous pouvez également mettre à niveau la version des bibliothèques R qui sont installés sur le serveur, en modifiant votre contrat de maintenance pour utiliser la stratégie de prise en charge de cycle de vie moderne, comme décrit dans [la section suivante](#bkmk_sqlbindr). Lorsque vous procédez ainsi, la version de R est installé avec SQL Server est mis à jour sur la même planification utilisée pour les mises à jour de machine Learning Server (anciennement Microsoft R Server).

**S’applique à :** SQL Server 2016 R Services, avec la version 9.0.0 de R Server ou une version antérieure

### <a name="5-r-components-missing-from-cu3-setup"></a>5. Composants R manquante dans le programme d’installation CU3

Un nombre limité de machines virtuelles ont été mis en service sans les fichiers d’installation de R doivent être inclus dans SQL Server. Le problème s’applique aux machines virtuelles configurées dans la période de 2018-01-05 pour 2018-01-23. Ce problème peut également affecter les installations locales, si vous avez appliqué la mise à jour SQL Server 2017 CU3 pendant la période à partir de 2018-01-05 pour 2018-01-23.

Une version de service a été fournie qui inclut la version correcte des fichiers d’installation de R.

+ [Package de mise à jour cumulative 3 pour SQL Server 2017 KB4052987](https://www.microsoft.com/download/details.aspx?id=56128).

Pour installer les composants et réparer SQL Server 2017 CU3, vous devez désinstaller CU3 et réinstaller la version mise à jour :

1. Téléchargez le fichier d’installation mis à jour CU3, qui inclut les programmes d’installation de R.
2. Désinstallez CU3. Dans le panneau de configuration, recherchez **désinstaller une mise à jour**, puis sélectionnez « Hotfix 3015 pour SQL Server 2017 (KB4052987) (64 bits) ». Passez aux étapes de désinstallation.
3. Réinstaller la mise à jour CU3, en double-cliquant sur la mise à jour pour KB4052987 que vous venez de télécharger : `SQLServer2017-KB4052987-x64.exe`. Suivez les instructions d'installation.

### <a name="6-unable-to-install-python-components-in-offline-installations-of-sql-server-2017-ctp-20-or-later"></a>6. Impossible d’installer les composants de Python dans des installations hors connexion de SQL Server 2017 CTP 2.0 ou version ultérieure

Si vous installez une version préliminaire de SQL Server 2017 sur un ordinateur sans accès à internet, le programme d’installation peut échouer afficher la page de demande pour l’emplacement des composants Python téléchargés. Dans ce cas, vous pouvez installer la fonctionnalité Services Machine Learning, mais pas les composants de Python.

Ce problème est résolu dans la version release. En outre, cette limitation ne s’applique pas aux composants de R.

**S’applique à :** SQL Server 2017 avec Python

### <a name="bkmk_sqlbindr"></a> Avertissement de version incompatible lorsque vous vous connectez à une version antérieure de SQL Server R Services à partir d’un client à l’aide de [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]

Lorsque vous exécutez le code R dans un serveur SQL Server 2016 contexte de calcul, vous pouvez rencontrer l’erreur suivante :

> *Vous exécutez la version 9.0.0 de Microsoft R Client sur votre ordinateur, ce qui est incompatible avec la version 8.0.3 de Microsoft R Server. Téléchargez et installez une version compatible.*

Ce message s’affiche si une des deux instructions suivantes est vraie,

+ Vous avez installé R Server (autonome) sur un ordinateur client à l’aide de l’Assistant Installation de [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].
+ Vous avez installé Microsoft R Server à l’aide de la [séparer le programme d’installation de Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

Pour s’assurer que le serveur et le client utilisent la même version que vous devrez peut-être utiliser _liaison_, pris en charge pour Microsoft R Server 9.0 et versions ultérieures mettre à niveau les composants R dans les instances de SQL Server 2016. Pour déterminer si prise en charge des mises à niveau est disponible pour votre version de R Services, consultez [mettre à niveau une instance de R Services à l’aide de SqlBindR.exe](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

**S’applique à :** SQL Server 2016 R Services, avec la version 9.0.0 de R Server ou une version antérieure

### <a name="7-setup-for-sql-server-2016-service-releases-might-fail-to-install-newer-versions-of-r-components"></a>7. La configuration des versions de services de SQL Server 2016 peut échouer à installer de nouvelles versions des composants R

Lorsque vous installez une mise à jour cumulative ou que vous installez un service pack pour SQL Server 2016 sur un ordinateur qui n’est pas connecté à internet, l’Assistant installation peut ne pas afficher l’invite qui vous permet de mettre à jour les composants R à l’aide des fichiers CAB téléchargés. Cet échec se produit généralement lorsque plusieurs composants ont été installés avec le moteur de base de données.

Pour résoudre ce problème, vous pouvez installer la version de service en utilisant la ligne de commande et en spécifiant le `MRCACHEDIRECTORY` argument comme indiqué dans cet exemple, qui installe les mises à jour CU1 :

`C:\<path to installation media>\SQLServer2016-KB3164674-x64.exe /Action=Patch /IACCEPTROPENLICENSETERMS /MRCACHEDIRECTORY=<path to CU1 CAB files>`

Pour obtenir les programmes d’installation plus récente, consultez [installer les composants d’apprentissage automatique sans accès à internet](install/sql-ml-component-install-without-internet-access.md).

**S’applique à :** SQL Server 2016 R Services, avec la version 9.0.0 de R Server ou une version antérieure

### <a name="8-launchpad-services-fails-to-start-if-the-version-is-different-from-the-r-version"></a>8. Le service LaunchPad ne parvient pas à démarrer si la version est différente de la version de R

Si vous installez SQL Server R Services séparément à partir du moteur de base de données, et les versions de build sont différentes, vous pouvez voir l’erreur suivante dans le journal des événements système :

> *Le service Launchpad de SQL Server a échoué car l’erreur suivante : Le service n’a pas répondu à la demande de démarrage ou de contrôle en temps voulu.*

Par exemple, cette erreur peut se produire si vous installez le moteur de base de données à l’aide de la version release, appliquer un correctif pour mettre à niveau le moteur de base de données, puis ajouter la fonctionnalité R Services à l’aide de la version release.

Pour éviter ce problème, utilisez un utilitaire tel que le Gestionnaire de fichiers pour comparer les versions de Launchpad.exe avec la version des fichiers binaires SQL, tels que sqldk.dll. Tous les composants doivent avoir le même numéro de version. Si vous mettez à niveau un composant, veillez à appliquer la même mise à niveau à tous les autres composants installés.

Recherchez le Launchpad dans le `Binn` dossier pour l’instance. Par exemple, dans une installation par défaut de SQL Server 2016, le chemin d’accès peut être `C:\Program Files\Microsoft SQL Server\MSSQL.13.InstanceNameMSSQL\Binn`. 

### <a name="9-remote-compute-contexts-are-blocked-by-a-firewall-in-sql-server-instances-that-are-running-on-azure-virtual-machines"></a>9. Contextes de calcul distants sont bloqués par un pare-feu dans les instances de SQL Server qui s’exécutent sur des machines virtuelles Azure

Si vous avez installé [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] sur une machine virtuelle Windows Azure, vous ne pouvez pas être en mesure d’utiliser des contextes de calcul qui nécessitent l’utilisation de l’espace de travail de la machine virtuelle. La raison est que, par défaut, le pare-feu sur les machines virtuelles Azure inclut une règle qui bloque accès pour les comptes d’utilisateur locaux R l'réseau.

Pour résoudre ce problème, sur la machine virtuelle Azure, ouvrez **pare-feu Windows avec fonctions avancées de sécurité**, sélectionnez **règles de trafic sortant**et désactivez la règle suivante : **Bloquer l’accès réseau pour les comptes d’utilisateur locaux R dans l’instance SQL Server MSSQLSERVER**. Vous pouvez également laisser la règle est activée, mais modifier la propriété de sécurité à **Autoriser si paramètres sécurisés**.

### <a name="10-implied-authentication-in-sqlexpress"></a>10. Authentification implicite dans SQLEXPRESS

Lorsque vous exécutez des travaux R à partir d’une station de travail de science des données à distance à l’aide de l’authentification Windows intégrée, SQL Server utilise *l’authentification implicite* pour générer tous les appels ODBC locaux qui peuvent être requis par le script. Toutefois, cette fonctionnalité ne marchait pas dans la version RTM de SQL Server Express Edition.

Pour résoudre ce problème, nous vous recommandons d’effectuer la mise à niveau vers une version ultérieure du service.

Si la mise à niveau n’est pas possible, pour résoudre ce problème, utilisez une connexion SQL pour exécuter des travaux R distants susceptibles de nécessiter des appels ODBC incorporés.

**S’applique à :** SQL Server 2016 R Services Express Edition

### <a name="11-performance-limits-when-libraries-used-by-sql-server-are-called-from-other-tools"></a>11. Limites de performances lorsque les bibliothèques utilisées par SQL Server sont appelées à partir d’autres outils

Il est possible d’appeler le bibliothèques machine learning qui sont installés pour SQL Server à partir d’une application externe, telle que RGui. Cela peut être la méthode la plus pratique pour effectuer certaines tâches, telles que l’installation de nouveaux packages, ou en cours d’exécution des tests ad hoc sur les exemples de code très courte. Toutefois, en dehors de SQL Server, les performances peuvent être limitées. 

Par exemple, même si vous utilisez SQL Server Enterprise Edition, R s’exécute en mode monothread lorsque vous exécutez votre code R à l’aide des outils externes. Pour obtenir les avantages de performances dans SQL Server, établir une connexion SQL Server et utiliser [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) pour appeler le runtime de script externe.

En règle générale, évitez d’appeler le bibliothèques machine learning qui sont utilisés par SQL Server à partir d’outils externes. Si vous avez besoin pour le débogage R ou Python code, il est généralement plus facile à faire en dehors de SQL Server. Pour obtenir les mêmes bibliothèques qui se trouvent dans SQL Server, vous pouvez installer Microsoft R Client, [SQL Server 2017 Machine Learning Server (autonome)](install/sql-machine-learning-standalone-windows-install.md), ou [SQL Server 2016 R Server (autonome)](install/sql-r-standalone-windows-install.md).

### <a name="12-sql-server-data-tools-does-not-support-permissions-required-by-external-scripts"></a>12. SQL Server Data Tools ne prend pas en charge les autorisations requises par les scripts externes

Lorsque vous utilisez Visual Studio ou SQL Server Data Tools pour publier un projet de base de données, si n’importe quel principal dispose des autorisations spécifiques à l’exécution du script externe, vous pouvez obtenir une erreur similaire à celle-ci :

> *Modèle TSQL : Erreur détectée lors d’un processus d’ingénierie de la base de données. L’autorisation n’a pas été reconnue et n’a pas été importée.*

Actuellement le modèle DACPAC ne prend pas en charge les autorisations utilisées par R Services ou des Services Machine Learning, telles que GRANT ANY EXTERNAL SCRIPT ou EXECUTE ANY EXTERNAL SCRIPT. Ce problème sera résolu dans une version ultérieure.

Pour résoudre ce problème, exécutez l’octroi supplémentaire instructions dans un script de post-déploiement.

### <a name="13-external-script-execution-is-throttled-due-to-resource-governance-default-values"></a>13. L’exécution du script externe est limitée en raison de valeurs par défaut de gouvernance des ressources

Dans Enterprise Edition, vous pouvez utiliser des pools de ressources pour gérer les processus de script externe. Dans les quelques premières versions de mise en production, la mémoire maximale pouvant être allouée aux processus R était de 20 pour cent. Par conséquent, si le serveur possédait 32 Go de RAM, les exécutables R (RTerm.exe et BxlServer.exe) d’utiliser un maximum de 6,4 Go dans une demande unique.

Si vous rencontrez des limitations de ressources, vérifiez la valeur par défaut actuelle. Si 20 pour cent ne suffit pas, consultez la documentation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur la façon de modifier cette valeur.

**S’applique à :** SQL Server 2016 R Services, Enterprise Edition

## <a name="r-script-execution-issues"></a>Problèmes d’exécution du script R

Cette section contient des problèmes connus qui sont spécifiques à l’exécution de R sur SQL Server, ainsi que certains problèmes liés aux bibliothèques R et outils publiées par Microsoft, y compris RevoScaleR.

Pour les autres problèmes connus susceptibles d’affecter des solutions R, consultez le [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues) site.

### <a name="1-access-denied-warning-when-executing-r-scripts-on-sql-server-in-a-non-default-location"></a>1. Accès refusé avertissement lors de l’exécution de scripts R sur SQL Server dans un emplacement non par défaut

Si l’instance de SQL Server a été installé à un emplacement non défini par défaut, comme en dehors de la `Program Files` dossier, l’avertissement ACCESS_DENIED est déclenché lorsque vous essayez d’exécuter des scripts qui installent un package. Exemple :

> *Dans `normalizePath(path.expand(path), winslash, mustWork)` : chemin d’accès [2] = « ~ExternalLibraries/R/8/1 » : L’accès est refusé*

La raison est qu’une fonction R tente de lire le chemin d’accès et échoue si le groupe d’utilisateurs intégrés **SQLRUserGroup**, n’a pas accès en lecture. L’avertissement est déclenché ne bloque pas l’exécution du script R en cours, mais l’avertissement peut se répéter à plusieurs reprises à chaque fois que l’utilisateur exécute n’importe quel autre script R.

Si vous avez installé SQL Server à l’emplacement par défaut, cette erreur ne se produit pas, car tous les utilisateurs Windows ont des autorisations de lecture sur le `Program Files` dossier.

Ce problème ia résolu dans une version de service à venir. Pour résoudre ce problème, fournissez le groupe, **SQLRUserGroup**, avec accès en lecture pour tous les dossiers parents de `ExternalLibraries`.

### <a name="2-serialization-error-between-old-and-new-versions-of-revoscaler"></a>2. Erreur de sérialisation entre les versions anciennes et nouvelles de RevoScaleR

Lorsque vous passez d’un modèle à l’aide d’un format sérialisé à une instance distante de SQL Server, vous pouvez obtenir l’erreur : 

> *Erreur dans memDecompress (données, type = décompresser) erreur interne de -3 dans memDecompress(2).*

Cette erreur est générée si vous avez enregistré le modèle à l’aide d’une version récente de la fonction de sérialisation, [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel), mais l’instance de SQL Server où vous désérialisez le modèle a une version antérieure des APIs RevoScaleR, à partir de SQL Server 2017 CU2 ou version antérieure.

Pour résoudre ce problème, vous pouvez mettre à niveau l’instance de SQL Server 2017 CU3 ou version ultérieure.

L’erreur n’apparaît pas si la version d’API est identique, ou si vous déplacez un modèle enregistré avec une fonction de sérialisation plus anciennes vers un serveur qui utilise une version plus récente de l’API de sérialisation.

En d’autres termes, utilisez la même version de RevoScaleR pour les opérations de sérialisation et la désérialisation.

### <a name="3-real-time-scoring-does-not-correctly-handle-the-learningrate-parameter-in-tree-and-forest-models"></a>3. Calcul de score en temps réel ne gère pas correctement le _learningRate_ paramètre dans les modèles d’arborescence et de forêt

Si vous créez un modèle à l’aide d’un arbre de décision ou de la méthode de forêt de décision et que vous spécifiez le taux d’apprentissage, vous pouvez voir des résultats incohérents lorsque vous utilisez `sp_rxpredict` ou le code SQL `PREDICT` (fonction), par rapport à l’aide `rxPredict`.

La cause est une erreur dans l’API qui modélise les processus sérialisés et est limitée à la `learningRate` paramètre : par exemple, dans [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees), ou

Ce problème est résolu dans une version de service à venir.

### <a name="4-limitations-on-processor-affinity-for-r-jobs"></a>4. Limitations sur l’affinité du processeur pour les tâches R

Dans la build de la version initiale de SQL Server 2016, vous pouvez définir l’affinité du processeur uniquement pour les processeurs sur le premier k-group. Par exemple, si le serveur est une machine à 2 sockets avec deux k-groups, seuls les processeurs du premier groupe de k sont utilisés pour les processus R. La même restriction s’applique lorsque vous configurez la gouvernance des ressources pour les tâches de script R.

Ce problème est résolu dans le Service Pack 1 de SQL Server 2016. Nous vous recommandons de mettre à niveau vers la dernière version de service.

**S’applique à :** Version RTM de SQL Server 2016 R Services

### <a name="5-changes-to-column-types-cannot-be-performed-when-reading-data-in-a-sql-server-compute-context"></a>5. Les modifications des types de colonne ne peuvent pas être effectuées lors de la lecture de données dans un contexte de calcul SQL Server

Si votre contexte de calcul est défini sur l’instance SQL Server, vous ne pouvez pas utiliser l’argument _colClasses_ (ou d’autres arguments similaires) pour modifier le type de données des colonnes dans votre code R.

Par exemple, l’instruction suivante génère une erreur si la colonne CRSDepTimeStr n’est pas déjà un entier :

```R
data <- RxSqlServerData(
  sqlQuery = "SELECT CRSDepTimeStr, ArrDelay  FROM AirlineDemoSmall", 
  connectionString = connectionString, 
  colClasses = c(CRSDepTimeStr = "integer"))
```

Pour résoudre ce problème, vous pouvez réécrire la requête SQL pour utiliser CAST ou CONVERT et présenter les données à R en utilisant le type de données correct. En règle générale, performances sont mieux lorsque vous travaillez avec des données à l’aide de SQL plutôt que par modification des données dans le code R.

**S’applique à :** SQL Server 2016 R Services

### <a name="6-limits-on-size-of-serialized-models"></a>6. Limite la taille des modèles sérialisés

Lorsque vous enregistrez un modèle dans une table SQL Server, vous devez sérialiser le modèle et enregistrez-le dans un format binaire. En théorie, la taille maximale d’un modèle qui peut être stocké avec cette méthode est 2 Go, ce qui est la taille maximale des colonnes varbinary dans SQL Server.

Si vous avez besoin d’utiliser des modèles plus volumineux, les solutions de contournement suivantes sont disponibles :

+ Prendre des mesures pour réduire la taille de votre modèle. Certains packages R open source incluent un grand nombre d’informations dans l’objet de modèle, et une grande partie de ces informations peut être supprimée pour le déploiement. 
+ Sélection de fonctionnalités permet de supprimer les colonnes inutiles.
+ Si vous utilisez un algorithme open source, envisagez une mise en œuvre similaire à l’aide de l’algorithme correspondant dans MicrosoftML ou RevoScaleR. Ces packages ont été optimisés pour les scénarios de déploiement.
+ Une fois que le modèle a été rationalisé et la taille réduite à l’aide de la procédure précédente, consultez si le [memCompress](https://www.rdocumentation.org/packages/base/versions/3.4.1/topics/memCompress) fonction dans R de base peut être utilisée pour réduire la taille du modèle avant de le transmettre à SQL Server. Cette option est recommandée lorsque le modèle est proche de la limite de 2 Go.
+ Pour les modèles plus volumineux, vous pouvez utiliser le serveur SQL Server [FileTable](../relational-databases/blob/filetables-sql-server.md) pour stocker les modèles de fonctionnalités, plutôt que d’utiliser une colonne varbinary.

    Pour utiliser les FileTables, vous devez ajouter une exception de pare-feu, car les données stockées dans les FileTables sont gérées par le pilote de système de fichiers Filestream dans SQL Server, et les règles de pare-feu par défaut bloquent l’accès de fichier de réseau. Pour plus d’informations, consultez [activer les conditions préalables pour FileTable](../relational-databases/blob/enable-the-prerequisites-for-filetable.md).

    Une fois que vous avez activé le FileTable, pour écrire le modèle, vous obtenez un chemin d’accès de SQL à l’aide de l’API de table de fichiers et puis le modèle d’écriture à cet emplacement à partir de votre code. Lorsque vous avez besoin de lire le modèle, vous obtenez le chemin d’accès à partir de SQL, puis appelez le modèle en utilisant le chemin d’accès à partir de votre script. Pour plus d’informations, consultez [accéder aux FileTables avec les API de fichier d’entrée-sortie](../relational-databases/blob/access-filetables-with-file-input-output-apis.md).

### <a name="7-avoid-clearing-workspaces-when-you-execute-r-code-in-a-includessnoversionincludesssnoversion-mdmd-compute-context"></a>7. Éviter l’effacement d’espaces de travail lorsque vous exécutez le code R dans un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contexte de calcul

Si vous utilisez une commande R pour effacer votre espace de travail des objets lors de l’exécution de code R un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contexte de calcul ou si vous désactivez l’espace de travail dans le cadre d’un script R appelée à l’aide de [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), vous pouvez obtenir cette erreur : *espace de travail objet revoScriptConnection introuvable*

`revoScriptConnection` est un objet dans l’espace de travail R qui contient des informations sur une session R appelée à partir de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Toutefois, si votre code R inclut une commande pour effacer l’espace de travail (comme `rm(list=ls()))`) toutes les informations sur la session et les autres objets dans l’espace de travail R sont également effacés.

Pour résoudre ce problème, évitez l’effacement des variables et autres objets en cours d’exécution R [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Bien que l’effacement de l’espace de travail est courant lorsque vous travaillez dans la console R, il peut avoir des conséquences inattendues.

* Pour supprimer des variables spécifiques, utilisez le R `remove` fonction : par exemple, `remove('name1', 'name2', ...)`
* Si plusieurs variables sont à supprimer, enregistrez les noms des variables temporaires dans une liste et effectuez un nettoyage périodique.

### <a name="8-restrictions-on-data-that-can-be-provided-as-input-to-an-r-script"></a>8. Restrictions sur les données qui peuvent être fournies comme entrée à un script R

Dans un script R, vous ne pouvez pas utiliser les types de résultats de requête suivants :

- Données issues d’une requête [!INCLUDE[tsql](../includes/tsql-md.md)] qui référence des colonnes à chiffrement intégral.
  
- Données issues d’une requête [!INCLUDE[tsql](../includes/tsql-md.md)] qui référence des colonnes masquées.
  
     Si vous avez besoin d’utiliser des données masquées dans un script R, une solution de contournement possible consiste à effectuer une copie des données dans une table temporaire et à utiliser ces données à la place.

### <a name="9-use-of-strings-as-factors-can-lead-to-performance-degradation"></a>9. Utiliser des chaînes comme facteurs peuvent entraîner une dégradation des performances

À l’aide de variables de type chaîne comme facteurs peuvent augmenter considérablement la quantité de mémoire utilisée pour les opérations R. Il s’agit en général d’un problème connu avec R, et il existe de nombreux articles sur le sujet. Par exemple, consultez [facteurs ne sont pas des citoyens de première classe dans R, en John Mount, dans R-blogueurs)](https://www.r-bloggers.com/factors-are-not-first-class-citizens-in-r/) ou [stringsasfactors sur : Une biographie non autorisée, par Roger Peng](https://simplystatistics.org/2015/07/24/stringsasfactors-an-unauthorized-biography/). 

Bien que le problème n’est pas spécifique à SQL Server, il peut considérablement affecter les performances du code R exécuté dans SQl Server. Les chaînes sont généralement stockés en tant que varchar ou nvarchar, et si une colonne de données de chaîne a de nombreuses valeurs uniques, le processus de conversion en interne le ces entiers et retour vers les chaînes par R peut même entraîner erreurs d’allocation de mémoire.

Si vous n'avez pas absolument besoin un type de données de chaîne pour d’autres opérations, les valeurs de chaîne de mappage à une valeur numérique (entier) type de données comme partie de la préparation des données peut être avantageux en termes de performances et mise à l’échelle.

Pour une description de ce problème et autres conseils, consultez [performances pour R Services - optimisation des données](r/r-and-data-optimization-r-services.md).

### <a name="10-arguments-varstokeep-and-varstodrop-are-not-supported-for-sql-server-data-sources"></a>10. Arguments *varsToKeep* et *varsToDrop* ne sont pas pris en charge pour les sources de données SQL Server

Lorsque vous utilisez la fonction rxDataStep pour écrire les résultats dans une table, à l’aide du *varsToKeep* et *varsToDrop* est un moyen pratique de spécifier les colonnes à inclure ou exclure dans le cadre de l’opération. Toutefois, ces arguments ne sont pas pris en charge pour les sources de données SQL Server.

### <a name="11-limited-support-for-sql-data-types-in-spexecuteexternalscript"></a>11. Prise en charge pour les types de données SQL dans sp limitée\_exécuter\_externe\_script

Pas tous les types de données qui sont prises en charge dans SQL peuvent être utilisés dans R. Pour résoudre ce problème, envisagez de convertir le type de données non pris en charge un type de données pris en charge avant de transmettre les données à sp\_exécuter\_externe\_script.

Pour plus d’informations, consultez [R bibliothèques et types de données](r/r-libraries-and-data-types.md).

### <a name="12-possible-string-corruption-using-unicode-strings-in-varchar-columns"></a>12. Corruption de chaîne possible à l’aide de chaînes unicode dans des colonnes varchar

En passant les données unicode dans les colonnes varchar de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à R/Python peut provoquer une altération de chaîne. Cela est dû à l’encodage pour ces chaînes unicode dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] classements peut ne pas correspondent avec l’encodage de UTF-8 par défaut utilisé dans R/Python. 

Pour envoyer les données de chaîne non-ASCII à partir de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à R/Python, utilisez l’encodage UTF-8 (disponible dans [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]) ou utiliser le type nvarchar pour le même.

### <a name="13-only-one-value-of-type-raw-can-be-returned-from-spexecuteexternalscript"></a>13. Qu’une seule valeur de type `raw` peut être retourné à partir de `sp_execute_external_script`

Lorsqu’un type de données binaires (R **brutes** type de données) est retournée à partir de R, la valeur doit être envoyée dans la trame de données de sortie.

Avec les données les types autres que **brutes**, vous pouvez retourner des valeurs de paramètre, ainsi que les résultats de la procédure stockée en ajoutant le mot clé OUTPUT. Pour plus d’informations, consultez [paramètres](https://docs.microsoft.com/sql/relational-databases/stored-procedures/parameters).

Si vous souhaitez utiliser plusieurs jeux de sortie qui incluent des valeurs de type **brutes**, une solution de contournement possible consiste à effectuer plusieurs appels de la procédure stockée, ou pour envoyer le résultat redéfinit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l’aide de ODBC.

### <a name="14-loss-of-precision"></a>14. Perte de précision

Étant donné que [!INCLUDE[tsql](../includes/tsql-md.md)] et R prennent en charge différents types de données, les types de données numériques peuvent subir une perte de précision lors de la conversion.

Pour plus d’informations sur la conversion implicite du type de données, consultez [R bibliothèques et types de données](r/r-libraries-and-data-types.md).

### <a name="15-variable-scoping-error-when-you-use-the-transformfunc-parameter"></a>15. Variable d’étendue d’erreur lorsque vous utilisez le paramètre transformfunc est utilisé

Pour transformer des données pendant que vous modélisez, vous pouvez passer un *transformFunc* argument dans une fonction telle que `rxLinmod` ou `rxLogit`. Toutefois, les appels de fonction imbriquée peuvent entraîner d’étendue des erreurs dans le contexte de calcul SQL Server, même si les appels fonctionnent correctement dans le contexte de calcul local.

> *L’exemple de jeu de données pour l’analyse n’a aucune variable*

Par exemple, supposons que vous avez défini deux fonctions, `f` et `g`, dans votre environnement global local, et `g` appels `f`. En appels distribués ou distants impliquant `g`, l’appel à `g` risque d’échouer avec cette erreur, car `f` est introuvable, même si vous avez transmis à la fois `f` et `g` à l’appel distant.

Si vous rencontrez ce problème, vous pouvez le résoudre en incorporant la définition de `f` dans votre définition de `g`, n’importe où avant l’appel habituel de `g` par `f`.

Exemple :

```R
f <- function(x) { 2*x * 3 }
g <- function(y) {
              a <- 10 * y
               f(a)
}
```

Pour éviter cette erreur, réécrivez la définition comme suit :

```R
g <- function(y){
              f <- function(x) { 2*x +3}
              a <- 10 * y
              f(a)
}
```

### <a name="16-data-import-and-manipulation-using-revoscaler"></a>16. Importation et manipulation de données à l’aide de RevoScaleR

Lorsque **varchar** colonnes sont lus à partir d’une base de données, un espace blanc est tronqué. Pour éviter cela, placez les chaînes entre caractères autres qu’un espace.

Lorsque les fonctions comme `rxDataStep` servent à créer des tables de base de données qui ont **varchar** colonnes, la largeur de colonne est estimée en fonction d’un échantillon des données. Si la largeur peut varier, il peut être nécessaire de remplir toutes les chaînes en une longueur commune.

L’utilisation d’une transformation pour modifier le type de données d’une variable n’est pas prise en charge quand des appels répétés à `rxImport` ou `rxTextToXdf` sont effectués pour importer et ajouter des lignes, combinant plusieurs fichiers d’entrée dans un fichier .xdf unique.

### <a name="17-limited-support-for-rxexec"></a>17. Prise en charge limitée pour rxExec

Dans SQL Server 2016, le `rxExec` fonction qui est fournie par le RevoScaleR package peut être utilisé uniquement en mode monothread.

### <a name="18-increase-the-maximum-parameter-size-to-support-rxgetvarinfo"></a>18. Augmenter la taille maximale de paramètre pour prendre en charge rxGetVarInfo

Si vous utilisez des jeux de données avec un grand nombre de variables (par exemple, plus de 40 000), définissez la `max-ppsize` indicateur lorsque vous démarrez R pour utiliser des fonctions telles que `rxGetVarInfo`. L’indicateur `max-ppsize` spécifie la taille maximale de la pile de protection du pointeur.

Si vous utilisez la console R (par exemple, RGui.exe ou RTerm.exe), vous pouvez définir la valeur de _max-ppsize_ sur 500000 en tapant :

```R
R --max-ppsize=500000
```

### <a name="19-issues-with-the-rxdtree-function"></a>19. Problèmes liés à la fonction rxDTree

La fonction `rxDTree` ne prend pas en charge actuellement les transformations dans les formules. En particulier, l’utilisation de la syntaxe `F()` pour créer des facteurs à la volée n’est pas prise en charge. Toutefois, les données numériques sont placées automatiquement.

Les facteurs ordonnés sont traités de la même façon que les facteurs dans toutes les fonctions d’analyse RevoScaleR, sauf `rxDTree`.

### <a name="20-datatable-as-an-outputdataset-in-r"></a>20. Data.table comme un OutputDataSet dans R

À l’aide de `data.table` comme un `OutputDataSet` R n'est pas prise en charge dans SQL Server 2017 Cumulative Update 13 (CU13) et versions antérieures. Le message suivant peut apparaître :

```
Msg 39004, Level 16, State 20, Line 2
A 'R' script error occurred during execution of 
'sp_execute_external_script' with HRESULT 0x80004004.
Msg 39019, Level 16, State 2, Line 2
An external script error occurred: 
Error in alloc.col(newx) : 
  Internal error: length of names (0) is not length of dt (11)
Calls: data.frame ... as.data.frame -> as.data.frame.data.table -> copy -> alloc.col

Error in execution.  Check the output for more information.
Error in eval(expr, envir, enclos) : 
  Error in execution.  Check the output for more information.
Calls: source -> withVisible -> eval -> eval -> .Call
Execution halted
```

`data.table` comme un `OutputDataSet` dans R est pris en charge dans SQL Server 2017 Cumulative Update 14 (CU14) et versions ultérieures.

## <a name="python-script-execution-issues"></a>Problèmes d’exécution du script Python

Cette section contient des problèmes connus qui sont spécifiques à l’exécution de Python sur SQL Server, ainsi que des problèmes liés aux packages Python publiés par Microsoft, y compris [revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) et [microsoftml](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package).

### <a name="1-call-to-pretrained-model-fails-if-path-to-model-is-too-long"></a>1. Appel de modèle préformé échoue si le chemin d’accès au modèle est trop long

Si vous avez installé les modèles préformés dans une version de SQL Server 2017, le chemin d’accès complet au fichier de modèle formé peut être trop long pour Python à lire. Cette limitation est résolue dans une version ultérieure du service.

Il existe plusieurs solutions possibles : 

+ Lorsque vous installez les modèles préformés, choisissez un emplacement personnalisé.
+ Si possible, installez l’instance de SQL Server sous un chemin d’installation personnalisé avec un chemin plus court, tel que C:\SQL\MSSQL14. MSSQLSERVER.
+ Utilisez l’utilitaire Windows [Fsutil](https://technet.microsoft.com/library/cc788097(v=ws.11).aspx) pour créer un lien physique qui mappe le fichier de modèle à un chemin plus court.
+ Mettre à jour vers la dernière version de service.

### <a name="2-error-when-saving-serialized-model-to-sql-server"></a>2. Erreur lors de l’enregistrement a sérialisé le modèle vers SQL Server

Lorsque vous passer d’un modèle à une instance distante de SQL Server et que vous tentez de lire le modèle binaire à l’aide de la `rx_unserialize` fonctionner dans [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package), vous pouvez obtenir l’erreur : 

> *NameError: name 'rx_unserialize_model' is not defined*

Cette erreur est générée si vous avez enregistré le modèle à l’aide d’une version récente de la fonction de sérialisation, mais l’instance de SQL Server où vous désérialisez le modèle ne reconnaît pas la API de sérialisation.

Pour résoudre ce problème, mettez à niveau l’instance de SQL Server 2017 CU3 ou version ultérieure.

### <a name="3-failure-to-initialize-a-varbinary-variable-causes-an-error-in-bxlserver"></a>3. Échec d’initialisation d’une variable varbinary provoque une erreur dans BxlServer

Si vous exécutez le code Python dans SQL Server à l’aide `sp_execute_external_script`et le code possède des variables de type varbinary (max), varchar (max) ou des types semblables de sortie, la variable doit être initialisée ou définie comme faisant partie de votre script. Sinon, le composant d’échange de données, BxlServer, déclenche une erreur et s’arrête de fonctionner.

Cette limitation sera résolue dans une version de service à venir. Pour résoudre ce problème, assurez-vous que la variable est initialisée dans le script Python. N’importe quelle valeur valide peut être utilisé, comme dans les exemples suivants :

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

### <a name="4-telemetry-warning-on-successful-execution-of-python-code"></a>4. Avertissement de télémétrie sur la réussite de l’exécution de code Python

À compter de SQL Server 2017 CU2, le message suivant peut apparaître même si sinon le code Python s’exécute correctement :

> *Message (s) STDERR à partir du script externe :*
>  *~PYTHON_SERVICES\lib\site-packages\revoscalepy\utils\RxTelemetryLogger*
> *SyntaxWarning : telemetry_state est utilisé avant la déclaration globale*

Ce problème a été résolu dans SQL Server 2017 Cumulative Update 3 (CU3). 

### <a name="5-numeric-decimal-and-money-data-types-not-supported"></a>5. Types de données numérique, décimal et de l’argent ne pas pris en charge

À compter de SQL Server 2017 Cumulative Update 12 (CU12), les types de données numérique, décimal et de l’argent avec jeux de résultats sont non pris en charge lors de l’utilisation de Python avec `sp_execute_external_script`. Les messages suivants peuvent apparaître :

> *[Code : 39004, état SQL : S1000] une erreur de script « Python » s’est produite pendant l’exécution de « sp_execute_external_script » avec HRESULT 0 x 80004004.*

> *[Code : 39019, état SQL : S1000] s’est produite lors d’une erreur de script externe :*
> 
> *Erreur de SqlSatelliteCall : Type non pris en charge dans le schéma de sortie. Types pris en charge : de type bit, smallint, int, datetime, smallmoney, réelles et float. char, varchar est partiellement prises en charge.*

Ce problème a été résolu dans SQL Server 2017 Cumulative Update 14 (CU14).

## <a name="revolution-r-enterprise-and-microsoft-r-open"></a>Revolution R Enterprise et Microsoft R Open

Cette section répertorie les problèmes propres à la connectivité, de développement et les outils de performances qui sont fournis par Revolution Analytique R. Ces outils ont été fournis dans les versions préliminaires de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].

En règle générale, nous vous recommandons de désinstaller ces versions précédentes et d’installer la dernière version de SQL Server ou Microsoft R Server.

### <a name="1-revolution-r-enterprise-is-not-supported"></a>1. Revolution R Enterprise n’est pas pris en charge.

Installation de Revolution R Enterprise côte à côte avec n’importe quelle version de [!INCLUDE[rsql_productname_md](../includes/rsql-productname-md.md)] n’est pas pris en charge.

Si vous avez une licence existante for Revolution R Enterprise, vous devez le placer sur un ordinateur distinct à la fois le [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance et toute station de travail que vous souhaitez utiliser pour se connecter à la [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance.

Certaines versions préliminaires de [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)] inclus un environnement de développement R pour Windows qui a été créé par Revolution Analytique. Cet outil n’est plus disponible et il n’est pas pris en charge.

Pour la compatibilité avec [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)], nous vous recommandons d’installer Microsoft R Client à la place. [Outils R pour Visual Studio](https://www.visualstudio.com/vs/rtvs/) et [Visual Studio Code](https://code.visualstudio.com/) prend également en charge les solutions de Microsoft R.

### <a name="2-compatibility-issues-with-sqlite-odbc-driver-and-revoscaler"></a>2. Problèmes de compatibilité avec le pilote ODBC de SQLite et RevoScaleR

Révision 0.92 du pilote ODBC de SQLite est incompatible avec RevoScaleR. Les révisions 0.88 à 0.91, 0.93 et ultérieur sont connues pour être compatibles.

## <a name="see-also"></a>Voir aussi

[Nouveautés de SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md)

[Résolution des problèmes de machine learning dans SQL Server](machine-learning-troubleshooting-faq.md)
