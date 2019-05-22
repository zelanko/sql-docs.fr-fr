---
title: Installer des Extensions de langage Machine SQL Server (Java) sur Linux | Microsoft Docs
description: Découvrez comment installer les Extensions de langage SQL Server (Java) sur Red Hat, Ubuntu et SUSE.
author: dphansen
ms.author: davidph
manager: cgronlun
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6d25739fb4f2ef104ba86c8e9124162e67fd8553
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65995077"
---
# <a name="install-sql-server-2019-language-extensions-java-on-linux"></a>Installer des Extensions de langage SQL Server 2019 (Java) sur Linux

[SQL Server Machine Learning Services](../advanced-analytics/what-is-sql-server-machine-learning.md) s’exécute sur les systèmes d’exploitation Linux à partir de cette version préliminaire de SQL Server 2019. Suivez les étapes décrites dans cet article pour installer l’extension du langage Java. 

Extensions de langage sont un module complémentaire pour le moteur de base de données. Bien que vous puissiez [installer le moteur de base de données et les Extensions de langage simultanément](#install-all), il est recommandé d’installer et configurer le moteur de base de données SQL Server tout d’abord, afin que vous pouvez résoudre les problèmes avant d’ajouter plus de composants. 

Emplacement du package pour les extensions Java se trouvent dans les référentiels de code source SQL Server Linux. Si vous avez configuré déjà des référentiels de code source pour l’installation du moteur de base de données, vous pouvez exécuter la **mssql-server-extensibilité-java** commandes d’installation à l’aide de la même inscription de référentiel de package.

Extensions de langage est également pris en charge sur les conteneurs Linux. Nous ne fournissons pas de conteneurs préconfigurés avec des Extensions de langage, mais vous pouvez en créer un à partir des conteneurs SQL Server à l’aide de [un exemple de modèle disponible sur GitHub](https://github.com/Microsoft/mssql-docker/tree/master/linux/preview/examples/mssql-mlservices).

## <a name="uninstall-previous-ctp"></a>Désinstaller la version CTP précédente

La liste des packages a changé au CTP versions antérieures, ce qui entraîne moins de packages. Nous vous recommandons de désinstallation de CTP 2.x pour supprimer tous les packages précédentes avant d’installer la version CTP 3.0. Installation côte à côte de plusieurs versions n’est pas pris en charge.

### <a name="1-confirm-package-installation"></a>1. Confirmer l’installation du package

Vous pouvez souhaiter vérifier l’existence d’une installation précédente dans un premier temps. Les fichiers suivants indiquent une installation existante : checkinstallextensibility.sh, exthost, launchpad.

```bash
ls /opt/microsoft/mssql/bin
```

### <a name="2-uninstall-previous-ctp-2x-packages"></a>2. Désinstaller des packages de 2.x CTP précédentes

Désinstallez au niveau du package le plus bas. N’importe quel package amont dépendant d’un package de niveau inférieur est automatiquement désinstallé.

  + Pour l’intégration de Java, vous devez supprimer **mssql-server-extensibilité-java**

Commandes de suppression de packages apparaissent dans le tableau suivant.

| Plateforme  | Commandes de suppression de package | 
|-----------|----------------------------|
| RHEL  | `sudo yum remove msssql-server-extensibility-java` |
| SLES  | `sudo zypper remove msssql-server-extensibility-java` |
| Ubuntu    | `sudo apt-get remove msssql-server-extensibility-java`|

### <a name="3-proceed-with-ctp-30-install"></a>3. Poursuivre l’installation de la version CTP 3.0

Installez au niveau du package le plus élevé en suivant les instructions dans cet article pour votre système d’exploitation.

Pour chaque ensemble de spécifiques du système d’exploitation d’instructions d’installation, *plus haut niveau de package* est soit **exemple 1 : installation complète** pour l’ensemble de packages, ou **exemple 2 : installation minimale**  pour le plus petit nombre de packages requis pour une installation viable.

1. Exécutez les commandes d’installation à l’aide de gestionnaires de packages et de la syntaxe de votre distribution Linux : 

   + [RedHat](#RHEL)
   + [Ubuntu](#ubuntu)
   + [SUSE](#suse)

## <a name="prerequisites"></a>Prérequis

+ La version de Linux doit être [pris en charge par SQL Server](sql-server-linux-release-notes-2019.md#supported-platforms), mais n’inclut ne pas le moteur Docker. Versions prises en charge sont les suivantes :

   + [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)

   + [SUSE Enterprise Linux Server](quickstart-install-connect-suse.md)

   + [Ubuntu](quickstart-install-connect-ubuntu.md)

+ Vous devez disposer d’un outil pour l’exécution des commandes T-SQL. Un éditeur de requête est nécessaire pour la validation et la configuration de post-installation. Nous vous recommandons de [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download?view=sql-server-2017#get-azure-data-studio-for-linux), téléchargeable gratuitement qui s’exécute sur Linux.

## <a name="package-list"></a>Liste des packages

Sur un appareil connecté à internet, les packages sont téléchargés et installés indépendamment le moteur de base de données à l’aide de l’installeur de package pour chaque système d’exploitation. Le tableau suivant décrit tous les packages disponibles.

| Nom du package | Applies-to | Description |
|--------------|----------|-------------|
|mssql-server-extensibility  | Toutes les langues | Infrastructure d’extensibilité permettant d’exécuter le code Java. |
|mssql-server-extensibility-java | Java | Extension de Java pour le chargement d’un environnement d’exécution Java. Il n’existe aucune des bibliothèques supplémentaires ou des packages pour Java. |

<a name="RHEL"></a>

## <a name="install-language-extensions"></a>Installer les Extensions de langage

Vous pouvez installer des Extensions de langage et de Java sur Linux en installant **mssql-server-extensibilité-java**. Lorsque vous installez **mssql-server-extensibilité-java**, le package installe automatiquement JRE 8 s’il n’est pas déjà installé. Il ajoute également le chemin d’accès de la machine virtuelle Java dans une variable d’environnement appelée variable.

> [!Note]
> Sur un serveur connecté à internet, les dépendances de package sont téléchargés et installés dans le cadre de l’installation du package principal. Si votre serveur n’est pas connecté à internet, consultez plus de détails dans le [le programme d’installation hors connexion](#offline-install).

### <a name="redhat-install-command"></a>Commande d’installation de Red Hat

Vous pouvez installer des Extensions de langage pour Java sur Red Hat à l’aide de la commande ci-dessous.

> [!Tip]
> Si possible, exécutez `yum clean all` pour actualiser les packages sur le système avant l’installation.

```bash
# Install as root or sudo
sudo yum install mssql-server-extensibility-java
```

<a name="ubuntu"></a>

### <a name="ubuntu-install-command"></a>Commande d’installation Ubuntu

Vous pouvez installer des Extensions de langage pour Java sur Ubuntu à l’aide de la commande ci-dessous.

> [!Tip]
> Si possible, exécutez `apt-get update` pour actualiser les packages sur le système avant l’installation. En outre, certaines images docker d’Ubuntu peut-être pas l’option de transport apt https. Pour l’installer, utiliser `apt-get install apt-transport-https`.

```bash
# Install as root or sudo
sudo apt-get install mssql-server-extensibility-java
```

<a name="suse"></a>

### <a name="suse-install-command"></a>Commande d’installation SUSE

Vous pouvez installer des Extensions de langage pour Java sur SUSE à l’aide de la commande ci-dessous.

```bash
# Install as root or sudo
sudo zypper install mssql-server-extensibility-java
```

## <a name="post-install-config-required"></a>Configuration de post-installation (obligatoire)

1. Accorder des autorisations sur Linux

    Vous n’avez pas besoin d’effectuer cette étape si vous utilisez des bibliothèques externes. La méthode recommandée de l’utilisation est à l’aide de bibliothèques externes. Pour faciliter la création d’une bibliothèque externe à partir de votre fichier jar, consultez [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)

    Si vous n’utilisez pas les bibliothèques externes, vous devez fournir à SQL Server avec les autorisations d’exécution des classes Java dans votre fichier jar.

    Pour accorder un en lecture et exécution d’accès à un fichier jar, exécutez la commande suivante **chmod** commande sur le fichier jar. Nous vous recommandons de toujours placer vos fichiers de classe dans un fichier jar, lorsque vous travaillez avec SQL Server. Pour créer un fichier jar, consultez [la création d’un fichier jar](https://docs.microsoft.com/sql/language-extensions/how-to/create-a-java-jar-file-from-class-files).

    ```cmd
    chmod ug+rx <MyJarFile.jar>
    ```

    Vous devez également accorder les autorisations de mssql_satellite le fichier jar à lecture/exécution.

    ```cmd
    chown mssql_satellite:mssql_satellite <MyJarFile.jar>
    ```

    Une configuration supplémentaire est essentiellement via les [outil mssql-conf](sql-server-linux-configure-mssql-conf.md).

2. Ajoutez le compte d’utilisateur mssql utilisé pour exécuter le service SQL Server. Cela est nécessaire si vous n’avez pas exécuté le programme d’installation précédemment.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

3. Activer l’accès réseau sortant. Un accès réseau sortant est désactivé par défaut. Pour activer les demandes sortantes, définissez le « outboundnetworkaccess » à l’aide de l’outil mssql-conf de propriété booléenne. Pour plus d’informations, consultez [configurer SQL Server sur Linux avec mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-outbound-access).

   ```bash
   # Run as SUDO or root
   # Enable outbound requests over the network
   sudo /opt/mssql/bin/mssql-conf set extensibility outboundnetworkaccess 1
   ```

4. Redémarrez le service Launchpad de SQL Server et l’instance du moteur de base de données pour lire les valeurs mises à jour à partir du fichier INI. Un message de redémarrage vous rappelle chaque fois qu’un paramètre dépendant de l’extensibilité est modifié.  

   ```bash
   systemctl restart mssql-launchpadd

   systemctl restart mssql-server.service
   ```

5. Activer l’exécution de script externe à l’aide d’Azure Data Studio ou un autre outil comme SQL Server Management Studio (Windows uniquement) qui s’exécute Transact-SQL.

   ```bash
   EXEC sp_configure 'external scripts enabled', 1
   RECONFIGURE WITH OVERRIDE
   ```

6. Redémarrez le `mssql-launchpadd` à nouveau de service.

## <a name="verify-installation"></a>Vérifier l'installation

Intégration des fonctionnalités Java n’inclut pas les bibliothèques, mais vous pouvez exécuter `grep -r JRE_HOME /etc` pour confirmer la création de la variable d’environnement JAVA_HOME.

Pour valider l’installation, exécuter un script T-SQL qui exécute un système stockée procédure d’appel de Java. Vous aurez besoin un outil de requête pour cette tâche. Azure Data Studio est un bon choix. Autres outils couramment utilisés tels que SQL Server Management Studio ou PowerShell sont Windows uniquement. Si vous avez un ordinateur Windows grâce à ces outils, utilisez-le pour vous connecter à votre installation de Linux du moteur de base de données.

<a name="install-all"></a>

## <a name="full-install-of-sql-server-and-language-extensions"></a>Installation complète de SQL Server et les Extensions de langage

Vous pouvez installer et configurer le moteur de base de données et les Services Machine Learning dans une procédure en ajoutant des packages de Java et des paramètres sur une commande qui installe le moteur de base de données.

1. Fournir une ligne de commande qui inclut le moteur de base de données, ainsi que les fonctionnalités d’extension de langage.

  Vous pouvez ajouter Java installer d’extensibilité pour un moteur de base de données.

  ```bash
  sudo yum install -y mssql-server mssql-server-extensibility-java 
  ```

3. Accepter les contrats de licence et terminer la configuration de post-installation. Utilisez le **mssql-conf** outil pour cette tâche.

  ```bash
  sudo /opt/mssql/bin/mssql-conf setup
  ```

  Vous êtes invité à accepter le contrat de licence pour le moteur de base de données, choisissez une édition et définir le mot de passe administrateur. 

4. Redémarrez le service, si vous êtes invité à le faire.

  ```bash
  sudo systemctl restart mssql-server.service
  ```

## <a name="unattended-installation"></a>Installation sans assistance

À l’aide de la [installation sans assistance](https://docs.microsoft.com/sql/linux/sql-server-linux-setup#unattended) pour le moteur de base de données, ajoutez les packages pour mssql-server-extensibilité-java.

<a name="offline-install"></a>


## <a name="offline-installation"></a>Installation hors connexion

Suivez le [installation hors connexion](sql-server-linux-setup.md#offline) obtenir des instructions pour obtenir des instructions sur l’installation des packages. Recherchez votre site de téléchargement et puis télécharger les packages spécifiques à l’aide de la liste des packages.

> [!Tip]
> Plusieurs outils de gestion de package de fournissent des commandes qui peuvent vous aider à déterminent les dépendances de package. Pour yum, utilisez `sudo yum deplist [package]`. Pour Ubuntu, utilisez `sudo apt-get install --reinstall --download-only [package name]` suivie `dpkg -I [package name].deb`.

#### <a name="download-site"></a>Site de téléchargement

Vous pouvez télécharger des packages à partir de [ https://packages.microsoft.com/ ](https://packages.microsoft.com/). Tous les packages pour Java sont colocalisés avec le package du moteur de base de données. 

#### <a name="redhat7-paths"></a>Chemins d’accès RedHat/7

|||
|--|----|
| mssql/extensibility-java packages | [https://packages.microsoft.com/rhel/7/mssql-server-preview/](https://packages.microsoft.com/rhel/7/mssql-server-preview/) |

#### <a name="ubuntu1604-paths"></a>Chemins d’accès/16.04 Ubuntu

|||
|--|----|
| mssql/extensibility-java packages | [https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/) |

#### <a name="suse12-paths"></a>Chemins d’accès SUSE/12

|||
|--|----|
| mssql/extensibility-java packages | [https://packages.microsoft.com/sles/12/mssql-server-preview/](https://packages.microsoft.com/sles/12/mssql-server-preview/) |

#### <a name="package-list"></a>Liste des packages

Selon les extensions que vous souhaitez utiliser, télécharger les packages nécessaires pour une langue spécifique. Noms de fichiers incluent des informations sur la plateforme dans le suffixe, mais les noms de fichier ci-dessous doivent être suffisamment proches pour vous permettre de déterminer les fichiers à obtenir.

```
# Core packages 
mssql-server-15.0.1000
mssql-server-extensibility-15.0.1000

# Java
mssql-server-extensibility-java-15.0.1000
```

## <a name="limitations-in-ctp-releases"></a>Limitations dans les versions CTP

Extensibilité des Extensions de langage et de Java sur Linux est toujours en cours de développement. Les fonctionnalités suivantes ne sont pas encore disponibles dans la version d’évaluation.

+ Actuellement, l’authentification implicite n’est pas disponible sur Linux pour l’instant, ce qui signifie que vous ne peut pas se connecter au serveur à partir de Java en cours d’exécution pour accéder aux données ou autres ressources.


### <a name="resource-governance"></a>Gouvernance des ressources

Il existe une parité entre Linux et Windows pour [gouvernance des ressources](../t-sql/statements/create-external-resource-pool-transact-sql.md) pour les pools de ressources externes, mais les statistiques de [sys.dm_resource_governor_external_resource_pools](../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) ont actuellement unités différentes sur Linux. Unités sont alignées dans une prochaine version CTP.
 
| Nom de colonne   | Description | Valeur sur Linux | 
|---------------|--------------|---------------|
|peak_memory_kb | La quantité maximale de mémoire utilisée pour le pool de ressources. | Sur Linux, cette statistique provient du sous-système de mémoire « cgroups », où la valeur est memory.max_usage_in_bytes |
|write_io_count | Total d’écriture e/s émises depuis que les statistiques du gouverneur de ressources ont été réinitialisées. | Sur Linux, cette statistique est alimentée à partir du sous-système de blkio « cgroups », où la valeur sur la ligne de l’écriture est blkio.throttle.io_serviced | 
|read_io_count | Total de lecture e/s émises depuis que les statistiques du gouverneur de ressources ont été réinitialisées. | Sur Linux, cette statistique est alimentée à partir du sous-système de blkio « cgroups », où la valeur sur la ligne de lecture est blkio.throttle.io_serviced | 
|total_cpu_kernel_ms | Le temps processeur cumulé utilisateur noyau en millisecondes depuis que les statistiques du gouverneur de ressources ont été réinitialisées. | Sur Linux, cette statistique est alimentée à partir du sous-système de cpuacct « cgroups », où la valeur sur la ligne de l’utilisateur est cpuacct.stat |  
|total_cpu_user_ms | Temps utilisateur processeur cumulé en millisecondes depuis que les statistiques du gouverneur de ressources ont été réinitialisées.| Sur Linux, cette statistique est alimentée à partir du sous-système de cpuacct « cgroups », où la valeur de la valeur de ligne du système est cpuacct.stat | 
|active_processes_count | Le nombre de processus externes en cours d’exécution au moment de la demande.| Sur Linux, cette statistique est alimentée à partir du sous-système de PID GGroups, où la valeur est pids.current | 

## <a name="next-steps"></a>Étapes suivantes

Les développeurs Java peuvent démarrer avec des exemples simples et apprendre les bases du fonctionne de Java avec SQL Server. Pour votre prochaine étape, consultez les liens suivants :

+ [Tutoriel : Expressions régulières avec Java](../language-extensions/tutorials/search-for-string-using-regular-expressions-in-java.md)