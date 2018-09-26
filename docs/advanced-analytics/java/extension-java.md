---
title: Extension de langage Java dans SQL Server 2019 | Microsoft Docs
description: Exécuter du code Java sur SQL Server 2019 à l’aide de l’extension du langage Java.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8acb0a72435306cdec8740ffb41ff499eea61fac
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46714986"
---
# <a name="java-language-extension-in-sql-server-2019"></a>Extension de langage Java dans SQL Server 2019 

À compter de SQL Server 2019, vous pouvez exécuter le code Java personnalisé dans le [infrastructure d’extensibilité](../concepts/extensibility-framework.md) comme module complémentaire pour l’instance du moteur de base de données. 

L’infrastructure d’extensibilité est une architecture pour l’exécution de code externe : Java (à partir de SQL Server 2019), [Python (à partir de SQL Server 2017)](../concepts/extension-python.md), et [R (à partir de SQL Server 2016)](../concepts/extension-r.md). L’exécution de code est isolée des processus de moteur de base, mais est entièrement intégrée à l’exécution des requêtes SQL Server. Cela signifie que vous pouvez transmettre des données à partir de n’importe quelle requête SQL Server à l’exécution externe et consommer ou conserver les résultats dans SQL Server.

Comme avec toute extension de langage de programmation, la procédure stockée système [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) est l’interface pour l’exécution de code Java précompilé.

## <a name="1---feature-installation"></a>1 - installation de fonctionnalité

Exécutez le programme d’installation de SQL Server 2019 sur Windows ou Linux pour installer l’extension du langage Java. Une instance du moteur de base de données SQL Server 2019 est requise. Impossible d’ajouter l’intégration Java vers des versions antérieures.

Sur Windows, démarrez le [Assistant Installation](../install/sql-machine-learning-services-windows-install.md). Dans sélection de fonctionnalités, sélectionnez **Machine Learning Services (en base de données)**. Bien que l’intégration Java n’est pas fourni avec les bibliothèques machine learning, il s’agit de l’option dans le programme d’installation qui fournit l’infrastructure d’extensibilité. Si vous le souhaitez, vous pouvez omettre R et Python.

