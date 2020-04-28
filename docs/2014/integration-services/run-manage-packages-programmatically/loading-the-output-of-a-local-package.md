---
title: Chargement de la sortie d’un package local | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow [Integration Services], loading results
- loading data flow results
ms.assetid: aba8ecb7-0dcf-40d0-a2a8-64da0da94b93
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 843c5e8cbb857271d4cbd07288e24bfbd98019e3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "78176619"
---
# <a name="loading-the-output-of-a-local-package"></a>Chargement de la sortie d'un package local
  Les applications clientes peuvent lire la sortie des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] quand la sortie est enregistrée dans les destinations [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] via [!INCLUDE[vstecado](../../includes/vstecado-md.md)], ou quand la sortie est enregistrée dans une destination de fichier plat à l’aide des classes présentes dans l’espace de noms **System.IO**. Toutefois, une application cliente peut également lire directement la sortie d'un package dans la mémoire, sans avoir besoin d'étape intermédiaire pour rendre les données persistantes. La clé de cette solution est l' `Microsoft.SqlServer.Dts.DtsClient` espace de noms, qui contient des implémentations `IDbConnection`spécialisées `IDbCommand`des interfaces, et **IDbDataParameter** de l’espace de noms **System. Data** . L’assembly Microsoft.SqlServer.Dts.DtsClient.dll est installé par défaut dans **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**.

> [!NOTE]
>  Conformément à la procédure décrite dans cette rubrique, la propriété DelayValidation de la tâche de flux de données et de tous les objets parents doit avoir la valeur par défaut **False**.

## <a name="description"></a>Description
 Cette procédure montre comment développer une application cliente en code managé qui charge directement la sortie d'un package avec une destination DataReader à partir de la mémoire. Les étapes résumées ici sont illustrées dans l'exemple de code qui suit.

#### <a name="to-load-data-package-output-into-a-client-application"></a>Pour charger la sortie d'un package de données dans une application cliente

1.  Dans le package, configurez une destination DataReader afin de recevoir la sortie que vous souhaitez lire dans l'application cliente. Donnez un nom descriptif à la destination DataReader, puisque vous l'utiliserez ultérieurement dans votre application cliente. Prenez note du nom de la destination DataReader.

2.  Dans le projet de développement, définissez une référence à `Microsoft.SqlServer.Dts.DtsClient` l’espace de noms en localisant l’assembly **Microsoft. SqlServer. Dts. DtsClient. dll**. Par défaut, cet assembly est installé dans **C:\Program Files\Microsoft SQL Server\100\DTS\Binn**. Importez l’espace de noms dans votre code `Using` à l' [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] `Imports` aide de l’instruction C# ou.

3.  Dans votre code, créez un objet de type `DtsClient.DtsConnection` avec une chaîne de connexion qui contient les paramètres de ligne de commande requis par **dtexec. exe** pour exécuter le package. Pour plus d'informations, consultez [Utilitaire dtexec](../packages/dtexec-utility.md). Ouvrez ensuite la connexion à l'aide de cette chaîne de connexion. Vous pouvez également vous servir de l’utilitaire **dtexecui** pour créer visuellement la chaîne de connexion nécessaire.

    > [!NOTE]
    >  L'exemple de code montre le chargement du package à partir du système de fichiers en utilisant la syntaxe `/FILE <path and filename>`. Toutefois, vous pouvez également charger le package à partir de la base de données MSDB en utilisant la syntaxe `/SQL <package name>` ou à partir du magasin de packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en utilisant la syntaxe `/DTS \<folder name>\<package name>`.

4.  Créez un objet de type `DtsClient.DtsCommand` qui utilise le `DtsConnection` créé précédemment et qui définit sa propriété `CommandText` sur le nom de la destination DataReader dans le package. Appelez ensuite la méthode `ExecuteReader` de l'objet de commande pour charger les résultats de package dans un nouveau DataReader.

5.  Vous pouvez éventuellement paramétrer indirectement la sortie du package en utilisant la collection d'objets `DtsDataParameter` sur l'objet `DtsCommand` pour passer des valeurs aux variables définies dans le package. Dans le package, vous pouvez utiliser ces variables comme paramètres de requête ou dans des expressions pour affecter les résultats retournés à la destination DataReader. Vous devez définir ces variables dans le package dans l’espace de noms **DtsClient** avant de pouvoir les utiliser `DtsDataParameter` avec l’objet à partir d’une application cliente. (Vous devrez peut-être cliquer sur le bouton de barre d’outils **choisir les colonnes de variables** dans la fenêtre **variables** pour afficher la colonne **espace de noms** .) Dans votre code client, lorsque vous ajoutez un `DtsDataParameter` à la `Parameters` collection de `DtsCommand`, omettez la référence d’espace de noms DtsClient à partir du nom de la variable. Par exemple :

    ```
    command.Parameters.Add(new DtsDataParameter("MyVariable", 1));
    ```

