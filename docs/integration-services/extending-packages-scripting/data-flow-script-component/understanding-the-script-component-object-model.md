---
title: "Présentation du modèle objet de composant Script | Documents Microsoft"
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
- Script component [Integration Services], object model
ms.assetid: 2a0aae82-39cc-4423-b09a-72d2f61033bd
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 09de00344fe94087b6287b07c4b1ffe933d27b7c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="understanding-the-script-component-object-model"></a>Présentation du modèle objet du composant Script
  Comme indiqué dans [de codage et débogage du composant Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md), le projet de composant Script contient trois éléments de projet :  
  
1.  Le **ScriptMain** élément qui contienne le **ScriptMain** classe dans laquelle vous écrivez votre code. Le **ScriptMain** classe hérite de la **UserComponent** classe.  
  
2.  Le **ComponentWrapper** élément qui contienne le **UserComponent** une instance de classe <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> qui contient les méthodes et propriétés que vous allez utiliser pour traiter les données et d’interagir avec le package. Le **ComponentWrapper** élément contient également **connexions** et **Variables** classes de collection.  
  
3.  Le **BufferWrapper** élément qui contient des classes qui hérite de <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> pour chaque propriétés d’entrée et de sortie et typée pour chaque colonne.  
  
 Lorsque vous écrivez votre code dans le **ScriptMain** élément, vous allez utiliser les objets, méthodes et propriétés présentées dans cette rubrique. Chaque composant n'utilise pas toutes les méthodes répertoriées ici ; cependant, lorsque ces méthodes sont utilisées, elles le sont dans l'ordre indiqué.  
  
 La classe de base <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> ne contient pas de code d'implémentation pour les méthodes présentées dans cette rubrique. Il est donc inutile, mais sans conséquence, d'ajouter un appel à l'implémentation de la classe de base à votre propre implémentation de la méthode.  
  
 Pour plus d’informations sur la façon d’utiliser les méthodes et propriétés de ces classes dans un type particulier de composant de Script, consultez la section [des exemples supplémentaires de composant de Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md). Les rubriques d'exemples contiennent également des exemples de code complets.  
  
## <a name="acquireconnections-method"></a>Méthode AcquireConnections  
 Généralement, les sources et les destinations doivent se connecter à une source de données externe. Substituez la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> de la classe de base <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> pour extraire la connexion ou les informations de connexion du gestionnaire de connexions approprié.  
  
 L’exemple suivant retourne un **System.Data.SqlClient.SqlConnection** à partir d’un gestionnaire de connexions ADO.NET.  
  
```vb  
Dim connMgr As IDTSConnectionManager100  
Dim sqlConn As SqlConnection  
  
Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
    connMgr = Me.Connections.MyADONETConnection  
    sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)  
  
End Sub  
```  
  
 L’exemple suivant retourne un chemin d’accès complet et le nom de fichier d’un gestionnaire de connexions fichier plat et ouvre ensuite le fichier en utilisant un **System.IO.StreamReader**.  
  
```vb  
Private textReader As StreamReader  
Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
    Dim connMgr As IDTSConnectionManager100 = _  
        Me.Connections.MyFlatFileSrcConnectionManager  
    Dim exportedAddressFile As String = _  
        CType(connMgr.AcquireConnection(Nothing), String)  
    textReader = New StreamReader(exportedAddressFile)  
  
End Sub  
```  
  
## <a name="preexecute-method"></a>Méthode PreExecute  
 Substituez la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PreExecute%2A> de la classe de base <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> lorsque vous devez effectuer un traitement une seule fois avant d'entamer le traitement des lignes de données. Par exemple, dans une destination, vous pouvez configurer la commande paramétrable que la destination utilise pour insérer chaque ligne de données dans la source de données.  
  
```vb  
    Dim sqlConn As SqlConnection  
    Dim sqlCmd As SqlCommand  
    Dim sqlParam As SqlParameter  
...  
    Public Overrides Sub PreExecute()  
  
        sqlCmd = New SqlCommand("INSERT INTO Person.Address2(AddressID, City) " & _  
            "VALUES(@addressid, @city)", sqlConn)  
        sqlParam = New SqlParameter("@addressid", SqlDbType.Int)  
        sqlCmd.Parameters.Add(sqlParam)  
        sqlParam = New SqlParameter("@city", SqlDbType.NVarChar, 30)  
        sqlCmd.Parameters.Add(sqlParam)  
  
    End Sub  
```  
  
```csharp  
SqlConnection sqlConn;   
SqlCommand sqlCmd;   
SqlParameter sqlParam;   
  
public override void PreExecute()   
{   
  
    sqlCmd = new SqlCommand("INSERT INTO Person.Address2(AddressID, City) " + "VALUES(@addressid, @city)", sqlConn);   
    sqlParam = new SqlParameter("@addressid", SqlDbType.Int);   
    sqlCmd.Parameters.Add(sqlParam);   
    sqlParam = new SqlParameter("@city", SqlDbType.NVarChar, 30);   
    sqlCmd.Parameters.Add(sqlParam);   
  
}  
```  
  
