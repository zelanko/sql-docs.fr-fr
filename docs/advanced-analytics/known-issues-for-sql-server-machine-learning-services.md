---
title: Problèmes connus liés au langage R et à l’intégration python
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: be55e779f335277a1c0f03fe871b8dcb952e088f
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470402"
---
# <a name="known-issues-in-machine-learning-services"></a>Problèmes connus dans Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article décrit les problèmes connus ou les limitations avec les composants Machine Learning qui sont fournis en tant qu’option dans [SQL Server 2016 R services](install/sql-r-services-windows-install.md) et [SQL Server 2017 machine learning services avec R et Python](install/sql-machine-learning-services-windows-install.md).

## <a name="setup-and-configuration-issues"></a>Problèmes d’installation et de configuration

Pour obtenir une description des processus et des questions courantes liées à l’installation et à la configuration initiales, consultez [FAQ sur la mise à niveau et l’installation](r/upgrade-and-installation-faq-sql-server-r-services.md). Il contient des informations sur les mises à niveau, l’installation côte à côte et l’installation de nouveaux composants R ou python.

### <a name="1-inconsistent-results-in-mkl-computations-due-to-missing-environment-variable"></a>1. Résultats incohérents dans les calculs MKL en raison d’une variable d’environnement manquante

**S’applique à :** Fichiers binaires R_SERVER 9,0, 9,1, 9,2 ou 9,3.

R_SERVER utilise Intel Math Kernel Library (MKL). Pour les calculs impliquant des MKL, des résultats incohérents peuvent se produire si une variable d’environnement est manquante dans votre système. 

Définissez la variable `'MKL_CBWR'=AUTO` d’environnement pour garantir la reproductibilité numérique conditionnelle dans R_SERVER. Pour plus d’informations, consultez [Présentation de la reproductibilité numérique conditionnelle (CNR)](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr).

**Solution de contournement**

1. Dans le panneau de configuration, cliquez sur système **et sécurité** >  > **paramètres** > système avancés**variables d’environnement**.

2. Créez un utilisateur ou une variable système. 

  + Définissez le nom de la variable sur «MKL_CBWR».
  + Affectez à’variable value’la valeur’AUTO'.

3. Redémarrez R_SERVER. Sur SQL Server, vous pouvez redémarrer SQL Server Launchpad service.

> [!NOTE]
> Si vous exécutez la version préliminaire SQL Server 2019 sur Linux, modifiez ou créez *. bash_profile* dans le répertoire de racine de votre utilisateur, `export MKL_CBWR="AUTO"`en ajoutant la ligne. Exécutez ce fichier en tapant `source .bash_profile` à l’invite de commandes bash. Redémarrez R_SERVER `Sys.getenv()` en tapant à l’invite de commandes R.

### <a name="2-r-script-runtime-error-sql-server-2017-cu5-cu7-regression"></a>2. Erreur d’exécution de script R (SQL Server 2017 CU5-CU7 Regression)

Pour SQL Server 2017, dans les mises à jour cumulatives 5 à 7, il existe une régression dans le fichier **rlauncher. config** , où le chemin d’accès du fichier du répertoire temporaire inclut un espace. Cette régression a été corrigée dans CU8.

L’erreur qui s’affiche lorsque vous exécutez le script R comprend les messages suivants:

> *Impossible de communiquer avec le runtime pour le script «R». Vérifiez la configuration requise du runtime «R».*
>
> Message (s) STDERR à partir du script externe: 
>
> *Erreur irrécupérable: impossible de créer’R_TempDir'*

**Solution de contournement**

Appliquez CU8 lorsqu’il devient disponible. Vous pouvez également recréer **rlauncher. config** en exécutant **registerrext** avec Uninstall/install dans une invite de commandes avec élévation de privilèges. 

```cmd
<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExt.exe /uninstall /sqlbinnpath:<SQLInstanceBinnPath> /userpoolsize:0 /instance:<SQLInstanceName>

<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExt.exe /install /sqlbinnpath:<SQLInstanceBinnPath> /userpoolsize:0 /instance:<SQLInstanceName>
```

L’exemple suivant montre les commandes avec l’instance par défaut «MSSQL14. MSSQLSERVER «installé dans le répertoire C:\Program Files\Microsoft\"SQL Server:

```cmd
"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRext.exe" /uninstall /sqlbinnpath:"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\Binn" /userpoolsize:0 /instance:MSSQLSERVER

"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRext.exe" /install /sqlbinnpath:"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\Binn" /userpoolsize:0 /instance:MSSQLSERVER
```

### <a name="3-unable-to-install-sql-server-machine-learning-features-on-a-domain-controller"></a>3. Impossible d’installer les fonctionnalités de Machine Learning de SQL Server sur un contrôleur de domaine

Si vous essayez d’installer SQL Server 2016 R services ou SQL Server 2017 Machine Learning Services sur un contrôleur de domaine, le programme d’installation échoue, avec les erreurs suivantes:

> *Une erreur s’est produite lors du processus d’installation de la fonctionnalité*
> 
> *Impossible de trouver le groupe avec l’identité*
> 
> *Code d’erreur du composant: 0x80131509*

