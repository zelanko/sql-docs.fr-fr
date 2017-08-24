---
title: "Amélioration de la sortie d’erreur avec le composant Script | Documents Microsoft"
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
helpviewer_keywords:
- transformations [Integration Services], components
- Script component [Integration Services], examples
- error outputs [Integration Services], enhancing
- Script component [Integration Services], transformation components
ms.assetid: f7c02709-f1fa-4ebd-b255-dc8b81feeaa5
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 3881b57f4089dbb075d019f9bd1a88a96a307b72
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="enhancing-an-error-output-with-the-script-component"></a>Amélioration d'une sortie d'erreur à l'aide du composant Script
  Par défaut, les deux colonnes supplémentaires dans un [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sortie d’erreur, ErrorCode et ErrorColumn, contiennent uniquement des codes numériques identifiant un numéro d’erreur et l’ID de la colonne dans laquelle l’erreur s’est produite. Ces valeurs numériques peuvent être limité sans la description de l’erreur et le nom de la colonne.  
  
 Cette rubrique décrit comment ajouter la description d’erreur et le nom de colonne à des données de sortie d’erreur existantes dans le flux de données à l’aide du composant Script. L'exemple ajoute la description d'erreur qui correspond à un code d'erreur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] prédéfini spécifique à l'aide de la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> de l'interface <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>, disponible via la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> du composant Script. L’exemple ajoute le nom de colonne qui correspond à l’ID de lignage capturées à l’aide de la <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData130.GetIdentificationStringByID%2A> méthode de la même interface.  
  
> [!NOTE]  
>  Si vous souhaitez créer un composant que vous pouvez réutiliser plus facilement dans plusieurs tâches de flux de données et plusieurs packages, utilisez le code présenté dans cet exemple de composant Script comme point de départ pour un composant de flux de données personnalisé. Pour plus d’informations, consultez [Développement d’un composant de flux de données personnalisé](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise un composant Script configuré en tant que transformation pour ajouter la description d’erreur et le nom de colonne à des données de sortie d’erreur existantes dans le flux de données.  
  
 Pour plus d’informations sur la façon de configurer le composant de Script pour une utilisation en tant que transformation dans le flux de données, consultez [création d’une Transformation synchrone avec le composant Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) et [création d’une Transformation asynchrone avec le composant de Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).  
  
#### <a name="to-configure-this-script-component-example"></a>Pour configurer cet exemple de composant Script  
  
1.  Avant de créer le composant Script, configurez un composant en amont dans le flux de données pour rediriger des lignes vers sa sortie d'erreur lorsqu'une erreur ou troncation se produit. À des fins de test, vous pouvez configurer un composant de manière à garantir que des erreurs se produiront, par exemple en configurant une transformation de recherche entre deux tables où la recherche échouera.  
  
2.  Ajoutez un nouveau composant Script à l'aire du concepteur de flux de données et configurez-le en tant que transformation.  
  
3.  Connectez la sortie d'erreur du composant en amont au nouveau composant Script.  
  
4.  Ouvrez le **éditeur de Transformation de Script**et sur le **Script** page, pour le **ScriptLanguage** propriété, sélectionnez le langage de script.  
  
5.  Cliquez sur **modifier le Script** pour ouvrir le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE et ajoutez l’exemple de code indiqué ci-dessous.  
  
6.  Fermez VSTA.  
  
7.  Dans l’éditeur de Transformation de Script, sur le **colonnes d’entrée** , sélectionnez les colonnes ErrorCode et ErrorColumn.  
  
8.  Sur le **entrées et sorties** , ajoutez deux nouvelles colonnes.  
  
    -   Ajouter une nouvelle colonne de sortie de type **chaîne** nommé **ErrorDescription**. Augmentez la longueur par défaut de la nouvelle colonne à 255 pour prendre en charge les longs messages.  
  
    -   Ajouter une autre nouvelle colonne de sortie de type **chaîne** nommé **ColumnName**. Augmentez la longueur par défaut de la nouvelle colonne à 255 pour prendre en charge les valeurs de type long.  
  
9. Fermer le **éditeur de Transformation de Script.**  
  
10. Attachez la sortie du composant Script à une destination appropriée. Les destinations de fichiers plats sont les plus faciles à configurer à des fins de test ad hoc.  
  
11. Exécutez le package.  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
      Row.ErrorDescription = _  
        Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
  
      Dim componentMetaData130 = TryCast(Me.ComponentMetaData, IDTSComponentMetaData130)  
      If componentMetaData130 IsNot Nothing Then  
        Row.ColumnName = componentMetaData130.GetIdentificationStringByID(Row.ErrorColumn)  
         End If  
  
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
  
      var componentMetaData130 = this.ComponentMetaData as IDTSComponentMetaData130;  
      if (componentMetaData130 != null)  
        {  
            Row.ColumnName = componentMetaData130.GetIdentificationStringByID(Row.ErrorColumn);  
        }  
  
    }  
}  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs dans les données](../../integration-services/data-flow/error-handling-in-data.md)   
 [À l’aide de sorties d’erreur dans un composant de flux de données](../../integration-services/extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)   
 [Création d’une Transformation synchrone avec le composant de Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)   
  
  