## <a name="processing-inputs-and-outputs"></a>Traitement des entrées et des sorties  
  
### <a name="processing-inputs"></a>Traitement des entrées  
 Les composants Script configurés en tant que transformations ou destinations possèdent une entrée.  
  
#### <a name="what-the-bufferwrapper-project-item-provides"></a>Composants fournis par l'élément de projet BufferWrapper  
 Pour chaque d’entrée que vous avez configurée, la **BufferWrapper** élément de projet contient une classe qui dérive de <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> et a le même nom que l’entrée. Chaque classe de mémoire tampon d'entrée contient les propriétés, fonctions et méthodes suivantes :  
  
-   Des propriétés d'accesseur typées et nommées pour chaque colonne d'entrée sélectionnée. Ces propriétés sont en lecture seule ou en lecture/écriture selon le **Type d’utilisation** spécifiée pour la colonne sur le **colonnes d’entrée** page de la **éditeur de Transformation de Script**.  
  
-   A  **\<colonne > _IsNull** colonne de propriété pour chaque sélectionné d’entrée. Cette propriété est également en lecture seule ou en lecture/écriture selon le **Type d’utilisation** spécifiée pour la colonne.  
  
-   A **DirectRowTo\<outputbuffer >** méthode pour chaque de sortie configurée. Vous allez utiliser ces méthodes lors du filtrage de lignes à une des multiples sorties dans le même **ExclusionGroup**.  
  
-   A **NextRow** fonction permettant d’obtenir la ligne d’entrée suivante et un **EndOfRowset** afin de déterminer si la dernière mémoire tampon de données a été traitée. Vous n’est généralement pas nécessaire ces fonctions lorsque vous utilisez l’entrée du traitement des méthodes implémentées dans le **UserComponent** classe de base. La section suivante fournit plus d’informations sur la **UserComponent** classe de base.  
  
#### <a name="what-the-componentwrapper-project-item-provides"></a>Composants fournis par l'élément de projet ComponentWrapper  
 L’élément de projet ComponentWrapper contient une classe nommée **UserComponent** qui dérive de <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>. Le **ScriptMain** classe dans laquelle vous écrivez votre code personnalisé dérive à son tour **UserComponent**. Le **UserComponent** classe contient les méthodes suivantes :  
  
-   Une implémentation substituée de la **ProcessInput** (méthode). C’est la méthode que les flux de données du moteur appelle au moment de l’exécution après le **PreExecute** (méthode), elle peut être appelée plusieurs fois. **ProcessInput** remet le traitement de la  **\<inputbuffer > _ProcessInput** (méthode). Le **ProcessInput** méthode vérifie la fin de la mémoire tampon d’entrée et, si la fin de la mémoire tampon a été atteinte, appelle le substituable **FinishOutputs** méthode et privé **MarkOutputsAsFinished** (méthode). Le **MarkOutputsAsFinished** méthode appelle ensuite **SetEndOfRowset** sur la dernière mémoire tampon de sortie.  
  
-   Une implémentation substituable de la  **\<inputbuffer > _ProcessInput** (méthode). Cette implémentation par défaut parcourt simplement chaque ligne d’entrée et les appels  **\<inputbuffer > _ProcessInputRow**.  
  
-   Une implémentation substituable de la  **\<inputbuffer > _ProcessInputRow** (méthode). L'implémentation par défaut est vide. Il s'agit normalement de la méthode que vous devez substituer pour écrire votre code de traitement de données personnalisé.  
  
#### <a name="what-your-custom-code-should-do"></a>Opérations à effectuer par votre code personnalisé  
 Vous pouvez utiliser les méthodes suivantes pour traiter des entrées dans le **ScriptMain** classe :  
  
-   Substituer  **\<inputbuffer > _ProcessInputRow** pour traiter les données dans chaque ligne d’entrée qui traversent.  
  
-   Substituer  **\<inputbuffer > _ProcessInput** uniquement si vous devez effectuer une autre opération lors d’une boucle dans les lignes d’entrée. (Par exemple, vous devez vérifier la présence de **EndOfRowset** pour exécuter une autre action une fois toutes les lignes ont été traitées.) Appelez  **\<inputbuffer > _ProcessInputRow** pour effectuer le traitement de la ligne.  
  
-   Substituer **FinishOutputs** si vous devez effectuer une opération sur les sorties avant leur fermeture.  
  
 Le **ProcessInput** méthode garantit que ces méthodes sont appelées aux moments appropriés.  
  
### <a name="processing-outputs"></a>Traitement des sorties  
 Les composants Script configurés en tant que sources ou transformations possèdent une ou plusieurs sorties.  
  
