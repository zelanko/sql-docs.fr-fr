---
title: Création d’une destination à l’aide du composant Script | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], destination components
- destinations [Integration Services], components
- input columns [Integration Services]
ms.assetid: 214e22e8-7e7d-4876-b690-c138e5721b81
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c20fbb5ade8d9ba37e463426cb49b2591b9da785
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85426976"
---
# <a name="creating-a-destination-with-the-script-component"></a>Création d'une destination à l'aide du composant Script
  Les composants de destination dans le flux de données d'un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] permettent d'enregistrer des données provenant de sources et de transformations en amont dans une source de données. En principe, le composant de destination se connecte à la source de données via un gestionnaire de connexions existant.

 Pour obtenir une vue d’ensemble du composant script, consultez [extension du workflow de données avec le composant Script] (. /extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md.

 Le composant Script et le code d'infrastructure qu'il génère simplifient considérablement le processus qui consiste à développer un composant de flux de données personnalisé. Toutefois, pour comprendre le fonctionnement du composant Script, il peut être utile de lire les étapes permettant de développer des composants de flux de données personnalisés dans la section [Développement d’un composant de flux de données personnalisé](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) et plus particulièrement [Développement d’un composant de destination personnalisé](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md).

## <a name="getting-started-with-a-destination-component"></a>Mise en route d'un composant de destination
 Lorsque vous ajoutez un composant Script à l’onglet Flux de données du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)], la boîte de dialogue **Sélectionner le type de composant de script** s’ouvre et vous invite à sélectionner un script de type **Source**, **Destination** ou **Transformation**. Dans cette boîte de dialogue, sélectionnez **Destination**.

 Ensuite, connectez la sortie d'une transformation au composant de destination dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)]. À des fins de test, vous pouvez connecter directement une source à une destination sans transformation.

## <a name="configuring-a-destination-component-in-metadata-design-mode"></a>Configuration d'un composant de destination en mode Création de métadonnées
 Après avoir sélectionné l’option de création d’un composant de destination, configurez le composant dans l’**Éditeur de transformation de script**. Pour plus d’informations, consultez [Configuration du composant Script dans l’éditeur de composant de script](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).

 Pour sélectionner le langage de script qui sera utilisé par le composant Script, vous devez définir la propriété **ScriptLanguage** dans la page **Script** de la boîte de dialogue **Éditeur de transformation de script**.

> [!NOTE]
>  Pour définir le langage de script par défaut du composant Script, utilisez l’option **Langage de script** dans la page **Général** de la boîte de dialogue **Options**. Pour plus d'informations, consultez [General Page](../general-page-of-integration-services-designers-options.md).

 Un composant de destination de flux de données possède une entrée et aucune sortie. La configuration de l’entrée du composant est l’une des étapes à exécuter en mode Création des métadonnées, à l’aide de l’**Éditeur de transformation de script**, avant d’écrire le script personnalisé.

