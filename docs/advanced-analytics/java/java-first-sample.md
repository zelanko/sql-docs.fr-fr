---
title: Exemple de Java et didacticiel pour SQL Server 2019 - SQL Server Machine Learning Services
description: Exécutez l’exemple de code Java sur SQL Server 2019 pour apprendre les étapes pour l’utilisation de l’extension du langage Java avec les données de SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/23/2019
ms.topic: conceptual
author: nelgson
ms.author: negust
ms.reviewer: dphansen
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 000318716b07f58e94bd5c482d9c349e5d4e5481
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473769"
---
# <a name="sql-server-regex-java-sample"></a>Exemple d’expression régulière Java SQL Server

Cet exemple montre une classe Java qui reçoit les deux colonnes (ID et texte) à partir de SQL Server et également prend une expression régulière comme paramètre d’entrée. La classe retourne deux colonnes à SQL Server (ID et texte).

Pour un texte donné dans la colonne de texte envoyé à la classe Java, le code vérifie si l’expression régulière donnée est remplie et retourne ce texte avec l’ID d’origine. 

Cet exemple particulier utilise une expression régulière qui vérifie si un texte contient le mot « Java » ou « java ».

## <a name="microsoft-extensibility-sdk-for-java-for-microsoft-sql-server"></a>Extensibilité de Microsoft SDK pour Java pour Microsoft SQL Server

 Dans CTP 2.5, nous allons modifier le mode de qu'implémentation de code Java qui utilise l’extension du langage Java pour communiquer avec SQL Server. Ceci fournira une meilleure expérience de développeur lors de l’interaction avec SQL Server à partir de Java.

Sur le SDK, vous devez considérer comme une interface d’assistance, ce qui le rendre plus facile à implémenter le code Java en cours d’exécution par rapport à SQL Server.

> [!NOTE]
> L’introduction du kit SDK est un grand changement dans les CTP précédentes. Les exemples précédents vous aviez travail devra être mise à jour pour utiliser le SDK.

Pour plus d’informations, consultez le [documentation du SDK](java-sdk.md).

## <a name="prerequisites"></a>Prérequis

+ Instance du moteur de base de données de SQL Server 2019 avec l’infrastructure d’extensibilité et l’extension de programmation Java [sur Windows](../install/sql-machine-learning-services-windows-install.md) ou [sur Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-setup). Pour plus d’informations sur la configuration du système, consultez [extension de langage Java dans SQL Server 2019](extension-java.md). Pour plus d’informations sur les exigences de codage, consultez [l’appel de Java dans SQL Server](howto-call-java-from-sql.md).

+ SQL Server Management Studio ou Azure Data Studio pour l’exécution de T-SQL.

+ Java SE Development Kit (JDK) 8 ou JRE 8 Windows on ou Linux.