Sur Linux, installez le [moteur de base de données](https://docs.microsoft.com/sql/linux/sql-server-linux-setup), ainsi que le [package d’extensibilité et package d’extension Java](../../linux/sql-server-linux-setup-machine-learning.md).

Les exemples suivants illustrent la syntaxe pour chaque système d’exploitation Linux.

```bash
# RedHat install commands
sudo yum install mssql-server-extensibility
sudo yum install mssql-server-extensibility-java

# Ubuntu install commands
sudo apt-get install mssql-server-extensibility
sudo apt-get install mssql-server-extensibility-java

# USE install commands
sudo zypper install mssql-server-extensibility
sudo zypper install mssql-server-extensibility-java
```

## <a name="2---configuration"></a>2 - configuration

À l’aide de SQL Server Management Studio ou un autre outil qui exécute le script Transact-SQL, de configurer l’exécution du script externe sur l’instance du moteur de base de données.

  ```sql
  EXEC sp_configure 'external scripts enabled', 1
  RECONFIGURE WITH OVERRIDE
-- No restart is required after this step as of SQl Server 2019
 ```

## <a name="3---bring-your-own-java"></a>3 - mettre votre propre Java

Une différence précédente intégrations de langages tels que R et Python est que vous contrôlez qui JVM est utilisée avec SQL Server.

| Version de Java | Système d'exploitation |
|--------------|------------------|
| [Java 1.10](http://jdk.java.net/10/)   | Windows |
| Java 1.8   | Linux | 

Étant donné que Java est une compatibilité descendante, les versions antérieures peuvent fonctionner, mais les versions prises en charge et testées pour cette première version CTP sont répertoriées dans le tableau.

> [!Note]
>Pour exécuter Java avec SQL Server, vous techniquement suffit le [Java Runtime Environment](http://www.oracle.com/technetwork/java/javase/downloads/jre10-downloads-4417026.html) installé (JRE). Le JDK est un environnement de développement, y compris le compilateur Java et autres de développement de kit de lots associés. Si vous déjà un environnement de développement et devez uniquement un runtime Java sur l’ordinateur serveur, vous pouvez ignorer les instructions d’installation de JDK et uniquement installer JRE.

## <a name="jdk-on-windows"></a>JDK sur Windows

Télécharger la version Windows de le [Java SE Development Kit (JDK)](http://www.oracle.com/technetwork/java/javase/downloads/jdk10-downloads-4416644.html).

Installer le JDK sous la valeur par défaut des fichiers de /Program / de lecture de dossier si vous souhaitez éviter d’avoir à accorder l’autorisation de **tous les PACKAGES D’APPLICATION** et le **SQLRUserGroup** groupes de sécurité sur un autre emplacement . Les mêmes recommandations s’appliquent pour l’accès à vos dossiers de classpath Java, où vous conservez vos fichiers .class ou .jar. 

> [!Note]
> Le modèle d’autorisation et d’isolation pour les extensions a changé dans cette version. Pour plus d’informations, consultez [différences dans une installation de Services de SQL Server Machine Learning 2019](../install/sql-machine-learning-services-ver15.md).

<a name="perms-nonwindows"></a>

### <a name="grant-access-to-non-default-jdk-folder-windows-only"></a>Accorder l’accès au dossier JDK non définis par défaut (Windows uniquement)

Vous pouvez ignorer cette étape si vous avez installé le JDK/JRE dans le dossier par défaut. Pour une installation de l’autre dossier, exécutez les scripts PowerShell suivants pour accorder l’accès à la **SQLRUsergroup** et comptes de service SQL Server (dans ALL_APPLICATION_PACKAGES) pour accéder à la machine virtuelle Java et l’instruction classpath Java.

#### <a name="sqlrusergroup-permissions"></a>Autorisations SQLRUserGroup

```powershell
$Acl = Get-Acl "<YOUR PATH TO JDK / CLASSPATH>"
$Ar = New-Object  system.security.accesscontrol.filesystemaccessrule("SQLRUsergroup","FullControl","Allow")
$Acl.SetAccessRule($Ar)
Set-Acl ""<YOUR PATH TO JDK / CLASSPATH>" $Acl 
```

#### <a name="appcontainer-permissions"></a>Autorisations AppContainer

```powershell
$Acl = Get-Acl "<YOUR PATH TO JDK / CLASSPATH>" 
$Ar = New-Object  system.security.accesscontrol.filesystemaccessrule("ALL APPLICATION PACKAGES","FullControl","Allow") 
$Acl.SetAccessRule($Ar) 
Set-Acl "<YOUR PATH TO JDK / CLASSPATH>" $Acl 
```

### <a name="add-the-jdk-path-to-javahome"></a>Ajouter le chemin d’accès JDK à JAVA_HOME
Vous devez également ajouter le chemin d’installation de JDK/JRE (par exemple, « C:\Program Files\Java\jdk-10.0.2 ») à une variable d’environnement système que vous nommez « JAVA_HOME ». 

Pour créer une variable système, utilisez le panneau de configuration > système et sécurité > système pour accéder à **propriétés système avancées**. Cliquez sur **Variables d’environnement** , puis créez une nouvelle variable système pour JAVA_HOME.

![Variable d’environnement pour Java Home](../media/java/env-variable-java-home.png "le programme d’installation pour Java")

## <a name="jdk-on-linux"></a>JDK sur Linux

Sur Linux, le package mssql-server-extensibilité-java installe automatiquement JRE 1.8 s’il n’est pas déjà installé. Il ajoute également le chemin d’accès de la machine virtuelle Java dans une variable d’environnement appelée JAVA_HOME.

## <a name="limitations-in-ctp-20"></a>Limitations dans CTP 2.0

* Le nombre de valeurs dans les tampons d’entrée et de sortie ne peut pas dépasser `MAX_INT (2^31-1)` puisque c’est le nombre maximal d’éléments qui peuvent être alloués dans un tableau en Java.

* Paramètres de sortie dans sp_execute_external_script ne sont pas pris en charge dans cette version.

* Aucune prise en charge du type de données LOB pour les jeux de données d’entrée et de sortie dans cette version. Consultez [types de données Java et SQL Server](java-sql-datatypes.md) pour plus d’informations sur les données dont les types sont pris en charge dans cette version CTP.

* Diffusion en continu à l’aide du paramètre sp_execute_external_script @r_rowsPerRead n’est pas pris en charge dans cette version CTP.

* Partitionnement à l’aide du paramètre sp_execute_external_script @input_data_1_partition_by_columns n’est pas pris en charge dans cette version CTP.

## <a name="next-steps"></a>Étapes suivantes

+ [L’appel de Java dans SQL Server](howto-call-java-from-sql.md)
+ [Exemple Java dans SQL Server](java-first-sample.md)
+ [Types de données Java et SQL Server](java-sql-datatypes.md)