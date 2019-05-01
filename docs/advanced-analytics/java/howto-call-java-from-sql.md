---
title: L’appel de Java à partir de SQL - SQL Server Machine Learning Services
description: Découvrez comment appeler des classes Java à partir de procédures stockées SQL Server à l’aide de l’extension de langage dans SQL Server 2019 de programmation de Java.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/23/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a75878ccc4f14d03f84102dd48bfd43a6e04daea
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473557"
---
# <a name="how-to-call-java-from-sql-server-2019-preview"></a>L’appel de Java à partir de la version préliminaire de SQL Server 2019

Lorsque vous utilisez le [extension de langage Java](extension-java.md), le [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) système, procédure stockée est l’interface utilisée pour appeler le runtime Java. Autorisations sur la base de données s’appliquent à l’exécution de code Java.

Cet article explique les détails d’implémentation des méthodes qui s’exécutent sur SQL Server et les classes Java. Une fois que vous êtes familiarisé avec ces détails, passez en revue la [exemple Java](java-first-sample.md) l’étape suivante.

Il existe deux méthodes pour appeler des classes Java dans SQL Server :

1. Placez les fichiers .class ou .jar dans votre [classpath Java](#classpath). Il est disponible pour Windows et Linux.

2. Charger des classes compilées dans un fichier .jar et d’autres dépendances dans la base de données à l’aide de la [bibliothèque externe](#external-library) DDL. Cette option est disponible pour Windows et Linux à partir de CTP 2.4.

> [!NOTE]
> La recommandation générale, utiliser les fichiers .jar et .class pas les fichiers. Cela est courant dans Java et facilite l’expérience globale. Voir aussi : [Comment créer un fichier jar à partir de fichiers de classe](extension-java.md#create-jar).

<a name="classpath"></a>

## <a name="classpath"></a>Chemin de classe

### <a name="basic-principles"></a>Principes de base

* Des classes Java personnalisées compilées doivent exister dans les fichiers .class ou les fichiers .jar dans votre chemin de classe Java. Le [les paramètre CLASSPATH](#set-classpath) fournit le chemin d’accès aux fichiers Java compilés. 

* La méthode de Java que vous appelez doit être fournie dans le paramètre « script » sur la procédure stockée.

* Si la classe appartient à un package, le « packageName » doit être fourni.

* « params » est utilisé pour transmettre des paramètres à une classe Java. Appel d’une méthode qui requiert des arguments n'est pas pris en charge, ce qui rend les paramètres de la seule façon de passer des valeurs d’argument à votre méthode. 

> [!Note]
> Cette note reformule prises en charge et non pris en charge des opérations spécifiques à Java dans CTP 2.x.
> * Sur la procédure stockée, les paramètres d’entrée sont pris en charge. Paramètres de sortie ne sont pas.
> * Diffusion en continu à l’aide du paramètre sp_execute_external_script @r_rowsPerRead n’est pas pris en charge.
> * Partitionnement à l’aide de @input_data_1_partition_by_columns n’est pas pris en charge.
> * Parallèle à l’aide de traitement @parallel= 1 est prise en charge.

### <a name="call-java-class"></a>Appelez la classe Java

Applicable à Windows et Linux, le [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) système, procédure stockée est l’interface utilisée pour appeler le runtime Java. L’exemple suivant montre un sp_execute_external_script à l’aide de l’extension de Java et les paramètres pour spécifier le chemin d’accès, le script et votre code personnalisé.

> [!NOTE]
> Notez que vous n’avez pas besoin de définir la méthode à appeler. Par défaut, une méthode appelée **exécuter** est appelée. Cela signifie que vous devez suivre le Kit de développement et d’implémenter une méthode à exécuter dans votre classe Java.

```sql
DECLARE @param1 int
SET @param1 = 3

EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'<packageName>.<ClassName>'
, @input_data_1 = N'<Input Query>'
, @param1 = @param1
```

<a name="set-classpath"></a>

### <a name="set-classpath"></a>Définir le chemin de classe

Une fois que vous avez compilé votre classe Java ou les classes et créé un fichier jar dans votre chemin de classe Java, vous avez deux options pour fournir le chemin de classe pour l’extension de SQL Server Java :

**Option 1 : Utiliser des bibliothèques externes** l’option la plus simple consiste à apporter à SQL Server de trouver automatiquement vos classes en créant des bibliothèques externes et en pointant la bibliothèque vers un fichier jar. [Utiliser des bibliothèques externes pour Java](howto-call-java-from-sql.md#external-library)

**Option 2 : Inscrire une variable d’environnement système**

Tout comme vous avez créé une variable d’environnement système pour le runtime Java, vous pouvez créer une variable d’environnement système et fournir les chemins d’accès à votre fichier jar qui contient les classes. Pour ce faire, vous devez créer une variable d’environnement appelée « CLASSPATH ».

<a name="external-library"></a>

## <a name="external-library"></a>Bibliothèque externe

Dans SQL Server 2019 CTP 2.4, vous pouvez utiliser des bibliothèques externes pour le langage Java sur Windows et Linux. Vous pouvez compiler vos classes dans un fichier .jar et chargez le fichier .jar et les autres dépendances dans la base de données à l’aide de la [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) DDL.

Exemple montrant comment charger un fichier .jar avec bibliothèque externe :

```sql 
CREATE EXTERNAL LIBRARY myJar
FROM (CONTENT = '<local path to .jar file>') 
WITH (LANGUAGE = 'Java'); 
GO
```

En créant une bibliothèque externe, SQL Server auront automatiquement accès aux classes Java et vous n’avez pas besoin de définir des autorisations spéciales à l’instruction classpath.

Exemple d’appel d’une méthode dans une classe à partir d’un package téléchargé comme une bibliothèque externe :

```sql
EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'MyPackage.MyCLass'
, @input_data_1 = N'SELECT * FROM MYTABLE'
with result sets ((column1 int))
```

Pour plus d’informations, consultez [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="next-steps"></a>Étapes suivantes

+ [Exemple Java dans SQL Server](java-first-sample.md)
+ [Types de données Java et SQL Server](java-sql-datatypes.md)
+ [Extension de langage Java dans SQL Server](extension-java.md)
