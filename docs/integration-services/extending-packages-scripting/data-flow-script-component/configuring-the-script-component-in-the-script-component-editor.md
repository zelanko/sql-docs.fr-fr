---
title: "Configuration du composant Script dans l’éditeur de composant Script | Documents Microsoft"
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
- SSIS Script component
- Script Component Editor
- SSIS Script component, configuring
- Script component [Integration Services], configuring
ms.assetid: 586dd799-f383-4d6d-b1a1-f09233d14f0a
caps.latest.revision: 46
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8488fcc7d402430f66b9b9018b31956a5a1d8383
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="configuring-the-script-component-in-the-script-component-editor"></a>Configuration du composant Script dans l'éditeur de composant de script
  Avant d’écrire un code personnalisé dans le composant Script, vous devez sélectionner le type de composant de flux de données que vous souhaitez créer : source, transformation ou destination, puis configurez les métadonnées du composant et les propriétés dans le **éditeur de Transformation de Script**.  
  
## <a name="selecting-the-type-of-component-to-create"></a>Sélection du type de composant à créer  
 Lorsque vous ajoutez un composant de Script au volet flux de données de [!INCLUDE[ssIS](../../../includes/ssis-md.md)] concepteur, le **sélectionner le Type de composant Script** boîte de dialogue s’affiche. Préconfigurez le composant en tant que source, transformation ou destination. Après avoir effectué cette sélection initiale effectuée, vous pouvez continuer à configurer le composant dans le **éditeur de Transformation de Script**.  
  
 Pour définir le langage de script par défaut pour le composant de Script, utilisez la **langage de script** option sur le **général** page de la **Options** boîte de dialogue. Pour plus d'informations, consultez [General Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx).  
  
## <a name="understanding-the-two-design-time-modes"></a>Fonctionnement des deux modes au moment du design  
 Dans le Concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)], le composant Script propose deux modes : le mode Création des métadonnées et le mode Création du code.  
  
 Lorsque vous ouvrez le **éditeur de Transformation de Script**, le composant entre le mode Création de métadonnées. Ce mode vous permet de sélectionner des colonnes d'entrée et d'ajouter ou configurer des sorties et des colonnes de sortie, mais il ne vous permet pas d'écrire du code. Après avoir configuré les métadonnées du composant, vous pouvez basculer en mode Création de code afin d'écrire le script.  
  
 Lorsque vous basculez en mode de conception de code en cliquant sur **modifier le Script**, le composant Script verrouille les métadonnées pour empêcher toute modification supplémentaire, puis génère automatiquement le code de base à partir des métadonnées des entrées et sorties. Une fois que le code généré automatiquement est complet, vous êtes en mesure d'entrer votre code personnalisé. Votre code utilise les classes de base générées automatiquement pour traiter les lignes d'entrée, accéder à des mémoires tampons et des colonnes dans les mémoires tampons et extraire du package des gestionnaires de connexions et des variables, sous la forme d'objets fortement typés.  
  
 Après avoir entré votre code personnalisé en mode Création de code, vous pouvez revenir en mode Création de métadonnées. Cette opération ne supprime pas le code entré, mais les modifications ultérieures apportées aux métadonnées provoquent la régénération de la classe de base. Après quoi, la validation de votre composant risque d'échouer du fait que des objets référencés par votre code personnalisé peuvent ne plus exister ou avoir été modifiés. Dans ce cas, vous devez corriger votre code manuellement afin qu'il puisse être correctement compilé avec la classe de base régénérée.  
  
## <a name="configuring-the-component-in-metadata-design-mode"></a>Configuration du composant en mode Création de métadonnées  
 Le mode Création de métadonnées vous permet de sélectionner des colonnes d'entrée; et d'ajouter et configurer des sorties et des colonnes de sortie, mais il ne vous permet pas d'écrire du code. Après avoir configuré les métadonnées du composant, basculez en mode Création de code afin d'écrire le script.  
  
 Les propriétés que vous devez configurer dans l'éditeur personnalisé dépendent de l'utilisation du composant Script. Le composant Script peut être configuré en tant que source, transformation ou destination. En fonction de l'utilisation qui est faite du composant, il prendra en charge une entrée ou des sorties, ou bien les deux. Le code personnalisé que vous écrivez traite les lignes et les colonnes d'entrée et de sortie.  
  
