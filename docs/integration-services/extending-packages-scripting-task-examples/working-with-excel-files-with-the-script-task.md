---
title: "Utilisation des fichiers Excel avec la tâche de Script | Documents Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], Excel files
- Script task [Integration Services], examples
- Excel [Integration Services]
ms.assetid: b8fa110a-2c9c-4f5a-8fe1-305555640e44
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 46bf53c35663393ad600f02600961cf0295386bf
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="working-with-excel-files-with-the-script-task"></a>Utilisation de fichiers Excel avec la tâche de script
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] fournit le gestionnaire de connexions Excel, la source Excel et la destination Excel pour utiliser des données stockées dans des feuilles de calcul au format de fichier [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel. Les techniques décrites dans cette rubrique utilisent la tâche de script pour obtenir des informations sur les bases de données (fichiers de classeur) et tables (feuilles de calcul et plages nommées) Excel disponibles. Ces exemples peuvent être modifiés facilement afin d'utiliser l'une des autres sources de données basées sur des fichiers prises en charge par le fournisseur OLE DB [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet.  
  
 [Configuration d’un Package pour tester les exemples](#configuring)  
  
 [Exemple 1 : Vérifier l’existence d’un fichier Excel](#example1)  
  
 [Exemple 2 : Vérifier l’existence d’un tableau Excel](#example2)  
  
 [Exemple 3 : Obtenir la liste des fichiers Excel dans un dossier](#example3)  
  
 [Exemple 4 : Obtenir une liste de Tables dans un fichier Excel](#example4)  
  
 [Affichage des résultats des exemples](#testing)  
  
> [!NOTE]  
>  Si vous souhaitez créer une tâche plus facilement réutilisable sur plusieurs packages, envisagez d'utiliser le code indiqué dans l'exemple de tâche de script comme point de départ d'une tâche personnalisée. Pour plus d’informations, consultez [Développement d’une tâche personnalisée](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
##  <a name="configuring"></a>Configuration d’un Package pour tester les exemples  
 Vous pouvez configurer un package unique pour tester tous les exemples de cette rubrique. Les exemples utilisent de nombreuses variables de package et classes [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] identiques.  
  
#### <a name="to-configure-a-package-for-use-with-the-examples-in-this-topic"></a>Pour configurer un package à utiliser avec les exemples de cette rubrique  
  
1.  Créez un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] et ouvrez le package par défaut afin de le modifier.  
  
2.  **Variables**. Ouvrez le **Variables** fenêtre et définir les variables suivantes :  
  
    -   `ExcelFile`, de type **chaîne**. Entrez le chemin d'accès complet et le nom de fichier d'un classeur Excel existant.  
  
    -   `ExcelTable`, de type **chaîne**. Entrez le nom d'une feuille de calcul ou d'une plage nommée existante dans le classeur nommé dans la valeur de la variable `ExcelFile`. Cette valeur respecte la casse.  
  
    -   `ExcelFileExists`, de type **booléenne**.  
  
    -   `ExcelTableExists`, de type **booléenne**.  
  
    -   `ExcelFolder`, de type **chaîne**. Entrez le chemin d'accès complet d'un dossier qui contient au moins un classeur Excel.  
  
    -   `ExcelFiles`, de type **objet**.  
  
    -   `ExcelTables`, de type **objet**.  
  
3.  **Instructions Imports**. La plupart des exemples de code impliquent que vous importiez l'un des espaces de noms [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] suivants ou les deux au début de votre fichier de script :  
  
    -   **System.IO**, pour les opérations de système de fichiers.  
  
    -   **System.Data.OleDb**, pour ouvrir des fichiers Excel en tant que sources de données.  
  
4.  **Références**. Les exemples de code qui lisent des informations de schéma à partir de fichiers Excel requièrent une référence supplémentaire dans le projet de script pour le **System.Xml** espace de noms.  
  
5.  Définir le langage de script par défaut pour le composant de Script à l’aide de la **langage de script** option sur le **général** page de la **Options** boîte de dialogue. Pour plus d'informations, consultez [General Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx).  
  
##  <a name="example1"></a>Description de l’exemple 1 : Vérifier l’existence d’un fichier Excel  
 Cet exemple détermine si le fichier de classeur Excel spécifié dans la variable `ExcelFile` existe, puis définit la valeur booléenne de la variable `ExcelFileExists` sur le résultat. Vous pouvez utiliser cette valeur booléenne pour créer une branche dans le flux de travail du package.  
  
#### <a name="to-configure-this-script-task-example"></a>Pour configurer cet exemple de tâche de script  
  
1.  Ajouter une nouvelle tâche de Script au package et remplacez son nom par **ExcelFileExists**.  
  
2.  Dans le **éditeur de tâche de Script**, dans le **Script** , cliquez sur **ReadOnlyVariables** et entrez la valeur de propriété à l’aide d’une des méthodes suivantes :  
  
    -   Type **ExcelFile**.  
  
         -ou-  
  
    -   Cliquez sur le bouton de sélection (**...** ) bouton en regard du champ de propriété, puis dans le **sélectionner des variables** boîte de dialogue, sélectionnez le **ExcelFile** variable.  
  
3.  Cliquez sur **ReadWriteVariables** et entrez la valeur de propriété à l’aide d’une des méthodes suivantes :  
  
    -   Type **ExcelFileExists**.  
  
         -ou-  
  
    -   Cliquez sur le bouton de sélection (**...** ) bouton en regard du champ de propriété, puis dans le **sélectionner des variables** boîte de dialogue, sélectionnez le **ExcelFileExists** variable.  
  
4.  Cliquez sur **modifier le Script** pour ouvrir l’éditeur de script.  
  
5.  Ajouter un **importations** instruction pour le **System.IO** espace de noms en haut du fichier de script.  
  
6.  Ajoutez le code ci-dessous.  
  
### <a name="example-1-code"></a>Exemple 1 de Code  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim fileToTest As String  
  
    fileToTest = Dts.Variables("ExcelFile").Value.ToString  
    If File.Exists(fileToTest) Then  
      Dts.Variables("ExcelFileExists").Value = True  
    Else  
      Dts.Variables("ExcelFileExists").Value = False  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
  {  
    string fileToTest;  
  
    fileToTest = Dts.Variables["ExcelFile"].Value.ToString();  
    if (File.Exists(fileToTest))  
    {  
      Dts.Variables["ExcelFileExists"].Value = true;  
    }  
    else  
    {  
      Dts.Variables["ExcelFileExists"].Value = false;  
    }  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  }  
}  
```  
  
##  <a name="example2"></a>Description de l’exemple 2 : Vérifier l’existence d’un tableau Excel  
 Cet exemple détermine si la feuille de calcul ou la plage nommée Excel spécifiée dans la variable `ExcelTable` existe dans le fichier de classeur Excel spécifié dans la variable `ExcelFile`, puis définit la valeur booléenne de la variable `ExcelTableExists` sur le résultat. Vous pouvez utiliser cette valeur booléenne pour créer une branche dans le flux de travail du package.  
  
#### <a name="to-configure-this-script-task-example"></a>Pour configurer cet exemple de tâche de script  
  
1.  Ajouter une nouvelle tâche de Script au package et remplacez son nom par **ExcelTableExists**.  
  
2.  Dans le **éditeur de tâche de Script**, dans le **Script** , cliquez sur **ReadOnlyVariables** et entrez la valeur de propriété à l’aide d’une des méthodes suivantes :  
  
    -   Type **ExcelTable** et **ExcelFile** séparés par des virgules**.**  
  
         -ou-  
  
    -   Cliquez sur le bouton de sélection (**...** ) bouton en regard du champ de propriété, puis dans le **sélectionner des variables** boîte de dialogue, sélectionnez le **ExcelTable** et **ExcelFile** variables.  
  
3.  Cliquez sur **ReadWriteVariables** et entrez la valeur de propriété à l’aide d’une des méthodes suivantes :  
  
    -   Type **ExcelTableExists**.  
  
         -ou-  
  
    -   Cliquez sur le bouton de sélection (**...** ) bouton en regard du champ de propriété, puis dans le **sélectionner des variables** boîte de dialogue, sélectionnez le **ExcelTableExists** variable.  
  
4.  Cliquez sur **modifier le Script** pour ouvrir l’éditeur de script.  
  
5.  Ajoutez une référence à la **System.Xml** assembly dans le projet de script.  
  
6.  Ajouter **importations** instructions pour le **System.IO** et **System.Data.OleDb** espaces de noms en haut du fichier de script.  
  
7.  Ajoutez le code ci-dessous.  
  
### <a name="example-2-code"></a>Code de l’exemple 2  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim fileToTest As String  
    Dim tableToTest As String  
    Dim connectionString As String  
    Dim excelConnection As OleDbConnection  
    Dim excelTables As DataTable  
    Dim excelTable As DataRow  
    Dim currentTable As String  
  
    fileToTest = Dts.Variables("ExcelFile").Value.ToString  
    tableToTest = Dts.Variables("ExcelTable").Value.ToString  
  
    Dts.Variables("ExcelTableExists").Value = False  
    If File.Exists(fileToTest) Then  
      connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=" & fileToTest & _  
        ";Extended Properties=Excel 8.0"  
      excelConnection = New OleDbConnection(connectionString)  
      excelConnection.Open()  
      excelTables = excelConnection.GetSchema("Tables")  
      For Each excelTable In excelTables.Rows  
        currentTable = excelTable.Item("TABLE_NAME").ToString  
        If currentTable = tableToTest Then  
          Dts.Variables("ExcelTableExists").Value = True  
        End If  
      Next  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
    public void Main()  
        {  
            string fileToTest;  
            string tableToTest;  
            string connectionString;  
            OleDbConnection excelConnection;  
            DataTable excelTables;  
            string currentTable;  
  
            fileToTest = Dts.Variables["ExcelFile"].Value.ToString();  
            tableToTest = Dts.Variables["ExcelTable"].Value.ToString();  
  
            Dts.Variables["ExcelTableExists"].Value = false;  
            if (File.Exists(fileToTest))  
            {  
                connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" +  
                "Data Source=" + fileToTest + ";Extended Properties=Excel 8.0";  
                excelConnection = new OleDbConnection(connectionString);  
                excelConnection.Open();  
                excelTables = excelConnection.GetSchema("Tables");  
                foreach (DataRow excelTable in excelTables.Rows)  
                {  
                    currentTable = excelTable["TABLE_NAME"].ToString();  
                    if (currentTable == tableToTest)  
                    {  
                        Dts.Variables["ExcelTableExists"].Value = true;  
                    }  
                }  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
}  
```  
  
##  <a name="example3"></a>Description de l’exemple 3 : Obtenir la liste des fichiers Excel dans un dossier  
 Cet exemple remplit un tableau à l'aide de la liste des fichiers Excel détectés dans le dossier spécifié dans la valeur de la variable `ExcelFolder`, puis copie le tableau dans la variable `ExcelFiles`. Vous pouvez utiliser l'énumérateur Foreach à partir d'une variable pour parcourir les fichiers inclus dans le tableau.  
  
#### <a name="to-configure-this-script-task-example"></a>Pour configurer cet exemple de tâche de script  
  
1.  Ajouter une nouvelle tâche de Script au package et remplacez son nom par **GetExcelFiles**.  
  
2.  Ouvrez le **éditeur de tâche de Script**, dans le **Script** , cliquez sur **ReadOnlyVariables** et entrez la valeur de propriété à l’aide d’une des méthodes suivantes :  
  
    -   Type **ExcelFolder**  
  
         -ou-  
  
    -   Cliquez sur le bouton de sélection (**...** ) bouton en regard du champ de propriété, puis dans le **sélectionner des variables** boîte de dialogue, sélectionnez la variable ExcelFolder.  
  
3.  Cliquez sur **ReadWriteVariables** et entrez la valeur de propriété à l’aide d’une des méthodes suivantes :  
  
    -   Type **ExcelFiles**.  
  
         -ou-  
  
    -   Cliquez sur le bouton de sélection (**...** ) bouton en regard du champ de propriété, puis dans le **sélectionner des variables** boîte de dialogue, sélectionnez la variable ExcelFiles.  
  
4.  Cliquez sur **modifier le Script** pour ouvrir l’éditeur de script.  
  
5.  Ajouter un **importations** instruction pour le **System.IO** espace de noms en haut du fichier de script.  
  
6.  Ajoutez le code ci-dessous.  
  
### <a name="example-3-code"></a>Exemple 3 de Code  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Const FILE_PATTERN As String = "*.xls"  
  
    Dim excelFolder As String  
    Dim excelFiles As String()  
  
    excelFolder = Dts.Variables("ExcelFolder").Value.ToString  
    excelFiles = Directory.GetFiles(excelFolder, FILE_PATTERN)  
  
    Dts.Variables("ExcelFiles").Value = excelFiles  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
  {  
    const string FILE_PATTERN = "*.xls";  
  
    string excelFolder;  
    string[] excelFiles;  
  
    excelFolder = Dts.Variables["ExcelFolder"].Value.ToString();  
    excelFiles = Directory.GetFiles(excelFolder, FILE_PATTERN);  
  
    Dts.Variables["ExcelFiles"].Value = excelFiles;  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  }  
}  
```  
  
### <a name="alternate-solution"></a>Autre solution  
 Au lieu d'utiliser une tâche de script pour dresser la liste des fichiers Excel dans un tableau, vous pouvez également utiliser l'énumérateur ForEach File pour parcourir tous les fichiers Excel inclus dans un dossier. Pour plus d’informations, consultez [parcourir les fichiers Excel et les Tables à l’aide d’un conteneur de boucles Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md).  
  
##  <a name="example4"></a>Description de l’exemple 4 : Obtenir la liste des Tables dans un fichier Excel  
 Cet exemple remplit un tableau à l'aide de la liste des feuilles de calcul et plages nommées détectées dans le fichier de classeur Excel spécifié par la valeur de la variable `ExcelFile`, puis copie le tableau dans la variable `ExcelTables`. Vous pouvez utiliser l'énumérateur Foreach à partir d'une variable pour parcourir les tables incluses dans le tableau.  
  
> [!NOTE]  
>  La liste des tableaux d'un classeur Excel comprend à la fois les feuilles de calcul (affectées du suffixe $) et les plages nommées. Si vous devez filtrer la liste uniquement pour obtenir uniquement les feuilles de calcul ou les plages nommées, vous pouvez être amené à ajouter du code supplémentaire.  
  
#### <a name="to-configure-this-script-task-example"></a>Pour configurer cet exemple de tâche de script  
  
1.  Ajouter une nouvelle tâche de Script au package et remplacez son nom par **GetExcelTables**.  
  
2.  Ouvrez le **éditeur de tâche de Script**, dans le **Script** , cliquez sur **ReadOnlyVariables** et entrez la valeur de propriété à l’aide d’une des méthodes suivantes :  
  
    -   Type **ExcelFile**.  
  
         -ou-  
  
    -   Cliquez sur le bouton de sélection (**...** ) bouton en regard du champ de propriété, puis dans le **sélectionner des variables** boîte de dialogue, sélectionnez la variable ExcelFile.  
  
3.  Cliquez sur **ReadWriteVariables** et entrez la valeur de propriété à l’aide d’une des méthodes suivantes :  
  
    -   Type **ExcelTables**.  
  
         -ou-  
  
    -   Cliquez sur le bouton de sélection (**...** ) bouton en regard du champ de propriété, puis dans le **sélectionner des variables** boîte de dialogue, sélectionnez le ExcelTablesvariable.  
  
4.  Cliquez sur **modifier le Script** pour ouvrir l’éditeur de script.  
  
5.  Ajoutez une référence à la **System.Xml** espace de noms dans le projet de script.  
  
6.  Ajouter un **importations** instruction pour le **System.Data.OleDb** espace de noms en haut du fichier de script.  
  
7.  Ajoutez le code ci-dessous.  
  
### <a name="example-4-code"></a>Code de l'exemple 4  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim excelFile As String  
    Dim connectionString As String  
    Dim excelConnection As OleDbConnection  
    Dim tablesInFile As DataTable  
    Dim tableCount As Integer = 0  
    Dim tableInFile As DataRow  
    Dim currentTable As String  
    Dim tableIndex As Integer = 0  
  
    Dim excelTables As String()  
  
    excelFile = Dts.Variables("ExcelFile").Value.ToString  
    connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=" & excelFile & _  
        ";Extended Properties=Excel 8.0"  
    excelConnection = New OleDbConnection(connectionString)  
    excelConnection.Open()  
    tablesInFile = excelConnection.GetSchema("Tables")  
    tableCount = tablesInFile.Rows.Count  
    ReDim excelTables(tableCount - 1)  
    For Each tableInFile In tablesInFile.Rows  
      currentTable = tableInFile.Item("TABLE_NAME").ToString  
      excelTables(tableIndex) = currentTable  
      tableIndex += 1  
    Next  
  
    Dts.Variables("ExcelTables").Value = excelTables  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
        {  
            string excelFile;  
            string connectionString;  
            OleDbConnection excelConnection;  
            DataTable tablesInFile;  
            int tableCount = 0;  
            string currentTable;  
            int tableIndex = 0;  
  
            string[] excelTables = new string[5];  
  
            excelFile = Dts.Variables["ExcelFile"].Value.ToString();  
            connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" +  
                "Data Source=" + excelFile + ";Extended Properties=Excel 8.0";  
            excelConnection = new OleDbConnection(connectionString);  
            excelConnection.Open();  
            tablesInFile = excelConnection.GetSchema("Tables");  
            tableCount = tablesInFile.Rows.Count;  
  
            foreach (DataRow tableInFile in tablesInFile.Rows)  
            {  
                currentTable = tableInFile["TABLE_NAME"].ToString();  
                excelTables[tableIndex] = currentTable;  
                tableIndex += 1;  
            }  
  
            Dts.Variables["ExcelTables"].Value = excelTables;  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
}  
```  
  
### <a name="alternate-solution"></a>Autre solution  
 Au lieu d'utiliser une tâche de script pour dresser la liste des tables Excel dans un tableau, vous pouvez également utiliser l'énumérateur d'ensemble de lignes du schéma ADO.NET Foreach pour parcourir toutes les tables (autrement dit, les feuilles de calcul et les plages nommées) contenues dans un fichier de classeur Excel. Pour plus d’informations, consultez [parcourir les fichiers Excel et les Tables à l’aide d’un conteneur de boucles Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md).  
  
##  <a name="testing"></a>Affichage des résultats des exemples  
 Si vous avez configuré chacun des exemples de cette rubrique dans le même package, vous pouvez connecter toutes les tâches de script à une tâche de script supplémentaire qui affiche la sortie de tous les exemples.  
  
#### <a name="to-configure-a-script-task-to-display-the-output-of-the-examples-in-this-topic"></a>Pour configurer une tâche de script afin d'afficher la sortie des exemples de cette rubrique  
  
1.  Ajouter une nouvelle tâche de Script au package et remplacez son nom par **DisplayResults**.  
  
2.  Connectez chacune les quatre exemples tâches de Script à une autre, afin que chaque tâche s’exécute une fois la tâche précédente terminée et le quatrième exemple de tâche à la **DisplayResults** tâche.  
  
3.  Ouvrez le **DisplayResults** de tâches dans le **éditeur de tâche de Script**.  
  
4.  Sur le **Script** , cliquez sur **ReadOnlyVariables** et utilisez une des méthodes suivantes pour ajouter tous les sept variables répertoriées dans [configuration d’un Package pour tester les exemples](#configuring):  
  
    -   Tapez le nom de chaque variable en les séparant par des virgules.  
  
         -ou-  
  
    -   Cliquez sur le bouton de sélection (**...** ) bouton en regard du champ de propriété, puis dans le **sélectionner des variables** boîte de dialogue, sélectionnez les variables.  
  
5.  Cliquez sur **modifier le Script** pour ouvrir l’éditeur de script.  
  
6.  Ajouter **importations** instructions pour le **Microsoft.VisualBasic** et **System.Windows.Forms** espaces de noms en haut du fichier de script.  
  
7.  Ajoutez le code ci-dessous.  
  
8.  Exécutez le package et examinez les résultats qui s'affichent dans un message.  
  
### <a name="code-to-display-the-results"></a>Code permettant d'afficher les résultats  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Const EOL As String = ControlChars.CrLf  
  
    Dim results As String  
    Dim filesInFolder As String()  
    Dim fileInFolder As String  
    Dim tablesInFile As String()  
    Dim tableInFile As String  
  
    results = _  
      "Final values of variables:" & EOL & _  
      "ExcelFile: " & Dts.Variables("ExcelFile").Value.ToString & EOL & _  
      "ExcelFileExists: " & Dts.Variables("ExcelFileExists").Value.ToString & EOL & _  
      "ExcelTable: " & Dts.Variables("ExcelTable").Value.ToString & EOL & _  
      "ExcelTableExists: " & Dts.Variables("ExcelTableExists").Value.ToString & EOL & _  
      "ExcelFolder: " & Dts.Variables("ExcelFolder").Value.ToString & EOL & _  
      EOL  
  
    results &= "Excel files in folder: " & EOL  
    filesInFolder = DirectCast(Dts.Variables("ExcelFiles").Value, String())  
    For Each fileInFolder In filesInFolder  
      results &= " " & fileInFolder & EOL  
    Next  
    results &= EOL  
  
    results &= "Excel tables in file: " & EOL  
    tablesInFile = DirectCast(Dts.Variables("ExcelTables").Value, String())  
    For Each tableInFile In tablesInFile  
      results &= " " & tableInFile & EOL  
    Next  
  
    MessageBox.Show(results, "Results", MessageBoxButtons.OK, MessageBoxIcon.Information)  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
        {  
            const string EOL = "\r";  
  
            string results;  
            string[] filesInFolder;  
            //string fileInFolder;  
            string[] tablesInFile;  
            //string tableInFile;  
  
            results = "Final values of variables:" + EOL + "ExcelFile: " + Dts.Variables["ExcelFile"].Value.ToString() + EOL + "ExcelFileExists: " + Dts.Variables["ExcelFileExists"].Value.ToString() + EOL + "ExcelTable: " + Dts.Variables["ExcelTable"].Value.ToString() + EOL + "ExcelTableExists: " + Dts.Variables["ExcelTableExists"].Value.ToString() + EOL + "ExcelFolder: " + Dts.Variables["ExcelFolder"].Value.ToString() + EOL + EOL;  
  
            results += "Excel files in folder: " + EOL;  
            filesInFolder = (string[])(Dts.Variables["ExcelFiles"].Value);  
            foreach (string fileInFolder in filesInFolder)  
            {  
                results += " " + fileInFolder + EOL;  
            }  
            results += EOL;  
  
            results += "Excel tables in file: " + EOL;  
            tablesInFile = (string[])(Dts.Variables["ExcelTables"].Value);  
            foreach (string tableInFile in tablesInFile)  
            {  
                results += " " + tableInFile + EOL;  
            }  
  
            MessageBox.Show(results, "Results", MessageBoxButtons.OK, MessageBoxIcon.Information);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de connexions Excel](../../integration-services/connection-manager/excel-connection-manager.md)   
 [Effectuer une boucle dans des fichiers et des tables Excel en utilisant un conteneur de boucles Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
  
