---
title: Mise à niveau de la version d’un composant de flux de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.topic: reference
helpviewer_keywords:
- PerformUpgrade method
- custom data flow components [Integration Services], upgrading version
- data flow components [Integration Services], upgrading version
- upgrading data flow components [Integration Services]
ms.assetid: c2a298c6-01b3-4ad1-884d-6108165eb56e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c4f4847df58b1b65248dafc908aa39243ff10c36
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48052929"
---
# <a name="upgrading-the-version-of-a-data-flow-component"></a>Mise à niveau de la version d'un composant de flux de données
  Les packages créés avec une version antérieure de votre composant peuvent contenir des métadonnées qui ne sont plus valides, telles que des propriétés personnalisées dont l'utilisation a été modifiée dans les versions plus récentes du composant. Vous pouvez remplacer la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> de la classe de base <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> pour mettre à jour les métadonnées précédemment enregistrées dans les packages plus anciens afin de refléter les propriétés actuelles de votre composant.  
  
> [!NOTE]  
>  Lorsque vous recompilez un composant personnalisé pour une nouvelle version de [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], vous n'avez pas à modifier la valeur de la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A> si les propriétés du composant n'ont pas changé.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant contient le code de la version 2.0 d'un composant de flux de données fictif. Le nouveau numéro de version est défini dans la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A> de l'objet <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>. Le composant possède une propriété qui définit la manière dont les valeurs numériques qui dépassent un seuil doivent être gérées. Dans la version 1.0 du composant fictif, cette propriété a été nommée `RaiseErrorOnInvalidValue` et acceptait une valeur booléenne True ou False. Dans la version 2.0 du composant fictif, la propriété a été renommée `InvalidValueHandling` et accepte l'une des quatre valeurs possibles d'une énumération personnalisée.  
  
 La méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> remplacée dans l'exemple suivant effectue les actions suivantes :  
  
-   Obtient la version actuelle du composant.  
  
-   Obtient la valeur de l'ancienne propriété personnalisée.  
  
-   Supprime l'ancienne propriété de la collection de propriétés personnalisées.  
  
-   Définit la valeur de la nouvelle propriété personnalisée selon la valeur de l'ancienne propriété, si possible.  
  
-   Définit les métadonnées de version sur la version actuelle du composant.  
  
> [!NOTE]  
>  Le moteur de flux de données transmet son propre numéro de version dans la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> dans le paramètre *pipelineVersion*. Ce paramètre est inutile dans la version 1.0 de [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], mais peut s'avérer utile dans les versions suivantes.  
  
 L'exemple de code utilise uniquement les deux valeurs d'énumération qui mappent directement aux valeurs booléennes antérieures de la propriété personnalisée. Les utilisateurs peuvent sélectionner les autres valeurs d'énumération disponibles via l'interface utilisateur personnalisée du composant, dans l'éditeur avancé ou par programme. Pour plus d’informations sur l’affichage des valeurs d’énumération pour une propriété personnalisée dans l’Éditeur avancé, consultez « Création de propriétés personnalisées » dans [Méthodes de conception d’un composant de flux de données](design-time-methods-of-a-data-flow-component.md).  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
