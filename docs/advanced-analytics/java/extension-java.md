---
title: Extension de langage Java dans SQL Server 2019 | Microsoft Docs
description: Exécuter du code Java sur SQL Server 2019 à l’aide de l’extension du langage Java.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/12/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 2d69a255c56c3b15051a393b74eb1492a4f830f4
ms.sourcegitcommit: 93e3bb8941411b808e00daa31121367e96fdfda1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49359336"
---
# <a name="java-language-extension-in-sql-server-2019"></a>Extension de langage Java dans SQL Server 2019 

À compter de SQL Server 2019, vous pouvez exécuter le code Java personnalisé dans le [infrastructure d’extensibilité](../concepts/extensibility-framework.md) comme module complémentaire pour l’instance du moteur de base de données. 

L’infrastructure d’extensibilité est une architecture pour l’exécution de code externe : Java (à partir de SQL Server 2019), [Python (à partir de SQL Server 2017)](../concepts/extension-python.md), et [R (à partir de SQL Server 2016)](../concepts/extension-r.md). L’exécution de code est isolée des processus de moteur de base, mais est entièrement intégrée à l’exécution des requêtes SQL Server. Cela signifie que vous pouvez transmettre des données à partir de n’importe quelle requête SQL Server à l’exécution externe et consommer ou conserver les résultats dans SQL Server.

Comme avec toute extension de langage de programmation, la procédure stockée système [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) est l’interface pour l’exécution de code Java précompilé.

## <a name="prerequisites"></a>Prérequis

Un 2019 de serveur SQL est obligatoire. Les versions antérieures n’ont pas d’intégration Java. 

Exigences de version de Java varient entre Windows et Linux. Java Runtime Environment (JRE) est la configuration minimale requise, mais le JDK est utiles si vous avez besoin du compilateur Java ou des packages de développement. Étant donné que le JDK est tout compris, si vous installez le JDK, JRE n’est pas nécessaire.

| Système d'exploitation | Version de Java | Téléchargement JRE | Téléchargement JDK |
|------------------|--------------|--------------|--------------|
| Windows          | 1.10         | [JRE 10](http://www.oracle.com/technetwork/java/javase/downloads/jre10-downloads-4417026.html) | [JDK 10](http://www.oracle.com/technetwork/java/javase/downloads/jdk10-downloads-4416644.html)  |
| Linux            | 1.8          |  [JRE 8](https://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html) | [JDK 8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  |  

Sur Linux, le **mssql-server-extensibilité-java** package installe automatiquement JRE 1.8 s’il n’est pas déjà installé. Scripts d’installation a également ajouter le chemin d’accès de la machine virtuelle Java pour une variable d’environnement appelée JAVA_HOME.

Sur Windows, nous vous recommandons d’installer le JDK sous la valeur par défaut /Program fichiers / dossiers si possible. Sinon, une configuration supplémentaire est nécessaire pour accorder des autorisations aux exécutables. Pour plus d’informations, consultez le [accorder des autorisations (Windows)](#perms-nonwindows) section dans ce document.

> [!Note]
> Étant donné que Java est une compatibilité descendante, les versions antérieures peuvent fonctionner, mais les versions prises en charge et testées pour cette première version CTP sont répertoriées dans le tableau.

<a name="install-on-linux"></a>

## <a name="install-on-linux"></a>Installer sur Linux

Vous pouvez installer le [de base de données du moteur et l’extension Java ensemble](../../linux/sql-server-linux-setup-machine-learning.md#chained-installation), ou ajouter la prise en charge de Java à une instance existante. Les exemples suivants ajouter l’extension de Java à une installation existante.  

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

### <a name="grant-permissions-to-java-executables"></a>Accorder des autorisations pour des exécutables de Java

Par défaut, le compte sous lequel exécutent des processus externes n’a pas accès aux fichiers JRE ou JDK. Dans cette section, exécutez le script PowerShell suivant pour accorder des autorisations pour autoriser l’accès.

1. Recherchez et copiez l’emplacement de l’installation de JDK ou JRE. Par exemple, il peut être C:\Program Files\Java\jdk-10.0.2.

2. Ouvrez PowerShell avec des droits d’administrateur. Si vous n’êtes pas familiarisé avec cette tâche, consultez [cet article](https://www.top-password.com/blog/5-ways-to-run-powershell-as-administrator-in-windows-10/) pour obtenir des conseils.

3. Exécutez le script suivant pour accorder **SQLRUserGroup** autorisations pour les exécutables de Java. 

  **SQLRUserGroup** spécifie les autorisations sous les exécuter des processus externes. Par défaut, les membres de ce groupe sont autorisés à R Python des fichiers programme et installés par SQL Server, mais pas de Java. Pour exécuter des exécutables de Java, vous devez donner **SQLRUserGroup** autorisé à le faire.

   ```powershell
   $Acl = Get-Acl "<YOUR PATH TO JDK / CLASSPATH>"
   $Ar = New-Object  system.security.accesscontrol.filesystemaccessrule("SQLRUsergroup","FullControl","Allow")
   $Acl.SetAccessRule($Ar)
   Set-Acl "<YOUR PATH TO JDK / CLASSPATH>" $Acl 
   ```
4. Exécutez le script suivant pour accorder **tous les PACKAGES D’APPLICATION** également les autorisations. 

  Dans SQL Server 2019, conteneurs remplacement les comptes de travail en tant que le mécanisme d’isolation, avec les processus qui s’exécutent au sein de conteneurs, sous l’identité du compte de service Launchpad, qui est membre du **SQLRUserGroup**. Pour plus d’informations, consultez [installer de différences dans un 2019 de serveur SQL](../install/sql-machine-learning-services-ver15.md).

   ```powershell
   $Acl = Get-Acl "<YOUR PATH TO JDK / CLASSPATH>" 
   $Ar = New-Object  system.security.accesscontrol.filesystemaccessrule("ALL APPLICATION PACKAGES","FullControl","Allow") 
   $Acl.SetAccessRule($Ar) 
   Set-Acl "<YOUR PATH TO JDK / CLASSPATH>" $Acl 
   ```

5. Répétez les deux étapes précédentes sur les dossiers de classpath Java contenant les fichiers .class ou .jar que vous souhaitez exécuter sur SQL Server. Par exemple, si vous conservez vos programmes compilés dans un chemin d’accès comme C:\JavaPrograms\my-app, accorder **SQLRUserGroup** et **tous les PACKAGES D’APPLICATION** autorisation sur le dossier afin que les programmes peuvent être chargées.

  Veillez à accorder des autorisations sur le chemin d’accès complet, en commençant à partir du dossier racine. Autorisation sur simplement le dossier conteneur ne suffire pour le chargement de votre code.

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

## <a name="next-steps"></a>Étapes suivantes

+ [L’appel de Java dans SQL Server](howto-call-java-from-sql.md)
+ [Exemple Java dans SQL Server](java-first-sample.md)
+ [Types de données Java et SQL Server](java-sql-datatypes.md)