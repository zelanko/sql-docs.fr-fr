---
title: Extension de langage Java dans SQL Server 2019 - Extensions de langage SQL Server
description: Installer, configurer et valider l’extension du langage Java sur SQL Server 2019 pour les systèmes Linux et Windows.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/23/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: db57689227445b0f50d6ff59fbf81e1d84ecacdb
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64775491"
---
# <a name="java-language-extension-in-sql-server-2019"></a>Extension de langage Java dans SQL Server 2019 

À compter de la version préliminaire de SQL Server 2019 sur Windows et Linux, vous pouvez exécuter personnalisé code Java à l’aide du [infrastructure d’extensibilité](../concepts/extensibility-framework.md) comme module complémentaire pour l’instance du moteur de base de données.

L’infrastructure d’extensibilité est une architecture pour l’exécution de code externe : Java (à partir de SQL Server 2019), [Python (à partir de SQL Server 2017)](../concepts/extension-python.md), et [R (à partir de SQL Server 2016)](../concepts/extension-r.md). L’exécution de code est isolée des processus du moteur de base, mais entièrement intégrée à l’exécution des requêtes SQL Server. Cela signifie que vous pouvez transmettre des données à partir de n’importe quelle requête SQL Server à l’exécution externe (Java) et consommer ou conserver les résultats dans SQL Server.

Comme avec toute extension de langage de programmation, la procédure stockée système [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) est l’interface pour l’exécution de code Java précompilé.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Prérequis

Une instance de version préliminaire de SQL Server 2019 est nécessaire. Les versions antérieures n’ont pas de l’intégration de Java.

Java 8 est actuellement la version prise en charge. Les versions plus récentes, telles que Java 11, doit avec l’extension de langage, mais n’est actuellement pas pris en charge. Java Runtime Environment (JRE) est la configuration minimale requise, mais le JDK est utile si vous devez le compilateur et les packages de développement. Étant donné que le JDK est tout compris, si vous installez le JDK, JRE n’est pas nécessaire.

Vous pouvez utiliser la distribution de votre choix Java 8. Voici deux distributions suggérées :

