---
title: "Création d’une Transformation synchrone avec le composant de Script | Documents Microsoft"
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
- synchronous outputs [Integration Services]
- transformation components [Integration Services]
- Script component [Integration Services], transformation components
ms.assetid: aa1bee1a-ab06-44d8-9944-4bff03d73016
caps.latest.revision: 64
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3d4a507c31f77449aba7eb884c39bf68c7c78581
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="creating-a-synchronous-transformation-with-the-script-component"></a>Création d'une transformation synchrone à l'aide du composant Script
  Vous utilisez un composant de transformation dans le flux de données d'un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour modifier et analyser les données acheminées de la source à la destination. Une transformation à sorties synchrones traite chacune des lignes d'entrée lorsqu'elles traversent le composant. Une transformation à sorties asynchrones patiente jusqu'à ce qu'elle ait reçu toutes les lignes d'entrée pour achever son traitement. Cette rubrique décrit une transformation synchrone. Pour plus d’informations sur les transformations asynchrones, consultez [création d’une Transformation asynchrone avec le composant de Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md). Pour plus d’informations sur la différence entre les composants synchrones et asynchrones, consultez [fonctionnement synchrone et asynchrone des Transformations](../../integration-services/understanding-synchronous-and-asynchronous-transformations.md).  
  
 Pour une vue d’ensemble du composant Script, consultez [étendre le flux de données avec le composant Script](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
 Le composant Script et le code d'infrastructure qu'il génère simplifient considérablement le processus qui consiste à développer un composant de flux de données personnalisé. Toutefois, pour comprendre le fonctionnement du composant Script, vous pouvez s’avérer utile de lire les étapes à suivre dans le développement d’un composant de flux de données personnalisé dans la section sur [développer un composant de flux de données personnalisé](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md), notamment [développer un composant de Transformation personnalisé à sorties synchrones](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md).  
  
## <a name="getting-started-with-a-synchronous-transformation-component"></a>Mise en route d'un composant de transformation synchrone  
 Lorsque vous ajoutez un composant de Script au volet flux de données de [!INCLUDE[ssIS](../../includes/ssis-md.md)] concepteur, le **sélectionner le Type de composant Script** boîte de dialogue s’ouvre et vous invite à sélectionner un type de composant Source, Destination ou Transformation. Dans cette boîte de dialogue, sélectionnez **Transformation**.  
  
## <a name="configuring-a-synchronous-transformation-component-in-metadata-design-mode"></a>Configuration d'un composant de transformation synchrone en mode Création des métadonnées  
 Après avoir sélectionné l’option pour créer un composant de transformation, vous configurez le composant à l’aide de la **éditeur de Transformation de Script**. Pour plus d’informations, consultez [configuration du composant Script dans l’éditeur de composant Script](../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).  
  
 Pour définir le langage de script pour le composant de Script, vous définissez la **ScriptLanguage** propriété sur le **Script** page de la **éditeur de Transformation de Script**.  
  
> [!NOTE]  
>  Pour définir la valeur par défaut de langage de script par le composant de Script, utilisez la **langage de script** option sur le **général** page de la **Options** boîte de dialogue. Pour plus d’informations, consultez [générales Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx).  
  
 Un composant de transformation de flux de données comporte une entrée et prend en charge une ou plusieurs sorties. Configuration de l’entrée et les sorties du composant est une des étapes à exécuter en mode de création de métadonnées, à l’aide de la **éditeur de Transformation de Script**, avant d’écrire votre script personnalisé.  
  
### <a name="configuring-input-columns"></a>Configuration de colonnes d'entrée  
 Un composant de transformation a une entrée.  
  
 Sur le **colonnes d’entrée** page de la **éditeur de Transformation de Script,** la liste de colonnes affiche les colonnes disponibles à partir de la sortie du composant en amont du flux de données. Sélectionnez les colonnes à transformer ou à passer. Marquez toutes les colonnes que vous souhaitez transformer sur place comme accessibles en lecture/écriture.  
  
 Pour plus d’informations sur la **colonnes d’entrée** page de la **éditeur de Transformation de Script**, consultez [éditeur de Transformation de Script &#40; Page de colonnes d’entrée &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-input-columns-page.md).  
  
### <a name="configuring-inputs-outputs-and-output-columns"></a>Configuration des entrées, des sorties et des colonnes de sortie  
 Un composant de transformation prend en charge une ou plusieurs sorties.  
  
 Sur le **entrées et sorties** page de la **éditeur de Transformation de Script**, vous pouvez voir qu’une seule sortie a été créée, mais la sortie ne comporte aucune colonne. Dans cette page de l'éditeur, vous pouvez avoir besoin ou envie de configurer les éléments suivants.  
  
-   Créez une ou plusieurs sorties supplémentaires, telles qu'une sortie d'erreur simulée pour les lignes qui contiennent des valeurs inattendues. Utilisez le **ajouter une sortie** et **supprimer une sortie** boutons pour gérer les sorties du composant de transformation synchrone. Toutes les lignes d'entrée sont dirigées vers toutes les sorties disponibles sauf si vous indiquez que vous envisagez de rediriger chaque ligne vers une sortie ou une autre. Vous indiquez que vous souhaitez rediriger les lignes en spécifiant une valeur entière non nulle pour le **ExclusionGroup** propriété sur les sorties. La valeur entière spécifique entrée dans **ExclusionGroup** pour identifier les sorties n’est pas significative, mais vous devez utiliser le même entier de manière cohérente pour le groupe spécifié de sorties.  
  
    > [!NOTE]  
    >  Vous pouvez également utiliser une valeur de propriété **ExclusionGroup** non nulle avec une sortie unique lorsque vous ne souhaitez pas générer des sorties pour toutes les lignes. Toutefois, dans ce cas, vous devez appeler explicitement la **DirectRowTo\<outputbuffer >** pour chaque ligne que vous souhaitez envoyer à la sortie.  
  
-   Attribuez un plus nom descriptif à l'entrée et aux sorties. Le composant Script utilise ces noms pour générer les propriétés d'accesseur typées qui vous permettent de référencer l'entrée et les sorties dans le script.  
  
-   Laissez des colonnes inchangées pour les transformations synchrones. En général, une transformation synchrone n'ajoute pas de colonnes au flux de données. Les données sont modifiées sur place dans le tampon, et le tampon est transmis au composant suivant dans le flux de données. Le cas échéant, vous n'avez pas à ajouter et configurer explicitement des colonnes de sortie sur les sorties de la transformation. Les sorties apparaissent dans l'éditeur sans aucune colonne définie explicitement.  
  
-   Ajoutez de nouvelles colonnes aux sorties d'erreur simulées pour les erreurs au niveau des lignes. Normalement, plusieurs sorties dans le même **ExclusionGroup** ont le même jeu de colonnes de sortie. Toutefois, si vous créez une sortie d'erreur simulée, vous pouvez ajouter plus de colonnes pour contenir des informations d'erreur. Pour plus d’informations sur la façon dont le flux de données du moteur traite les lignes d’erreur, consultez [à l’aide de sorties d’erreur dans un composant de flux de données](../../integration-services/extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md). Notez que, dans le composant Script, vous devez écrire votre propre code pour remplir les colonnes supplémentaires à l'aide des informations d'erreur appropriées. Pour plus d’informations, consultez [en simulant une sortie d’erreur du composant de Script](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).  
  
 Pour plus d’informations sur la **entrées et sorties** page de la **éditeur de Transformation de Script**, consultez [éditeur de Transformation de Script &#40; les entrées et sorties de Page &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-inputs-and-outputs-page.md).  
  
### <a name="adding-variables"></a>Ajout de variables  
 Si vous souhaitez utiliser des variables existantes dans votre script, vous pouvez les ajouter dans le **ReadOnlyVariables** et **ReadWriteVariables** des champs de propriété sur le **Script** page de la **éditeur de Transformation de Script**.  
  
 Lorsque vous ajoutez plusieurs variables dans les champs de propriété, séparez les noms de variables par des virgules. Vous pouvez également sélectionner plusieurs variables en cliquant sur le bouton de sélection (**...** ) situé en regard du **ReadOnlyVariables** et **ReadWriteVariables** champs de propriété, puis en sélectionnant les variables dans le **sélectionner des variables** boîte de dialogue.  
  
 Pour obtenir des informations générales sur l’utilisation de variables avec le composant Script, consultez [à l’aide de Variables dans le composant Script](../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).  
  
 Pour plus d’informations sur la **Script** page de la **éditeur de Transformation de Script**, consultez [éditeur de Transformation de Script &#40; Page script &#41; ](../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
## <a name="scripting-a-synchronous-transformation-component-in-code-design-mode"></a>Script d'un composant de transformation synchrone en mode Création du code  
 Après avoir configuré les métadonnées du composant, vous pouvez écrire votre script personnalisé. Dans le **éditeur de Transformation de Script**, dans le **Script** , cliquez sur **modifier le Script** pour ouvrir le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE où vous pouvez ajouter votre script personnalisé. Le langage de script que vous utilisez varie selon que vous avez sélectionné [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual c# comme langage de script pour le **ScriptLanguage** propriété sur le **Script** page.  
  
 Pour obtenir des informations importantes qui s’applique à tous les types de composants créés à l’aide du composant Script, consultez [de codage et débogage du composant Script](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="understanding-the-auto-generated-code"></a>Fonctionnement du code généré automatiquement  
 Lorsque vous ouvrez l’IDE VSTA après avoir créé et configuré un composant de transformation, le texte modifiable **ScriptMain** classe s’affiche dans l’éditeur de code avec un stub pour le **ProcessInputRow** (méthode). Le **ScriptMain** classe est l’emplacement où vous allez écrire votre code personnalisé, et **ProcessInputRow** est la méthode la plus importante dans un composant de transformation.  
  
 Si vous ouvrez la fenêtre **Explorateur de projets** dans VSTA, vous constatez que le composant Script a également généré des éléments de projet **BufferWrapper** et **ComponentWrapper** en lecture seule. Le **ScriptMain** classe hérite de la **UserComponent** classe dans le **ComponentWrapper** élément de projet.  
  
 Au moment de l’exécution, le moteur de flux de données appelle la **ProcessInput** méthode dans le **UserComponent** classe, qui remplace le <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> méthode de la <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> classe parente. Le **ProcessInput** méthode parcourt à son tour les lignes dans la mémoire tampon d’entrée et appelle la **ProcessInputRow** méthode une fois pour chaque ligne.  
  
### <a name="writing-your-custom-code"></a>Écriture du code personnalisé  
 Un composant de transformation à sorties synchrones constitue le plus simple à écrire de tous les composants de flux de données. Par exemple, l'exemple à sortie unique présenté ultérieurement dans cette rubrique se compose du code personnalisé suivant :  
  
```vb  
Row.City = UCase(Row.City)  
```  
  
```csharp  
Row.City = (Row.City).ToUpper();  
  
```  
  
 Pour terminer la création d’un composant de transformation synchrone personnalisé, vous utilisez la **ProcessInputRow** méthode pour transformer les données dans chaque ligne de la mémoire tampon d’entrée. Le moteur de flux de données passe ce tampon, lorsqu'il est complet, au composant suivant dans le flux de données.  
  
 Selon vos besoins, vous pouvez également écrire un script dans le **PreExecute** et **PostExecute** méthodes, disponibles dans le **ScriptMain** (classe), pour effectuer un traitement préliminaire ou final.  
  
### <a name="working-with-multiple-outputs"></a>Utilisation de plusieurs sorties  
 La direction de lignes d'entrée vers l'une de deux sorties possibles ne requiert pas beaucoup plus de code personnalisé que le scénario de la sortie unique présenté précédemment. Par exemple, l'exemple à deux sorties présenté ultérieurement dans cette rubrique se compose du code personnalisé suivant :  
  
```vb  
Row.City = UCase(Row.City)  
If Row.City = "REDMOND" Then  
    Row.DirectRowToMyRedmondAddresses()  
Else  
    Row.DirectRowToMyOtherAddresses()  
End If  
```  
  
```csharp  
Row.City = (Row.City).ToUpper();  
  
if (Row.City=="REDMOND")  
{  
    Row.DirectRowToMyRedmondAddresses();  
}  
else  
{  
    Row.DirectRowToMyOtherAddresses();  
}  
```  
  
 Dans cet exemple, le composant Script génère le **DirectRowTo\<OutputBufferX >** méthodes pour vous, basées sur les noms des sorties que vous avez configuré. Vous pouvez utiliser un code similaire pour diriger des lignes d'erreur vers une sortie d'erreur simulée.  
  
## <a name="examples"></a>Exemples  
 Ces exemples présentent le code personnalisé requis dans le **ScriptMain** classe pour créer un composant de transformation synchrone.  
  
> [!NOTE]  
>  Ces exemples utilisent la **Person.Address** de table dans le **AdventureWorks** exemple de base de données et transmettent ses première et quatrième colonnes, le **intAddressID** et **nvarchar (30) Ville** colonnes, dans le flux de données. Les mêmes données sont utilisées dans les exemples de source, transformation et destination de cette section. Des conditions préalables et des hypothèses supplémentaires sont documentées pour chaque exemple.  
  
### <a name="single-output-synchronous-transformation-example"></a>Exemple de transformation synchrone à sortie unique  
 Cet exemple présente un composant de transformation synchrone à sortie unique. Cette transformation passe via le **AddressID** colonne et convertit le **Ville** colonne en majuscules.  
  
 Si vous souhaitez exécuter cet exemple de code, vous devez configurer le package et le composant comme suit :  
  
1.  Ajoutez un nouveau composant Script à l'aire du concepteur de flux de données et configurez-le en tant que transformation.  
  
2.  Connectez la sortie d'une source ou d'une autre transformation au nouveau composant de transformation dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Cette sortie doit fournir des données à partir de la **Person.Address** table de la **AdventureWorks** base de données qui contient le **AddressID** et **Ville** colonnes.  
  
3.  Ouvrez l' **Éditeur de transformation de script**. Sur le **colonnes d’entrée** page, sélectionnez le **AddressID** et **Ville** colonnes. Marque le **Ville** colonne en lecture/écriture.  
  
4.  Sur le **entrées et sorties** page, renommez l’entrée et de sortie avec des noms plus descriptifs, tels que **MyAddressInput** et **MyAddressOutput**. Notez que la **SynchronousInputID** de la sortie correspond à la **ID** de l’entrée. Par conséquent, vous n'avez pas à ajouter et configurer des colonnes de sortie.  
  
5.  Dans la page **Script** , cliquez sur **Modifier le script** , puis entrez le script suivant. Ensuite, fermez l'environnement de développement de script et l' **Éditeur de transformation de script**.  
  
6.  Créer et configurer un composant de destination qui attend le **AddressID** et **Ville** colonnes, comme un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, ou l’exemple de composant de destination présenté dans [création d’une Destination avec le composant Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md). Connectez ensuite la sortie de la transformation au composant de destination. Vous pouvez créer une table de destination en exécutant la commande suivante [!INCLUDE[tsql](../../includes/tsql-md.md)] dans les **AdventureWorks** base de données :  
  
    ```sql
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
7.  Exécutez l'exemple.  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
        Row.City = UCase(Row.City)  
  
    End Sub  
  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
  
{  
    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
    {  
  
        Row.City = (Row.City).ToUpper();  
  
    }  
  
}  
```  
  
### <a name="two-output-synchronous-transformation-example"></a>Exemple de transformation synchrone à deux sorties  
 Cet exemple présente un composant de transformation synchrone à deux sorties. Cette transformation passe via le **AddressID** colonne et convertit le **Ville** colonne en majuscules. Si le nom de la ville est Redmond, l'exemple dirige la ligne vers une seule sortie ; il dirige toutes les autres lignes vers une autre sortie.  
  
 Si vous souhaitez exécuter cet exemple de code, vous devez configurer le package et le composant comme suit :  
  
1.  Ajoutez un nouveau composant Script à l'aire du concepteur de flux de données et configurez-le en tant que transformation.  
  
2.  Connectez la sortie d'une source ou d'une autre transformation au nouveau composant de transformation dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Cette sortie doit fournir des données à partir de la **Person.Address** table de la **AdventureWorks** base de données exemple contienne au moins les **AddressID** et **Ville** colonnes.  
  
3.  Ouvrez l' **Éditeur de transformation de script**. Sur le **colonnes d’entrée** page, sélectionnez le **AddressID** et **Ville** colonnes. Marque le **Ville** colonne en lecture/écriture.  
  
4.  Sur le **entrées et sorties** page, créez une deuxième sortie. Après avoir ajouté la nouvelle sortie, assurez-vous que vous définissez son **SynchronousInputID** à la **ID** de l’entrée. Cette propriété est déjà définie sur la première sortie, créée par défaut. Pour chaque sortie, définir le **ExclusionGroup** propriété la même valeur différente de zéro pour indiquer que vous allez fractionner les lignes d’entrée entre deux sorties s’excluent mutuellement. Il n'est pas nécessaire d'ajouter des colonnes de sortie aux sorties.  
  
5.  Renommer de l’entrée et les sorties avec des noms plus descriptifs, tels que **MyAddressInput**, **MyRedmondAddresses**, et **MyOtherAddresses**.  
  
6.  Dans la page **Script** , cliquez sur **Modifier le script** , puis entrez le script suivant. Ensuite, fermez l'environnement de développement de script et l' **Éditeur de transformation de script**.  
  
7.  Créer et configurer deux composants de destination qui attendent le **AddressID** et **Ville** colonnes, comme un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, une destination de fichier plat ou l’exemple de composant de destination présenté dans [création d’une Destination avec le composant Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md). Puis connectez chacune des sorties de la transformation à l'un des composants de destination. Vous pouvez créer des tables de destination en exécutant un [!INCLUDE[tsql](../../includes/tsql-md.md)] commande semblable à la suivante (avec les noms de table unique) dans le **AdventureWorks** base de données :  
  
    ```sql
    CREATE TABLE [Person].[Address2](  
        [AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL  
    ```  
  
8.  Exécutez l'exemple.  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
        Row.City = UCase(Row.City)  
  
        If Row.City = "REDMOND" Then  
            Row.DirectRowToMyRedmondAddresses()  
        Else  
            Row.DirectRowToMyOtherAddresses()  
        End If  
  
    End Sub  
  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
  
public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
    {  
  
        Row.City = (Row.City).ToUpper();  
  
        if (Row.City == "REDMOND")  
        {  
            Row.DirectRowToMyRedmondAddresses();  
        }  
        else  
        {  
            Row.DirectRowToMyOtherAddresses();  
        }  
  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des Transformations synchrones et asynchrones] (~/integration-services/understanding-synchronous-and-asynchronous-transformations.md   
 [Création d’une Transformation asynchrone avec le composant Script] (~/integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md   
 [Développement d’un composant de Transformation personnalisé à sorties synchrones] (~/integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md  
  
  



