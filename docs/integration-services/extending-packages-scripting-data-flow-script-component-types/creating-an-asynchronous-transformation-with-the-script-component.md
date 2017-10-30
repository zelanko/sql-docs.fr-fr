---
title: "Création d’une Transformation asynchrone avec le composant de Script | Documents Microsoft"
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
- asynchronous outputs [Integration Services]
- transformation components [Integration Services]
- Script component [Integration Services], transformation components
ms.assetid: 0d814404-21e4-4a68-894c-96fa47ab25ae
caps.latest.revision: 63
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4da61e00337430a3eaef84e40f9f732a572cc45b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="creating-an-asynchronous-transformation-with-the-script-component"></a>Création d'une transformation asynchrone à l'aide du composant Script
  Vous utilisez un composant de transformation dans le flux de données d'un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour modifier et analyser les données acheminées de la source à la destination. Une transformation à sorties synchrones traite chacune des lignes d'entrée lorsqu'elles traversent le composant. Une transformation à sorties asynchrones peut attendre avant de procéder au traitement jusqu'à ce que la transformation a reçu toutes les lignes d’entrée, ou la transformation peut exporter certaines lignes avant d’avoir reçu toutes les lignes d’entrée. Cette rubrique examine une transformation asynchrone. Si votre traitement requiert une transformation synchrone, consultez [création d’une Transformation synchrone avec le composant de Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md). Pour plus d’informations sur les différences entre les composants synchrones et asynchrones, consultez [fonctionnement synchrone et asynchrone des Transformations](../../integration-services/understanding-synchronous-and-asynchronous-transformations.md).  
  
 Pour une vue d’ensemble du composant Script, consultez [étendre le flux de données avec le composant Script](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
 Le composant Script et le code d'infrastructure qu'il génère simplifient le processus qui consiste à développer un composant de flux de données personnalisé. Toutefois, pour comprendre le fonctionnement du composant Script, vous pouvez s’avérer utile de consulter les étapes à suivre dans le développement d’un composant de flux de données personnalisées dans le [développer un composant de flux de données personnalisé](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) section et surtout [développer un composant de Transformation personnalisé à sorties synchrones](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md).  
  
## <a name="getting-started-with-an-asynchronous-transformation-component"></a>Mise en route d'un composant de transformation asynchrone  
 Lorsque vous ajoutez un composant de Script à l’onglet flux de données de [!INCLUDE[ssIS](../../includes/ssis-md.md)] concepteur, le **sélectionner le Type de composant Script** boîte de dialogue vous invite à préconfigurer le composant en tant que source, transformation ou destination. Dans cette boîte de dialogue, sélectionnez **Transformation**.  
  
## <a name="configuring-an-asynchronous-transformation-component-in-metadata-design-mode"></a>Configuration d'un composant de transformation asynchrone en mode Création de métadonnées  
 Après avoir sélectionné l’option pour créer un composant de transformation, vous configurez le composant à l’aide de la **éditeur de Transformation de Script**. Pour plus d’informations, consultez [configuration du composant Script dans l’éditeur de composant Script](../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).  
  
 Pour sélectionner le langage de script qui utilise le composant de Script, vous définissez la **ScriptLanguage** propriété sur le **Script** page de la **éditeur de Transformation de Script** boîte de dialogue.  
  
> [!NOTE]  
>  Pour définir la valeur par défaut de langage de script par le composant de Script, utilisez la **langage de script** option sur le **général** page de la **Options** boîte de dialogue. Pour plus d'informations, consultez [General Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx).  
  
 Un composant de transformation de flux de données possède une entrée et prend en charge une ou plusieurs sorties. Configuration de l’entrée et les sorties de votre composant est une des étapes que vous devez exécuter en mode de création de métadonnées, à l’aide de la **éditeur de Transformation de Script**, avant d’écrire votre script personnalisé.  
  
### <a name="configuring-input-columns"></a>Configuration de colonnes d'entrée  
 Un composant de transformation créé à l'aide du composant Script possède une seule entrée.  
  
 Sur le **colonnes d’entrée** page de la **éditeur de Transformation de Script**, la liste de colonnes affiche les colonnes disponibles à partir de la sortie du composant en amont du flux de données. Sélectionnez les colonnes à transformer ou à passer. Marquez toutes les colonnes que vous souhaitez transformer sur place comme accessibles en lecture/écriture.  
  
 Pour plus d’informations sur la **colonnes d’entrée** page de la **éditeur de Transformation de Script**, consultez [éditeur de Transformation de Script &#40; Page de colonnes d’entrée &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-input-columns-page.md).  
  
### <a name="configuring-inputs-outputs-and-output-columns"></a>Configuration des entrées, des sorties et des colonnes de sortie  
 Un composant de transformation prend en charge une ou plusieurs sorties.  
  
 Généralement, une transformation à sorties asynchrones possède deux sorties. Par exemple, lorsque vous comptez le nombre d'adresses situées dans une ville spécifique, vous pouvez transférer les données d'adresse à une sortie, tout en envoyant le résultat de l'agrégation à une autre sortie. La sortie d'agrégation requiert également une nouvelle colonne de sortie.  
  
 Sur le **entrées et sorties** page de la **éditeur de Transformation de Script**, vous voyez qu’une seule sortie a été créée par défaut, mais aucune colonne de sortie n’ont été créés. Dans cette page de l'éditeur, vous pouvez configurer les éléments suivants :  
  
-   Vous pouvez créer une ou plusieurs sorties supplémentaires, telles qu'une sortie pour le résultat d'une agrégation. Utilisez le **ajouter une sortie** et **supprimer une sortie** boutons pour gérer les sorties du composant de transformation asynchrone. Définir le **SynchronousInputID** propriété de chaque sortie à zéro pour indiquer que la sortie ne consiste pas simplement transmettre les données à partir d’un composant en amont ou transformer sur place dans les colonnes et lignes existantes. C'est ce paramètre qui rend les sorties asynchrones par rapport à l'entrée.  
  
-   Vous pouvez assigner un nom convivial à l'entrée et aux sorties. Le composant Script utilise ces noms pour générer les propriétés d'accesseur typées qui vous permettent de référencer l'entrée et les sorties dans le script.  
  
-   Généralement, une transformation asynchrone ajoute des colonnes au flux de données. Lorsque le **SynchronousInputID** propriété d’une sortie est égale à zéro, indiquant que la sortie ne consiste pas simplement transmettre les données à partir d’un composant en amont ou transformer sur place dans les colonnes et lignes existantes, vous devez ajouter et configurer des colonnes de sortie de manière explicite sur la sortie. Les colonnes de sortie ne portent pas le même nom que les colonnes d'entrée auxquelles elles sont mappées.  
  
-   Vous pouvez ajouter d'autres colonnes pour contenir des informations supplémentaires. Vous devez écrire votre propre code pour remplir les colonnes supplémentaires de données. Pour plus d’informations sur le comportement d’une sortie d’erreur standard de reproduction, consultez [en simulant une sortie d’erreur du composant de Script](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).  
  
 Pour plus d’informations sur la **entrées et sorties** page de la **éditeur de Transformation de Script**, consultez [éditeur de Transformation de Script &#40; les entrées et sorties de Page &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-inputs-and-outputs-page.md).  
  
### <a name="adding-variables"></a>Ajout de variables  
 S’il existe des variables les valeurs dont vous souhaitez utiliser dans votre script, vous pouvez les ajouter dans les champs de propriété ReadOnlyVariables et ReadWriteVariables dans les **Script** page de la **éditeur de Transformation de Script**.  
  
 Lorsque vous ajoutez plusieurs variables dans les champs de propriété, séparez les noms de variables par des virgules. Vous pouvez également sélectionner plusieurs variables en cliquant sur le bouton de sélection (**...** ) situé en regard du **ReadOnlyVariables** et **ReadWriteVariables** champs de propriété, puis en sélectionnant les variables dans le **sélectionner des variables** boîte de dialogue.  
  
 Pour obtenir des informations générales sur l’utilisation de variables avec le composant Script, consultez [à l’aide de Variables dans le composant Script](../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).  
  
 Pour plus d’informations sur la **Script** page de la **éditeur de Transformation de Script**, consultez [éditeur de Transformation de Script &#40; Page script &#41; ](../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
## <a name="scripting-an-asynchronous-transformation-component-in-code-design-mode"></a>Script d'un composant de transformation asynchrone en mode Création de code  
 Après avoir configuré toutes les métadonnées du composant, vous pouvez écrire votre script personnalisé. Dans le **éditeur de Transformation de Script**, dans le **Script** , cliquez sur **modifier le Script** pour ouvrir le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE où vous pouvez ajouter votre script personnalisé. Le langage de script que vous utilisez varie selon que vous avez sélectionné [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual c# comme langage de script pour le **ScriptLanguage** propriété sur le **Script** page.  
  
 Pour obtenir des informations importantes qui s’applique à tous les types de composants créés à l’aide du composant Script, consultez [de codage et débogage du composant Script](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="understanding-the-auto-generated-code"></a>Fonctionnement du code généré automatiquement  
 Lorsque vous ouvrez l’IDE VSTA après avoir créé et configuré un composant de transformation, le texte modifiable **ScriptMain** classe s’affiche dans l’éditeur de code avec les stubs pour le ProcessInputRow et les méthodes CreateNewOutputRows. La classe ScriptMain est où vous allez écrire votre code personnalisé et ProcessInputRow est la méthode la plus importante dans un composant de transformation. Le **CreateNewOutputRows** méthode est généralement utilisée dans un composant source, ce qui ressemble à une transformation asynchrone car les deux composants doivent créer leurs propres lignes de sortie.  
  
 Si vous ouvrez le VSTA **Explorateur de projets** fenêtre, vous pouvez voir que le composant Script a également généré en lecture seule **BufferWrapper** et **ComponentWrapper** éléments de projet. La classe ScriptMain hérite de la classe UserComponent dans le **ComponentWrapper** élément de projet.  
  
 Au moment de l’exécution, le moteur de flux de données appelle la méthode PrimeOutput le **UserComponent** classe, qui remplace le <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PrimeOutput%2A> méthode de la <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> classe parente. La méthode PrimeOutput appelle à son tour la méthode CreateNewOutputRows.  
  
 Ensuite, le moteur de flux de données appelle la méthode ProcessInput dans la classe UserComponent, qui remplace le <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> méthode de la <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> classe parente. À son tour, la méthode ProcessInput parcourt les lignes dans la mémoire tampon d’entrée et appelle la méthode ProcessInputRow une fois pour chaque ligne.  
  
### <a name="writing-your-custom-code"></a>Écriture du code personnalisé  
 Pour terminer la création d’un composant de transformation asynchrone personnalisé, vous devez utiliser la méthode ProcessInputRow substituée pour traiter les données dans chaque ligne de la mémoire tampon d’entrée. Comme les sorties ne sont pas synchrones avec l'entrée, vous devez écrire explicitement des lignes de données dans les sorties.  
  
 Dans une transformation asynchrone, vous pouvez utiliser la méthode AddRow pour ajouter des lignes à la sortie appropriée à partir de méthodes ProcessInputRow ou ProcessInput. Il est inutile d’utiliser la méthode CreateNewOutputRows. Si vous écrivez une seule ligne de résultats, tels que les résultats de l’agrégation dans une sortie particulière, vous pouvez créer au préalable de la ligne de sortie à l’aide de la méthode CreateNewOutputRows et remplir ses valeurs ultérieurement après avoir traité toutes les lignes d’entrée. Toutefois il n’est pas utile de créer plusieurs lignes dans la méthode CreateNewOutputRows, car le composant de Script seulement vous permet d’utiliser la ligne actuelle dans une entrée ou de sortie. La méthode CreateNewOutputRows est plus importante dans un composant source où il n’existe aucune ligne d’entrée à traiter.  
  
 Vous pouvez souhaiter également substituer la méthode ProcessInput lui-même, afin que vous pouvez effectuer d’autres traitements préliminaires ou finaux avant ou après la boucle de la mémoire tampon d’entrée et de l’appeler ProcessInputRow pour chaque ligne. Par exemple, un des exemples de code de cette rubrique substitue ProcessInput pour compter le nombre d’adresses dans une ville spécifique en tant que ProcessInputRow parcourt les lignes**.** L’exemple écrit la valeur de synthèse dans la deuxième sortie une fois toutes les lignes ont été traitées. L’exemple termine à la sortie dans ProcessInput, car les mémoires tampons de sortie ne sont plus disponibles lorsque PostExecute est appelée.  
  
 Selon vos besoins, vous pouvez souhaiter également écrire un script dans les méthodes PreExecute et PostExecute disponibles dans la classe ScriptMain pour exécuter tout traitement préliminaire ou final.  
  
> [!NOTE]  
>  Si vous développez un composant de flux de données personnalisé à partir de zéro, il serait important de substituer la méthode PrimeOutput au cache des références aux tampons de sortie afin que vous pouvez ajouter des lignes de données aux mémoires tampons ultérieurement. Dans le composant Script, cela n’est pas nécessaire, car vous avez une classe générée automatiquement qui représente chaque mémoire tampon de sortie dans le **BufferWrapper** élément de projet.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre le code personnalisé requis dans la classe ScriptMain pour créer un composant de transformation asynchrone.  
  
> [!NOTE]  
>  Ces exemples utilisent la **Person.Address** de table dans le **AdventureWorks** exemple de base de données et transmettent ses première et quatrième colonnes, le **intAddressID** et **nvarchar (30) Ville** colonnes, dans le flux de données. Les mêmes données sont utilisées dans les exemples de source, transformation et destination de cette section. Des conditions préalables et des hypothèses supplémentaires sont documentées pour chaque exemple.  
  
 Cet exemple présente un composant de transformation asynchrone à deux sorties. Cette transformation passe via le **AddressID** et **Ville** colonnes à une sortie, tandis qu’il compte le nombre d’adresses situées dans une ville spécifique (Redmond, Washington, États-Unis), puis renvoie la valeur obtenue vers une deuxième sortie.  
  
 Si vous souhaitez exécuter cet exemple de code, vous devez configurer le package et le composant comme suit :  
  
1.  Ajoutez un nouveau composant Script à l'aire du concepteur de flux de données et configurez-le en tant que transformation.  
  
2.  Connectez la sortie d'une source ou d'une autre transformation au nouveau composant de transformation dans le concepteur. Cette sortie doit fournir des données à partir de la **Person.Address** table de la **AdventureWorks** base de données exemple contienne au moins les **AddressID** et **Ville** colonnes.  
  
3.  Ouvrez l' **Éditeur de transformation de script**. Sur le **colonnes d’entrée** page, sélectionnez le **AddressID** et **Ville** colonnes.  
  
4.  Sur le **entrées et sorties** page, ajoutez et configurez le **AddressID** et **Ville** des colonnes sur la première sortie de sortie. Ajoutez une deuxième sortie, puis ajoutez sur cette dernière une colonne de sortie pour la valeur résumée. Attribuez la valeur 0 à la propriété SynchronousInputID de la première sortie, car cet exemple copie explicitement chaque ligne d'entrée vers la première sortie. La propriété SynchronousInputID de la sortie récemment créée a déjà la valeur 0.  
  
5.  Renommez l'entrée, les sorties et la nouvelle colonne de sortie avec des noms plus descriptifs. L’exemple utilise **MyAddressInput** comme nom de l’entrée, **MyAddressOutput** et **MySummaryOutput** pour les sorties, et **MyRedmondCount** pour la colonne de sortie sur la deuxième sortie.  
  
6.  Dans la page **Script** , cliquez sur **Modifier le script** , puis entrez le script suivant. Ensuite, fermez l'environnement de développement de script et l' **Éditeur de transformation de script**.  
  
7.  Créer et configurer un composant de destination pour la première sortie qui attend le **AddressID** et **Ville** colonnes, comme un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, ou l’exemple de composant de destination présenté dans [création d’une Destination avec le composant Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md),. Puis connectez la première sortie de la transformation, **MyAddressOutput**, au composant de destination. Vous pouvez créer une table de destination en exécutant la commande suivante [!INCLUDE[tsql](../../includes/tsql-md.md)] dans les **AdventureWorks** base de données :  
  
    ```sql
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
8.  Créez et configurez un autre composant de destination pour la deuxième sortie. Puis connectez la deuxième sortie de la transformation, **MySummaryOutput**, au composant de destination. Comme la deuxième sortie écrit une seule ligne avec une seule valeur, vous pouvez configurer facilement une destination à l'aide d'un gestionnaire de connexions de fichiers plats qui se connecte à un nouveau fichier contenant une seule colonne. Dans l’exemple, cette colonne de destination est nommée **MyRedmondCount**.  
  
9. Exécutez l'exemple.  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Private myRedmondAddressCount As Integer  
  
    Public Overrides Sub CreateNewOutputRows()  
  
        MySummaryOutputBuffer.AddRow()  
  
    End Sub  
  
    Public Overrides Sub MyAddressInput_ProcessInput(ByVal Buffer As MyAddressInputBuffer)  
  
        While Buffer.NextRow()  
            MyAddressInput_ProcessInputRow(Buffer)  
        End While  
  
        If Buffer.EndOfRowset Then  
            MyAddressOutputBuffer.SetEndOfRowset()  
            MySummaryOutputBuffer.MyRedmondCount = myRedmondAddressCount  
            MySummaryOutputBuffer.SetEndOfRowset()  
        End If  
  
    End Sub  
  
    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
        With MyAddressOutputBuffer  
            .AddRow()  
            .AddressID = Row.AddressID  
            .City = Row.City  
        End With  
  
        If Row.City.ToUpper = "REDMOND" Then  
            myRedmondAddressCount += 1  
        End If  
  
    End Sub  
  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
  
{  
    private int myRedmondAddressCount;  
  
    public override void CreateNewOutputRows()  
    {  
  
        MySummaryOutputBuffer.AddRow();  
  
    }  
  
    public override void MyAddressInput_ProcessInput(MyAddressInputBuffer Buffer)  
    {  
  
        while (Buffer.NextRow())  
        {  
            MyAddressInput_ProcessInputRow(Buffer);  
        }  
  
        if (Buffer.EndOfRowset())  
        {  
            MyAddressOutputBuffer.SetEndOfRowset();  
            MySummaryOutputBuffer.MyRedmondCount = myRedmondAddressCount;  
            MySummaryOutputBuffer.SetEndOfRowset();  
        }  
  
    }  
  
    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
    {  
  
        {  
            MyAddressOutputBuffer.AddRow();  
            MyAddressOutputBuffer.AddressID = Row.AddressID;  
            MyAddressOutputBuffer.City = Row.City;  
        }  
  
        if (Row.City.ToUpper() == "REDMOND")  
        {  
            myRedmondAddressCount += 1;  
        }  
  
    }  
  
}  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des Transformations synchrones et asynchrones](../../integration-services/understanding-synchronous-and-asynchronous-transformations.md)   
 [Création d’une Transformation synchrone avec le composant de Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)   
 [Développement d’un composant de Transformation personnalisé à sorties asynchrones](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)  
  
  

