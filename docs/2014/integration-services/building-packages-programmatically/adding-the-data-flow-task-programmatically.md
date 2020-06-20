---
title: Ajout de la tâche de flux de données par programmation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- adding Data Flow task
- SSIS data flow
- data flow task [Integration Services], adding
- MainPipe object
ms.assetid: 0ca03712-a82e-4aa7-949b-f869a8936ddf
author: janinezhang
ms.author: janinez
ms.openlocfilehash: a17575543fd5db37078a37a3512da28b3a8718ea
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84925080"
---
# <a name="adding-the-data-flow-task-programmatically"></a>Ajout de la tâche de flux de données par programmation
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] inclut une tâche appelée flux de données, représentée par l'espace de noms <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper> dans le modèle objet. La tâche de flux de données est une tâche spécialisée, hautement performante, dédiée à la transformation et au déplacement de données pendant l'exécution de package. Comme les autres tâches, la tâche de flux de données est encapsulée par l'objet <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> et, du point de vue du moteur d'exécution, rien ne la différencie des autres tâches du package. Toutefois, le flux de données contient des objets supplémentaires appelés composants de flux de données. Il s'agit des composants qui permettent de déplacer les données d'une source à une destination, parfois par le biais d'une transformation. Les composants définissent le sens du déplacement et le mode de transformation des données. Pour configurer la tâche de flux de données, il est nécessaire d'ajouter des composants à la tâche, puis de les connecter pour établir le flux des données et obtenir la transformation souhaitée.  
  
 Une tâche de flux de données comporte trois types de composants : **Sources de flux de données**, **Transformations du flux de données** et **Destinations du flux de données**, affichés dans cet ordre dans la boîte à outils du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Ces types sont également appelés sources, transformations ou destinations pour simplifier. Comme leur nom l'indique, les données sont acheminées d'une source à une transformation, puis à une destination. Cette description très simplifiée du flux de données permet d'illustrer le concept. Toutefois, la tâche de flux de données est suffisamment flexible et puissante pour gérer plusieurs sources et connecter de nombreuses transformations qui envoient la sortie à plusieurs destinations.  
  
 La tâche de flux de données est ajoutée à un package de la même manière que les autres tâches sont ajoutées. Une fois que la tâche de flux de données a été ajoutée, vous pouvez la configurer en y ajoutant des composants que vous pourrez configurer et connecter à la tâche.  
  
## <a name="sample"></a>Exemple  
 L'exemple de code suivant indique comment ajouter une tâche de flux de données à un package. Cet exemple requiert une référence aux assemblys Microsoft.SqlServer.PipelineHost, Microsoft.SqlServer.DTSPipelineWrap et Microsoft.SqlServer.ManagedDTS.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
      Executable e = p.Executables.Add("STOCK:PipelineTask");  
      TaskHost thMainPipe = e as TaskHost;  
      MainPipe dataFlowTask = thMainPipe.InnerObject as MainPipe;   
    }  
  }  
}  
```  
  
```vb  
Imports System.IO  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    Dim e As Executable = p.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As TaskHost = CType(e, TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
  End Sub  
  
End Module  
```  
  
## <a name="external-resources"></a>Ressources externes  
 Entrée de blog, [EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223), sur blogs.msdn.com.  
  
![Icône de Integration Services (petite)](../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Découverte des composants de flux de données par programme](../building-packages-programmatically/discovering-data-flow-components-programmatically.md)  
  
  