| Distribution | Version de Java | Systèmes d’exploitation | JDK | JRE |
|-|-|-|-|-|
| [Oracle Java SE](https://www.oracle.com/technetwork/java/javase/downloads/index.html) | 8 | Windows et Linux | Oui | Oui |
| [Zulu OpenJDK](https://www.azul.com/downloads/zulu/) | 8 | Windows et Linux | Oui | Non |

Sur Linux, actuellement le **mssql-server-extensibilité-java** package installe automatiquement JRE 8 s’il n’est pas déjà installé. Scripts d’installation a également ajouter le chemin d’accès de la machine virtuelle Java pour une variable d’environnement appelée variable.

Sur Windows, nous vous recommandons d’installer le JDK sous la valeur par défaut `/Program Files/` dossier si possible. Sinon, une configuration supplémentaire est nécessaire pour accorder des autorisations aux exécutables. Pour plus d’informations, consultez le [accorder des autorisations (Windows)](#perms-nonwindows) section dans ce document.

> [!Note]
> Étant donné que Java est une compatibilité descendante, les versions antérieures peuvent fonctionner, mais la version prise en charge et testée pour cette première version CTP est Java 8. 

<a name="install-on-linux"></a>

## <a name="install-on-linux"></a>Installer sur Linux

Vous pouvez installer le [de base de données du moteur et l’extension Java ensemble](../../linux/sql-server-linux-setup-machine-learning.md#install-all), ou ajouter la prise en charge de Java à une instance existante. Les exemples suivants ajouter l’extension de Java à une installation existante.  

```bash
# RedHat install commands
sudo yum install mssql-server-extensibility-java

# Ubuntu install commands
sudo apt-get install mssql-server-extensibility-java

# SUSE install commands
sudo zypper install mssql-server-extensibility-java
```

Lorsque vous installez **mssql-server-extensibilité-java**, le package installe automatiquement JRE 8 s’il n’est pas déjà installé. Il ajoute également le chemin d’accès de la machine virtuelle Java dans une variable d’environnement appelée variable.

Après avoir terminé l’installation, l’étape suivante consiste [configurer l’exécution du script externe](#configure-script-execution).

> [!Note]
> Sur un appareil connecté à internet, les dépendances de package sont téléchargés et installés dans le cadre de l’installation du package principal. Pour plus d’informations, notamment le programme d’installation hors connexion, consultez [installer SQL Server Machine Learning Services sur Linux](../../linux/sql-server-linux-setup-machine-learning.md).

### <a name="grant-permissions-on-linux"></a>Accorder des autorisations sur Linux

Vous n’avez pas besoin d’effectuer cette étape si vous utilisez des bibliothèques externes. La méthode recommandée de l’utilisation est à l’aide de bibliothèques externes. Pour faciliter la création d’une bibliothèque externe à partir de votre fichier jar, consultez [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)

Si vous n’utilisez pas les bibliothèques externes, vous devez fournir à SQL Server avec les autorisations d’exécution des classes Java dans votre fichier jar.

Pour accorder un en lecture et exécution d’accès à un fichier jar, exécutez la commande suivante **chmod** commande sur le fichier jar. Nous vous recommandons de toujours placer vos fichiers de classe dans un fichier jar, lorsque vous travaillez avec SQL Server. Pour créer un fichier jar, consultez [la création d’un fichier jar](#create-jar).

```cmd
chmod ug+rx <MyJarFile.jar>
```

Vous devez également accorder les autorisations de mssql_satellite le fichier jar à lecture/exécution.

```cmd
chown mssql_satellite:mssql_satellite <MyJarFile.jar>
```

<a name="install-on-windows"></a>

## <a name="install-on-windows"></a>Installer sur Windows

1. Vérifiez qu'une version prise en charge de Java est installée. Pour plus d’informations, consultez le [conditions préalables](#prerequisites).

2. [Exécutez le programme d’installation](../install/sql-machine-learning-services-windows-install.md) pour installer SQL Server 2019.

3. Lorsque vous accédez à la sélection de fonctionnalités, choisissez **Machine Learning Services (en base de données)**. 

   Bien que l’intégration Java n’est pas fourni avec les bibliothèques machine learning, il s’agit de l’option dans le programme d’installation qui fournit l’infrastructure d’extensibilité. Si vous le souhaitez, vous pouvez omettre R et Python.

4. Terminez l’Assistant installation et poursuivez avec les deux tâches.

### <a name="add-the-jrehome-variable"></a>Ajoutez la variable variable

Variable est une variable d’environnement qui spécifie l’emplacement de l’interpréteur Java. Dans cette étape, créez une variable d’environnement système pour elle sur Windows.

1. Recherchez et copiez le chemin d’accès de base de JRE (par exemple, `C:\Program Files\Zulu\zulu-8\jre\`).

    En fonction de votre distribution Java par défaut, votre emplacement du JDK ou JRE peut être différente de celle de l’exemple de chemin ci-dessus.
    Même si vous avez un JDK installé, vous avez souvent heures seront obtenir un sous-dossier JRE dans le cadre de cette installation, donc pointer vers le dossier de jre dans ce cas.
    L’extension Java essaye de charger le jvm.dll à partir du chemin d’accès % JRE_HOME%\bin\server.

2. Dans le panneau de configuration, ouvrez **système et sécurité**, ouvrez **système**, puis cliquez sur **propriétés système avancées**.

3. Cliquez sur **Variables d’environnement**.

4. Créer une nouvelle variable système pour `JRE_HOME` avec la valeur du chemin d’accès du JDK/JRE (trouvé à l’étape 1).

5. Redémarrez [Launchpad](../concepts/extensibility-framework.md#launchpad).

    1. Ouvrez le [Gestionnaire de configuration SQL Server](../../relational-databases/sql-server-configuration-manager.md).

    2. Sous SQL Server Services, cliquez sur SQL Server Launchpad et sélectionnez **redémarrer**.

<a name="perms-nonwindows"></a>

### <a name="grant-access-to-non-default-jre-folder-windows-only"></a>Accorder l’accès au dossier JRE non définis par défaut (Windows uniquement)

Si vous n’avez pas installé le JDK ou JRE sous program files, vous devez effectuer les étapes suivantes. Exécuter le **icacls** commandes à partir d’un *avec élévation de privilèges* ligne pour accorder l’accès à la **SQLRUsergroup** et comptes de service SQL Server (dans **ALL_APPLICATION_ PACKAGES**) pour accéder à l’environnement JRE. Les commandes seront de manière récursive accorder l’accès à tous les fichiers et dossiers situés sous le chemin d’accès du répertoire donné.

#### <a name="sqlrusergroup-permissions"></a>Autorisations SQLRUserGroup

Pour une instance nommée, ajoutez le nom de l’instance à SQLRUsergroup (par exemple, `SQLRUsergroupINSTANCENAME`).

```cmd
icacls "<PATH to JRE>" /grant "SQLRUsergroup":(OI)(CI)RX /T
```

Vous pouvez ignorer cette étape si vous avez installé le JDK/JRE dans le dossier par défaut sous program files sur Windows.

#### <a name="appcontainer-permissions"></a>Autorisations AppContainer

```cmd
icacls "PATH to JRE" /grant "ALL APPLICATION PACKAGES":(OI)(CI)RX /T
```

<a name="configure-script-execution"></a>

## <a name="configure-script-execution"></a>Configurer l’exécution du script

À ce stade, vous êtes presque prêt à exécuter du code Java sur Linux ou Windows. Comme dernière étape, basculez vers SQL Server Management Studio, studio de données Azure, SQL CMD ou un autre outil qui vous permet d’exécuter le script Transact-SQL pour permettre l’exécution du script externe.

  ```sql
  EXEC sp_configure 'external scripts enabled', 1
  RECONFIGURE WITH OVERRIDE
-- No restart is required after this step as of SQl Server 2019
 ```

## <a name="verify-installation"></a>Vérifier l'installation

Pour vérifier l’installation est opérationnelle, créer et exécuter un [exemple d’application](java-first-sample.md) à l’aide de l’exécution de Java que vous venez d’installez et ajouté à la variable.

## <a name="differences-in-ctp-25"></a>Différences dans les CTP 2.5

Si vous êtes déjà familiarisé avec les Services Machine Learning, le modèle d’autorisation et d’isolation pour les extensions a changé dans cette version. Pour plus d’informations, consultez [différences dans une installation de Services de SQL Server Machine Learning 2019](../install/sql-machine-learning-services-ver15.md).

## <a name="limitations-in-ctp-25"></a>Limitations dans les CTP 2.5

* Le nombre de valeurs dans les tampons d’entrée et de sortie ne peut pas dépasser `MAX_INT (2^31-1)` puisque c’est le nombre maximal d’éléments qui peuvent être alloués dans un tableau en Java.

* Dans les paramètres de sortie [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) ne sont pas pris en charge dans cette version.

* Diffusion en continu à l’aide du paramètre sp_execute_external_script @r_rowsPerRead n’est pas pris en charge dans cette version CTP.

* Partitionnement à l’aide du paramètre sp_execute_external_script @input_data_1_partition_by_columns n’est pas pris en charge dans cette version CTP.

<a name="create-jar"></a>

## <a name="how-to-create-a-jar-file-from-class-files"></a>Comment créer un fichier jar à partir de fichiers de classe

Nous vous recommandons de toujours empaquetage vos fichiers de classe dans un fichier jar lors de l’exécution à partir de SQL Server.
Pour créer un fichier jar à partir de fichiers de classe, accédez au dossier contenant votre fichier de classe et exécutez la commande suivante :

```cmd
jar -cf <MyJar.jar> *.class
```

Assurez-vous que le chemin d’accès à **jar.exe** fait partie de la variable système path. Vous pouvez également spécifier le chemin complet vers le fichier jar qui se trouve sous "/ bin" dans le dossier JDK : `C:\Users\MyUser\Desktop\jdk1.8.0_201\bin\jar -cf <MyJar.jar> *.class`

## <a name="next-steps"></a>Étapes suivantes

+ [L’appel de Java dans SQL Server](howto-call-java-from-sql.md)
+ [Exemple Java dans SQL Server](java-first-sample.md)
+ [Extensibilité de Microsoft SDK pour Java pour Microsoft SQL Server](java-sdk.md)
+ [Types de données Java et SQL Server](java-sql-datatypes.md)
