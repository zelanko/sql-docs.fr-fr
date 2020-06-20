---
title: Présentation du modèle objet du composant Script | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], object model
ms.assetid: 2a0aae82-39cc-4423-b09a-72d2f61033bd
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 80d61a4b4742163d999aa2f5d70e70336e680e27
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84967245"
---
# <a name="understanding-the-script-component-object-model"></a>Présentation du modèle objet du composant Script
  Comme indiqué dans [codage et débogage du composant Script] (.. /Extending-packages-Scripting/Data-Flow-script-Component/Coding-and-Debugging-the-script-Component.MD, le projet de composant script contient trois éléments de projet :

1.  L'élément `ScriptMain`, qui contient la classe `ScriptMain` dans laquelle vous écrivez votre code. La classe `ScriptMain` hérite de la classe `UserComponent`.

2.  L'élément `ComponentWrapper`, qui contient la classe `UserComponent`, une instance de <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> contenant les méthodes et les propriétés qui permettent de traiter les données et d'interagir avec le package. L'élément `ComponentWrapper` contient également des classes de collection `Connections` et `Variables`.

3.  L'élément `BufferWrapper`, qui contient des classes qui héritent de <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> pour chaque entrée et sortie, et des propriétés typées pour chaque colonne.

 Les objets, méthodes et propriétés présentés dans cette rubrique vous permettent d'écrire du code dans l'élément `ScriptMain`. Chaque composant n'utilise pas toutes les méthodes répertoriées ici ; cependant, lorsque ces méthodes sont utilisées, elles le sont dans l'ordre indiqué.

 La classe de base <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> ne contient pas de code d'implémentation pour les méthodes présentées dans cette rubrique. Il est donc inutile, mais sans conséquence, d'ajouter un appel à l'implémentation de la classe de base à votre propre implémentation de la méthode.

 Pour plus d’informations sur l’utilisation des méthodes et des propriétés de ces classes dans un type de composant Script particulier, consultez la section [Autres exemples de composants Script](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md). Les rubriques d'exemples contiennent également des exemples de code complets.

## <a name="acquireconnections-method"></a>Méthode AcquireConnections
 Généralement, les sources et les destinations doivent se connecter à une source de données externe. Substituez la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> de la classe de base <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> pour extraire la connexion ou les informations de connexion du gestionnaire de connexions approprié.

 L'exemple suivant retourne `System.Data.SqlClient.SqlConnection` à partir d'un gestionnaire de connexions ADO.NET.

```vb
Dim connMgr As IDTSConnectionManager100
Dim sqlConn As SqlConnection

Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

    connMgr = Me.Connections.MyADONETConnection
    sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)

End Sub
```

 L'exemple suivant retourne un chemin d'accès complet et un nom de fichier à partir d'un gestionnaire de connexions de fichiers plats, puis ouvre le fichier à l'aide de `System.IO.StreamReader`.

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
 Pour chaque entrée configurée, l'élément de projet `BufferWrapper` contient une classe qui dérive de <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> et qui porte le même nom que l'entrée. Chaque classe de mémoire tampon d'entrée contient les propriétés, fonctions et méthodes suivantes :

-   Des propriétés d'accesseur typées et nommées pour chaque colonne d'entrée sélectionnée. Ces propriétés sont en lecture seule ou en lecture/écriture selon le **Type d’utilisation** spécifié pour la colonne dans la page **Colonnes d’entrée** de l’**Éditeur de transformation de script**.

-   Propriété ** \<column> _IsNull** pour chaque colonne d’entrée sélectionnée. Cette propriété est également en lecture seule ou en lecture/écriture selon le **Type d’utilisation** spécifié pour la colonne.

-   Méthode **méthode DirectRowTo \<outputbuffer> ** pour chaque sortie configurée. Vous utilisez ces méthodes lorsque vous filtrez des lignes vers l'une des multiples sorties dans le même `ExclusionGroup`.

-   Une fonction `NextRow` pour récupérer la ligne d'entrée suivante et une fonction `EndOfRowset` pour déterminer si la dernière mémoire tampon de données a été traitée. Généralement, vous n'avez pas besoin de ces fonctions lorsque vous exécutez les méthodes de traitement d'entrée implémentées dans la classe de base `UserComponent`. La section suivante fournit des informations supplémentaires sur la classe de base `UserComponent`.

#### <a name="what-the-componentwrapper-project-item-provides"></a>Composants fournis par l'élément de projet ComponentWrapper
 L'élément de projet ComponentWrapper contient une classe nommée `UserComponent` dérivée de <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>. La classe `ScriptMain` dans laquelle vous écrivez votre code personnalisé dérive à son tour de `UserComponent`. La classe `UserComponent` contient les méthodes suivantes :

-   Une implémentation substituée de la méthode `ProcessInput`. Il s'agit de la méthode que le moteur de flux de données appelle au moment de l'exécution, juste après la méthode `PreExecute`. Elle peut être appelée plusieurs fois. `ProcessInput`transfère le traitement à la méthode ** \<inputbuffer> _ProcessInput** . La méthode `ProcessInput` recherche ensuite la fin de la mémoire tampon d'entrée et si elle la trouve, appelle la méthode `FinishOutputs` substituable et la méthode `MarkOutputsAsFinished` privée. Puis, la méthode `MarkOutputsAsFinished` appelle `SetEndOfRowset` sur la dernière mémoire tampon de sortie.

-   Implémentation substituable de la méthode ** \<inputbuffer> _ProcessInput** . Cette implémentation par défaut parcourt simplement chaque ligne d’entrée et appelle ** \<inputbuffer> _ProcessInputRow**.

-   Implémentation substituable de la méthode ** \<inputbuffer> _ProcessInputRow** . L'implémentation par défaut est vide. Il s'agit normalement de la méthode que vous devez substituer pour écrire votre code de traitement de données personnalisé.

#### <a name="what-your-custom-code-should-do"></a>Opérations à effectuer par votre code personnalisé
 Vous pouvez utiliser les méthodes suivantes pour traiter l'entrée dans la classe `ScriptMain` :

-   Remplacez ** \<inputbuffer> _ProcessInputRow** pour traiter les données dans chaque ligne d’entrée lors de leur transmission.

-   Remplacez ** \<inputbuffer> _ProcessInput** uniquement si vous devez effectuer une opération supplémentaire en effectuant une boucle dans les lignes d’entrée. (Par exemple, vous devez tester pour que `EndOfRowset` effectue une autre action une fois que toutes les lignes ont été traitées.) Appelez ** \<inputbuffer> _ProcessInputRow** pour effectuer le traitement de ligne.

-   Substituez `FinishOutputs` si vous devez effectuer une opération sur les sorties avant leur fermeture.

 La méthode `ProcessInput` garantit que ces méthodes sont appelées aux moments appropriés.

### <a name="processing-outputs"></a>Traitement des sorties
 Les composants Script configurés en tant que sources ou transformations possèdent une ou plusieurs sorties.

#### <a name="what-the-bufferwrapper-project-item-provides"></a>Composants fournis par l'élément de projet BufferWrapper
 Pour chaque sortie configurée, l'élément de projet BufferWrapper contient une classe qui dérive de <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> et qui porte le même nom que la sortie. Chaque classe de mémoire tampon d'entrée contient les propriétés et méthodes suivantes :

-   Des propriétés d'accesseur nommées, typées et en écriture seule pour chaque colonne de sortie.

-   Propriété ** \<column> _IsNull** en écriture seule pour chaque colonne de sortie sélectionnée que vous pouvez utiliser pour affecter la valeur à la colonne `null` .

-   Une méthode `AddRow` pour ajouter une ligne vide à la mémoire tampon de sortie.

-   Une méthode `SetEndOfRowset` pour indiquer au moteur de flux de données qu'aucune mémoire tampon de données supplémentaires n'est attendue. Il existe également une fonction `EndOfRowset` pour déterminer si la mémoire tampon active est la dernière mémoire tampon de données. En général, vous n’avez pas besoin de ces fonctions lorsque vous utilisez les méthodes de traitement d’entrée implémentées dans la `UserComponent` classe de base.

#### <a name="what-the-componentwrapper-project-item-provides"></a>Composants fournis par l'élément de projet ComponentWrapper
 L'élément de projet ComponentWrapper contient une classe nommée `UserComponent` dérivée de <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>. La classe `ScriptMain` dans laquelle vous écrivez votre code personnalisé dérive à son tour de `UserComponent`. La classe `UserComponent` contient les méthodes suivantes :

-   Une implémentation substituée de la méthode `PrimeOutput`. Le moteur de flux de données appelle cette méthode avant `ProcessInput` au moment de l'exécution. La méthode est appelée une seule fois. `PrimeOutput` fait appel à la méthode `CreateNewOutputRows` pour effectuer le traitement. Puis, si le composant est une source (autrement dit, le composant ne possède pas d'entrée), `PrimeOutput` appelle la méthode `FinishOutputs` substituable et la méthode `MarkOutputsAsFinished` privée. La méthode `MarkOutputsAsFinished` appelle `SetEndOfRowset` sur la dernière mémoire tampon de sortie.

