---
title: Enregistrement et définition d’entrées de journal dans un composant de flux de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- logs [Integration Services], custom
- custom log entries [Integration Services]
- custom data flow components [Integration Services], logging
- data flow components [Integration Services], logging
ms.assetid: 2190dba9-59b5-480b-b8e9-21d5a54c5917
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 04fbfbe124c5db65fd601a0aa03ec724c7bc83b4
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436956"
---
# <a name="logging-and-defining-log-entries-in-a-data-flow-component"></a>Enregistrement et définition d'entrées de journal dans un composant de flux de données
  Les composants de flux de données personnalisés peuvent publier des messages dans une entrée de journal existante à l'aide de la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.PostLogMessage%2A> de l'interface <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>. Ils peuvent également présenter des informations à l'utilisateur en utilisant la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireInformation%2A>, ou des méthodes semblables, de l'interface <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>. Toutefois, cette procédure induit une surcharge causée par le déclenchement et la gestion d'événements supplémentaires et force l'utilisateur à passer en revue les messages d'information documentés pour rechercher ceux susceptibles de l'intéresser. Vous pouvez utiliser une entrée de journal personnalisée, tel que décrit ci-dessous, pour fournir aux utilisateurs de votre composant des informations de journal personnalisées étiquetées.  
  
## <a name="registering-and-using-a-custom-log-entry"></a>Inscription et utilisation d'une entrée de journal personnalisée  
  
### <a name="registering-a-custom-log-entry"></a>Inscription d'une entrée de journal personnalisée  
 Pour inscrire une entrée de journal personnalisée destinée à votre composant, substituez la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterLogEntries%2A> de la classe de base <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>. L'exemple suivant inscrit une entrée de journal personnalisée et lui fournit un nom et une description.  
  
```csharp  
using Microsoft.SqlServer.Dts.Runtime;  
...  
private const string MyLogEntryName = "My Custom Component Log Entry";  
private const string MyLogEntryDescription = "Log entry from My Custom Component ";  
...  
    public override void RegisterLogEntries()  
    {  
      this.LogEntryInfos.Add(MyLogEntryName,  
        MyLogEntryDescription,  
        Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT);  
    }  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
...  
Private Const MyLogEntryName As String = "My Custom Component Log Entry"   
Private Const MyLogEntryDescription As String = "Log entry from My Custom Component "  
...  
Public  Overrides Sub RegisterLogEntries()   
  Me.LogEntryInfos.Add(MyLogEntryName, _  
    MyLogEntryDescription, _  
    Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT)   
End Sub  
```  
  
 L'énumération <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency> fournit au Runtime une indication quant à la fréquence de journalisation de l'événement :  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_OCCASIONAL> : l'événement est enregistré épisodiquement, mais pas à chaque exécution.  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT> : l'événement est enregistré un nombre constant de fois pendant chaque exécution.  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_PROPORTIONAL> : l'événement est enregistré un nombre de fois proportionnel à la quantité de travail accompli.  
  
 L'exemple ci-dessus utilise <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT> car le composant s'attend à enregistrer une entrée une fois par exécution.  
  
 Après l’inscription de l’entrée de journal personnalisée et l’ajout d’une instance de votre composant personnalisé à l’aire du concepteur de flux de données, la boîte de dialogue **Enregistrement** dans le concepteur affiche une nouvelle entrée de journal appelée « Entrée de journal de mon composant personnalisé » dans la liste des entrées de journal disponibles.  
  
### <a name="logging-to-a-custom-log-entry"></a>Enregistrement dans une entrée de journal personnalisée  
 Après l'inscription de l'entrée de journal personnalisée, le composant peut désormais enregistrer des messages personnalisés. L'exemple suivant écrit une entrée de journal personnalisée pendant l'exécution de la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> qui contient le texte d'une instruction SQL utilisée par le composant.  
  
```csharp  
public override void PreExecute()  
{  
  DateTime now = DateTime.Now;  
  byte[] additionalData = null;  
  this.ComponentMetaData.PostLogMessage(MyLogEntryName,  
    this.ComponentMetaData.Name,  
    "Command Sent was: " + myCommand.CommandText,  
    now, now, 0, ref additionalData);  
}  
```  
  
```vb  
Public  Overrides Sub PreExecute()   
  Dim now As DateTime = DateTime.Now   
  Dim additionalData As Byte() = Nothing   
  Me.ComponentMetaData.PostLogMessage(MyLogEntryName, _  
    Me.ComponentMetaData.Name, _  
    "Command Sent was: " + myCommand.CommandText, _  
    now, now, 0, additionalData)   
End Sub  
```  
  
 À présent, lorsque l’utilisateur exécute le package, après avoir sélectionné l’option « Entrée de journal de mon composant personnalisé » dans la boîte de dialogue **Enregistrement**, le journal contient une entrée clairement étiquetée « Utilisateur ::Entrée de journal de mon composant personnalisé ». Cette nouvelle entrée de journal contient le texte de l'instruction SQL, l'horodateur et toutes les données supplémentaires enregistrées par le développeur.  
  
![Icône de Integration Services (petite)](../../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Journalisation Integration Services &#40;SSIS&#41;](../../performance/integration-services-ssis-logging.md)  
  
  
