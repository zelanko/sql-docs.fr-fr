---
title: Extension de langage Java dans SQL Server 2019 - SQL Server Machine Learning Services
description: Installer, configurer et valider l’extension du langage Java sur SQL Server 2019 pour les systèmes Linux et Windows.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/07/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a258573ff7506f2533c2f91edb5751cfd1121dc8
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53431713"
---
# <a name="java-language-extension-in-sql-server-2019"></a>Extension de langage Java dans SQL Server 2019 

À compter de la version préliminaire de SQL Server 2019 sur Windows et Linux, vous pouvez exécuter le code Java personnalisé dans le [infrastructure d’extensibilité](../concepts/extensibility-framework.md) comme module complémentaire pour l’instance du moteur de base de données. 

L’infrastructure d’extensibilité est une architecture pour l’exécution de code externe : Java (à partir de SQL Server 2019), [Python (à partir de SQL Server 2017)](../concepts/extension-python.md), et [R (à partir de SQL Server 2016)](../concepts/extension-r.md). L’exécution de code est isolée des processus de moteur de base, mais est entièrement intégrée à l’exécution des requêtes SQL Server. Cela signifie que vous pouvez transmettre des données à partir de n’importe quelle requête SQL Server à l’exécution externe et consommer ou conserver les résultats dans SQL Server.

Comme avec toute extension de langage de programmation, la procédure stockée système [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) est l’interface pour l’exécution de code Java précompilé.

## <a name="prerequisites"></a>Prérequis

Une instance de version préliminaire de SQL Server 2019 est nécessaire. Les versions antérieures n’ont pas d’intégration Java. 

Exigences de version de Java varient entre Windows et Linux. Java Runtime Environment (JRE) est la configuration minimale requise, mais le JDK est utiles si vous avez besoin du compilateur Java ou des packages de développement. Étant donné que le JDK est tout compris, si vous installez le JDK, JRE n’est pas nécessaire.