-   Une implémentation substituable de la méthode `CreateNewOutputRows`. L'implémentation par défaut est vide. Il s'agit normalement de la méthode que vous devez substituer pour écrire votre code de traitement de données personnalisé.

#### <a name="what-your-custom-code-should-do"></a>Opérations à effectuer par votre code personnalisé
 Vous pouvez utiliser les méthodes suivantes pour traiter les sorties dans la classe `ScriptMain` :

-   Substituez `CreateNewOutputRows` uniquement lorsque vous pouvez ajouter et remplir des lignes de sortie avant de traiter des lignes d'entrée. Par exemple, vous pouvez utiliser `CreateNewOutputRows` dans une source, mais dans une transformation à sorties asynchrones, vous devez appeler `AddRow` pendant ou après le traitement des données d'entrée.

-   Substituez `FinishOutputs` si vous devez effectuer une opération sur les sorties avant leur fermeture.

 La méthode `PrimeOutput` garantit que ces méthodes sont appelées aux moments appropriés.

## <a name="postexecute-method"></a>Méthode PostExecute
 Substituez la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PostExecute%2A> de la classe de base <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> lorsque vous devez effectuer un traitement une seule fois après avoir traité les lignes de données. Par exemple, dans une source, vous pouvez fermer `System.Data.SqlClient.SqlDataReader` qui vous a permis de charger des données dans le flux de données.

> [!IMPORTANT]
>  La collection de `ReadWriteVariables` est uniquement disponible dans la méthode `PostExecute`. Par conséquent, vous ne pouvez pas incrémenter directement la valeur d'une variable de package à mesure que vous traitez chaque ligne de données. Incrémentez plutôt la valeur d'une variable locale, puis attribuez à la variable de package la valeur de la variable locale dans la méthode `PostExecute` une fois que toutes les données ont été traitées.

## <a name="releaseconnections-method"></a>Méthode ReleaseConnections
 Généralement, les sources et les destinations doivent se connecter à une source de données externe. Substituez la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReleaseConnections%2A> de la classe de base <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> pour fermer et libérer la connexion que vous avez ouverte précédemment dans la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A>.

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

![Icône de Integration Services (petite)](../../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.

## <a name="see-also"></a>Voir aussi
 [Configuration du composant script dans l’éditeur de composant de script](configuring-the-script-component-in-the-script-component-editor.md) [codage et débogage du composant Script] (.. /extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md


