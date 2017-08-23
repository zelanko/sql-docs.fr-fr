---
title: "Composant de flux de déclenchement et définition d’événements dans les données | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- CSharp
helpviewer_keywords:
- data flow components [Integration Services], events
- events [Integration Services], custom
- custom events [Integration Services]
- custom data flow components [Integration Services], events
- events [Integration Services], raising
- predefined events [Integration Services]
ms.assetid: 1d8c5358-9384-47a8-b7cb-7b0650384119
caps.latest.revision: 51
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a900b27c9056d95fb2284d8ba9d6b09d9c6635b5
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="raising-and-defining-events-in-a-data-flow-component"></a>Déclenchement et définition d'événements dans un composant de flux de données
  Les développeurs de composants peuvent déclencher un sous-ensemble des événements définis dans l'interface <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> en appelant les méthodes exposées sur la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>. Vous pouvez également définir des événements personnalisés à l'aide de la collection <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A>, puis les déclencher pendant l'exécution en utilisant la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>. Cette section décrit comment créer et déclencher un événement. Elle fournit également des conseils sur l'opportunité de déclencher des événements au moment de la conception.  
  
## <a name="raising-events"></a>Le déclenchement d’événements  
 Composants de déclenchent des événements à l’aide de la **incendie\<X >** méthodes de la <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface. Vous pouvez déclencher des événements pendant la conception et l'exécution de composants. En général, les méthodes <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> et <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A> sont appelées pendant la validation, lors de la conception de composants. Ces événements affichent des messages dans la **liste d’erreurs** volet de [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] et fournir des commentaires aux utilisateurs du composant lorsqu’un composant est configuré correctement.  
  
 Les composants peuvent également déclencher des événements à tout moment pendant l'exécution. Les événements permettent aux développeurs de composants de fournir des commentaires aux utilisateurs du composant pendant son exécution. L'appel de la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> pendant l'exécution risque de provoquer l'échec du package.  
  
## <a name="defining-and-raising-custom-events"></a>Définition et déclenchement d'événements personnalisés  
  
### <a name="defining-a-custom-event"></a>Définition d'un événement personnalisé  
 L'appel de la méthode <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> de la collection <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> permet de créer des événements personnalisés. Cette collection est définie par la tâche de flux de données et fournie en tant que propriété au développeur de composants par le biais de la classe de base <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>. Cette classe contient des événements personnalisés définis par la tâche de flux de données et des événements personnalisés définis par le composant pendant l'exécution de la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A>.  
  
 Les événements personnalisés d'un composant ne sont pas conservés dans le package XML. Par conséquent, la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> est appelée pendant la conception et l'exécution pour permettre au composant de définir les événements qu'il déclenche.  
  
 Le *allowEventHandlers* paramètre de la <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> méthode spécifie si le composant autorise <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> objets doit être créé pour l’événement. Notez que les <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> sont synchrones. Par conséquent, le composant ne recommence à s'exécuter qu'après la fin de l'exécution d'un <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> attaché à l'événement personnalisé. Si le *allowEventHandlers* paramètre est **true**, chaque paramètre de l’événement est effectuée automatiquement la disposition des <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> objets via des variables qui sont créés et renseignés automatiquement par le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime.  
  
### <a name="raising-a-custom-event"></a>Déclenchement d'un événement personnalisé  
 Les composants déclenchent des événements personnalisés en appelant la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> et en fournissant le nom, le texte et les paramètres de l'événement. Si le *allowEventHandlers* paramètre est **true**, tout <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> qui sont créés pour l’événement personnalisé sont exécutés par le [!INCLUDE[ssIS](../../../includes/ssis-md.md)] moteur d’exécution.  
  
### <a name="custom-event-sample"></a>Exemple d'événement personnalisé  
 L'exemple de code suivant présente un composant qui définit un événement personnalisé pendant l'exécution de la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A>, puis qui déclenche l'événement au moment de l'exécution en appelant la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>.  
  
```csharp  
public override void RegisterEvents()  
{  
    string [] parameterNames = new string[2]{"RowCount", "StartTime"};  
    ushort [] parameterTypes = new ushort[2]{ DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)};  
    string [] parameterDescriptions = new string[2]{"The number of rows to sort.", "The start time of the Sort operation."};  
    EventInfos.Add("StartingSort","Fires when the component begins sorting the rows.",false,ref parameterNames, ref paramterTypes, ref parameterDescriptions);  
}  
public override void ProcessInput(int inputID, PipelineBuffer buffer)  
{  
    while (buffer.NextRow())  
    {  
       // Process buffer rows.  
    }  
  
    IDTSEventInfo100 eventInfo = EventInfos["StartingSort"];  
    object []arguments = new object[2]{buffer.RowCount, DateTime.Now };  
    ComponentMetaData.FireCustomEvent("StartingSort", "Beginning sort operation.", ref arguments, ComponentMetaData.Name, ref FireSortEventAgain);  
}  
```  
  
```vb  
Public  Overrides Sub RegisterEvents()   
  Dim parameterNames As String() = New String(2) {"RowCount", "StartTime"}   
  Dim parameterTypes As System.UInt16() = New System.UInt16(2) {DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)}   
  Dim parameterDescriptions As String() = New String(2) {"The number of rows to sort.", "The start time of the Sort operation."}   
  EventInfos.Add("StartingSort", "Fires when the component begins sorting the rows.", False, parameterNames, paramterTypes, parameterDescriptions)   
End Sub   
  
Public  Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)   
  While buffer.NextRow   
  End While   
  Dim eventInfo As IDTSEventInfo100 = EventInfos("StartingSort")   
  Dim arguments As Object() = New Object(2) {buffer.RowCount, DateTime.Now}   
  ComponentMetaData.FireCustomEvent("StartingSort", _  
    "Beginning sort operation.", arguments, _  
    ComponentMetaData.Name, FireSortEventAgain)   
End Sub  
```  

## <a name="see-also"></a>Voir aussi  
 [Integration Services &#40; SSIS &#41; Gestionnaires d’événements](../../../integration-services/integration-services-ssis-event-handlers.md)   
 [Ajoutez un gestionnaire d’événements à un Package](http://msdn.microsoft.com/library/5e56885d-8658-480a-bed9-3f2f8003fd78)  
  
  