6.  Appelez la méthode `Read` du DataReader autant de fois que nécessaire pour faire une boucle dans les lignes de données de sortie. Utilisez les données, ou enregistrez-les à des fins d'utilisation ultérieure, dans l'application cliente.

    > [!IMPORTANT]
    >  La méthode `Read` de cette implémentation du DataReader retourne `true` une dernière fois une fois que la dernière ligne de données a été lue. Cela rend difficile l'utilisation du code habituel qui effectue une boucle dans le DataReader alors que `Read` retourne `true`. Si votre code essaie de fermer le DataReader ou la connexion après avoir lu le nombre attendu de lignes, sans un dernier appel supplémentaire de la méthode `Read`, le code déclenchera une exception non prise en charge. Toutefois, si votre code essaie de lire des données sur cette dernière itération via une boucle, lorsque `Read` retourne encore `true` mais que la dernière ligne est passée, le code déclenchera un `ApplicationException` non pris en charge avec le message : « SSIS IDataReader se trouve au-delà de la fin du jeu de résultats ». Ce comportement est différent de celui des autres implémentations DataReader. Par conséquent, lors de l'utilisation d'une boucle pour lire les lignes du DataReader pendant que `Read` retourne `true`, vous devez écrire le code de sorte à détecter, tester et ignorer ce `ApplicationException` anticipé sur le dernier appel réussi de la méthode `Read`. Ou, si vous connaissez à l'avance le nombre de lignes attendu, vous pouvez traiter les lignes, puis appeler la méthode `Read` une fois de plus avant de fermer le DataReader et la connexion.

7.  Appelez la méthode `Dispose` de l'objet `DtsCommand`. Cet appel s'avère particulièrement important si vous avez utilisé des objets `DtsDataParameter`.

8.  Fermez le DataReader et les objets de connexion.

## <a name="example"></a>Exemple
 L'exemple suivant exécute un package qui calcule une valeur d'agrégation unique et qui enregistre cette valeur dans une destination DataReader, puis qui lit cette valeur depuis le DataReader et qui l'affiche dans une zone de texte sur un Windows Form.

 L'utilisation de paramètres n'est pas requise lors du chargement de la sortie d'un package dans une application cliente. Si vous ne souhaitez pas utiliser un paramètre, vous pouvez omettre l’utilisation de la variable dans l’espace de noms **DtsClient** et omettre le code qui utilise l' `DtsDataParameter` objet.

#### <a name="to-create-the-test-package"></a>Pour créer le package de test

1.  Créez un nouveau package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. L'exemple de code utilise « DtsClientWParamPkg.dtsx » comme nom de package.

2.  Ajoutez une variable de type Chaîne à l'espace de noms DtsClient. L'exemple de code utilise le pays comme nom de la variable. (Vous pouvez être amené à cliquer sur le bouton de barre d’outils **Choisir les colonnes variables** dans la fenêtre **Variables** pour afficher la colonne **Espace de noms**.)

3.  Ajoutez un gestionnaire de connexions OLE DB qui se connecte à l'exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].

4.  Ajoutez une tâche de flux de données au package et basculez vers l'aire de conception du flux de données.

5.  Ajoutez une source OLE DB au flux de données et configurez-la afin d'utiliser le gestionnaire de connexions OLE DB créé précédemment, ainsi que la commande SQL suivante :

    ```
    SELECT * FROM Sales.vIndividualCustomer WHERE CountryRegionName = ?
    ```

6.  Cliquez `Parameters` sur et, dans la boîte de dialogue **définir les paramètres** de la requête, mappez le paramètre d’entrée unique dans la requête, Parameter0, à la variable DtsClient :: Country.

7.  Ajoutez une transformation d'agrégation au flux de données et connectez la sortie de la source OLE DB à la transformation. Ouvrez l’éditeur de transformation d’agrégation et configurez-le pour effectuer une opération « Count All » sur toutes les colonnes d’entrée (*) et pour générer la sortie de la valeur agrégée avec l’alias CustomerCount.

8.  Ajoutez une destination DataReader au flux de données et connectez la sortie de la transformation d'agrégation à la destination DataReader. L'exemple de code utilise « DataReaderDest » comme nom du DataReader. Sélectionnez l'unique colonne d'entrée disponible, CustomerCount, pour la destination.

9. Enregistrez le package. L'application de test créée par la suite va exécuter le package et extraire directement sa sortie de la mémoire.

#### <a name="to-create-the-test-application"></a>Pour créer l'application de test

1.  Créez une nouvelle application Windows Forms.

2.  Ajoutez une référence à l' `Microsoft.SqlServer.Dts.DtsClient` espace de noms en accédant à l’assembly portant le même nom dans **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**.

3.  Copiez et collez l'exemple de code suivant dans le module de code pour le formulaire.

4.  Modifiez la valeur de la `dtexecArgs` variable comme requis afin qu’elle contienne les paramètres de ligne de commande requis par **dtexec. exe** pour exécuter le package. L'exemple de code charge le package à partir du système de fichiers.

5.  Modifiez la valeur de la `dataReaderName` variable comme obligatoire afin qu’elle contienne le nom de la destination DataReader dans le package.

