---
title: Exemple de Java et didacticiel pour SQL Server 2019 - SQL Server Machine Learning Services
description: Exécutez l’exemple de code Java sur SQL Server 2019 pour apprendre les étapes pour l’utilisation de l’extension du langage Java avec les données de SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/27/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a2fd078d0b9c61678a83cc1b3b5da70adbd69779
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493424"
---
# <a name="sql-server-java-sample-walkthrough"></a>Exemple de procédure SQL Server Java

Cet exemple montre une classe Java qui reçoit les deux colonnes (ID et texte) à partir de SQL Server et retourne deux colonnes à SQL Server (ID et ngram). Pour une combinaison de chaîne et un ID donné, le code génère les permutations de ngrams (sous-chaînes), retour de ces permutations, ainsi que l’ID d’origine. La longueur de la ngram est définie par un paramètre envoyé à la classe Java.

## <a name="prerequisites"></a>Prérequis

+ Instance du moteur de base de données de SQL Server 2019 avec l’infrastructure d’extensibilité et l’extension de programmation Java [sur Windows](../install/sql-machine-learning-services-windows-install.md) ou [sur Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-setup). Pour plus d’informations sur la configuration du système, consultez [extension de langage Java dans SQL Server 2019](extension-java.md). Pour plus d’informations sur les exigences de codage, consultez [l’appel de Java dans SQL Server](howto-call-java-from-sql.md).

+ SQL Server Management Studio ou un autre outil pour l’exécution de T-SQL.

+ Java SE Development Kit (JDK) 8 sur Windows ou Linux.

À l’aide de la compilation de ligne de commande **javac** est suffisant pour ce didacticiel. 

## <a name="1---load-sample-data"></a>1 - charger des exemples de données

Tout d’abord, créer et remplir un *passe en revue* table avec **ID** et **texte** colonnes. Se connecter à SQL Server et exécutez le script suivant pour créer une table :

```sql
DROP TABLE IF exists reviews;
GO
CREATE TABLE reviews(
    id int NOT NULL,
    "text" nvarchar(30) NOT NULL)

INSERT INTO reviews(id, "text") VALUES (1, 'AAA BBB CCC DDD EEE FFF')
INSERT INTO reviews(id, "text") VALUES (2, 'GGG HHH III JJJ KKK LLL')
INSERT INTO reviews(id, "text") VALUES (3, 'MMM NNN OOO PPP QQQ RRR')
GO
```

## <a name="2---class-ngramjava"></a>2 - classe Ngram.java

Commencez par créer la classe principale. Il s’agit de la première des trois classes.

Dans cette étape, créez une classe appelée **Ngram.java** et copiez le code Java suivant dans ce fichier. 


```java
//We will package our classes in a package called pkg
//Packages are option in Java-SQL, but required for this sample.
package pkg;

import java.util.List;
import java.util.stream.Collectors;
import java.util.stream.IntStream;

public class Ngram {

    //Required: This is only required if you are passing data in @input_data_1
    //from SQL Server in sp_execute_external_script
    public static int[] inputDataCol1 = new int[1];
    public static String[] inputDataCol2 = new String[1];

    //Required: Input null map. Size just needs to be set to "1"
    public static boolean[][] inputNullMap = new boolean[1][1];

    //Required: Output data columns returned back to SQL Server
    public static int[] outputDataCol1;
    public static String[] outputDataCol2;

    //Required: Output null map. Is populated with true or false values 
    //to indicate nulls
    public static boolean[][] outputNullMap;

    //Optional: This is only required if parameters are passed with @params
    // from SQL Server in sp_execute_external_script
    // n is giving us the size of ngram substrings
    public static int param1;

    //Optional: The number of rows we will be returning
    public static int numberOfRows;

    //Required: Number of output columns returned
    public static short numberOfOutputCols;

    /*Java main method - Only for testing purposes outside of SQL Server
    public static void main(String... args) {
        //getNGrams();
    }*/

    //This is the method we will be calling from SQL Server
    public static void getNGrams() {

        System.out.println("inputDataCol1.length= "+ inputDataCol1.length);
        if (inputDataCol1.length == 0 ) {
            // TODO: Set empty return
            return;
        }
        //Using a stream to "loop" over the input data inputDataCol1.length. You can also use a for loop for this.
        final List<InputRow> inputDataSet = IntStream.range(0, inputDataCol1.length)
                .mapToObj(i -> new InputRow(inputDataCol1[i], inputDataCol2[i]))
                .collect(Collectors.toList());


        //Again, we are using a stream to loop over data
        final List<OutputRow> outputDataSet = inputDataSet.stream()
                // Generate ngrams of size n for each incoming string
                // Each invocation of ngrams returns a list. flatMap flattens
                // the resulting list-of-lists to a flat list.
                .flatMap(inputRow -> ngrams(param1, inputRow.text).stream().map(s -> new OutputRow(inputRow.id, s)))
                .collect(Collectors.toList());

        //Print the outputDataSet
        System.out.println(outputDataSet);

        //Set the number of rows and columns we will be returning
        numberOfOutputCols = 2;
        numberOfRows = outputDataSet.size();
        outputDataCol1 = new int[numberOfRows]; // ID column
        outputDataCol2 = new String[numberOfRows]; //The ngram column
        outputNullMap = new boolean[2][numberOfRows];// output null map

        //Since we don't have any null values, we will populate all values in the outputNullMap to false
        IntStream.range(0, numberOfRows).forEach(i -> {
            final OutputRow outputRow = outputDataSet.get(i);
            outputDataCol1[i] = outputRow.id;
            outputDataCol2[i] = outputRow.ngram;
            outputNullMap[0][i] = false;
            outputNullMap[1][i] = false;
        });
    }

    // Example: ngrams(3, "abcde") = ["abc", "bcd", "cde"].
    private static List<String> ngrams(int n, String text) {
        return IntStream.range(0, text.length() - n + 1)
                .mapToObj(i -> text.substring(i, i + n))
                .collect(Collectors.toList());
    }
}
```