### <a name="inputs-columns-page-of-the-script-transformation-editor"></a>Page Colonnes d'entrée de l'Éditeur de transformation de script  
 Le **colonnes d’entrée** page de la **éditeur de Transformation de Script** s’affiche pour les transformations et destinations, mais pas pour les sources. Cette page vous permet de sélectionner les colonnes d'entrée disponibles à mettre à la disposition de votre script personnalisé et spécifier les accès en lecture seule ou en lecture/écriture à ces colonnes.  
  
 Dans le projet de code qui doit être généré en fonction de ces métadonnées, l'élément de projet BufferWrapper contient une classe pour chaque entrée, et cette classe contient des propriétés d'accesseur typées pour chaque colonne d'entrée sélectionnée. Par exemple, si vous sélectionnez un nombre entier **CustomerID** colonne et une chaîne **CustomerName** colonne d’une entrée nommée **CustomerInput**, l’élément de projet BufferWrapper contient une **CustomerInput** classe qui dérive de <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer>et le **CustomerInput** classe expose une propriété entière nommée **CustomerID** et une propriété de chaîne nommée **CustomerName**. Cette convention permet d'écrire du code avec la vérification de type tel que ci-dessous :  
  
```vb  
Dim currentCustomerID as Integer = CustomerInput.CustomerID  
Dim currentCustomerName as String = CustomerInput.CustomerName  
```  
  
 Pour plus d’informations sur la façon de configurer les colonnes d’entrée pour un type spécifique de composant de flux de données, consultez l’exemple approprié sous [développement des Types de composants Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).  
  
### <a name="inputs-and-outputs-page-of-the-script-transformation-editor"></a>Page Entrées et sorties de l'Éditeur de transformation de script  
 Le **entrées et sorties** page de la **éditeur de Transformation de Script** est affichée pour les sources, transformations et destinations. Cette page vous permet d'ajouter, supprimer et configurer des entrées, des sorties et des colonnes de sortie à utiliser dans votre script personnalisé, en tenant compte des contraintes suivantes :  
  
-   Lorsqu'il est utilisé en tant que source, le composant Script ne possède pas d'entrée et prend en charge plusieurs sorties.  
  
-   Lorsqu'il est utilisé en tant que transformation, le composant Script prend en charge une entrée et plusieurs sorties.  
  
-   Lorsqu'il est utilisé en tant que destination, le composant Script prend en charge une entrée et ne possède pas de sortie.  
  
 Dans le projet de code qui doit être généré en fonction de ces métadonnées, l'élément de projet BufferWrapper contient une classe pour chaque entrée et chaque sortie. Par exemple, si vous créez une sortie nommée **CustomerOutput**, l’élément de projet BufferWrapper contient une **CustomerOutput** classe qui dérive de <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer>et le **CustomerOutput** classe contiendra des propriétés d’accesseur typées pour chaque colonne de sortie créé.  
  
 Vous pouvez configurer les colonnes de sortie uniquement sur le **entrées et sorties** page. Vous pouvez sélectionner des colonnes d’entrée pour les transformations et destinations sur le **des colonnes d’entrée** page. Les propriétés d'accesseur typées créées dans l'élément de projet BufferWrapper sont en écriture seule pour les colonnes de sortie. Les propriétés d’accesseur pour les colonnes d’entrée seront en lecture seule ou lecture/écriture selon le type d’utilisation que vous avez sélectionné pour chaque colonne sur le **des colonnes d’entrée** page.  
  
 Pour plus d’informations sur la configuration des entrées et sorties pour un type spécifique de données de composant de flux de voir l’exemple approprié sous [développement des Types de composants Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).  
  
