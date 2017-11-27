---
title: "Création d’une Destination avec le composant Script | Documents Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting-data-flow-script-component-types
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
helpviewer_keywords:
- Script component [Integration Services], destination components
- destinations [Integration Services], components
- input columns [Integration Services]
ms.assetid: 214e22e8-7e7d-4876-b690-c138e5721b81
caps.latest.revision: 57
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 7680aac73590f92eadd615b9d164967e61877664
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="creating-a-destination-with-the-script-component"></a>Création d'une destination à l'aide du composant Script
  Les composants de destination dans le flux de données d'un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] permettent d'enregistrer des données provenant de sources et de transformations en amont dans une source de données. En principe, le composant de destination se connecte à la source de données via un gestionnaire de connexions existant.  
  
 Pour une vue d’ensemble du composant Script, consultez [étendre le flux de données avec le composant Script](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
 Le composant Script et le code d'infrastructure qu'il génère simplifient considérablement le processus qui consiste à développer un composant de flux de données personnalisé. Toutefois, pour comprendre le fonctionnement du composant Script, vous pouvez s’avérer utile de consulter les étapes pour le développement d’un composants de flux de données personnalisées dans le [développer un composant de flux de données personnalisé](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) section et surtout [développer un composant de Destination personnalisé](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md).  
  
## <a name="getting-started-with-a-destination-component"></a>Mise en route d'un composant de destination  
 Lorsque vous ajoutez un composant de Script à l’onglet flux de données de [!INCLUDE[ssIS](../../includes/ssis-md.md)] concepteur, le **sélectionner le Type de composant Script** boîte de dialogue s’ouvre et vous invite à sélectionner un **Source**, **Destination**, ou **Transformation** script. Dans cette boîte de dialogue, sélectionnez **Destination**.  
  
 Ensuite, connectez la sortie d'une transformation au composant de destination dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)]. À des fins de test, vous pouvez connecter directement une source à une destination sans transformation.  
  
## <a name="configuring-a-destination-component-in-metadata-design-mode"></a>Configuration d'un composant de destination en mode Création de métadonnées  
 Après avoir sélectionné l’option pour créer un composant de destination, vous configurez le composant à l’aide de la **éditeur de Transformation de Script**. Pour plus d’informations, consultez [configuration du composant Script dans l’éditeur de composant Script](../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).  
  
 Pour sélectionner le langage de script qui utilise la destination de Script, vous définissez la **ScriptLanguage** propriété sur le **Script** page de la **éditeur de Transformation de Script** boîte de dialogue.  
  
> [!NOTE]  
>  Pour définir la valeur par défaut de langage de script par le composant de Script, utilisez la **langage de script** option sur le **général** page de la **Options** boîte de dialogue. Pour plus d'informations, consultez [General Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx).  
  
 Un composant de destination de flux de données possède une entrée et aucune sortie. Configuration de l’entrée du composant est une des étapes à exécuter en mode de création de métadonnées, à l’aide de la **éditeur de Transformation de Script**, avant d’écrire votre script personnalisé.  
  
### <a name="adding-connection-managers"></a>Ajout de gestionnaires de connexions  
 En principe, une composant de destination utilise un gestionnaire de connexions existant pour se connecter à la source de données dans laquelle il enregistre les données du flux de données. Dans la page **Gestionnaires de connexions** de l' **Éditeur de transformation de script**, cliquez sur **Ajouter** pour ajouter le gestionnaire de connexions approprié.  
  
 Toutefois, un gestionnaire de connexions n'est qu'une unité pratique qui permet d'encapsuler et de stocker les informations requises pour se connecter à une source de données d'un type particulier. Vous devez écrire votre propre code personnalisé pour charger ou enregistrer vos données et éventuellement ouvrir et fermer la connexion à la source de données.  
  
 Pour obtenir des informations générales sur l’utilisation des gestionnaires de connexions avec le composant Script, consultez [connexion aux Sources de données dans le composant Script](../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md).  
  
 Pour plus d’informations sur la **gestionnaires de connexions** page de la **éditeur de Transformation de Script**, consultez [éditeur de Transformation de Script &#40; Page gestionnaires de connexions &#41; ](../../integration-services/data-flow/transformations/script-transformation-editor-connection-managers-page.md).  
  
### <a name="configuring-inputs-and-input-columns"></a>Configuration d'entrées et de colonnes d'entrée  
 Un composant de destination possède une entrée et aucune sortie.  
  
 Sur le **colonnes d’entrée** page de la **éditeur de Transformation de Script**, la liste de colonnes affiche les colonnes disponibles à partir de la sortie du composant en amont du flux de données. Sélectionnez les colonnes à enregistrer.  
  
 Pour plus d’informations sur la **colonnes d’entrée** page de la **éditeur de Transformation de Script**, consultez [éditeur de Transformation de Script &#40; Page de colonnes d’entrée &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-input-columns-page.md).  
  
 Le **entrées et sorties** page de la **éditeur de Transformation de Script** affiche une seule entrée, vous pouvez renommer. La propriété d'accesseur créée dans le code généré automatiquement vous permet de référencer l'entrée dans le script par son nom.  
  
 Pour plus d’informations sur la **entrées et sorties** page de la **éditeur de Transformation de Script**, consultez [éditeur de Transformation de Script &#40; les entrées et sorties de Page &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-inputs-and-outputs-page.md).  
  
### <a name="adding-variables"></a>Ajout de variables  
 Si vous souhaitez utiliser des variables existantes dans votre script, vous pouvez les ajouter dans le **ReadOnlyVariables** et **ReadWriteVariables** des champs de propriété sur le **Script** page de la **éditeur de Transformation de Script**.  
  
 Lorsque vous ajoutez plusieurs variables dans les champs de propriété, séparez les noms de variables par des virgules. Vous pouvez également sélectionner plusieurs variables en cliquant sur le bouton de sélection (**...** ) situé en regard du **ReadOnlyVariables** et **ReadWriteVariables** champs de propriété, puis en sélectionnant les variables dans le **sélectionner des variables** boîte de dialogue.  
  
 Pour obtenir des informations générales sur l’utilisation de variables avec le composant Script, consultez [à l’aide de Variables dans le composant Script](../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).  
  
 Pour plus d’informations sur la **Script** page de la **éditeur de Transformation de Script**, consultez [éditeur de Transformation de Script &#40; Page script &#41; ](../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
## <a name="scripting-a-destination-component-in-code-design-mode"></a>Script d'un composant de destination en mode Création de code  
 Après avoir configuré les métadonnées du composant, vous pouvez écrire votre script personnalisé. Dans le **éditeur de Transformation de Script**, dans le **Script** , cliquez sur **modifier le Script** pour ouvrir le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE où vous pouvez ajouter votre script personnalisé. Le langage de script que vous utilisez varie selon que vous avez sélectionné [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual c# comme langage de script pour le **ScriptLanguage** propriété sur le **Script** page.  
  
 Pour obtenir des informations importantes qui s’applique à tous les types de composants créés à l’aide du composant Script, consultez [de codage et débogage du composant Script](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="understanding-the-auto-generated-code"></a>Fonctionnement du code généré automatiquement  
 Lorsque vous ouvrez l’IDE VSTA après avoir créé et configuré un composant de destination, le texte modifiable **ScriptMain** classe s’affiche dans l’éditeur de code avec un stub pour le **ProcessInputRow** (méthode). Le **ScriptMain** classe est l’emplacement où vous allez écrire votre code personnalisé, et **ProcessInputRow** est la méthode la plus importante dans un composant de destination.  
  
 Si vous ouvrez la fenêtre **Explorateur de projets** dans VSTA, vous constatez que le composant Script a également généré des éléments de projet **BufferWrapper** et **ComponentWrapper** en lecture seule. La classe **ScriptMain** hérite de la classe **UserComponent** dans l'élément de projet **ComponentWrapper** .  
  
 Au moment de l’exécution, le moteur de flux de données appelle la **ProcessInput** méthode dans le **UserComponent** classe, qui remplace le <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> méthode de la <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> classe parente. Le **ProcessInput** méthode parcourt à son tour les lignes dans la mémoire tampon d’entrée et appelle la **ProcessInputRow** méthode une fois pour chaque ligne.  
  
### <a name="writing-your-custom-code"></a>Écriture du code personnalisé  
 Pour terminer la création d’un composant de destination personnalisé, vous souhaiterez écrire le script dans les méthodes suivantes disponibles dans le **ScriptMain** classe.  
  
1.  Substituez la méthode **AcquireConnections** pour vous connecter à la source de données externe. Extrayez l'objet de connexion, ou les informations de connexion requises, du gestionnaire de connexions.  
  
2.  Remplacer la **PreExecute** méthode de préparation enregistrer les données. Par exemple, vous voudrez créer et configurer un **SqlCommand** et ses paramètres dans cette méthode.  
  
3.  Utilisez la **ProcessInputRow** méthode pour copier chaque ligne d’entrée à la source de données externe. Par exemple, pour un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, vous pouvez copier les valeurs de colonne dans les paramètres d’un **SqlCommand** et exécutez la commande une fois pour chaque ligne. Pour une destination de fichier plat, vous pouvez écrire les valeurs pour chaque colonne à un **StreamWriter**, en le séparant les valeurs par le séparateur de colonnes.  
  
4.  Remplacer la **PostExecute** méthode pour vous déconnecter de la source de données externe, si nécessaire et pour effectuer le nettoyage nécessaire.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants montrent un code qui est requise dans le **ScriptMain** classe pour créer un composant de destination.  
  
> [!NOTE]  
>  Ces exemples utilisent la **Person.Address** de table dans le **AdventureWorks** exemple de base de données et transmettent ses première et quatrième colonnes, le  **int*AddressID*** et **nvarchar (30) Ville** colonnes, dans le flux de données. Les mêmes données sont utilisées dans les exemples de source, transformation et destination de cette section. Des conditions préalables et des hypothèses supplémentaires sont documentées pour chaque exemple.  
  
### <a name="adonet-destination-example"></a>Exemple de destination ADO.NET  
 Cet exemple montre un composant de destination qui utilise un fichier [!INCLUDE[vstecado](../../includes/vstecado-md.md)] Gestionnaire de connexions pour enregistrer les données du flux de données dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.  
  
 Si vous souhaitez exécuter cet exemple de code, vous devez configurer le package et le composant comme suit :  
  
1.  Créer un [!INCLUDE[vstecado](../../includes/vstecado-md.md)] Gestionnaire de connexions qui utilise le **SqlClient** fournisseur pour se connecter à la **AdventureWorks** base de données.  
  
2.  Créer une table de destination en exécutant la commande suivante [!INCLUDE[tsql](../../includes/tsql-md.md)] dans les **AdventureWorks** base de données :  
  
    ```sql
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
3.  Ajoutez un nouveau composant Script à l'aire du concepteur de flux de données et configurez-le en tant que destination.  
  
4.  Connectez la sortie d'une source ou transformation en amont au composant de destination dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)]. (Vous pouvez connecter directement une source à une destination sans transformation.) Cette sortie doit fournir des données à partir de la **Person.Address** table de la **AdventureWorks** base de données exemple contienne au moins les **AddressID** et **Ville** colonnes.  
  
5.  Ouvrez l' **Éditeur de transformation de script**. Sur le **des colonnes d’entrée** page, sélectionnez le **AddressID** et **Ville** colonnes d’entrée.  
  
6.  Sur le **entrées et sorties** page, renommez l’entrée avec un nom plus descriptif tel que **MyAddressInput**.  
  
7.  Sur le **gestionnaires de connexions** page, ajoutez ou créez le [!INCLUDE[vstecado](../../includes/vstecado-md.md)] Gestionnaire de connexions avec un nom tel que **MyADONETConnectionManager**.  
  
8.  Dans la page **Script** , cliquez sur **Modifier le script** , puis entrez le script suivant. Ensuite, fermez l'environnement de développement de script.  
  
9. Fermer le **éditeur de Transformation de Script** et exécuter l’exemple.  
  
```vb  
Imports System.Data.SqlClient  
...  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Dim connMgr As IDTSConnectionManager100  
    Dim sqlConn As SqlConnection  
    Dim sqlCmd As SqlCommand  
    Dim sqlParam As SqlParameter  
  
    Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
        connMgr = Me.Connections.MyADONETConnectionManager  
        sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)  
  
    End Sub  
  
    Public Overrides Sub PreExecute()  
  
        sqlCmd = New SqlCommand("INSERT INTO Person.Address2(AddressID, City) " & _  
            "VALUES(@addressid, @city)", sqlConn)  
        sqlParam = New SqlParameter("@addressid", SqlDbType.Int)  
        sqlCmd.Parameters.Add(sqlParam)  
        sqlParam = New SqlParameter("@city", SqlDbType.NVarChar, 30)  
        sqlCmd.Parameters.Add(sqlParam)  
  
    End Sub  
  
    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
        With sqlCmd  
            .Parameters("@addressid").Value = Row.AddressID  
            .Parameters("@city").Value = Row.City  
            .ExecuteNonQuery()  
        End With  
    End Sub  
  
    Public Overrides Sub ReleaseConnections()  
  
        connMgr.ReleaseConnection(sqlConn)  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System.Data.SqlClient;  
public class ScriptMain:  
    UserComponent  
  
{  
    IDTSConnectionManager100 connMgr;  
    SqlConnection sqlConn;  
    SqlCommand sqlCmd;  
    SqlParameter sqlParam;  
  
    public override void AcquireConnections(object Transaction)  
    {  
  
        connMgr = this.Connections.MyADONETConnectionManager;  
        sqlConn = (SqlConnection)connMgr.AcquireConnection(null);  
  
    }  
  
    public override void PreExecute()  
    {  
  
        sqlCmd = new SqlCommand("INSERT INTO Person.Address2(AddressID, City) " +  
            "VALUES(@addressid, @city)", sqlConn);  
        sqlParam = new SqlParameter("@addressid", SqlDbType.Int);  
        sqlCmd.Parameters.Add(sqlParam);  
        sqlParam = new SqlParameter("@city", SqlDbType.NVarChar, 30);  
        sqlCmd.Parameters.Add(sqlParam);  
  
    }  
  
    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
    {  
        {  
            sqlCmd.Parameters["@addressid"].Value = Row.AddressID;  
            sqlCmd.Parameters["@city"].Value = Row.City;  
            sqlCmd.ExecuteNonQuery();  
        }  
    }  
  
    public override void ReleaseConnections()  
    {  
  
        connMgr.ReleaseConnection(sqlConn);  
  
    }  
  
}  
```  
  
### <a name="flat-file-destination-example"></a>Exemple de destination de fichier plat  
 Cet exemple montre un composant de destination qui utilise un gestionnaire de connexions de fichiers plats existant pour enregistrer des données du flux de données dans un fichier plat.  
  
 Si vous souhaitez exécuter cet exemple de code, vous devez configurer le package et le composant comme suit :  
  
1.  Créez un gestionnaire de connexions de fichiers plats qui se connecte à un fichier de destination. Si le fichier n'existe pas, le composant de destination le crée. Configurer le fichier de destination en tant qu’un fichier délimité par des virgules qui contient le **AddressID** et **Ville** colonnes.  
  
2.  Ajoutez un nouveau composant Script à l'aire du concepteur de flux de données et configurez-le en tant que destination.  
  
3.  Connectez la sortie d'une source ou transformation en amont au composant de destination dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)]. (Vous pouvez connecter directement une source à une destination sans transformation.) Cette sortie doit fournir des données à partir de la **Person.Address** table de la **AdventureWorks** exemple de base de données et doit contenir au moins les **AddressID** et **Ville** colonnes.  
  
4.  Ouvrez l' **Éditeur de transformation de script**. Sur le **colonnes d’entrée** page, sélectionnez le **AddressID** et **Ville** colonnes.  
  
5.  Sur le **entrées et sorties** page, renommez l’entrée avec un nom plus descriptif, tel que **MyAddressInput**.  
  
6.  Sur le **gestionnaires de connexions** page, ajoutez ou créez la connexion de fichier plat manager avec un nom descriptif tel que **MyFlatFileDestConnectionManager**.  
  
7.  Dans la page **Script** , cliquez sur **Modifier le script** , puis entrez le script suivant. Ensuite, fermez l'environnement de développement de script.  
  
8.  Fermer le **éditeur de Transformation de Script** et exécuter l’exemple.  
  
```vb  
Imports System.IO  
...  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Dim copiedAddressFile As String  
    Private textWriter As StreamWriter  
    Private columnDelimiter As String = ","  
  
    Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
        Dim connMgr As IDTSConnectionManager100 = _  
            Me.Connections.MyFlatFileDestConnectionManager  
        copiedAddressFile = CType(connMgr.AcquireConnection(Nothing), String)  
  
    End Sub  
  
    Public Overrides Sub PreExecute()  
  
        textWriter = New StreamWriter(copiedAddressFile, False)  
  
    End Sub  
  
    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
        With textWriter  
            If Not Row.AddressID_IsNull Then  
                .Write(Row.AddressID)  
            End If  
            .Write(columnDelimiter)  
            If Not Row.City_IsNull Then  
                .Write(Row.City)  
            End If  
            .WriteLine()  
        End With  
  
    End Sub  
  
    Public Overrides Sub PostExecute()  
  
        textWriter.Close()  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System.IO;  
public class ScriptMain:  
    UserComponent  
  
{  
    string copiedAddressFile;  
    private StreamWriter textWriter;  
    private string columnDelimiter = ",";  
  
    public override void AcquireConnections(object Transaction)  
    {  
  
        IDTSConnectionManager100 connMgr = this.Connections.MyFlatFileDestConnectionManager;  
        copiedAddressFile = (string) connMgr.AcquireConnection(null);  
  
    }  
  
    public override void PreExecute()  
    {  
  
        textWriter = new StreamWriter(copiedAddressFile, false);  
  
    }  
  
    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
    {  
  
        {  
            if (!Row.AddressID_IsNull)  
            {  
                textWriter.Write(Row.AddressID);  
            }  
            textWriter.Write(columnDelimiter);  
            if (!Row.City_IsNull)  
            {  
                textWriter.Write(Row.City);  
            }  
            textWriter.WriteLine();  
        }  
  
    }  
  
    public override void PostExecute()  
    {  
  
        textWriter.Close();  
  
    }  
  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une Source avec le composant Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)   
 [Développement d’un composant de Destination personnalisé](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)  
  
  