L’échec se produit parce que, sur un contrôleur de domaine, le service ne peut pas créer les 20 comptes locaux requis pour exécuter Machine Learning. En général, nous vous déconseillons d’installer SQL Server sur un contrôleur de domaine. Pour plus d’informations, consultez le [Bulletin de Support 2032911](https://support.microsoft.com/help/2032911/you-may-encounter-problems-when-installing-sql-server-on-a-domain-cont).

### <a name="4-install-the-latest-service-release-to-ensure-compatibility-with-microsoft-r-client"></a>4. Installez la dernière version de service pour garantir la compatibilité avec Microsoft R Client

Si vous installez la dernière version de Microsoft R Client et que vous l’utilisez pour exécuter R sur SQL Server dans un contexte de calcul distant, vous pouvez obtenir une erreur semblable à la suivante:

> *Vous exécutez la version 9. x. x de Microsoft R Client sur votre ordinateur, ce qui est incompatible avec Microsoft R Server version 8. x.x. Téléchargez et installez une version compatible.*

SQL Server 2016 requiert que les bibliothèques R sur le client correspondent exactement aux bibliothèques R sur le serveur. La restriction a été supprimée pour les versions ultérieures à R Server version9.0.1. Toutefois, si vous rencontrez cette erreur, vérifiez la version des bibliothèques R utilisée par votre client et le serveur et, si nécessaire, mettez à jour le client pour qu’il corresponde à la version du serveur.

La version de R installée avec SQL Server R Services est mise à jour chaque fois qu’une version de SQL Server Service est installée. Pour vous assurer que vous disposez toujours des versions les plus récentes des composants R, veillez à installer tous les service packs.

Pour garantir la compatibilité avec Microsoft R Client 9.0.0, installez les mises à jour décrites dans cet [article de support](https://support.microsoft.com/kb/3210262).

Pour éviter les problèmes liés aux packages R, vous pouvez également mettre à niveau la version des bibliothèques R installées sur le serveur, en modifiant votre contrat de maintenance afin d’utiliser la stratégie de support du cycle de vie moderne, comme décrit dans [la section suivante](#bkmk_sqlbindr). Dans ce cas, la version de R installée avec SQL Server est mise à jour selon la même planification que celle utilisée pour les mises à jour de machine learning Server (anciennement Microsoft R Server).

**S’applique à :** SQL Server 2016 R services, avec R Server version 9.0.0 ou antérieure

### <a name="5-r-components-missing-from-cu3-setup"></a>5. Composants R absents du programme d’installation de CU3

Un nombre limité de machines virtuelles Azure a été configuré sans les fichiers d’installation de R qui doivent être inclus avec SQL Server. Le problème s’applique aux machines virtuelles approvisionnées au cours de la période allant de 2018-01-05 à 2018-01-23. Ce problème peut également affecter les installations locales, si vous avez appliqué la mise à jour CU3 pour SQL Server 2017 au cours de la période de 2018-01-05 à 2018-01-23.

Une version de service qui inclut la version correcte des fichiers d’installation R a été fournie.

+ [Package de mise à jour cumulative 3 pour SQL Server 2017 KB4052987](https://www.microsoft.com/download/details.aspx?id=56128).

Pour installer les composants et réparer SQL Server 2017 CU3, vous devez désinstaller CU3 et réinstaller la version mise à jour:

1. Téléchargez le fichier d’installation CU3 mis à jour, qui comprend les programmes d’installation R.
2. Désinstallez CU3. Dans le panneau de configuration, recherchez **désinstaller une mise à jour**, puis sélectionnez «correctif 3015 pour SQL Server 2017 (KB4052987) (64 bits)». Effectuez les étapes de désinstallation.
3. Réinstallez la mise à jour CU3 en double-cliquant sur la mise à jour de KB4052987 que `SQLServer2017-KB4052987-x64.exe`vous venez de télécharger:. Suivez les instructions d'installation.

### <a name="6-unable-to-install-python-components-in-offline-installations-of-sql-server-2017-ctp-20-or-later"></a>6. Impossible d’installer les composants python dans les installations hors connexion de SQL Server 2017 CTP 2,0 ou version ultérieure

Si vous installez une version précommerciale de SQL Server 2017 sur un ordinateur sans accès à Internet, le programme d’installation peut ne pas afficher la page qui invite à entrer l’emplacement des composants python téléchargés. Dans ce type d’instance, vous pouvez installer la fonctionnalité Machine Learning Services, mais pas les composants Python.

Ce problème est résolu dans la version Release. En outre, cette limitation ne s’applique pas aux composants R.

**S’applique à :** SQL Server 2017 avec Python

### <a name="bkmk_sqlbindr"></a>Avertissement de version incompatible quand vous vous connectez à une version antérieure de SQL Server R Services à partir d’un client à l’aide de[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]

Quand vous exécutez du code R dans un contexte de calcul SQL Server 2016, vous pouvez voir l’erreur suivante:

> *Vous exécutez la version 9.0.0 de Microsoft R Client sur votre ordinateur, ce qui est incompatible avec la version 8.0.3 de Microsoft R Server. Téléchargez et installez une version compatible.*

Ce message s’affiche si l’une des deux instructions suivantes est vraie,

+ Vous avez installé R Server (autonome) sur un ordinateur client à l’aide de l' [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]Assistant Installation de.
+ Vous avez installé Microsoft R Server à l’aide du [programme d’installation Windows distinct](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

Pour vous assurer que le serveur et le client utilisent la même version, vous devrez peut-être utiliser la _liaison_, pris en charge pour Microsoft R Server 9,0 et versions ultérieures, pour mettre à niveau les composants R dans SQL Server instances 2016. Pour déterminer si la prise en charge des mises à niveau est disponible pour votre version de R services, consultez [mettre à niveau une instance de r services à l’aide de SqlBindR. exe](install/upgrade-r-and-python.md).

**S’applique à :** SQL Server 2016 R services, avec R Server version 9.0.0 ou antérieure

### <a name="7-setup-for-sql-server-2016-service-releases-might-fail-to-install-newer-versions-of-r-components"></a>7. La configuration des versions de services de SQL Server 2016 peut échouer à installer de nouvelles versions des composants R

Lorsque vous installez une mise à jour cumulative ou installez un Service Pack pour SQL Server 2016 sur un ordinateur qui n’est pas connecté à Internet, l’Assistant installation peut ne pas afficher l’invite qui vous permet de mettre à jour les composants R à l’aide des fichiers CAB téléchargés. Cet échec se produit généralement lorsque plusieurs composants ont été installés avec le moteur de base de données.

Pour résoudre ce problème, vous pouvez installer la version du service à l’aide de la ligne `MRCACHEDIRECTORY` de commande et en spécifiant l’argument comme indiqué dans cet exemple, qui installe les mises à jour CU1:

`C:\<path to installation media>\SQLServer2016-KB3164674-x64.exe /Action=Patch /IACCEPTROPENLICENSETERMS /MRCACHEDIRECTORY=<path to CU1 CAB files>`

Pour obtenir les derniers programmes d’installation, consultez [installer des composants machine learning sans accès à Internet](install/sql-ml-component-install-without-internet-access.md).

**S’applique à :** SQL Server 2016 R services, avec R Server version 9.0.0 ou antérieure

### <a name="8-launchpad-services-fails-to-start-if-the-version-is-different-from-the-r-version"></a>8. Les services Launchpad ne parvient pas à démarrer si la version est différente de la version R

Si vous installez SQL Server R Services séparément du moteur de base de données, et que les versions de build sont différentes, vous pouvez voir l’erreur suivante dans le journal des événements système:

> *Le service SQL Server Launchpad n’a pas pu démarrer en raison de l’erreur suivante: Le service n’a pas répondu à temps à la demande de démarrage ou de contrôle.*

Par exemple, cette erreur peut se produire si vous installez le moteur de base de données à l’aide de la version Release, appliquez un correctif pour mettre à niveau le moteur de base de données, puis ajoutez la fonctionnalité R services à l’aide de la version Release.

Pour éviter ce problème, utilisez un utilitaire tel que le gestionnaire de fichiers pour comparer les versions de launchpad. exe à la version des fichiers binaires SQL, par exemple sqldk. dll. Tous les composants doivent avoir le même numéro de version. Si vous mettez à niveau un composant, veillez à appliquer la même mise à niveau à tous les autres composants installés.

Recherchez Launchpad dans le `Binn` dossier de l’instance. Par exemple, dans une installation par défaut de SQL Server 2016, le chemin d' `C:\Program Files\Microsoft SQL Server\MSSQL.13.InstanceNameMSSQL\Binn`accès peut être. 

### <a name="9-remote-compute-contexts-are-blocked-by-a-firewall-in-sql-server-instances-that-are-running-on-azure-virtual-machines"></a>9. Les contextes de calcul distants sont bloqués par un pare-feu dans SQL Server instances qui s’exécutent sur des machines virtuelles Azure

Si vous avez installé [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] sur une machine virtuelle Windows Azure, vous risquez de ne pas pouvoir utiliser les contextes de calcul qui requièrent l’utilisation de l’espace de travail de la machine virtuelle. Cela est dû au fait que, par défaut, le pare-feu sur les machines virtuelles Azure comprend une règle qui bloque l’accès réseau pour les comptes d’utilisateur R locaux.

Pour résoudre ce problème, sur la machine virtuelle Azure, ouvrez **pare-feu Windows avec fonctions avancées de sécurité**, sélectionnez **règles de trafic sortant**et désactivez la règle suivante: **Bloque l’accès réseau pour les comptes d’utilisateurs locaux R dans SQL Server instance MSSQLSERVER**. Vous pouvez également laisser la règle activée, mais changer la propriété de sécurité pour **autoriser si**elle est sécurisée.

### <a name="10-implied-authentication-in-sqlexpress"></a>10. Authentification implicite dans SQLEXPRESS

Quand vous exécutez des tâches R à partir d’une station de travail de science des données distante à l’aide de l’authentification Windows intégrée, SQL Server utilise *l’authentification implicite* pour générer des appels ODBC locaux qui peuvent être requis par le script. Toutefois, cette fonctionnalité ne marchait pas dans la version RTM de SQL Server Express Edition.

Pour résoudre ce problème, nous vous recommandons d’effectuer la mise à niveau vers une version ultérieure du service.

Si la mise à niveau n’est pas possible, utilisez une connexion SQL pour exécuter les travaux R distants qui peuvent nécessiter des appels ODBC incorporés.

**S’applique à :** SQL Server 2016 R services Express Edition

### <a name="11-performance-limits-when-libraries-used-by-sql-server-are-called-from-other-tools"></a>11. Limites de performances lorsque des bibliothèques utilisées par SQL Server sont appelées à partir d’autres outils

Il est possible d’appeler les bibliothèques Machine Learning qui sont installées pour SQL Server à partir d’une application externe, telle que RGui. Cela peut être le moyen le plus pratique pour accomplir certaines tâches, telles que l’installation de nouveaux packages ou l’exécution de tests ad hoc sur des exemples de code très courts. Toutefois, en dehors de SQL Server, les performances peuvent être limitées. 

Par exemple, même si vous utilisez l’édition Enterprise de SQL Server, R s’exécute en mode mono-thread lorsque vous exécutez votre code R à l’aide d’outils externes. Pour obtenir les avantages des performances dans SQL Server, lancez une connexion SQL Server et utilisez [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) pour appeler le runtime de script externe.

En général, évitez d’appeler les bibliothèques Machine Learning utilisées par SQL Server à partir des outils externes. Si vous avez besoin de déboguer du code R ou python, il est généralement plus facile de le faire en dehors de SQL Server. Pour récupérer les mêmes bibliothèques que celles figurant dans SQL Server, vous pouvez installer Microsoft R Client, [SQL Server 2017 machine learning Server (autonome)](install/sql-machine-learning-standalone-windows-install.md)ou [SQL Server 2016 R Server (autonome)](install/sql-r-standalone-windows-install.md).

### <a name="12-sql-server-data-tools-does-not-support-permissions-required-by-external-scripts"></a>12. SQL Server Data Tools ne prend pas en charge les autorisations requises par les scripts externes

Quand vous utilisez Visual Studio ou SQL Server Data Tools pour publier un projet de base de données, si un principal a des autorisations spécifiques à l’exécution de scripts externes, vous pouvez obtenir une erreur semblable à celle-ci:

> *Modèle TSQL: Erreur détectée lors de l’ingénierie à rebours de la base de données. L’autorisation n’a pas été reconnue et n’a pas été importée.*

Actuellement, le modèle DACPAC ne prend pas en charge les autorisations utilisées par R services ou Machine Learning Services, telles que l’octroi d’un SCRIPT externe ou l’exécution d’un SCRIPT externe. Ce problème sera résolu dans une version ultérieure.

Pour contourner ce problème, exécutez les instructions GRANT supplémentaires dans un script de prédéploiement.

### <a name="13-external-script-execution-is-throttled-due-to-resource-governance-default-values"></a>13. L’exécution du script externe est limitée en raison des valeurs par défaut de la gouvernance des ressources

Dans Enterprise Edition, vous pouvez utiliser des pools de ressources pour gérer les processus de script externe. Dans certaines builds de version précoce, la mémoire maximale pouvant être allouée aux processus R était de 20%. Par conséquent, si le serveur dispose de 32 Go de RAM, les exécutables R (RTerm. exe et BxlServer. exe) pouvaient utiliser un maximum de 6,4 Go dans une même requête.

Si vous rencontrez des limitations de ressources, vérifiez la valeur par défaut actuelle. Si 20 pour cent n’est pas suffisant, consultez la [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] documentation pour savoir comment modifier cette valeur.

**S’applique à :** SQL Server 2016 R services, édition entreprise

## <a name="r-script-execution-issues"></a>Problèmes d’exécution de script R

Cette section contient des problèmes connus spécifiques à l’exécution de R sur SQL Server, ainsi que certains problèmes liés aux bibliothèques et aux outils R publiés par Microsoft, y compris RevoScaleR.

Pour obtenir d’autres problèmes connus susceptibles d’affecter les solutions R, consultez le site [machine learning Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues) .

### <a name="1-access-denied-warning-when-executing-r-scripts-on-sql-server-in-a-non-default-location"></a>1. Avertissement d’accès refusé lors de l’exécution de scripts R sur SQL Server dans un emplacement autre que celui par défaut

Si l’instance de SQL Server a été installée à un emplacement autre que celui par défaut, par exemple `Program Files` en dehors du dossier, l’avertissement ACCESS_DENIED est déclenché lorsque vous essayez d’exécuter des scripts qui installent un package. Exemple :

> *Dans `normalizePath(path.expand(path), winslash, mustWork)` : chemin d’accès [2] = "~ ExternalLibraries/R/8/1": Accès refusé*

En effet, une fonction R tente de lire le chemin d’accès et échoue si le groupe d’utilisateurs intégré **SQLRUserGroup**ne dispose pas d’un accès en lecture. L’avertissement déclenché ne bloque pas l’exécution du script R actuel, mais l’avertissement peut se répéter à plusieurs reprises chaque fois que l’utilisateur exécute un autre script R.

Si vous avez installé SQL Server à l’emplacement par défaut, cette erreur ne se produit pas, car tous les utilisateurs Windows ont des `Program Files` autorisations de lecture sur le dossier.

Ce problème a été résolu dans une prochaine version de service. Pour contourner ce problème, fournissez le groupe, **SQLRUserGroup**, avec un accès en lecture `ExternalLibraries`pour tous les dossiers parents de.

### <a name="2-serialization-error-between-old-and-new-versions-of-revoscaler"></a>2. Erreur de sérialisation entre les anciennes et les nouvelles versions de RevoScaleR

Lorsque vous transmettez un modèle à l’aide d’un format sérialisé à une instance de SQL Server distante, vous pouvez obtenir l’erreur suivante: 

> *Erreur dans memDecompress (données, type = Decompress) erreur interne-3 dans memDecompress (2).*

Cette erreur est générée si vous avez enregistré le modèle à l’aide d’une version récente de la fonction de sérialisation, [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel), mais que l’instance de SQL Server dans laquelle vous désérialisez le modèle a une version antérieure des API RevoScaleR, à partir de SQL Server 2017 Cu2 ou version antérieure.

Pour résoudre ce problème, vous pouvez mettre à niveau l’instance SQL Server 2017 vers CU3 ou une version ultérieure.

L’erreur ne s’affiche pas si la version de l’API est la même, ou si vous déplacez un modèle enregistré avec une fonction de sérialisation plus ancienne vers un serveur qui utilise une version plus récente de l’API de sérialisation.

En d’autres termes, utilisez la même version de RevoScaleR pour les opérations de sérialisation et de désérialisation.

### <a name="3-real-time-scoring-does-not-correctly-handle-the-learningrate-parameter-in-tree-and-forest-models"></a>3. La notation en temps réel ne gère pas correctement le paramètre _learningRate_ dans les modèles d’arborescence et de forêt

Si vous créez un modèle à l’aide d’une méthode de l’arbre de décision ou de la forêt de décision et spécifiez le taux `sp_rxpredict` d’apprentissage, `PREDICT` vous pouvez constater des résultats incohérents lors de l’utilisation de ou de la fonction SQL, par rapport à l’utilisation `rxPredict`de.

La cause est une erreur dans l’API qui traite les modèles sérialisés, et est limitée au `learningRate` paramètre: par exemple, dans [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees), ou

Ce problème est résolu dans une prochaine version de service.

### <a name="4-limitations-on-processor-affinity-for-r-jobs"></a>4. Limitations sur l’affinité du processeur pour les tâches R

Dans la version initiale de SQL Server 2016, vous pouviez définir l’affinité du processeur uniquement pour les processeurs dans le premier groupe k. Par exemple, si le serveur est un ordinateur à 2 sockets avec deux k-Groups, seuls les processeurs du premier k-Group sont utilisés pour les processus R. La même restriction s’applique lorsque vous configurez la gouvernance des ressources pour les tâches de script R.

Ce problème est résolu dans le Service Pack 1 de SQL Server 2016. Nous vous recommandons d’effectuer la mise à niveau vers la dernière version du service.

**S’applique à :** Version RTM de SQL Server 2016 R services

### <a name="5-changes-to-column-types-cannot-be-performed-when-reading-data-in-a-sql-server-compute-context"></a>5. Les modifications des types de colonne ne peuvent pas être effectuées lors de la lecture de données dans un contexte de calcul SQL Server

Si votre contexte de calcul est défini sur l’instance SQL Server, vous ne pouvez pas utiliser l’argument _colClasses_ (ou d’autres arguments similaires) pour modifier le type de données des colonnes dans votre code R.

Par exemple, l’instruction suivante génère une erreur si la colonne CRSDepTimeStr n’est pas déjà un entier :

```R
data <- RxSqlServerData(
  sqlQuery = "SELECT CRSDepTimeStr, ArrDelay  FROM AirlineDemoSmall", 
  connectionString = connectionString, 
  colClasses = c(CRSDepTimeStr = "integer"))
```

En guise de solution de contournement, vous pouvez réécrire la requête SQL pour utiliser CAST ou CONVERT et présenter les données à R en utilisant le type de données correct. En général, les performances sont meilleures quand vous travaillez avec des données à l’aide de SQL plutôt que de modifier des données dans le code R.

**S’applique à :** SQL Server 2016 R services

### <a name="6-limits-on-size-of-serialized-models"></a>6. Limites de la taille des modèles sérialisés

Lorsque vous enregistrez un modèle dans une table SQL Server, vous devez sérialiser le modèle et l’enregistrer dans un format binaire. Théoriquement, la taille maximale d’un modèle qui peut être stocké avec cette méthode est de 2 Go, qui est la taille maximale des colonnes varbinary dans SQL Server.

Si vous devez utiliser des modèles plus grands, les solutions de contournement suivantes sont disponibles:

+ Prenez les mesures nécessaires pour réduire la taille de votre modèle. Certains packages R Open source incluent une grande quantité d’informations dans l’objet de modèle, et la plupart de ces informations peuvent être supprimées pour le déploiement. 
+ Utilisez la sélection des fonctionnalités pour supprimer les colonnes inutiles.
+ Si vous utilisez un algorithme Open source, envisagez une implémentation similaire à l’aide de l’algorithme correspondant dans MicrosoftML ou RevoScaleR. Ces packages ont été optimisés pour les scénarios de déploiement.
+ Une fois le modèle rationalisé et la taille réduite à l’aide des étapes précédentes, consultez si la fonction [memCompress](https://www.rdocumentation.org/packages/base/versions/3.4.1/topics/memCompress) dans la base R peut être utilisée pour réduire la taille du modèle avant de le passer à SQL Server. Cette option est recommandée lorsque le modèle est proche de la limite de 2 Go.
+ Pour les modèles plus volumineux, vous pouvez utiliser [la fonctionnalité SQL Server](../relational-databases/blob/filetables-sql-server.md) filetable pour stocker les modèles, plutôt que d’utiliser une colonne varbinary.

    Pour utiliser FileTables, vous devez ajouter une exception de pare-feu, car les données stockées dans FileTables sont gérées par le pilote du système de fichiers FILESTREAM dans SQL Server, et les règles de pare-feu par défaut bloquent l’accès au fichier réseau. Pour plus d’informations, consultez [activer les conditions préalables pour les](../relational-databases/blob/enable-the-prerequisites-for-filetable.md)filetables.

    Une fois que vous avez activé filetable, pour écrire le modèle, vous pouvez obtenir un chemin d’accès à partir de SQL à l’aide de l’API filetable, puis écrire le modèle à cet emplacement à partir de votre code. Lorsque vous avez besoin de lire le modèle, vous pouvez obtenir le chemin d’accès à partir de SQL, puis appeler le modèle à l’aide du chemin d’accès à partir de votre script. Pour plus d’informations, consultez [accéder à FileTables avec des API d’entrée-sortie de fichier](../relational-databases/blob/access-filetables-with-file-input-output-apis.md).

### <a name="7-avoid-clearing-workspaces-when-you-execute-r-code-in-a-includessnoversionincludesssnoversion-mdmd-compute-context"></a>7. Éviter l’effacement des espaces de travail lorsque vous exécutez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] du code R dans un contexte de calcul

Si vous utilisez une commande r pour effacer votre espace de travail d’objets tout en exécutant du [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] code r dans un contexte de calcul, ou si vous effacez l’espace de travail dans le cadre d’un script r appelé à l’aide de [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), vous pouvez obtenir cette erreur: *espace de travail revoScriptConnection* de l’objet introuvable

`revoScriptConnection` est un objet dans l’espace de travail R qui contient des informations sur une session R appelée à partir de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Toutefois, si votre code R inclut une commande pour effacer l’espace de travail (comme `rm(list=ls()))`) toutes les informations sur la session et les autres objets dans l’espace de travail R sont également effacés.

Pour contourner ce problème, évitez de supprimer toute discrimination des variables et d’autres objets pendant que vous [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]exécutez R dans. Bien que l’effacement de l’espace de travail soit courant lorsque vous travaillez dans la console R, cela peut avoir des conséquences inattendues.

* Pour supprimer des variables spécifiques, utilisez la `remove` fonction R: par exemple,`remove('name1', 'name2', ...)`
* Si plusieurs variables sont à supprimer, enregistrez les noms des variables temporaires dans une liste et effectuez un nettoyage périodique.

### <a name="8-restrictions-on-data-that-can-be-provided-as-input-to-an-r-script"></a>8. Restrictions sur les données qui peuvent être fournies comme entrée à un script R

Dans un script R, vous ne pouvez pas utiliser les types de résultats de requête suivants :

- Données issues d’une requête [!INCLUDE[tsql](../includes/tsql-md.md)] qui référence des colonnes à chiffrement intégral.
  
- Données issues d’une requête [!INCLUDE[tsql](../includes/tsql-md.md)] qui référence des colonnes masquées.
  
     Si vous avez besoin d’utiliser des données masquées dans un script R, une solution de contournement possible consiste à effectuer une copie des données dans une table temporaire et à utiliser ces données à la place.

### <a name="9-use-of-strings-as-factors-can-lead-to-performance-degradation"></a>9. L’utilisation de chaînes en tant que facteurs peut entraîner une dégradation des performances

L’utilisation de variables de type chaîne comme facteurs peut augmenter de façon considérable la quantité de mémoire utilisée pour les opérations R. Il s’agit d’un problème connu avec R en général et il existe de nombreux articles sur le sujet. Par exemple, consultez les [facteurs ne sont pas des citoyens de première classe dans r, par John Mount, dans r-bloggers)](https://www.r-bloggers.com/factors-are-not-first-class-citizens-in-r/) ou [stringsAsFactors: Biographie non autorisée, par Roger Peng](https://simplystatistics.org/2015/07/24/stringsasfactors-an-unauthorized-biography/). 

Même si le problème n’est pas spécifique à SQL Server, il peut affecter les performances de l’exécution du code R dans SQl Server. Les chaînes sont généralement stockées sous la forme varchar ou nvarchar, et si une colonne de données de type chaîne a de nombreuses valeurs uniques, le processus de conversion interne de ces nombres en entiers et de retour en chaînes par R peut même entraîner des erreurs d’allocation de mémoire.

Si vous n’avez pas absolument besoin d’un type de données String pour d’autres opérations, le mappage des valeurs de chaîne à un type de données numérique (entier) dans le cadre de la préparation des données serait bénéfique du point de vue des performances et de la mise à l’échelle.

Pour plus d’informations sur ce problème et d’autres conseils, consultez [performances pour R services-optimisation des données](r/r-and-data-optimization-r-services.md).

### <a name="10-arguments-varstokeep-and-varstodrop-are-not-supported-for-sql-server-data-sources"></a>10. Les arguments *varsToKeep* et *varsToDrop* ne sont pas pris en charge pour les sources de données SQL Server

Lorsque vous utilisez la fonction rxDataStep pour écrire des résultats dans une table, l’utilisation de *varsToKeep* et de *varsToDrop* est un moyen pratique de spécifier les colonnes à inclure ou exclure dans le cadre de l’opération. Toutefois, ces arguments ne sont pas pris en charge pour les sources de données SQL Server.

### <a name="11-limited-support-for-sql-data-types-in-spexecuteexternalscript"></a>11. Prise en charge limitée des types de données\_SQL\_dans\_le script externe d’exécution SP

Tous les types de données pris en charge dans SQL ne peuvent pas être utilisés dans R. Pour contourner ce problème, envisagez d’effectuer un cast du type de données non pris en charge vers un\_type de\_données pris en charge avant de transmettre les données à un script externe d’exécution\_SP.

Pour plus d’informations, consultez [bibliothèques et types de données R](r/r-libraries-and-data-types.md).

### <a name="12-possible-string-corruption-using-unicode-strings-in-varchar-columns"></a>12. Endommagement possible des chaînes à l’aide de chaînes Unicode dans les colonnes varchar

Le passage de données Unicode dans des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] colonnes varchar de à R/python peut entraîner une altération de la chaîne. Cela est dû au fait que l’encodage de ces [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] chaînes Unicode dans les classements peut ne pas correspondre à l’encodage UTF-8 par défaut utilisé dans R/Python. 

Pour envoyer des données de chaîne non-ASCII [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] de à R/Python, utilisez l’encodage UTF-8 [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)](disponible dans) ou utilisez le type nvarchar pour le même.

### <a name="13-only-one-value-of-type-raw-can-be-returned-from-spexecuteexternalscript"></a>13. Une seule valeur de type `raw` peut être retournée à partir de`sp_execute_external_script`

Lorsqu’un type de données binaire (type  de données brutes r) est retourné à partir de r, la valeur doit être envoyée dans la trame de données de sortie.

Avec des types de données autres que **RAW**, vous pouvez retourner des valeurs de paramètre ainsi que les résultats de la procédure stockée en ajoutant le mot clé OUTPUT. Pour plus d’informations, consultez [paramètres](https://docs.microsoft.com/sql/relational-databases/stored-procedures/parameters).

Si vous souhaitez utiliser plusieurs jeux de sorties qui incluent des valeurs de type **RAW**, une solution de contournement possible consiste à effectuer plusieurs appels de la procédure stockée ou à renvoyer les jeux [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] de résultats vers à l’aide d’ODBC.

### <a name="14-loss-of-precision"></a>14. Perte de précision

Étant [!INCLUDE[tsql](../includes/tsql-md.md)] donné que et R prennent en charge différents types de données, les types de données numériques peuvent subir une perte de précision pendant la conversion.

Pour plus d’informations sur la conversion implicite de type de données, consultez [bibliothèques et types de données R](r/r-libraries-and-data-types.md).

### <a name="15-variable-scoping-error-when-you-use-the-transformfunc-parameter"></a>15. Erreur d’étendue de variable quand vous utilisez le paramètre Transformfunc est utilisé

Pour transformer des données pendant la modélisation, vous pouvez passer un argument *transformfunc est utilisé* dans une fonction telle que `rxLinmod` ou `rxLogit`. Toutefois, les appels de fonction imbriqués peuvent entraîner des erreurs de portée dans le contexte de calcul SQL Server, même si les appels fonctionnent correctement dans le contexte de calcul local.

> *L’exemple de jeu de données pour l’analyse n’a pas de variables*

Par exemple, supposons que vous avez défini deux fonctions `f` , `g`et, dans votre environnement global local, `g` et `f`que appelle. Dans les appels distribués `g`ou distants impliquant, l’appel à `g` peut échouer avec `f` cette erreur, car est introuvable, même `f` si `g` vous avez transmis à la fois et à l’appel distant.

Si vous rencontrez ce problème, vous pouvez le résoudre en incorporant la définition de `f` dans votre définition de `g`, n’importe où avant l’appel habituel de `g` par `f`.

Exemple :

```R
f <- function(x) { 2*x * 3 }
g <- function(y) {
              a <- 10 * y
               f(a)
}
```

Pour éviter cette erreur, réécrivez la définition comme suit:

```R
g <- function(y){
              f <- function(x) { 2*x +3}
              a <- 10 * y
              f(a)
}
```

### <a name="16-data-import-and-manipulation-using-revoscaler"></a>16. Importation et manipulation de données à l’aide de RevoScaleR

Lorsque les colonnes **varchar** sont lues à partir d’une base de données, l’espace blanc est tronqué. Pour éviter cela, placez les chaînes entre caractères autres qu’un espace.

Lorsque des fonctions telles `rxDataStep` que sont utilisées pour créer des tables de base de données qui ont des colonnes **varchar** , la largeur de colonne est estimée en fonction d’un échantillon des données. Si la largeur peut varier, il peut être nécessaire de remplir toutes les chaînes à une longueur commune.

L’utilisation d’une transformation pour modifier le type de données d’une variable n’est pas prise en charge quand des appels répétés à `rxImport` ou `rxTextToXdf` sont effectués pour importer et ajouter des lignes, combinant plusieurs fichiers d’entrée dans un fichier .xdf unique.

### <a name="17-limited-support-for-rxexec"></a>17. Prise en charge limitée de rxExec

Dans SQL Server 2016, la `rxExec` fonction fournie par le package RevoScaleR peut être utilisée uniquement en mode mono-thread.

### <a name="18-increase-the-maximum-parameter-size-to-support-rxgetvarinfo"></a>18. Augmenter la taille de paramètre maximale pour prendre en charge rxGetVarInfo

Si vous utilisez des jeux de données avec un très grand nombre de variables (par exemple, plus de 40 000 `max-ppsize` ), définissez l’indicateur lorsque vous démarrez R pour `rxGetVarInfo`utiliser des fonctions telles que. L’indicateur `max-ppsize` spécifie la taille maximale de la pile de protection du pointeur.

Si vous utilisez la console R (par exemple, RGui. exe ou RTerm. exe), vous pouvez définir la valeur de _Max-ppsize_ sur 500000 en tapant ce qui suit:

```R
R --max-ppsize=500000
```

### <a name="19-issues-with-the-rxdtree-function"></a>19. Problèmes avec la fonction rxDTree

La fonction `rxDTree` ne prend pas en charge actuellement les transformations dans les formules. En particulier, l’utilisation de la syntaxe `F()` pour créer des facteurs à la volée n’est pas prise en charge. Toutefois, les données numériques sont automatiquement Binned (.

Les facteurs ordonnés sont traités de la même façon que les facteurs dans toutes les fonctions d’analyse RevoScaleR, sauf `rxDTree`.

### <a name="20-datatable-as-an-outputdataset-in-r"></a>20. Data. table en tant que OutputDataSet dans R

L' `data.table` utilisation de `OutputDataSet` en tant que dans R n’est pas prise en charge dans SQL Server 2017 mise à jour cumulative 13 (CU13) et versions antérieures. Le message suivant peut s’afficher:

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

`data.table`en tant que dans R est pris en charge dans la mise à jour cumulative 14 de SQL Server 2017 (CU14) et versions ultérieures. `OutputDataSet`

## <a name="python-script-execution-issues"></a>Problèmes d’exécution de script Python

Cette section contient des problèmes connus spécifiques à l’exécution de Python sur SQL Server, ainsi que des problèmes liés aux packages python publiés par Microsoft, y compris [revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) et [microsoftml](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package).

### <a name="1-call-to-pretrained-model-fails-if-path-to-model-is-too-long"></a>1. L’appel au modèle préformé échoue si le chemin d’accès au modèle est trop long

Si vous avez installé les modèles préformés dans une version antérieure de SQL Server 2017, le chemin d’accès complet au fichier de modèle formé peut être trop long pour la lecture de Python. Cette limitation est résolue dans une version ultérieure du service.

Il existe plusieurs solutions possibles: 

+ Lorsque vous installez les modèles préformés, choisissez un emplacement personnalisé.
+ Si possible, installez l’instance de SQL Server sous un chemin d’installation personnalisé avec un chemin d’accès plus petit, tel que C:\SQL\MSSQL14. MSSQLSERVER.
+ Utilisez l’utilitaire Windows [fsutil](https://technet.microsoft.com/library/cc788097(v=ws.11).aspx) pour créer un lien physique qui mappe le fichier de modèle à un chemin d’accès plus bref.
+ Mettez à jour vers la dernière version du service.

### <a name="2-error-when-saving-serialized-model-to-sql-server"></a>2. Erreur lors de l’enregistrement du modèle sérialisé dans SQL Server

Lorsque vous transmettez un modèle à une instance de SQL Server distante et que vous tentez de `rx_unserialize` lire le modèle binaire à l’aide de la fonction dans [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package), vous pouvez obtenir l’erreur suivante: 

> *NameError: le nom’rx_unserialize_model’n’est pas défini*

Cette erreur est générée si vous avez enregistré le modèle à l’aide d’une version récente de la fonction de sérialisation, mais que l’instance de SQL Server où vous désérialisez le modèle ne reconnaît pas l’API de sérialisation.

Pour résoudre le problème, mettez à niveau l’instance SQL Server 2017 vers CU3 ou une version ultérieure.

### <a name="3-failure-to-initialize-a-varbinary-variable-causes-an-error-in-bxlserver"></a>3. L’échec de l’initialisation d’une variable varbinary provoque une erreur dans BxlServer

Si vous exécutez du code python dans SQL Server `sp_execute_external_script`à l’aide de, et que le code a des variables de sortie de type varbinary (max), varchar (max) ou des types similaires, la variable doit être initialisée ou définie dans le cadre de votre script. Dans le cas contraire, le composant d’échange de données, BxlServer, génère une erreur et cesse de fonctionner.

Cette limitation sera corrigée dans une prochaine version de service. Pour contourner ce problème, assurez-vous que la variable est initialisée dans le script Python. Vous pouvez utiliser n’importe quelle valeur valide, comme dans les exemples suivants:

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

### <a name="4-telemetry-warning-on-successful-execution-of-python-code"></a>4. Avertissement de télémétrie lors de l’exécution réussie du code python

À partir de SQL Server 2017 CU2, le message suivant peut s’afficher même si le code python s’exécute normalement:

> *Message (s) stderr à partir du script externe:* 
>  *~ PYTHON_SERVICES\lib\site-packages\revoscalepy\utils\RxTelemetryLogger*
> *SyntaxWarning: telemetry_state est utilisé avant la déclaration globale*

Ce problème a été résolu dans SQL Server 2017 mise à jour cumulative 3 (CU3). 

### <a name="5-numeric-decimal-and-money-data-types-not-supported"></a>5. Types de données numeric, Decimal et Money non pris en charge

À partir de SQL Server 2017, les types de données numeric, Decimal et Money de avec les jeux de résultats ne sont pas pris en charge lors de `sp_execute_external_script`l’utilisation de Python avec. Les messages suivants peuvent s’afficher:

> *Code 39004, état SQL: S1000] une erreur de script’Python’s’est produite lors de l’exécution de of’sp_execute_external_script’avec HRESULT 0x80004004.*

> *Code 39019, état SQL: S1000] une erreur de script externe s’est produite:*
> 
> *Erreur SqlSatelliteCall: Type non pris en charge dans le schéma de sortie. Types pris en charge: bit, smallint, int, DateTime, smallmoney, Real et float. Char, varchar sont partiellement pris en charge.*

Ce problème a été résolu dans la mise à jour cumulative 14 de SQL Server 2017 (CU14).

## <a name="revolution-r-enterprise-and-microsoft-r-open"></a>Revolution R Enterprise et Microsoft R Open

Cette section répertorie les problèmes spécifiques aux outils de connectivité, de développement et de performances de R fournis par Revolution Analytics. Ces outils ont été fournis dans les versions préliminaires antérieures [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]de.

En général, nous vous recommandons de désinstaller ces versions précédentes et d’installer la dernière version de SQL Server ou Microsoft R Server.

### <a name="1-revolution-r-enterprise-is-not-supported"></a>1. La révolution R Enterprise n’est pas prise en charge

L’installation de Revolution R Enterprise côte à côte avec n' [!INCLUDE[rsql_productname_md](../includes/rsql-productname-md.md)] importe quelle version de n’est pas prise en charge.

Si vous disposez déjà d’une licence pour Revolution R Enterprise, vous devez la placer sur un ordinateur distinct de l' [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance et de toute station de travail que vous souhaitez utiliser pour vous [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] connecter à l’instance.

Certaines versions préliminaires de [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)] incluaient un environnement de développement R pour Windows qui a été créé par Revolution Analytics. Cet outil n’est plus fourni et n’est pas pris en charge.

Pour la compatibilité [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)]avec, nous vous recommandons d’installer à la place Microsoft R client. [Outils R pour Visual Studio](https://www.visualstudio.com/vs/rtvs/) et [Visual Studio code](https://code.visualstudio.com/) prennent également en charge les solutions Microsoft R.

### <a name="2-compatibility-issues-with-sqlite-odbc-driver-and-revoscaler"></a>2. Problèmes de compatibilité avec le pilote ODBC de SQLite et RevoScaleR

La révision 0,92 du pilote ODBC SQLite est incompatible avec RevoScaleR. Les révisions de 0.88-0.91 et 0,93 et versions ultérieures sont connues pour être compatibles.

## <a name="see-also"></a>Voir aussi

[Nouveautés de SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md)

[Résolution des problèmes de Machine Learning dans SQL Server](machine-learning-troubleshooting-faq.md)
