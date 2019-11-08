---
title: Installer les extensions de langage SQL Server (Java) sur Linux
description: Découvrez comment installer des extensions de langage SQL Server (Java) sur Red Hat, Ubuntu et SUSE.
author: dphansen
ms.author: davidph
ms.reviewer: vanto
manager: cgronlun
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3e86da652231a06cd28318096ada3ae3aed7526e
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531234"
---
# <a name="install-sql-server-2019-language-extensions-java-on-linux"></a>Installer les extensions de langage SQL Server 2019 (Java) sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Les extensions de langage sont un module complémentaire du moteur de base de données. Bien que vous puissiez [installer le moteur de base de données et les extensions de langage simultanément](#install-all), il est recommandé d’installer et de configurer le moteur de base de données SQL Server en premier afin de pouvoir résoudre les problèmes avant d’ajouter d’autres composants. 

Suivez les étapes décrites dans cet article pour installer l’extension de langage Java.

L’emplacement des packages pour les extensions Java se trouve dans les référentiels source de SQL Server Linux. Si vous avez déjà configuré des référentiels source pour l’installation du moteur de base de données, vous pouvez exécuter les commandes d’installation du package **mssql-server-extensibility-java** à l’aide de la même inscription de référentiel.

Les extensions de langage sont également prises en charge sur les conteneurs Linux. Nous ne fournissons pas de conteneurs prédéfinis avec les extensions de langage, mais vous pouvez en créer un à partir des conteneurs SQL Server à l’aide [d’un exemple de modèle disponible sur GitHub](https://github.com/Microsoft/mssql-docker/tree/master/linux/preview/examples/mssql-mlservices).

Les extensions de langage et [Machine Learning Services](../advanced-analytics/index.yml) sont installés par défaut sur Clusters Big Data SQL Server. Si vous utilisez Clusters Big Data, vous n’avez pas besoin de suivre les étapes décrites dans cet article. Pour plus d’informations, consultez [Utiliser Machine Learning Services (Python et R) sur Clusters Big Data](../big-data-cluster/machine-learning-services.md).

## <a name="uninstall-preview-version"></a>Désinstaller la préversion

Si vous avez installé une préversion comme CTP (Community Technology Preview) ou RC (Release Candidate), nous vous recommandons de la désinstaller pour supprimer tous les packages précédents avant d’installer SQL Server 2019. L’installation côte à côte de plusieurs versions n’est pas prise en charge et la liste des packages a changé au cours des dernières préversions (CTP/RC).

### <a name="1-confirm-package-installation"></a>1. Confirmer l’installation du package

Vous souhaiterez peut-être vérifier l’existence d’une installation précédente comme première étape. Les fichiers suivants indiquent une installation existante : checkinstallextensibility.sh, exthost, launchpad.

```bash
ls /opt/microsoft/mssql/bin
```

### <a name="2-uninstall-previous-ctprc-packages"></a>2. Désinstaller les packages CTP/RC précédents

Désinstallez au niveau du package le plus bas. Tout package en amont dépendant d’un package de niveau inférieur est automatiquement désinstallé.

  + Pour l’intégration Java, supprimez **mssql-server-extensibility-java**

Les commandes de suppression des packages s’affichent dans le tableau suivant.

| Plateforme  | Commande(s) de suppression de package | 
|-----------|----------------------------|
| RHEL  | `sudo yum remove msssql-server-extensibility-java` |
| SLES  | `sudo zypper remove msssql-server-extensibility-java` |
| Ubuntu    | `sudo apt-get remove msssql-server-extensibility-java`|

### <a name="3-install-sql-server-2019"></a>3. Installer SQL Server 2019

Installez au niveau de package le plus élevé en suivant les instructions de cet article pour votre système d’exploitation.

Pour chaque ensemble d’instructions d’installation propres au système d’exploitation, le *niveau de package le plus élevé* est soit **Exemple 1 : Installation complète** pour l’ensemble complet de packages soit **Exemple 2 : Installation minimale**  pour le minimum de packages requis pour une installation viable.

1. Exécutez les commandes d’installation à l’aide des gestionnaires de package et de la syntaxe pour votre distribution Linux : 

   + [RedHat](#RHEL)
   + [Ubuntu](#ubuntu)
   + [SUSE](#suse)

## <a name="prerequisites"></a>Conditions préalables requises

+ La version de Linux doit être [prise en charge par SQL Server](sql-server-linux-release-notes-2019.md#supported-platforms), mais elle n’inclut pas le moteur Docker. Les versions prises en charge sont les suivantes :

   + [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)

   + [Serveur SUSE Enterprise Linux](quickstart-install-connect-suse.md)

   + [Ubuntu](quickstart-install-connect-ubuntu.md)

+ Vous devez disposer d’un outil pour l’exécution des commandes T-SQL. Un éditeur de requête est nécessaire pour la configuration et la validation postérieures à l’installation. Nous vous recommandons [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download?view=sql-server-2017#get-azure-data-studio-for-linux), un outil en téléchargement gratuit qui s’exécute sur Linux.

## <a name="package-list"></a>Liste des packages

Sur un appareil connecté à Internet, les packages sont téléchargés et installés indépendamment du moteur de base de données à l’aide du programme d’installation de package pour chaque système d’exploitation. Le tableau suivant décrit tous les packages disponibles.

| Nom du package | S’applique à | Description |
|--------------|----------|-------------|
|mssql-server-extensibility  | Toutes les langues | Infrastructure d’extensibilité utilisée pour l’extension de langage Java |
|mssql-server-extensibility-java | Java | Infrastructure d’extensibilité utilisée pour l’extension de langage Java et incluant un runtime Java pris en charge |

<a name="RHEL"></a>

## <a name="install-language-extensions"></a>Installer les extensions de langage

Vous pouvez installer les extensions de langage et Java sur Linux en installant **mssql-server-extensibility-java**. Lorsque vous installez **mssql-server-extensibility-java**, le package installe automatiquement JRE 11 s’il n’est pas déjà installé. Cela ajoute également le chemin d’accès JVM à une variable d’environnement appelée JRE_HOME.

> [!Note]
> Sur un serveur connecté à Internet, les dépendances de package sont téléchargées et installées dans le cadre de l’installation du package principal. Si votre serveur n’est pas connecté à Internet, consultez les détails de [Configuration hors connexion](#offline-install).

### <a name="redhat-install-command"></a>Commande d’installation RedHat

Vous pouvez installer les extensions de langage pour Java sur RedHat à l’aide de la commande ci-dessous.

> [!Tip]
> Si possible, exécutez `yum clean all` pour actualiser les packages sur le système avant l’installation.

```bash
# Install as root or sudo
sudo yum install mssql-server-extensibility-java
```

<a name="ubuntu"></a>

### <a name="ubuntu-install-command"></a>Commande d’installation Ubuntu

Vous pouvez installer les extensions de langage pour Java sur Ubuntu à l’aide de la commande ci-dessous.

> [!Tip]
> Si possible, exécutez `apt-get update` pour actualiser les packages sur le système avant l’installation. En outre, il se peut que certaines images de Docker d’Ubuntu ne disposent pas de l’option de transport https apt. Pour l’installer, utilisez `apt-get install apt-transport-https`.

```bash
# Install as root or sudo
sudo apt-get install mssql-server-extensibility-java
```

<a name="suse"></a>

### <a name="suse-install-command"></a>Commande d’installation de SUSE

Vous pouvez installer les extensions de langage pour Java sur SUSE à l’aide de la commande ci-dessous.

```bash
# Install as root or sudo
sudo zypper install mssql-server-extensibility-java
```

## <a name="post-install-config-required"></a>Configuration après installation (obligatoire)

1. Accorder des autorisations sur Linux

    Vous n’avez pas besoin d’effectuer cette étape si vous utilisez des bibliothèques externes. La façon de procéder recommandée est d’utiliser des bibliothèques externes. Pour obtenir de l’aide sur la création d’une bibliothèque externe à partir de votre fichier jar, consultez [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)

    Si vous n’utilisez pas de bibliothèques externes, vous devez fournir à SQL Server les autorisations nécessaires pour exécuter les classes Java dans votre fichier jar.

    Pour accorder l’accès en lecture et d’exécution à un fichier jar, exécutez la commande **chmod** suivante sur le fichier jar. Nous vous recommandons de toujours placer vos fichiers de classe dans un fichier jar lorsque vous travaillez avec SQL Server. Pour obtenir de l’aide sur la création d’un fichier jar, consultez [Comment créer un fichier jar](https://docs.microsoft.com/sql/language-extensions/how-to/create-a-java-jar-file-from-class-files).

    ```cmd
    chmod ug+rx <MyJarFile.jar>
    ```

    Vous devez également accorder à mssql_satellite les autorisations pour le fichier jar à lire/exécuter.

    ```cmd
    chown mssql_satellite:mssql_satellite <MyJarFile.jar>
    ```

    La configuration supplémentaire s’effectue principalement avec [l’outil mssql-conf](sql-server-linux-configure-mssql-conf.md).

2. Ajoutez le compte d’utilisateur mssql utilisé pour exécuter le service SQL Server. Cela est requis si vous n’avez pas exécuté l’installation précédemment.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

3. Activez l’accès réseau sortant. L’accès réseau sortant est désactivé par défaut. Pour activer les requêtes sortantes, définissez la propriété booléenne « outboundnetworkaccess » à l’aide de l’outil mssql-conf. Pour plus d’informations, consultez [Configurer SQL Server sur Linux avec mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-outbound-access).

   ```bash
   # Run as SUDO or root
   # Enable outbound requests over the network
   sudo /opt/mssql/bin/mssql-conf set extensibility outboundnetworkaccess 1
   ```

4. Redémarrez le service SQL Server Launchpad et l’instance du moteur de base de données pour lire les valeurs mises à jour à partir du fichier INI. Un message de redémarrage vous rappelle chaque fois qu’un paramètre relatif à l’extensibilité est modifié.  

   ```bash
   systemctl restart mssql-launchpadd

   systemctl restart mssql-server.service
   ```

5. Activez l’exécution du script externe à l’aide d’Azure Data Studio ou d’un autre outil comme SQL Server Management Studio (Windows uniquement) qui exécute Transact-SQL.

   ```bash
   EXEC sp_configure 'external scripts enabled', 1
   RECONFIGURE WITH OVERRIDE
   ```

6. Redémarrez le service `mssql-launchpadd`.

7. Pour chaque base de données dans laquelle vous souhaitez utiliser des extensions de langage, vous devez inscrire le langage externe avec [CREATE EXTERNAL LANGUAGE](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql).

## <a name="register-external-language"></a>Inscrire le langage externe

Pour chaque base de données dans laquelle vous souhaitez utiliser des extensions de langage, vous devez inscrire le langage externe avec [CREATE EXTERNAL LANGUAGE](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql).

L’exemple suivant ajoute un langage externe appelé Java à une base de données sur SQL Server sur Linux.

```SQL
CREATE EXTERNAL LANGUAGE Java
FROM (CONTENT = N'<path-to-tar.gz>', FILE_NAME = 'javaextension.so');
GO
```

Pour plus d’informations, consultez [CRÉER UN LANGAGE EXTERNE](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql).

## <a name="verify-installation"></a>Vérifier l'installation

L’intégration des fonctionnalités Java n’inclut pas les bibliothèques, mais vous pouvez exécuter `grep -r JRE_HOME /etc` pour confirmer la création de la variable d’environnement JAVA_HOME.

Pour valider l’installation, exécutez un script T-SQL qui exécute une procédure stockée système qui appelle Java. Vous aurez besoin d’un outil de requête pour cette tâche. Azure Data Studio est un bon choix. Les autres outils couramment utilisés, tels que SQL Server Management Studio ou PowerShell, sont uniquement disponibles sous Windows. Si vous disposez d’un ordinateur Windows avec ces outils, utilisez-le pour vous connecter à votre installation Linux du moteur de base de données.

<a name="install-all"></a>

## <a name="full-install-of-sql-server-and-language-extensions"></a>Installation complète de SQL Server et des extensions de langage

Vous pouvez installer et configurer le moteur de base de données et les extensions de langage en une seule procédure en ajoutant des packages Java et des paramètres sur une commande qui installe le moteur de base de données.

1. Fournissez une ligne de commande qui comprend le moteur de base de données ainsi que des fonctionnalités d’extension de langage.

  Vous pouvez ajouter l’extensibilité Java à une installation du moteur de base de données.

  ```bash
  sudo yum install -y mssql-server mssql-server-extensibility-java 
  ```

3. Acceptez les contrats de licence et terminez la configuration consécutive à l’installation. Utilisez l'outil **mssql-conf** pour cette tâche.

  ```bash
  sudo /opt/mssql/bin/mssql-conf setup
  ```

  Vous serez invité à accepter le contrat de licence pour le moteur de base de données, à choisir une édition et à définir le mot de passe administrateur. 

4. Redémarrez le service si vous y êtes invité.

  ```bash
  sudo systemctl restart mssql-server.service
  ```

## <a name="unattended-installation"></a>Installation sans assistance

À l'aide de [l’installation sans assistance](https://docs.microsoft.com/sql/linux/sql-server-linux-setup#unattended) du moteur de base de données, ajoutez les packages pour mssql-server-extensibility-java.

<a name="offline-install"></a>


## <a name="offline-installation"></a>Installation hors connexion

Suivez les instructions [d'installation hors connexion](sql-server-linux-setup.md#offline) pour connaître les étapes d’installation des packages. Recherchez votre site de téléchargement, puis téléchargez des packages spécifiques à l’aide de la liste de packages ci-dessous.

> [!Tip]
> Plusieurs outils de gestion des packages fournissent des commandes qui peuvent vous aider à déterminer les dépendances du package. Pour yum, utilisez `sudo yum deplist [package]`. Pour Ubuntu, utilisez `sudo apt-get install --reinstall --download-only [package name]`, suivi de `dpkg -I [package name].deb`.

#### <a name="download-site"></a>Site de téléchargement

Vous pouvez télécharger des packages à partir de [https://packages.microsoft.com/](https://packages.microsoft.com/). Tous les packages pour Java sont colocalisés avec le package du moteur de base de données. 

#### <a name="redhat7-paths"></a>Chemins RedHat/7

|||
|--|----|
| Packages mssql/extensibility-java | [https://packages.microsoft.com/rhel/7/mssql-server-preview/](https://packages.microsoft.com/rhel/7/mssql-server-preview/) |

#### <a name="ubuntu1604-paths"></a>Chemins d’accès Ubuntu/16.04

|||
|--|----|
| Packages mssql/extensibility-java | [https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/) |

#### <a name="suse12-paths"></a>Chemins SUSE/12

|||
|--|----|
| Packages mssql/extensibility-java | [https://packages.microsoft.com/sles/12/mssql-server-preview/](https://packages.microsoft.com/sles/12/mssql-server-preview/) |

#### <a name="package-list"></a>Liste des packages

Selon les extensions que vous souhaitez utiliser, téléchargez les packages nécessaires pour un langage spécifique. Les noms de fichiers exacts incluent des informations sur la plateforme dans le suffixe, mais les noms de fichier ci-dessous devraient être suffisamment proches pour vous permettre de déterminer les fichiers à obtenir.

```
# Core packages 
mssql-server-15.0.1000
mssql-server-extensibility-15.0.1000

# Java
mssql-server-extensibility-java-15.0.1000
```

## <a name="limitations"></a>Limitations

+ L’authentification implicite n’est actuellement pas disponible sur Linux, ce qui signifie que vous ne pouvez pas vous reconnecter au serveur à partir de Java en cours d’exécution pour accéder à des données ou à d’autres ressources.

### <a name="resource-governance"></a>Gouvernance des ressources

Il existe une parité entre Linux et Windows pour la [gouvernance des ressources](../t-sql/statements/create-external-resource-pool-transact-sql.md) pour les pools de ressources externes, mais les statistiques pour [sys.dm_resource_governor_external_resource_pools](../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) ont actuellement des unités différentes sur Linux. 
 
| Nom de colonne   | Description | Valeur sur Linux | 
|---------------|--------------|---------------|
|peak_memory_kb | Quantité maximale de mémoire utilisée pour le pool de ressources. | Sur Linux, cette statistique provient du sous-système de mémoire CGroups, où la valeur est memory.max_usage_in_bytes |
|write_io_count | Total des entrées/sorties d'écriture émises depuis que les statistiques du gouverneur de ressources ont été réinitialisées. | Sur Linux, cette statistique provient du sous-système blkIo CGroups, où la valeur de la ligne d’écriture est blkio.throttle.io_serviced | 
|read_io_count | Total des entrées/sorties de lecture émises depuis que les statistiques du gouverneur de ressources ont été réinitialisées. | Sur Linux, cette statistique provient du sous-système CGroups blkIo, où la valeur de la ligne de lecture est blkio.throttle.io_serviced | 
|total_cpu_kernel_ms | Le temps du noyau utilisateur cumulatif de l'UC, en millisecondes, depuis que les statistiques du gouverneur de ressources ont été réinitialisées. | Sur Linux, cette statistique provient du sous-système cpuacct CGroups, où la valeur sur la ligne utilisateur est cpuacct.stat |  
|total_cpu_user_ms | Le temps utilisateur cumulatif de l'UC, en millisecondes, depuis que les statistiques du gouverneur de ressources ont été réinitialisées.| Sur Linux, cette statistique provient du sous-système CGroups cpuacct, où la valeur sur la ligne système est cpuacct.stat | 
|active_processes_count | Nombre de processus externes en cours d’exécution au moment de la requête.| Sur Linux, cette statistique provient du sous-système GGroups pids, où la valeur est pids.current | 

## <a name="next-steps"></a>Étapes suivantes

Les développeurs peuvent démarrer avec quelques exemples simples et découvrir les principes de base du fonctionnement de Java avec SQL Server. Pour l’étape suivante, consultez les liens suivants :

+ [Tutoriel : Expressions régulières avec Java](../language-extensions/tutorials/search-for-string-using-regular-expressions-in-java.md)