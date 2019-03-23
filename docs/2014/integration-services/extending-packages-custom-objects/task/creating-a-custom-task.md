---
title: Création d’une tâche personnalisée | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom tasks [Integration Services], creating
ms.assetid: 42965c09-1782-4cdb-9ce1-216af4c23e0a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9123834f1c07a61fa0e1c48d29667d4d71ada359
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58385488"
---
# <a name="creating-a-custom-task"></a>Création d'une tâche personnalisée
  Les étapes de création d'une tâche personnalisée sont semblables aux étapes de création de tout autre objet personnalisé pour [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] :  
  
-   Créer une classe qui hérite de la classe de base. Pour une tâche, la classe de base est <xref:Microsoft.SqlServer.Dts.Runtime.Task>.  
  
-   Appliquer l'attribut qui identifie le type d'objet auprès de la classe. Pour une tâche, l'attribut est <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>.  
  
-   Substituer l'implémentation des méthodes et des propriétés de la classe de base. Pour une tâche, il s'agit notamment des méthodes <xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> et <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A>.  
  
-   Développer éventuellement une interface utilisateur personnalisée. Pour une tâche, cette opération requiert une classe qui implémente l'interface <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI>.  
  
## <a name="getting-started-with-a-custom-task"></a>Mise en route d'une tâche personnalisée  
  
### <a name="creating-projects-and-classes"></a>Création de projets et de classes  
 Comme toutes les tâches managées dérivent de la classe de base <xref:Microsoft.SqlServer.Dts.Runtime.Task>, la première étape de création d'une tâche personnalisée consiste à créer un projet Bibliothèque de classes dans votre langage de programmation managé par défaut et créer une classe qui hérite de la classe de base. Dans cette classe dérivée, vous devez substituer les méthodes et les propriétés de la classe de base pour implémenter vos fonctionnalités personnalisées.  
  
 Dans la même solution, créez un deuxième projet Bibliothèque de classes pour l'interface utilisateur personnalisée. Il est recommandé d'utiliser un assembly distinct pour l'interface utilisateur afin de faciliter le déploiement car vous pouvez ainsi mettre à jour et redéployer le gestionnaire de connexions ou son interface utilisateur de manière indépendante.  
  
 Configurez les deux projets pour qu'ils signent les assemblys qui seront créés au moment de la génération à l'aide d'un fichier de clé de nom fort.  
  
### <a name="applying-the-dtstask-attribute"></a>Application de l'attribut DtsTask  
 Appliquez l'attribut <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> à la classe que vous avez créée pour l'identifier en tant que tâche. Cet attribut fournit des informations au moment de la conception, telles que le nom, la description et le type de la tâche.  
  
 Utilisez la propriété <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> pour lier la tâche à son interface utilisateur personnalisée. Pour obtenir le jeton de clé publique requis pour cette propriété, vous pouvez utiliser **sn.exe -t** de manière à afficher le jeton de clé publique du fichier de paire de clés (.snk) que vous voulez utiliser pour signer l’assembly de l’interface utilisateur.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
namespace Microsoft.SSIS.Samples  
{  
  [DtsTask  
  (  
   DisplayName = "MyTask",  
   IconResource = "MyTask.MyTaskIcon.ico",  
   UITypeName = "My Custom Task," +  
   "Version=1.0.0.0," +  
   "Culture = Neutral," +  
   "PublicKeyToken = 12345abc6789de01",  
   TaskType = "PackageMaintenance",  
   TaskContact = "MyTask; company name; any other information",  
   RequiredProductLevel = DTSProductLevel.None  
   )]  
  public class MyTask : Task  
  {  
    // Your code here.  
  }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
  
<DtsTask(DisplayName:="MyTask", _  
 IconResource:="MyTask.MyTaskIcon.ico", _  
 UITypeName:="My Custom Task," & _  
 "Version=1.0.0.0,Culture=Neutral," & _  
 "PublicKeyToken=12345abc6789de01", _  
 TaskType:="PackageMaintenance", _  
 TaskContact:="MyTask; company name; any other information", _  
 RequiredProductLevel:=DTSProductLevel.None)> _  
Public Class MyTask  
  Inherits Task  
  
  ' Your code here.  
  
End Class 'MyTask  
```  
  
## <a name="building-deploying-and-debugging-a-custom-task"></a>Génération, déploiement et débogage d'une tâche personnalisée  
 Les étapes pour générer, déployer et déboguer une tâche personnalisée dans [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sont très semblables aux étapes requises pour les autres types d'objets personnalisés. Pour plus d’informations, consultez [Génération, déploiement et débogage d’objets personnalisés](../building-deploying-and-debugging-custom-objects.md).  
  
![Icône Integration Services (petite)](../../media/dts-16.gif "icône Integration Services (petite)")**rester jusqu'à la Date avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une tâche personnalisée](creating-a-custom-task.md)   
 [Codage d’une tâche personnalisée](coding-a-custom-task.md)   
 [Développement d’une interface utilisateur pour une tâche personnalisée](developing-a-user-interface-for-a-custom-task.md)  
  
  
