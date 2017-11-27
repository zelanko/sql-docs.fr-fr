---
title: "Chargement de la sortie d’un Package Local | Documents Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: run-manage-packages-programmatically
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow [Integration Services], loading results
- loading data flow results
ms.assetid: aba8ecb7-0dcf-40d0-a2a8-64da0da94b93
caps.latest.revision: 66
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 41de742c987d9f043f3dd247ee84af6a3eaf365b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="loading-the-output-of-a-local-package"></a>Chargement de la sortie d'un package local
  Les applications clientes peuvent lire la sortie de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] lors de la sortie est enregistrée dans les packages [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destinations à l’aide de [!INCLUDE[vstecado](../../includes/vstecado-md.md)], ou lorsque la sortie est enregistrée vers une destination de fichier plat en utilisant les classes dans le **System.IO** espace de noms. Toutefois, une application cliente peut également lire directement la sortie d'un package dans la mémoire, sans avoir besoin d'étape intermédiaire pour rendre les données persistantes. La clé de cette solution est la **Microsoft.SqlServer.Dts.DtsClient** espace de noms qui contient des implémentations spécialisées de la **IDbConnection**, **IDbCommand**, et **IDbDataParameter** des interfaces à partir de la **System.Data** espace de noms. L’assembly Microsoft.SqlServer.Dts.DtsClient.dll est installé par défaut dans **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**.  
  
> [!NOTE]  
>  La procédure décrite dans cette rubrique requiert que la propriété DelayValidation de la tâche de flux de données et de tous les objets parents être définie à sa valeur par défaut **False**.  
  
## <a name="description"></a> Description  
 Cette procédure montre comment développer une application cliente en code managé qui charge directement la sortie d'un package avec une destination DataReader à partir de la mémoire. Les étapes résumées ici sont illustrées dans l'exemple de code qui suit.  
  
#### <a name="to-load-data-package-output-into-a-client-application"></a>Pour charger la sortie d'un package de données dans une application cliente  
  
1.  Dans le package, configurez une destination DataReader afin de recevoir la sortie que vous souhaitez lire dans l'application cliente. Donnez un nom descriptif à la destination DataReader, puisque vous l'utiliserez ultérieurement dans votre application cliente. Prenez note du nom de la destination DataReader.  
  
2.  Dans le projet de développement, définissez une référence à la **Microsoft.SqlServer.Dts.DtsClient** espace de noms en localisant l’assembly **Microsoft.SqlServer.Dts.DtsClient.dll**. Par défaut, cet assembly est installé dans **C:\Program Files\Microsoft SQL Server\100\DTS\Binn**. Importez l’espace de noms dans votre code à l’aide du langage c# **Using** ou [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] **importations** instruction.  
  
3.  Dans votre code, créez un objet de type **DtsClient.DtsConnection** avec une chaîne de connexion qui contient les paramètres de ligne de commande requis par **dtexec.exe** pour exécuter le package. Pour plus d’informations, voir [dtexec Utility](../../integration-services/packages/dtexec-utility.md). Ouvrez ensuite la connexion à l'aide de cette chaîne de connexion. Vous pouvez également utiliser le **dtexecui** l’utilitaire pour créer la chaîne de connexion requise visuellement.  
  
    > [!NOTE]  
    >  L'exemple de code montre le chargement du package à partir du système de fichiers en utilisant la syntaxe `/FILE <path and filename>`. Toutefois, vous pouvez également charger le package à partir de la base de données MSDB en utilisant la syntaxe `/SQL <package name>` ou à partir du magasin de packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en utilisant la syntaxe `/DTS \<folder name>\<package name>`.  
  
4.  Créer un objet de type **DtsClient.DtsCommand** qui utilise déjà créé **DtsConnection** et définir son **CommandText** nom à la propriété de la destination DataReader dans le package. Appelez ensuite la **ExecuteReader** méthode de l’objet de commande pour charger les résultats du package dans un nouveau DataReader.  
  
5.  Si vous le souhaitez, vous pouvez paramétrer indirectement la sortie du package à l’aide de la collection de **DtsDataParameter** des objets sur le **DtsCommand** objet pour passer des valeurs aux variables définies dans le package. Dans le package, vous pouvez utiliser ces variables comme paramètres de requête ou dans des expressions pour affecter les résultats retournés à la destination DataReader. Vous devez définir ces variables dans le package dans le **DtsClient** espace de noms avant que vous pouvez les utiliser avec le **DtsDataParameter** objet à partir d’une application cliente. (Vous devrez peut-être cliquer sur le **choisir les colonnes variables** bouton de barre d’outils dans le **Variables** fenêtre pour afficher le **Namespace** colonne.) Dans votre code client, lorsque vous ajoutez un **DtsDataParameter** à la **paramètres** collection de la **DtsCommand**, omettre la référence d’espace de noms DtsClient dans le nom de variable. Exemple :  
  
    ```  
    command.Parameters.Add(new DtsDataParameter("MyVariable", 1));  
    ```  
  
6.  Appelez le **en lecture** méthode du DataReader à plusieurs reprises selon les besoins pour parcourir les lignes de données de sortie. Utilisez les données, ou enregistrez-les à des fins d'utilisation ultérieure, dans l'application cliente.  
  
    > [!IMPORTANT]  
    >  Le **en lecture** méthode de cette implémentation du DataReader retourne **true** une nouvelle fois après la dernière ligne de données a été lu. Cela rend difficile à utiliser du code habituel qui effectue une itération sur le DataReader alors que **en lecture** retourne **true**. Si votre code essaie de fermer le DataReader ou la connexion après avoir lu le nombre estimé de lignes, sans un dernier appel supplémentaire à la **en lecture** (méthode), le code lève une exception non gérée. Toutefois, si votre code essaie de lire des données sur cette dernière itération dans une boucle, lorsque **en lecture** retourne toujours **true** , mais la dernière ligne a été passée, le code déclenchera une non gérée **ApplicationException** avec le message « le IDataReader SSIS est au-delà de la fin du jeu de résultats ». Ce comportement est différent de celui des autres implémentations DataReader. Par conséquent, lorsque vous utilisez une boucle pour lire les lignes du DataReader pendant que **en lecture** retourne **true**, dont vous avez besoin d’écrire du code pour intercepter, tester et ignorer ce anticipées **ApplicationException** sur le dernier appel réussi de la **en lecture** (méthode). Ou, si vous connaissez à l’avance le nombre de lignes que prévu, vous pouvez traiter les lignes et appelez ensuite la **en lecture** méthode une fois de plus avant de fermer le DataReader et la connexion.  
  
7.  Appelez le **Dispose** méthode de la **DtsCommand** objet. Cela est particulièrement important si vous avez utilisé des **DtsDataParameter** objets.  
  
8.  Fermez le DataReader et les objets de connexion.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant exécute un package qui calcule une valeur d'agrégation unique et qui enregistre cette valeur dans une destination DataReader, puis qui lit cette valeur depuis le DataReader et qui l'affiche dans une zone de texte sur un Windows Form.  
  
 L'utilisation de paramètres n'est pas requise lors du chargement de la sortie d'un package dans une application cliente. Si vous ne souhaitez pas utiliser un paramètre, vous pouvez omettre l’utilisation de la variable dans le **DtsClient** espace de noms, ainsi que le code qui utilise le **DtsDataParameter** objet.  
  
#### <a name="to-create-the-test-package"></a>Pour créer le package de test  
  
1.  Créez un nouveau package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. L'exemple de code utilise « DtsClientWParamPkg.dtsx » comme nom de package.  
  
2.  Ajoutez une variable de type Chaîne à l'espace de noms DtsClient. L'exemple de code utilise le pays comme nom de la variable. (Vous devrez peut-être cliquer sur le **choisir les colonnes variables** bouton de barre d’outils dans le **Variables** fenêtre pour afficher le **Namespace** colonne.)  
  
3.  Ajoutez un gestionnaire de connexions OLE DB qui se connecte à l'exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
4.  Ajoutez une tâche de flux de données au package et basculez vers l'aire de conception du flux de données.  
  
5.  Ajoutez une source OLE DB au flux de données et configurez-la afin d'utiliser le gestionnaire de connexions OLE DB créé précédemment, ainsi que la commande SQL suivante :  
  
    ```  
    SELECT * FROM Sales.vIndividualCustomer WHERE CountryRegionName = ?  
    ```  
  
6.  Cliquez sur **paramètres** et, dans le **définition des paramètres de requête** boîte de dialogue zone, mapper le paramètre d’entrée unique dans la requête, Parameter0, à la variable DtsClient::Country.  
  
7.  Ajoutez une transformation d'agrégation au flux de données et connectez la sortie de la source OLE DB à la transformation. Ouvrez l'Éditeur de transformation d'agrégation et configurez-le afin d'effectuer une opération « COUNT ALL » sur toutes les colonnes d'entrée (*) et de générer la sortie de la valeur agrégée avec l'alias CustomerCount.  
  
8.  Ajoutez une destination DataReader au flux de données et connectez la sortie de la transformation d'agrégation à la destination DataReader. L'exemple de code utilise « DataReaderDest » comme nom du DataReader. Sélectionnez l'unique colonne d'entrée disponible, CustomerCount, pour la destination.  
  
9. Enregistrez le package. L'application de test créée par la suite va exécuter le package et extraire directement sa sortie de la mémoire.  
  
#### <a name="to-create-the-test-application"></a>Pour créer l'application de test  
  
1.  Créez une nouvelle application Windows Forms.  
  
2.  Ajoutez une référence à la **Microsoft.SqlServer.Dts.DtsClient** espace de noms en naviguant jusqu'à l’assembly du même nom dans **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**.  
  
3.  Copiez et collez l'exemple de code suivant dans le module de code pour le formulaire.  
  
4.  Modifier la valeur de la **dtexecArgs** variable en fonction des besoins afin qu’elle contienne les paramètres de ligne de commande requis par **dtexec.exe** pour exécuter le package. L'exemple de code charge le package à partir du système de fichiers.  
  
5.  Modifier la valeur de la **dataReaderName** variable en fonction des besoins afin qu’elle contienne le nom de la destination DataReader dans le package.  
  
6.  Placez un bouton et une zone de texte sur le formulaire. L’exemple de code utilise **btnRun** en tant que le nom du bouton et **txtResults** comme nom de la zone de texte.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des différences entre l’exécution locale et à distance](../../integration-services/run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)   
 [Le chargement et l’exécution d’un Package Local par programme](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)   
 [Chargement et exécution d’un package distant par programmation](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
  
  