> [!NOTE]  
>  Bien qu'il soit impossible de configurer directement une sortie en tant que sortie d'erreur dans le composant Script pour la gestion automatique des lignes d'erreur, vous pouvez reproduire les fonctionnalités d'une sortie d'erreur en créant une sortie supplémentaire et en utilisant un script pour diriger des lignes vers cette sortie, le cas échéant. Pour plus d’informations, consultez [en simulant une sortie d’erreur du composant de Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).  
  
#### <a name="exclusiongroup-and-synchronousinputid-properties-of-outputs"></a>Propriétés ExclusionGroup et SynchronousInputID des sorties  
 Le **ExclusionGroup** propriété a une valeur non nulle uniquement dans les transformations à sorties synchrones, dans laquelle votre code effectue le filtrage ou la création de branche et dirige chaque ligne à une des sorties qui partagent le même non nulle **ExclusionGroup** valeur. Par exemple, la transformation peut diriger des lignes vers la sortie par défaut ou vers une sortie d'erreur. Lorsque vous créez des sorties supplémentaires pour ce scénario, veillez à définir la valeur de la **SynchronousInputID** propriété à l’entier qui correspond à la **ID** de l’entrée du composant.  
  
 Le **SynchronousInputID** propriété a une valeur non nulle uniquement dans les transformations à sorties synchrones. Si la valeur de cette propriété est zéro, cela signifie que la sortie est asynchrone. Pour une sortie synchrone, dans lequel les lignes sont transmises à la sortie sélectionnée ou des sorties, sans ajouter de nouvelles lignes, cette propriété doit contenir le **ID** de l’entrée du composant.  
  
> [!NOTE]  
>  Lorsque le **éditeur de Transformation de Script** crée la première sortie, l’éditeur attribue le **SynchronousInputID** propriété de la sortie à la **ID** de l’entrée du composant. Toutefois, lorsque l’éditeur crée les sorties suivantes, l’éditeur définit les **SynchronousInputID** propriétés de ces sorties à zéro.  
>   
>  Si vous créez un composant à sorties synchrones, chaque sortie doit avoir son **SynchronousInputID** propriété définie sur la **ID** de l’entrée du composant. Par conséquent, chaque sortie créée par l’éditeur après la première sortie doit avoir son **SynchronousInputID** valeur modifiée à partir de zéro pour le **ID** de l’entrée du composant.  
>   
>  Si vous créez un composant à sorties asynchrones, chaque sortie doit avoir son **SynchronousInputID** propriété définie à zéro. Par conséquent, la première sortie doit avoir son **SynchronousInputID** valeur modifiée à partir de la **ID** de l’entrée du composant à zéro.  
  
 Pour obtenir un exemple de diriger des lignes à un des deux sorties synchrones dans le composant Script, consultez [création d’une Transformation synchrone avec le composant de Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md).  
  
### <a name="object-names-in-generated-script"></a>Noms d'objets dans le script généré  
 Le composant Script analyse les noms des entrées et des sorties, ainsi que les noms des colonnes dans les entrées et sorties. Puis, en fonction de ces noms, il génère des classes et des propriétés dans l'élément de projet BufferWrapper. Si les noms trouvés contiennent des caractères qui n’appartiennent pas aux catégories Unicode **UppercaseLetter**, **LowercaseLetter**, **TitlecaseLetter**, **ModifierLetter**, **OtherLetter**, ou **DecimalDigitLetter**, les caractères non valides sont supprimés des noms générés. Par exemple, des espaces sont supprimés, par conséquent, deux colonnes qui ont le nom d’entrée **FirstName** et [**prénom**] sont interprétés comme ayant le nom de colonne **FirstName**, avec des résultats imprévisibles. Pour éviter cette situation, les noms des entrées et des sorties, ainsi que des colonnes d'entrée et de sortie, utilisés par le composant Script doivent comporter uniquement des caractères appartenant aux catégories Unicode répertoriées dans cette section.  
  