#### <a name="what-the-bufferwrapper-project-item-provides"></a>Composants fournis par l'élément de projet BufferWrapper  
 Pour chaque sortie configurée, l'élément de projet BufferWrapper contient une classe qui dérive de <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> et qui porte le même nom que la sortie. Chaque classe de mémoire tampon d'entrée contient les propriétés et méthodes suivantes :  
  
-   Des propriétés d'accesseur nommées, typées et en écriture seule pour chaque colonne de sortie.  
  
-   Écriture seule  **\<colonne > _IsNull** propriété pour chaque colonne de sortie sélectionné que vous pouvez utiliser pour définir la valeur de colonne à **null**.  
  
-   Un **AddRow** méthode pour ajouter une nouvelle ligne vide dans la mémoire tampon de sortie.  
  
-   A **SetEndOfRowset** méthode pour informer le moteur de flux de données qu’aucun autre tampon de données n’est prévu. Il existe également un **EndOfRowset** fonction pour déterminer si la mémoire tampon actuelle est la dernière mémoire tampon de données. En général inutile ces fonctions lorsque vous utilisez l’entrée du traitement des méthodes implémentées dans le **UserComponent** classe de base.  
  
#### <a name="what-the-componentwrapper-project-item-provides"></a>Composants fournis par l'élément de projet ComponentWrapper  
 L’élément de projet ComponentWrapper contient une classe nommée **UserComponent** qui dérive de <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>. Le **ScriptMain** classe dans laquelle vous écrivez votre code personnalisé dérive à son tour **UserComponent**. Le **UserComponent** classe contient les méthodes suivantes :  
  
-   Une implémentation substituée de la **PrimeOutput** (méthode). Le moteur de flux de données appelle cette méthode avant **ProcessInput** au moment de l’exécution, et elle est appelée uniquement une seule fois. **PrimeOutput** remet le traitement de la **CreateNewOutputRows** (méthode). Ensuite, si le composant est une source (autrement dit, le composant n’a aucuns entrée), **PrimeOutput** appelle le substituable **FinishOutputs** méthode et privé **MarkOutputsAsFinished** (méthode). Le **MarkOutputsAsFinished** les appels de méthode **SetEndOfRowset** sur la dernière mémoire tampon de sortie.  
  
-   Une implémentation substituable de la **CreateNewOutputRows** (méthode). L'implémentation par défaut est vide. Il s'agit normalement de la méthode que vous devez substituer pour écrire votre code de traitement de données personnalisé.  
  
#### <a name="what-your-custom-code-should-do"></a>Opérations à effectuer par votre code personnalisé  
 Vous pouvez utiliser les méthodes suivantes pour traiter les sorties dans le **ScriptMain** classe :  
  
-   Substituer **CreateNewOutputRows** uniquement lorsque vous pouvez ajouter et remplir les lignes de sortie avant de traiter les lignes d’entrée. Par exemple, vous pouvez utiliser **CreateNewOutputRows** dans une source, mais dans une transformation à sorties asynchrones, vous devez appeler **AddRow** pendant ou après le traitement des données d’entrée.  
  
-   Substituer **FinishOutputs** si vous devez effectuer une opération sur les sorties avant leur fermeture.  
  
 Le **PrimeOutput** méthode garantit que ces méthodes sont appelées aux moments appropriés.  
  
## <a name="postexecute-method"></a>Méthode PostExecute  
 Substituez la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PostExecute%2A> de la classe de base <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> lorsque vous devez effectuer un traitement une seule fois après avoir traité les lignes de données. Par exemple, dans une source, vous souhaiterez fermer le **System.Data.SqlClient.SqlDataReader** que vous avez utilisé pour charger des données dans le flux de données.  
  
> [!IMPORTANT]  
>  La collection de **ReadWriteVariables** est disponible uniquement dans les **PostExecute** (méthode). Par conséquent, vous ne pouvez pas incrémenter directement la valeur d'une variable de package à mesure que vous traitez chaque ligne de données. Au lieu de cela, incrémenter la valeur d’une variable locale et définir la valeur de la variable de package à la valeur de la variable locale dans le **PostExecute** méthode une fois toutes les données ont été traitée.  
  
## <a name="releaseconnections-method"></a>Méthode ReleaseConnections  
 Sources et destinations généralement doivent se connecter à une source de données externe. Substituez la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReleaseConnections%2A> de la classe de base <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> pour fermer et libérer la connexion que vous avez ouverte précédemment dans la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A>.  
  
```vb  
    Dim connMgr As IDTSConnectionManager100  
...  
    Public Overrides Sub ReleaseConnections()  
  
        connMgr.ReleaseConnection(sqlConn)  
  
    End Sub  
```  
  
```csharp  
IDTSConnectionManager100 connMgr;  
  
public override void ReleaseConnections()  
{  
  
    connMgr.ReleaseConnection(sqlConn);  
  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration du composant Script dans l’éditeur de composant Script.](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)   
 [Codage et débogage du composant Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  

