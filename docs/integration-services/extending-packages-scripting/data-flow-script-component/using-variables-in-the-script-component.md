---
title: Utilisation de Variables dans le composant de Script | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Script component [Integration Services], using variables
ms.assetid: 92d1881a-1ef1-43ae-b1ca-48d0536bdbc2
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: bac1e6d96e872be0355282c3e12fc81054ca41cd
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="using-variables-in-the-script-component"></a>Utilisation de variables dans le composant Script
  Les variables stockent les valeurs qu'un package et ses conteneurs, tâches et gestionnaires d'événements peuvent utiliser au moment de l'exécution. Pour plus d’informations, consultez [Integration Services &#40;SSIS&#41; Variables](../../../integration-services/integration-services-ssis-variables.md).  
  
 Vous pouvez définir des variables existantes disponibles pour en lecture seule ou en lecture/écriture par votre script personnalisé en entrant des listes délimitée par des virgules de variables dans le **ReadOnlyVariables** et **ReadWriteVariables** champs sur le **Script** page de la **éditeur de Transformation de Script**. N'oubliez pas que les noms de variables respectent la casse. Utilisez le **valeur** propriété en lecture et en écriture aux variables individuelles. Le composant Script gère tout le verrouillage sous-jacent requis quand votre script manipule les variables au moment de l'exécution.  
  
> [!IMPORTANT]  
>  La collection de **ReadWriteVariables** est disponible uniquement dans les **PostExecute** méthode pour optimiser les performances et réduire le risque de conflits de verrouillage. Par conséquent, vous ne pouvez pas incrémenter directement la valeur d'une variable de package à mesure que vous traitez chaque ligne de données. Incrémenter la valeur d’une variable locale à la place et définir la valeur de la variable de package à la valeur de la variable locale dans le **PostExecute** méthode une fois toutes les données ont été traitée. Vous pouvez également utiliser la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A> pour contourner cette limitation, comme décrit ultérieurement dans cette rubrique. Toutefois, l'écriture directe dans une variable de package au fut et à mesure du traitement de chaque ligne aura des effets négatifs sur les performances et augmentera le risque de conflits de verrouillage.  
  
 Pour plus d’informations sur la **Script** page de la **éditeur de Transformation de Script**, consultez [configuration du composant Script dans l’éditeur de composant Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md) et [éditeur de Transformation de Script &#40; Page script &#41; ](../../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
 Le composant Script crée un **Variables** classe de collection dans le **ComponentWrapper** élément de projet avec une propriété d’accesseur fortement typé pour la valeur de chaque variable préconfigurée où la propriété a le même nom que la variable elle-même. Cette collection est exposée via le **Variables** propriété de la **ScriptMain** classe. La propriété de l'accesseur fournit une autorisation de lecture seule ou de lecture/écriture à la valeur de la variable. Par exemple, si vous avez ajouté une variable de type entier nommée `MyIntegerVariable` à la **ReadOnlyVariables** la liste, vous pouvez récupérer sa valeur dans votre script en utilisant le code suivant :  
  
 `Dim myIntegerVariableValue As Integer = Me.Variables.MyIntegerVariable`  
  
 Vous pouvez également utiliser la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A>, accessible en appelant `Me.VariableDispenser`, pour utiliser des variables dans le composant Script. Dans ce cas, vous n'utilisez pas les propriétés de l'accesseur typé et nommé pour les variables, mais vous accédez directement aux variables. Lorsque vous utilisez la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A>, vous devez gérer à la fois la sémantique de verrouillage et la conversion des types de données pour les valeurs de variables dans votre propre code. Vous devez utiliser la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A> au lieu des propriétés de l'accesseur nommé et typé si vous souhaitez utiliser une variable qui n'est pas disponible au moment du design mais qui est créée par programme au moment de l'exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services &#40; SSIS &#41; Variables](../../../integration-services/integration-services-ssis-variables.md)   
 [Utiliser des Variables dans des Packages](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)  
  
  