### <a name="adding-connection-managers"></a>Ajout de gestionnaires de connexions
 En principe, une composant de destination utilise un gestionnaire de connexions existant pour se connecter à la source de données dans laquelle il enregistre les données du flux de données. Dans la page **Gestionnaires de connexions** de l' **Éditeur de transformation de script**, cliquez sur **Ajouter** pour ajouter le gestionnaire de connexions approprié.

 Toutefois, un gestionnaire de connexions n'est qu'une unité pratique qui permet d'encapsuler et de stocker les informations requises pour se connecter à une source de données d'un type particulier. Vous devez écrire votre propre code personnalisé pour charger ou enregistrer vos données et éventuellement ouvrir et fermer la connexion à la source de données.

 Pour obtenir des informations générales sur l’utilisation des gestionnaires de connexions avec le composant Script, consultez [Connexion aux sources de données dans le composant Script](../extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md).

 Pour plus d’informations sur la page **Gestionnaires de connexions** de l’**Éditeur de transformation de script**, consultez [Éditeur de transformation de script &#40;page Gestionnaires de connexions&#41;](../script-transformation-editor-connection-managers-page.md).

### <a name="configuring-inputs-and-input-columns"></a>Configuration d'entrées et de colonnes d'entrée
 Un composant de destination possède une entrée et aucune sortie.

 Dans la page **Colonnes d’entrée** de l’**Éditeur de transformation de script**, la liste des colonnes affiche les colonnes disponibles dans la sortie du composant en amont du flux de données. Sélectionnez les colonnes à enregistrer.

 Pour plus d’informations sur la page **Colonnes d’entrée** de l’**Éditeur de transformation de script**, consultez [Éditeur de transformation de script &#40;page Colonnes d’entrée&#41;](../script-transformation-editor-input-columns-page.md).

 La page **Entrées et sorties** de l’**Éditeur de transformation de script** affiche une seule entrée que vous pouvez renommer. La propriété d'accesseur créée dans le code généré automatiquement vous permet de référencer l'entrée dans le script par son nom.

 Pour plus d’informations sur la page **Entrées et sorties** de l’**Éditeur de transformation de script**, consultez [Éditeur de transformation de script &#40;page Entrées et sorties&#41;](../script-transformation-editor-inputs-and-outputs-page.md).

### <a name="adding-variables"></a>Ajout de variables
 Si vous souhaitez utiliser des variables existantes dans votre script, vous pouvez les ajouter dans les `ReadOnlyVariables` champs de propriété et dans `ReadWriteVariables` la page **script** de l **'éditeur de transformation de script**.

 Lorsque vous ajoutez plusieurs variables dans les champs de propriété, séparez les noms de variables par des virgules. Vous pouvez également sélectionner plusieurs variables en cliquant sur le bouton des points de suspension (**...**) en regard des `ReadOnlyVariables` `ReadWriteVariables` champs de propriété et, puis en sélectionnant les variables dans la boîte de dialogue **Sélectionner des variables** .

 Pour obtenir des informations générales sur l’utilisation de variables avec le composant Script, consultez [Utilisation de variables dans le composant Script](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).

 Pour plus d’informations sur la page **Script** de l’**Éditeur de transformation de script**, consultez [Éditeur de transformation de script &#40;page Script&#41;](../script-transformation-editor-script-page.md).

## <a name="scripting-a-destination-component-in-code-design-mode"></a>Script d'un composant de destination en mode Création de code
 Après avoir configuré les métadonnées du composant, vous pouvez écrire votre script personnalisé. Dans l’**Éditeur de transformation de script**, dans la page **Script**, cliquez sur **Modifier le script** pour ouvrir l’environnement de développement intégré [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) où vous pouvez ajouter votre script personnalisé. Le langage de script utilisé varie selon que vous avez sélectionné [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# comme langage de script pour la propriété **ScriptLanguage** dans la page **Script**.

 Pour obtenir des informations importantes concernant tous les types de composants créés à l’aide du composant Script, consultez [Codage et débogage du composant Script](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).

### <a name="understanding-the-auto-generated-code"></a>Fonctionnement du code généré automatiquement
 Lorsque vous ouvrez l'environnement de développement intégré VSTA après avoir créé et configuré un composant de destination, la classe `ScriptMain` modifiable apparaît dans l'éditeur de code avec un stub pour la méthode `ProcessInputRow`. La classe `ScriptMain` est l'emplacement où vous allez écrire votre code personnalisé, et `ProcessInputRow` est la méthode la plus importante d'un composant de destination.

 Si vous ouvrez la fenêtre **Explorateur de projets** dans VSTA, vous pouvez voir que le composant script a également généré des éléments de projet et en lecture seule `BufferWrapper` `ComponentWrapper` . La classe `ScriptMain` hérite de la classe `UserComponent` dans l'élément de projet `ComponentWrapper`.

 Au moment de l'exécution, le moteur de flux de données appelle la méthode `ProcessInput` dans la classe `UserComponent`, qui remplace la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> de la classe parente <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>. La méthode `ProcessInput` parcourt à son tour les lignes du tampon d'entrée et appelle la méthode `ProcessInputRow` une fois pour chaque ligne.

### <a name="writing-your-custom-code"></a>Écriture du code personnalisé
 Pour terminer de créer un composant de destination personnalisé, vous pouvez écrire le script dans les méthodes suivantes disponibles dans la classe `ScriptMain`.

1.  Substituez la méthode `AcquireConnections` pour vous connecter à la source de données externe. Extrayez l'objet de connexion, ou les informations de connexion requises, du gestionnaire de connexions.

2.  Substituez la méthode `PreExecute` pour vous préparer à enregistrer les données. Par exemple, vous pouvez créer et configurer un `SqlCommand` et ses paramètres dans cette méthode.

3.  Utilisez la méthode `ProcessInputRow` substituée pour copier chaque ligne d'entrée vers la source de données externe. Par exemple, pour une destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez copier les valeurs de colonne dans les paramètres de `SqlCommand` et exécuter la commande une fois pour chaque ligne. Pour une destination de fichier plat, vous pouvez écrire les valeurs de chaque colonne dans `StreamWriter`, en séparant les valeurs par le délimiteur de colonne.

4.  Substituez la méthode `PostExecute` pour vous déconnecter de la source de données externe, le cas échéant, et pour effectuer toute autre opération de nettoyage nécessaire.

## <a name="examples"></a>Exemples
 Les exemples suivants présentent le code requis dans la classe `ScriptMain` pour créer un composant de destination.

> [!NOTE]
>  Ces exemples utilisent la table **Person. Address** dans l' `AdventureWorks` exemple de base de données et transmettent ses première et quatrième colonnes, les colonnes **int * AddressID*** et **nvarchar (30) City** , par le biais du Workflow. Les mêmes données sont utilisées dans les exemples de source, transformation et destination de cette section. Des conditions préalables et des hypothèses supplémentaires sont documentées pour chaque exemple.

### <a name="adonet-destination-example"></a>Exemple de destination ADO.NET
 Cet exemple montre un composant de destination qui utilise un gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] existant pour enregistrer des données du flux de données dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

 Si vous souhaitez exécuter cet exemple de code, vous devez configurer le package et le composant comme suit :

1.  Créez un gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] qui utilise le fournisseur `SqlClient` pour se connecter à la base de données `AdventureWorks`.

2.  Créez une table de destination en exécutant la commande [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante dans la base de données `AdventureWorks` :

    ```
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL)
    ```

3.  Ajoutez un nouveau composant Script à l'aire du concepteur de flux de données et configurez-le en tant que destination.

4.  Connectez la sortie d'une source ou transformation en amont au composant de destination dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)]. (Vous pouvez connecter une source directement à une destination sans aucune transformation.) Cette sortie doit fournir les données de la table **Person. Address** de l' `AdventureWorks` exemple de base de données qui contient au moins les colonnes **AddressID** et **City** .

5.  Ouvrez l' **Éditeur de transformation de script**. Dans la page **Colonnes d’entrée**, sélectionnez les colonnes d’entrée **AddressID** et **City**.

6.  Dans la page **Entrées et sorties**, renommez l’entrée en lui attribuant un nom plus descriptif, comme **MyAddressInput**.

7.  Dans la page **Gestionnaires de connexions**, ajoutez ou créez le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] et attribuez-lui un nom, par exemple **MyADONETConnectionManager**.

8.  Dans la page **Script** , cliquez sur **Modifier le script** , puis entrez le script suivant. Ensuite, fermez l'environnement de développement de script.

9. Fermez l’**Éditeur de transformation de script** et exécutez l’exemple.

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

1.  Créez un gestionnaire de connexions de fichiers plats qui se connecte à un fichier de destination. Si le fichier n'existe pas, le composant de destination le crée. Configurez le fichier de destination en tant que fichier délimité par des virgules qui contient les colonnes **AddressID** et **City**.

2.  Ajoutez un nouveau composant Script à l'aire du concepteur de flux de données et configurez-le en tant que destination.

3.  Connectez la sortie d'une source ou transformation en amont au composant de destination dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)]. (Vous pouvez connecter une source directement à une destination sans aucune transformation.) Cette sortie doit fournir les données de la table **Person. Address** de l' `AdventureWorks` exemple de base de données et doit contenir au moins les colonnes **AddressID** et **City** .

4.  Ouvrez l' **Éditeur de transformation de script**. Dans la page **Colonnes d’entrée**, sélectionnez les colonnes **AddressID** et **City**.

5.  Dans la page **Entrées et sorties**, renommez l’entrée en lui attribuant un nom plus descriptif, comme **MyAddressInput**.

6.  Dans la page **Gestionnaires de connexions**, ajoutez ou créez le gestionnaire de connexions de fichiers plats et attribuez-lui un nom descriptif, par exemple **MyFlatFileDestConnectionManager**.

7.  Dans la page **Script** , cliquez sur **Modifier le script** , puis entrez le script suivant. Ensuite, fermez l'environnement de développement de script.

8.  Fermez l’**Éditeur de transformation de script** et exécutez l’exemple.

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

![Icône de Integration Services (petite)](../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.

## <a name="see-also"></a>Voir aussi
 [Création d’une source avec le composant script](../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md) [développement d’un composant de destination personnalisé](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)


