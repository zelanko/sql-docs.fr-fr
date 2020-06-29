---
title: Amélioration d’une sortie d’erreur à l’aide du composant Script | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- transformations [Integration Services], components
- Script component [Integration Services], examples
- error outputs [Integration Services], enhancing
- Script component [Integration Services], transformation components
ms.assetid: f7c02709-f1fa-4ebd-b255-dc8b81feeaa5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 85978278c2a51cde45e18b742998b1f6229e8e7d
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85426966"
---
# <a name="enhancing-an-error-output-with-the-script-component"></a>Amélioration d'une sortie d'erreur à l'aide du composant Script
  Par défaut, les deux colonnes supplémentaires d'une sortie d'erreur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], ErrorCode et ErrorColumn, contiennent uniquement des codes numériques identifiant un numéro d'erreur et l'ID de la colonne dans laquelle l'erreur est survenue. L'usage de ces valeurs numériques peut être limité sans la description d'erreur correspondante.  
  
 Cette rubrique décrit comment ajouter une colonne de description d'erreur à des données de sortie d'erreur existantes dans le flux de données en utilisant le composant Script. L'exemple ajoute la description d'erreur qui correspond à un code d'erreur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] prédéfini spécifique à l'aide de la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> de l'interface <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>, disponible via la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> du composant Script.  
  
> [!NOTE]  
>  Si vous souhaitez créer un composant que vous pouvez réutiliser plus facilement dans plusieurs tâches de flux de données et plusieurs packages, utilisez le code présenté dans cet exemple de composant Script comme point de départ pour un composant de flux de données personnalisé. Pour plus d’informations, consultez [Développement d’un composant de flux de données personnalisé](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="example"></a>Exemple  
 L'exemple indiqué ici utilise un composant Script configuré en tant que transformation pour ajouter une colonne de description d'erreur à des données de sortie d'erreur existantes dans le flux de données.  
  
 Pour plus d’informations sur la configuration du composant script pour une utilisation en tant que transformation dans le workflow, consultez [création d’une transformation synchrone avec le composant script](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)et [création d’une transformation asynchrone à l’aide du composant script](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).  
  
#### <a name="to-configure-this-script-component-example"></a>Pour configurer cet exemple de composant Script  
  
1.  Avant de créer le composant Script, configurez un composant en amont dans le flux de données pour rediriger des lignes vers sa sortie d'erreur lorsqu'une erreur ou troncation se produit. À des fins de test, vous pouvez configurer un composant de manière à garantir que des erreurs se produiront, par exemple en configurant une transformation de recherche entre deux tables où la recherche échouera.  
  
2.  Ajoutez un nouveau composant Script à l'aire du concepteur de flux de données et configurez-le en tant que transformation.  
  
3.  Connectez la sortie d'erreur du composant en amont au nouveau composant Script.  
  
4.  Ouvrez l’**Éditeur de transformation de script**, puis dans la page **Script**, au niveau de la propriété **ScriptLanguage**, sélectionnez le langage de script.  
  
5.  Cliquez sur **Modifier le script** pour ouvrir l’environnement de développement intégré [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) et ajouter l’exemple de code indiqué ci-dessous.  
  
6.  Fermez VSTA.  
  
7.  Dans l’éditeur de transformation de script, dans la page **colonnes d’entrée** , sélectionnez la colonne ErrorCode.  
  
8.  Sur la page **entrées et sorties** , ajoutez une nouvelle colonne de sortie de type `String` nommée **ErrorDescription**. Augmentez la longueur par défaut de la nouvelle colonne à 255 pour prendre en charge les longs messages.  
  
9. Fermez l’**Éditeur de transformation de script**.  
  
10. Attachez la sortie du composant Script à une destination appropriée. Les destinations de fichiers plats sont les plus faciles à configurer à des fins de test ad hoc.  
  
11. Exécutez le package.  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
  Row.ErrorDescription = _  
    Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
  
    End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
{  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
  Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
  
    }  
}  
  
```  
  
![Icône de Integration Services (petite)](../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs dans les données](../data-flow/error-handling-in-data.md)   
 [Utilisation de sorties d’erreur dans un composant de flux de données](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)   
 [Création d’une transformation synchrone à l’aide du composant Script](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) 
  
  