+ [Kit de développement de Microsoft Java d’extensibilité pour Microsoft SQL Server](http://aka.ms/mssql-java-lang-extension) mssql-java-lang-extension.jar.

À l’aide de la compilation de ligne de commande **javac** est suffisant pour ce didacticiel.

## <a name="1---create-sample-data-in-a-sql-server-table"></a>1 - créer des exemples de données dans une table SQL Server

Tout d’abord, créer et remplir un *testdata* table avec **ID** et **texte** colonnes. Se connecter à SQL Server et exécutez le script suivant pour créer une table :

```sql
CREATE DATABASE javatest
GO
USE javatest
GO

-- Create table for test data
DROP TABLE IF exists testdata;
GO

CREATE TABLE testdata(
id int NOT NULL,
"text" nvarchar(100) NOT NULL)
GO

TRUNCATE TABLE testdata
GO

-- Insert data into test table
INSERT INTO testdata(id, "text") VALUES (1, 'This sentence contains java')
INSERT INTO testdata(id, "text") VALUES (2, 'This sentence does not')
INSERT INTO testdata(id, "text") VALUES (3, 'I love Java!')
GO
Select * FROM testdata
```

## <a name="2---class-regexsamplejava"></a>2 - classe RegexSample.java

Commencez par créer la classe principale.

Dans cette étape, créez une classe appelée **RegexSample.java** et copiez le code Java suivant dans ce fichier.

Cette classe principale est l’importation du Kit de développement logiciel, ce qui signifie que le fichier jar téléchargé à l’étape 1 doit être détectable à partir de cette classe.

> [!NOTE]
> Notez que cette classe importe le package SDK d’extension Java.
Consultez l’article sur le [Microsoft extensibilité SDK pour Java pour Microsoft SQL Server](java-sdk.md) pour plus d’informations.

```java
package pkg;

import com.microsoft.sqlserver.javalangextension.PrimitiveDataset;
import com.microsoft.sqlserver.javalangextension.AbstractSqlServerExtensionExecutor;
import java.util.LinkedHashMap;
import java.util.LinkedList;
import java.util.ListIterator;
import java.util.regex.*;

public class RegexSample extends AbstractSqlServerExtensionExecutor {
    private Pattern expr;

    public RegexSample() {
        // Setup the expected extension version, and class to use for input and output dataset
        executorExtensionVersion = SQLSERVER_JAVA_LANG_EXTENSION_V1;
        executorInputDatasetClassName = PrimitiveDataset.class.getName();
        executorOutputDatasetClassName = PrimitiveDataset.class.getName();
    }
    
    public PrimitiveDataset execute(PrimitiveDataset input, LinkedHashMap<String, Object> params) {
        // Validate the input parameters and input column schema
        validateInput(input, params);

        int[] inIds = input.getIntColumn(0);
        String[] inValues = input.getStringColumn(1);
        int rowCount = inValues.length;

        String regexExpr = (String)params.get("regexExpr");
        expr = Pattern.compile(regexExpr);

        System.out.println("regex expression: " + regexExpr);

        // Lists to store the output data
        LinkedList<Integer> outIds = new LinkedList<Integer>();
        LinkedList<String> outValues = new LinkedList<String>();

        // Evaluate each row
        for(int i = 0; i < rowCount; i++) {
            if (check(inValues[i])) {
                outIds.add(inIds[i]);
                outValues.add(inValues[i]);
            }
        }

        int outputRowCount = outValues.size();

        int[] idOutputCol = new int[outputRowCount];
        String[] valueOutputCol = new String[outputRowCount];

        // Convert the list of output columns to arrays
        outValues.toArray(valueOutputCol);

        ListIterator<Integer> it = outIds.listIterator(0);
        int rowId = 0;

        System.out.println("Output data:");
        while (it.hasNext()) {
            idOutputCol[rowId] = it.next().intValue();

            System.out.println("ID: " + idOutputCol[rowId] + " Value: " + valueOutputCol[rowId]);
            rowId++;
        }

        // Construct the output dataset
        PrimitiveDataset output = new PrimitiveDataset();

        output.addColumnMetadata(0, "ID", java.sql.Types.INTEGER, 0, 0);
        output.addColumnMetadata(1, "Text", java.sql.Types.NVARCHAR, 0, 0);

        output.addIntColumn(0, idOutputCol, null);
        output.addStringColumn(1, valueOutputCol);

        return output;
    }

    private void validateInput(PrimitiveDataset input, LinkedHashMap<String, Object> params) {
        // Check for the regex expression input parameter
        if (params.get("regexExpr") == null) {
            throw new IllegalArgumentException("Input parameter 'regexExpr' is not found");
        }

        // The expected input schema should be at least 2 columns, (INTEGER, STRING)
        if (input.getColumnCount() < 2) {
            throw new IllegalArgumentException("Unexpected input schema, schema should be an (INTEGER, NVARCHAR or VARCHAR)");
        }

        // Check that the input column types are expected
        if (input.getColumnType(0) != java.sql.Types.INTEGER &&
                (input.getColumnType(1) != java.sql.Types.VARCHAR && input.getColumnType(1) == java.sql.Types.NVARCHAR )) {
            throw new IllegalArgumentException("Unexpected input schema, schema should be an (INTEGER, NVARCHAR or VARCHAR)");
        }
    }

    private boolean check(String text) {
        Matcher m = expr.matcher(text);

        return m.find();
    }
}
```

## <a name="3-compile-and-create-jar-file"></a>3 compiler et créer le fichier .jar

Nous recommandons que vous empaquetez vos classes et les dépendances dans les fichiers .jar. La plupart des environnements de développement Java tels que Eclipse ou IntelliJ prise en charge de génération des fichiers jar lorsque vous le projet de build/compilation. Dans cet exemple, nous avons nommé le fichier jar **regex.jar**.

Si vous créez manuellement un fichier .jar, vous pouvez suivre les étapes, consultez [la création d’un fichier jar](extension-java.md#create-jar).

> [!NOTE]
> Cet exemple est l’utilisation de packages, ce qui signifie que le package « pkg » dans l’angle supérieur de la classe permet de s’assurer que le code compilé est enregistré dans un sous-dossier appelé « pkg ». Cela est effectué automatiquement si vous utilisez un IDE, mais si vous compilez manuellement à l’aide des classes **javac**, vous devez placer le code compilé dans le sous-dossier pkg manuellement.

## <a name="4---create-external-libraries"></a>4 - créer des bibliothèques externes

En créant une bibliothèque externe, SQL Server auront automatiquement accès aux fichiers jar et vous n’avez pas besoin de définir des autorisations spéciales à l’instruction classpath.

Dans cet exemple, vous devez créer deux bibliothèques externes. Un pour le Kit de développement et un pour l’exemple d’expression régulière Java.

1.  Télécharger [Microsoft extensibilité SDK pour Java pour Microsoft SQL Server](http://aka.ms/mssql-java-lang-extension) mssql-java-lang-extension.jar.

1. Créer une bibliothèque externe pour le sdk

```sql
-- Create external library for the SDK
CREATE EXTERNAL LIBRARY sdk
FROM (CONTENT = '<path>/mssql-java-lang-extension.jar')
WITH (LANGUAGE = 'Java');
GO
```

3. Créer une bibliothèque externe pour l’exemple d’expression régulière

```sql
-- Create external library for the regex sample
CREATE EXTERNAL LIBRARY regex
FROM (CONTENT = '<path>/regex.jar')
WITH (LANGUAGE = 'Java');
GO
```

## <a name="5---set-permissions-skip-if-you-performed-step-4"></a>5 - définir des autorisations (ignorer si vous avez effectué l’étape 4)

Cette étape n’est pas nécessaire si vous utilisez des bibliothèques externes. La méthode recommandée de travail consiste à créer une bibliothèque externe à partir du fichier jar de vous.

Si vous ne souhaitez pas utiliser les bibliothèques externes, vous devez définir les autorisations nécessaires. L’exécution du script réussit uniquement si les identités de processus ont accès à votre code. Vous trouverez plus d’informations sur la définition des autorisations [ici](extension-java.md).

### <a name="on-linux"></a>Sur Linux

Accorder des autorisations de lecture et d’exécution sur le chemin de classe pour le **mssql_satellite** utilisateur.

### <a name="on-windows"></a>Sur Windows

Accorder des autorisations « Lecture et exécution » pour **SQLRUserGroup** et **tous les packages d’application** SID sur le dossier contenant votre code Java compilé. 

L’arborescence entière doit disposer des autorisations, à partir de la racine à la dernière sub dossier parent. 
 
1. Cliquez sur le dossier (par exemple, « C:\myJavaCode »), choisissez **propriétés** > **sécurité**.
2. Cliquez sur **Modifier**.
3. Cliquez sur **Ajouter**.
4. Dans **sélectionner des utilisateurs, ordinateur, les comptes de Service ou groupes**:
   + Cliquez sur **Types d’objets** et assurez-vous que *principes de sécurité intégrés* et *groupes* sont sélectionnés.
   + Cliquez sur **emplacements** pour sélectionner le nom de l’ordinateur local en haut de la liste.
5. Entrez **SQLRUserGroup**, vérifiez le nom, puis cliquez sur OK pour ajouter le groupe.
6. Entrez **tous les PACKAGES D’APPLICATION**, vérifiez le nom, puis cliquez sur OK pour ajouter. Si le nom ne se résout pas, revisiter l’étape d’emplacements. Le SID est local sur votre ordinateur.

Assurez-vous que les deux identités de sécurité ont des autorisations « Lecture et exécution » sur le dossier et un sous-dossier « pkg ».

<a name="call-method"></a>

## <a name="2---call-the-java-class"></a>2 - appel de la classe Java

Pour appeler le code Java à partir de SQL Server, nous allons créer une procédure stockée qui appelle sp_execute_external_script. Dans le paramètre « script », nous allons définir quel [package]. [classe] nous voulons appeler. Dans cet exemple, la classe appartient à un package appelé **pkg** et un fichier de classe appelé **RegexSample.java**.

> [!NOTE]
>Nous n'allons pas la définir la méthode à appeler. Par défaut, le **exécuter** méthode sera appelée. Cela signifie que vous devez suivre l’interface du Kit de développement logiciel et implémenter une méthode à exécuter dans votre classe Java, si vous souhaitez être en mesure d’appeler la classe à partir de SQL Server.

```sql
/*
This stored procedure takes an input query (input dataset) and a regular expression and returns the rows that fulfilled the given regular expression. This sample uses a regular expression that checks if a text contains the word "Java" or "java" ([Jj]ava) 
*/

CREATE OR ALTER PROCEDURE [dbo].[java_regex] @expr nvarchar(200), @query nvarchar(400)
AS
BEGIN
--Call the Java program by giving the package.className in @script
--The method invoked in the Java code is always the "execute" method
EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'pkg.RegexSample'
, @input_data_1 = @query
, @params = N'@regexExpr nvarchar(200)'
, @regexExpr = @expr
with result sets ((ID int, text nvarchar(100)));
END
GO

--Now execute the above stored procedure and provide the regular expression and an input query
EXECUTE [dbo].[java_regex] N'[Jj]ava', N'SELECT id, text FROM testdata'
GO
```

### <a name="results"></a>Résultats

Après l’exécution de l’appel, vous devez obtenir un jeu de résultats avec deux lignes.

![Résulte de l’exemple Java](../media/java/java-sample-results.png "exemple de résultats")

### <a name="if-you-get-an-error"></a>Si vous obtenez une erreur

+ Lorsque vous compilez vos classes, le sous-dossier « pkg » doit contenir le code compilé pour toutes les trois classes.

+ Enfin, si vous n’utilisez pas les bibliothèques externes, vérifiez les autorisations sur *chaque* dossier, à partir de la racine dans le sous-dossier « pkg », pour vous assurer que les identités de sécurité en cours d’exécution du processus externe sont autorisés à lire et exécuter votre code.

## <a name="next-steps"></a>Étapes suivantes

+ [Extensibilité de Microsoft SDK pour Java pour Microsoft SQL Server](java-sdk.md)
+ [L’appel de Java dans SQL Server](howto-call-java-from-sql.md)
+ [Extensions de Java dans SQL Server](extension-java.md)
+ [Types de données Java et SQL Server](java-sql-datatypes.md)