## <a name="3---class-inputrowjava"></a>3 - classe InputRow.java

Créez une deuxième classe appelée **InputRow.java**, composé du code suivant et enregistrés dans le même emplacement que **Ngram.java**.

```java
package pkg;

//This object represents one input row
public class InputRow {
    public final int id;
    public final String text;

    public InputRow(final int id, final String text) {
        this.id = id;
        this.text = text;
    }
}
```

## <a name="4---class-outputrowjava"></a>4 - classe OutputRow.java

La troisième et dernière classe est appelée **OutputRow.java**. Copiez le code et les enregistrer en tant que OutputRow.java dans le même emplacement que les autres.

```java
package pkg;

//This object represents one output row
public class OutputRow {
    public final int id;
    public final String ngram;

    public OutputRow(final int id, final String ngram) {
        this.id = id;
        this.ngram = ngram;
    }

    @Override
    public String toString() { return id + ":" + ngram; }
}
```

## <a name="5---compile"></a>5 - compilation

Une fois que vos classes prêts, exécutez javac pour les compiler dans des fichiers « .class » (`javac Ngram.java InputRow.java OutputRow.java`). Vous devez obtenir trois fichiers .class pour cet exemple (Ngram.class InputRow.class et OutputRow.class).

Placez le code compilé dans un sous-dossier appelé « pkg » dans l’emplacement de chemin de classe. Si vous travaillez sur une station de travail de développement, cette étape est où vous copiez les fichiers à l’ordinateur SQL Server.

L’instruction classpath est l’emplacement du code compilé. Par exemple, sur Linux, si l’instruction classpath est « / home/myclasspath / », puis les fichiers .class doivent être dans « / home/myclasspath/pkg ». Dans l’exemple de script à l’étape 7, l’instruction CLASSPATH fourni dans le sp_execute_external_script est ' / home/myclasspath /' (en supposant que Linux). 

Sur Windows, nous recommandons l’utilisation d’un dossier relativement superficiel structure, un ou deux niveaux de profondeur, pour simplifier les autorisations. Par exemple, votre chemin de classe peut ressembler 'C:\myJavaCode' avec un sous-dossier appelé « \pkg » qui contient des classes compilées. 