<DtsPipelineComponent(ComponentType:=ComponentType.Transform, CurrentVersion:=2)> _  
Public Class PerformUpgrade  
  Inherits PipelineComponent  
  
  ' Define the set of possible values for the new custom property.  
  Private Enum InvalidValueHandling  
    Ignore  
    FireInformation  
    FireWarning  
    FireError  
  End Enum  
  
  Public Overloads Overrides Sub PerformUpgrade(ByVal pipelineVersion As Integer)  
  
    ' Obtain the current component version from the attribute.  
    Dim componentAttribute As DtsPipelineComponentAttribute = _  
      CType(Attribute.GetCustomAttribute(Me.GetType, _  
      GetType(DtsPipelineComponentAttribute), False), _  
      DtsPipelineComponentAttribute)  
    Dim currentVersion As Integer = componentAttribute.CurrentVersion  
  
    ' If the component version saved in the package is less than  
    '  the current version, Version 2, perform the upgrade.  
    If ComponentMetaData.Version < currentVersion Then  
  
      ' Get the current value of the old custom property, RaiseErrorOnInvalidValue,   
      ' and then remove the property from the custom property collection.  
      Dim oldValue As Boolean = False  
      Try  
        Dim oldProperty As IDTSCustomProperty100 = _  
          ComponentMetaData.CustomPropertyCollection("RaiseErrorOnInvalidValue")  
        oldValue = CType(oldProperty.Value, Boolean)  
        ComponentMetaData.CustomPropertyCollection.RemoveObjectByIndex("RaiseErrorOnInvalidValue")  
      Catch ex As Exception  
        ' If the old custom property is not available, ignore the error.  
      End Try  
  
      ' Set the value of the new custom property, InvalidValueHandling,  
      '  by using the appropriate enumeration value.  
      Dim newProperty As IDTSCustomProperty100 = _  
        ComponentMetaData.CustomPropertyCollection("InvalidValueHandling")  
      If oldValue = True Then  
        newProperty.Value = InvalidValueHandling.FireError  
      Else  
        newProperty.Value = InvalidValueHandling.Ignore  
      End If  
  
    End If  
  
    ' Update the saved component version metadata to the current version.  
    ComponentMetaData.Version = currentVersion  
  
  End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
[DtsPipelineComponent(ComponentType = ComponentType.Transform, CurrentVersion = 2)]  
public class PerformUpgradeCS :  
  PipelineComponent  
  
  // Define the set of possible values for the new custom property.  
{  
  private enum InvalidValueHandling  
  {  
    Ignore,  
    FireInformation,  
    FireWarning,  
    FireError  
  };  
  
  public override void PerformUpgrade(int pipelineVersion)  
  {  
  
    // Obtain the current component version from the attribute.  
    DtsPipelineComponentAttribute componentAttribute =   
      (DtsPipelineComponentAttribute)Attribute.GetCustomAttribute(this.GetType(), typeof(DtsPipelineComponentAttribute), false);  
    int currentVersion = componentAttribute.CurrentVersion;  
  
    // If the component version saved in the package is less than  
    //  the current version, Version 2, perform the upgrade.  
    if (ComponentMetaData.Version < currentVersion)  
  
    // Get the current value of the old custom property, RaiseErrorOnInvalidValue,   
    // and then remove the property from the custom property collection.  
    {  
      bool oldValue = false;  
      try  
      {  
        IDTSCustomProperty100 oldProperty =   
          ComponentMetaData.CustomPropertyCollection["RaiseErrorOnInvalidValue"];  
        oldValue = (bool)oldProperty.Value;  
        ComponentMetaData.CustomPropertyCollection.RemoveObjectByIndex("RaiseErrorOnInvalidValue");  
      }  
      catch (Exception ex)  
      {  
        // If the old custom property is not available, ignore the error.  
      }  
  
      // Set the value of the new custom property, InvalidValueHandling,  
      //  by using the appropriate enumeration value.  
      IDTSCustomProperty100 newProperty =   
         ComponentMetaData.CustomPropertyCollection["InvalidValueHandling"];  
      if (oldValue == true)  
      {  
        newProperty.Value = InvalidValueHandling.FireError;  
      }  
      else  
      {  
        newProperty.Value = InvalidValueHandling.Ignore;  
      }  
  
    }  
  
    // Update the saved component version metadata to the current version.  
    ComponentMetaData.Version = currentVersion;  
  
  }  
  
}  
```  
  
![Icône Integration Services (petite)](../../media/dts-16.gif "icône Integration Services (petite)")**rester jusqu'à la Date avec Integration Services** <br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
  