6.  Placez un bouton et une zone de texte sur le formulaire. L’exemple de code `btnRun` utilise comme nom du bouton et `txtResults` comme nom de la zone de texte.

7.  Exécutez l'application et cliquez sur le bouton. Après une brève pause pendant l'exécution du package, vous devez voir apparaître la valeur d'agrégation calculée par le package (le nombre de clients au Canada) dans la zone de texte sur le formulaire.

### <a name="sample-code"></a>Exemple de code

```vb
Imports System.Data
Imports Microsoft.SqlServer.Dts.DtsClient

Public Class Form1

  Private Sub btnRun_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnRun.Click

    Dim dtexecArgs As String
    Dim dataReaderName As String
    Dim countryName As String

    Dim dtsConnection As DtsConnection
    Dim dtsCommand As DtsCommand
    Dim dtsDataReader As IDataReader
    Dim dtsParameter As DtsDataParameter

    Windows.Forms.Cursor.Current = Cursors.WaitCursor

    dtexecArgs = "/FILE ""C:\...\DtsClientWParamPkg.dtsx"""
    dataReaderName = "DataReaderDest"
    countryName = "Canada"

    dtsConnection = New DtsConnection()
    With dtsConnection
      .ConnectionString = dtexecArgs
      .Open()
    End With

    dtsCommand = New DtsCommand(dtsConnection)
    dtsCommand.CommandText = dataReaderName

    dtsParameter = New DtsDataParameter("Country", DbType.String)
    dtsParameter.Direction = ParameterDirection.Input
    dtsCommand.Parameters.Add(dtsParameter)

    dtsParameter.Value = countryName

    dtsDataReader = dtsCommand.ExecuteReader(CommandBehavior.Default)

    With dtsDataReader
      .Read()
      txtResults.Text = .GetInt32(0).ToString("N0")
    End With

    'After reaching the end of data rows,
    ' call the Read method one more time.
    Try
      dtsDataReader.Read()
    Catch ex As Exception
      MessageBox.Show("Exception on final call to Read method:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception on final call to Read method", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    ' The following method is a best practice, and is
    '  required when using DtsDataParameter objects.
    dtsCommand.Dispose()

    Try
      dtsDataReader.Close()
    Catch ex As Exception
      MessageBox.Show("Exception closing DataReader:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception closing DataReader", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    Try
      dtsConnection.Close()
    Catch ex As Exception
      MessageBox.Show("Exception closing connection:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception closing connection", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    Windows.Forms.Cursor.Current = Cursors.Default

  End Sub

End Class
```

```csharp
using System;
using System.Windows.Forms;
using System.Data;
using Microsoft.SqlServer.Dts.DtsClient;

namespace DtsClientWParamCS
{
  public partial class Form1 : Form
  {
    public Form1()
    {
      InitializeComponent();
      this.btnRun.Click += new System.EventHandler(this.btnRun_Click);
    }

    private void btnRun_Click(object sender, EventArgs e)
    {
      string dtexecArgs;
      string dataReaderName;
      string countryName;

      DtsConnection dtsConnection;
      DtsCommand dtsCommand;
      IDataReader dtsDataReader;
      DtsDataParameter dtsParameter;

      Cursor.Current = Cursors.WaitCursor;

      dtexecArgs = @"/FILE ""C:\...\DtsClientWParamPkg.dtsx""";
      dataReaderName = "DataReaderDest";
      countryName = "Canada";

      dtsConnection = new DtsConnection();
      {
        dtsConnection.ConnectionString = dtexecArgs;
        dtsConnection.Open();
      }

      dtsCommand = new DtsCommand(dtsConnection);
      dtsCommand.CommandText = dataReaderName;

      dtsParameter = new DtsDataParameter("Country", DbType.String);
      dtsParameter.Direction = ParameterDirection.Input;
      dtsCommand.Parameters.Add(dtsParameter);

      dtsParameter.Value = countryName;

      dtsDataReader = dtsCommand.ExecuteReader(CommandBehavior.Default);

      {
        dtsDataReader.Read();
        txtResults.Text = dtsDataReader.GetInt32(0).ToString("N0");
      }

      //After reaching the end of data rows,
      // call the Read method one more time.
      try
      {
        dtsDataReader.Read();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception on final call to Read method:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception on final call to Read method", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      // The following method is a best practice, and is
      //  required when using DtsDataParameter objects.
      dtsCommand.Dispose();

      try
      {
        dtsDataReader.Close();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception closing DataReader:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception closing DataReader", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      try
      {
        dtsConnection.Close();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception closing connection:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception closing connection", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      Cursor.Current = Cursors.Default;

    }
  }
}
```

![Icône de Integration Services (petite)](../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.

## <a name="see-also"></a>Voir aussi
 [Comprendre les différences entre l’exécution locale et l’exécution distante et le](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) [chargement et l’exécution d’un package local par](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) programmation pour le [chargement et l’exécution d’un package distant](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)