Pour plus d’informations sur l’instruction classpath, consultez [définir le chemin de classe](howto-call-java-from-sql.md#set-classpath). 

### <a name="using-jar-files"></a>À l’aide de fichiers .jar

Si vous envisagez d’empaqueter vos classes et les dépendances dans les fichiers .jar, fournissez le chemin d’accès complet au fichier .jar dans le paramètre CLASSPATH de sp_execute_external_script. Par exemple, si le fichier jar est appelé « ngram.jar », le chemin de classe sera « / home/myclasspath/ngram.jar » sur Linux.

## <a name="6---create-external-library"></a>6 - créer une bibliothèque externe

En créant une bibliothèque externe, SQL Server auront automatiquement accès pour le fichier jar et vous n’avez pas besoin de définir des autorisations spéciales à l’instruction classpath.

```sql 
CREATE EXTERNAL LIBRARY ngram
FROM (CONTENT = '<path>/ngram.jar') 
WITH (LANGUAGE = 'Java'); 
GO
```

## <a name="7---set-permissions-skip-if-you-performed-step-6"></a>7 - définir des autorisations (ignorer si vous avez effectué l’étape 6)

Cette étape n’est pas nécessaire si vous utilisez des bibliothèques externes. La méthode recommandée de travail consiste à créer une bibliothèque externe à partir du fichier jar de vous. 

Si vous ne souhaitez pas utiliser les bibliothèques externes, vous devez définir les autorisations nécessaires. L’exécution du script réussit uniquement si les identités de processus ont accès à votre code. 

### <a name="on-linux"></a>Sur Linux

Accorder des autorisations de lecture et d’exécution sur le chemin de classe pour le **mssql_satellite** utilisateur.

### <a name="on-windows"></a>Sur Windows

Accorder des autorisations « Lecture et exécution » pour **SQLRUserGroup** et **tous les packages d’application** SID sur le dossier contenant votre code Java compilé. 

L’arborescence entière doit disposer des autorisations, à partir de la racine parent au dernier sous-dossier. 
 
1. Cliquez sur le dossier (par exemple, « C:\myJavaCode »), choisissez **propriétés** > **sécurité**.
2. Cliquez sur **Modifier**.
3. Cliquez sur **Ajouter**.
4. Dans **sélectionner des utilisateurs, ordinateur, les comptes de Service ou groupes**:
   + Cliquez sur **Types d’objets** et assurez-vous que *principes de sécurité intégrés* et *groupes* sont sélectionnés.
   + Cliquez sur **emplacements** pour sélectionner le nom de l’ordinateur local en haut de la liste.
5. Entrez **SQLRUserGroup**, vérifiez le nom, puis cliquez sur OK pour ajouter le groupe.
6. Entrez **tous les PACKAGES D’APPLICATION**, vérifiez le nom, puis cliquez sur OK pour ajouter. Si le nom ne se résout pas, revisiter l’étape d’emplacements. Le SID est local sur votre ordinateur.

Assurez-vous que les deux identités de sécurité ont des autorisations « Lecture et exécution » sur le dossier et un sous-dossier de « pkg ».

<a name="call-method"></a>

## <a name="8---call-getngrams"></a>8 - appel *getNgrams()*

Pour appeler le code à partir de SQL Server, spécifiez la méthode Java **getNgrams()** dans le paramètre « script » de sp_execute_external_script. Cette méthode appartient à un package appelé « pkg » et un fichier de classe appelé **Ngram.java**.

Cet exemple transmet le paramètre CLASSPATH pour fournir le chemin d’accès aux fichiers Java. Il utilise également « params » pour passer un paramètre à la classe Java. Assurez-vous que ce chemin de classe ne dépasse pas 30 caractères. Le cas échéant, augmentez la valeur dans le script ci-dessous.

+ Sur Linux, exécutez le code suivant dans SQL Server Management Studio ou un autre outil utilisé pour l’exécution de Transact-SQL. 

+ Sur Windows, remplacez @myClassPath à N'C:\myJavaCode\' (en supposant qu’il s’agit du dossier parent de \pkg) avant d’exécuter la requête dans SQL Server Management Studio ou un autre outil.

```sql
DECLARE @myClassPath nvarchar(50)
DECLARE @n int 
--This is where you store your classes or jars.
--This is the size of the ngram
SET @n = 3
EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'pkg.Ngram.getNGrams'
, @input_data_1 = N'SELECT id, text FROM reviews'
, @parallel = 0
, @params = N'@param1 INT'
, @param1 = @n
with result sets ((ID int, ngram varchar(20)))
GO
```

### <a name="results"></a>Résultats

Après l’exécution de l’appel, vous devez obtenir un jeu de résultats affichant les deux colonnes :

![Résulte de l’exemple Java](../media/java/java-sample-results.png "exemple de résultats")

### <a name="if-you-get-an-error"></a>Si vous obtenez une erreur

+ Lorsque vous compilez vos classes, le sous-dossier « pkg » doit contenir le code compilé pour toutes les trois classes.

+ La longueur du chemin de classe ne peut pas dépasser la valeur déclarée (`DECLARE @myClassPath nvarchar(50)`). Le cas échéant, le chemin d’accès est tronqué pour les 50 premiers caractères et votre code compilé ne sera pas chargé. Vous pouvez effectuer un `SELECT @myClassPath` pour vérifier la valeur. Augmentez la longueur si ne suffit pas 50 caractères. 

+ Enfin, vérifiez les autorisations sur *chaque* dossier, à partir de la racine dans le sous-dossier « pkg », pour vous assurer que les identités de sécurité en cours d’exécution du processus externe sont autorisés à lire et exécuter votre code.

## <a name="see-also"></a>Voir aussi

+ [L’appel de Java dans SQL Server](howto-call-java-from-sql.md)
+ [Extensions de Java dans SQL Server](extension-java.md)
+ [Types de données Java et SQL Server](java-sql-datatypes.md)