### <a name="script-page-of-the-script-transformation-editor"></a>Page Script de l'Éditeur de transformation de script  
 Sur le **Script** page de la **éditeur de tâche de Script**, vous affectez un nom unique et une description pour la tâche de Script. Vous pouvez également assigner des valeurs pour les propriétés suivantes.  
  
> [!NOTE]  
>  Dans [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] et les versions ultérieures, tous les scripts sont précompilés. Dans les versions précédentes, vous avez spécifié si les scripts étaient précompilés en définissant un **Precompile** propriété pour la tâche.  
  
#### <a name="validateexternalmetadata-property"></a>Propriété ValidateExternalMetadata  
 La valeur booléenne de la **ValidateExternalMetadata** propriété spécifie si le composant doit effectuer la validation par rapport à des sources de données externes au moment du design, ou s’il doit reporter la validation jusqu’au moment de l’exécution. Par défaut, la valeur de cette propriété est **True**; autrement dit, les métadonnées externes sont validée à la fois au moment du design et au moment de l’exécution. Vous voudrez définir la valeur de cette propriété sur **False** lorsqu’une source de données externe n’est pas disponible au moment du design : par exemple, lorsque le package télécharge la source ou crée la destination uniquement au moment de l’exécution.  
  
#### <a name="readonlyvariables-and-readwritevariables-properties"></a>Propriétés ReadOnlyVariables et ReadWriteVariables  
 Vous pouvez entrer des listes délimitées par des virgules de variables existantes comme valeurs de ces propriétés pour rendre les variables accessibles en lecture seule ou en lecture/écriture dans le code du composant Script. Les variables sont accessibles dans le code par le biais des propriétés <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReadOnlyVariables%2A> et <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReadWriteVariables%2A> de la classe de base générée automatiquement. Pour plus d’informations, consultez [à l’aide de Variables dans le composant Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).  
  
> [!NOTE]  
>  Les noms de variable respectent la casse.  
  
#### <a name="scriptlanguage"></a>ScriptLanguage  
 Vous pouvez sélectionner [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic ou [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# comme langage de programmation du composant Script.  
  
#### <a name="edit-script-button"></a>Bouton Modifier le script  
 Le **modifier le Script** bouton ouvre le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] outils IDE d’Applications (VSTA) dans laquelle vous écrivez votre script personnalisé. Pour plus d’informations, consultez [de codage et débogage du composant Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="connection-managers-page-of-the-script-transformation-editor"></a>Page Gestionnaires de connexions de l'Éditeur de transformation de script  
 Sur le **gestionnaires de connexions** page de la **éditeur de Transformation de Script**, vous ajoutez et supprimez les gestionnaires de connexions que vous souhaitez utiliser dans votre script personnalisé. En principe, vous devez référencer des gestionnaires de connexions lorsque vous créez un composant source ou un composant de destination.  
  
 Dans le code de projet sera généré en fonction de ces métadonnées, le **ComponentWrapper** élément de projet contient un **connexions** classe de collection qui a une propriété d’accesseur typées pour chaque gestionnaire de connexions sélectionné. Chaque propriété d'accesseur typée porte le même nom que le gestionnaire de connexions lui-même et retourne une référence à ce dernier sous la forme d'une instance de <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSConnectionManager100>. Par exemple, si vous avez ajouté un gestionnaire de connexions nommé `MyADONETConnection` sur la **gestionnaires de connexions** page de l’éditeur, vous pouvez obtenir une référence au Gestionnaire de connexions dans votre script en utilisant le code suivant :  
  
```vb  
Dim myADONETConnectionManager As IDTSConnectionManager100 = _  
    Me.Connections.MyADONETConnection  
```  
  
 Pour plus d’informations, consultez [connexion aux Sources de données dans le composant Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Codage et débogage du composant Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  