| Système d'exploitation | Version de Java | Téléchargement JRE | Téléchargement JDK |
|------------------|--------------|--------------|--------------|
| Windows          | 1.10         | [JRE 10](https://www.oracle.com/technetwork/java/javase/downloads/jre10-downloads-4417026.html) | [JDK 10](https://www.oracle.com/technetwork/java/javase/downloads/jdk10-downloads-4416644.html)  |
| Linux            | 1.8          |  [JRE 8](https://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html) | [JDK 8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  |  

Sur Linux, le **mssql-server-extensibilité-java** package installe automatiquement JRE 1.8 s’il n’est pas déjà installé. Scripts d’installation a également ajouter le chemin d’accès de la machine virtuelle Java pour une variable d’environnement appelée JAVA_HOME.

Sur Windows, nous vous recommandons d’installer le JDK sous la valeur par défaut /Program fichiers / dossiers si possible. Sinon, une configuration supplémentaire est nécessaire pour accorder des autorisations aux exécutables. Pour plus d’informations, consultez le [accorder des autorisations (Windows)](#perms-nonwindows) section dans ce document.

> [!Note]
> Étant donné que Java est une compatibilité descendante, les versions antérieures peuvent fonctionner, mais les versions prises en charge et testées pour cette première version CTP sont répertoriées dans le tableau.

<a name="install-on-linux"></a>

## <a name="install-on-linux"></a>Installer sur Linux

Vous pouvez installer le [de base de données du moteur et l’extension Java ensemble](../../linux/sql-server-linux-setup-machine-learning.md#install-all), ou ajouter la prise en charge de Java à une instance existante. Les exemples suivants ajouter l’extension de Java à une installation existante.  

```bash
# RedHat install commands
sudo yum install mssql-server-extensibility-java

# Ubuntu install commands
sudo apt-get install mssql-server-extensibility-java

# USE install commands
sudo zypper install mssql-server-extensibility-java
```

Lorsque vous installez **mssql-server-extensibilité-java**, le package installe automatiquement JRE 1.8 s’il n’est pas déjà installé. Il ajoute également le chemin d’accès de la machine virtuelle Java dans une variable d’environnement appelée JAVA_HOME.

Après avoir terminé l’installation, l’étape suivante consiste [configurer l’exécution du script externe](#configure-script-execution).

> [!Note]
> Sur un appareil connecté à internet, les dépendances de package sont téléchargés et installés dans le cadre de l’installation du package principal. Pour plus d’informations, notamment le programme d’installation hors connexion, consultez [installer SQL Server Machine Learning Services sur Linux](../../linux/sql-server-linux-setup-machine-learning.md).

### <a name="grant-permissions-on-linux"></a>Accorder des autorisations sur Linux

Pour fournir à SQL Server avec les autorisations d’exécution des classes Java, vous devez définir des autorisations.

Pour accorder en lecture et à l’exécution pour jar des fichiers ou des fichiers de classe, exécutez la commande suivante **chmod** commande sur chaque fichier de classe ou un fichier jar. Nous vous recommandons de placer vos fichiers de classe dans un fichier jar lorsque vous travaillez avec SQL Server. Pour créer un fichier jar, consultez [la création d’un fichier jar](#create-jar).

```cmd
chmod ug+rx <MyJarFile.jar>
```
Vous devez également accorder des autorisations de mssql_satellite sur le fichier du répertoire ou fichier jar à lecture/exécution.

* Si vous appelez des fichiers de classe à partir de SQL Server, mssql_satellite sera nécessaire en lecture / d’exécuter les autorisations sur *chaque* répertoire dans l’arborescence des dossiers, à partir de la racine vers le parent direct.

* Si vous appelez un fichier jar à partir de SQL Server, il suffit d’exécuter la commande sur le fichier jar lui-même.

```cmd
chown mssql_satellite:mssql_satellite <directory>
```

```cmd
chown mssql_satellite:mssql_satellite <MyJarFile.jar>
```

<a name="install-on-windows"></a>

## <a name="install-on-windows"></a>Installer sur Windows

1. [Exécutez le programme d’installation](../install/sql-machine-learning-services-windows-install.md) pour installer SQL Server 2019.

2. Lorsque vous accédez à la sélection de fonctionnalités, choisissez **Machine Learning Services (en base de données)**. 

   Bien que l’intégration Java n’est pas fourni avec les bibliothèques machine learning, il s’agit de l’option dans le programme d’installation qui fournit l’infrastructure d’extensibilité. Si vous le souhaitez, vous pouvez omettre R et Python.

3. Terminez l’Assistant installation et poursuivez avec les deux tâches.

### <a name="add-the-javahome-variable"></a>Ajoutez la variable JAVA_HOME

JAVA_HOME est une variable d’environnement qui spécifie l’emplacement de l’interpréteur Java. Dans cette étape, créez une variable d’environnement système pour elle sur Windows.

1. Recherchez et copiez le chemin d’installation de JDK/JRE (par exemple, C:\Program Files\Java\jdk-10.0.2).

  Dans CTP 2.0, définissant JAVA_HOME sur le dossier de base jdk ne fonctionne que pour Java 1.10. 

  Pour Java 1.8, étendre le chemin d’accès afin d’atteindre le jvm.dll sur Windows dans votre JDK (par exemple, « C:\Program Files\Java\jdk1.8.0_181\bin\server ». Vous pouvez également faire pointer vers un dossier de base de JRE : « C:\Program Files\Java\jre1.8.0_181 ».

2. Dans le panneau de configuration, ouvrez **système et sécurité**, ouvrez **système**, puis cliquez sur **propriétés système avancées**.

3. Cliquez sur **Variables d’environnement**.

4. Créer une nouvelle variable système pour JAVA_HOME.

   ![Variable d’environnement pour Java Home](../media/java/env-variable-java-home.png "le programme d’installation pour Java")

<a name="perms-nonwindows"></a>

### <a name="grant-access-to-non-default-jdk-folder-windows-only"></a>Accorder l’accès au dossier JDK non définis par défaut (Windows uniquement)

Vous pouvez ignorer cette étape si vous avez installé le JDK/JRE dans le dossier par défaut. 

Pour une installation de l’autre dossier, exécutez la **icacls** commandes à partir d’un *avec élévation de privilèges* ligne pour accorder l’accès à la **SQLRUsergroup** et comptes de service SQL Server (dans  **ALL_APPLICATION_PACKAGES**) pour accéder à la machine virtuelle Java et l’instruction classpath Java. Les commandes seront de manière récursive accorder l’accès à tous les fichiers et dossiers situés sous le chemin d’accès du répertoire donné.

#### <a name="sqlrusergroup-permissions"></a>Autorisations SQLRUserGroup

Pour une instance nommée, ajoutez le nom de l’instance à SQLRUsergroup (par exemple, `SQLRUsergroupINSTANCENAME`).

```cmd
icacls "<PATH TO CLASS or JAR FILES>" /grant "SQLRUsergroup":(OI)(CI)RX /T
```

#### <a name="appcontainer-permissions"></a>Autorisations AppContainer

```cmd
icacls "PATH to JDK/JRE" /grant "ALL APPLICATION PACKAGES":(OI)(CI)RX /T
```

### <a name="add-the-jre-path-to-javahome"></a>Ajouter le chemin d’accès JRE à JAVA_HOME
Vous devez également ajouter le chemin d’accès à l’environnement JRE dans la variable d’environnement JAVA_HOME système. Si vous avez uniquement un JRE installé, vous pouvez fournir le chemin d’accès du dossier JRE. Toutefois, si vous avez un JDK installé, vous devez fournir le chemin d’accès complet à la machine virtuelle Java, dans le dossier JRE sous JDK, comme suit : « C:\Program Files\Java\jdk1.8.0_191\jre\bin\server ».

Pour créer une variable système, utilisez le panneau de configuration > système et sécurité > système pour accéder à **propriétés système avancées**. Cliquez sur **Variables d’environnement** , puis créez une nouvelle variable système pour JAVA_HOME.

![Variable d’environnement pour Java Home](../media/java/env-variable-java-home.png "le programme d’installation pour Java")

<a name="configure-script-execution"></a>

## <a name="configure-script-execution"></a>Configurer l’exécution du script

À ce stade, vous êtes presque prêt à exécuter du code Java sur Linux ou Windows. Comme dernière étape, basculez vers SQL Server Management Studio ou un autre outil qui exécute le script Transact-SQL pour permettre l’exécution du script externe.

  ```sql
  EXEC sp_configure 'external scripts enabled', 1
  RECONFIGURE WITH OVERRIDE
-- No restart is required after this step as of SQl Server 2019
 ```

## <a name="verify-installation"></a>Vérifier l'installation

Pour vérifier l’installation est opérationnelle, créer et exécuter un [exemple d’application](java-first-sample.md) à l’aide du JDK que vous venez d’installer, en plaçant les fichiers dans le chemin de classe que vous avez configuré précédemment.

## <a name="differences-in-ctp-20"></a>Différences dans les CTP 2.0

Si vous êtes déjà familiarisé avec les Services Machine Learning, le modèle d’autorisation et d’isolation pour les extensions a changé dans cette version. Pour plus d’informations, consultez [différences dans une installation de Services de SQL Server Machine Learning 2019](../install/sql-machine-learning-services-ver15.md).

## <a name="limitations-in-ctp-20"></a>Limitations dans CTP 2.0

* Le nombre de valeurs dans les tampons d’entrée et de sortie ne peut pas dépasser `MAX_INT (2^31-1)` puisque c’est le nombre maximal d’éléments qui peuvent être alloués dans un tableau en Java.

* Dans les paramètres de sortie [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) ne sont pas pris en charge dans cette version.

* Aucune prise en charge du type de données LOB pour les jeux de données d’entrée et de sortie dans cette version. Consultez [types de données Java et SQL Server](java-sql-datatypes.md) pour plus d’informations sur les données dont les types sont pris en charge dans cette version CTP.

* Diffusion en continu à l’aide du paramètre sp_execute_external_script @r_rowsPerRead n’est pas pris en charge dans cette version CTP.

* Partitionnement à l’aide du paramètre sp_execute_external_script @input_data_1_partition_by_columns n’est pas pris en charge dans cette version CTP.

<a name="create-jar"></a>

## <a name="how-to-create-a-jar-file-from-class-files"></a>Comment créer un fichier jar à partir de fichiers de classe

Accédez au dossier contenant votre fichier de classe et exécutez la commande suivante :

```cmd
jar -cf <MyJar.jar> *.class
```

Assurez-vous que le chemin d’accès à **jar.exe** fait partie de la variable système path. Vous pouvez également spécifier le chemin complet vers le fichier jar qui se trouve sous "/ bin" dans le dossier JDK : `C:\Users\MyUser\Desktop\jdk-10.0.2\bin\jar -cf <MyJar.jar> *.class`

## <a name="next-steps"></a>Étapes suivantes

+ [L’appel de Java dans SQL Server](howto-call-java-from-sql.md)
+ [Exemple Java dans SQL Server](java-first-sample.md)
+ [Types de données Java et SQL Server](java-sql-datatypes.md)