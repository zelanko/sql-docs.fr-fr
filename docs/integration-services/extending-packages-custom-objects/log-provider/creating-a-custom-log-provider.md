---
title: "Création d’un fournisseur de journal personnalisé | Documents Microsoft"
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
- custom log providers [Integration Services], creating
ms.assetid: fc20af96-9eb8-4195-8d3f-8a4d7c753f24
caps.latest.revision: 58
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4e98f1b5a032353c27ffa1438eb7d01bd517892a
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="creating-a-custom-log-provider"></a>Création d'un module fournisseur d'informations personnalisé
  L'environnement d'exécution [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] possède des fonctionnalités de journalisation complètes. Un journal vous permet de capturer des événements qui se produisent pendant l'exécution d'un package. [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] inclut divers modules fournisseurs d'informations qui permettent de créer et stocker des journaux dans plusieurs formats, notamment XML, texte et base de données ou dans le journal des événements Windows. Si l'un de ces fournisseurs ou formats de sortie ne répond pas à vos besoins, vous pouvez créer un module fournisseur d'informations personnalisé.  
  
 Les étapes à suivre pour créer un module fournisseur d'informations personnalisé sont similaires à celles qui permettent de créer tout autre objet personnalisé pour [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] :  
  
-   Créer une classe qui hérite de la classe de base. Pour un module fournisseur d'informations, la classe de base est <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>.  
  
-   Appliquer l'attribut qui identifie le type d'objet auprès de la classe. Pour un module fournisseur d'informations, l'attribut est <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute>.  
  
-   Substituer l'implémentation des méthodes et des propriétés de la classe de base. Pour un module fournisseur d'informations, celles-ci incluent la propriété <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> et les méthodes <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> et <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A>.  
  
-   Interfaces utilisateur personnalisées pour les modules fournisseurs d’informations personnalisés ne sont pas implémentées dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
## <a name="getting-started-with-a-custom-log-provider"></a>Mise en route d'un module fournisseur d'informations personnalisé  
  
### <a name="creating-projects-and-classes"></a>Création de projets et de classes  
 Puisque tous les modules fournisseurs d'informations managés dérivent de la classe de base <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>, la première étape de création d'un module fournisseur d'informations personnalisé consiste à créer un projet Bibliothèque de classes dans votre langage de programmation managé par défaut, puis à créer une classe qui hérite de la classe de base. Dans cette classe dérivée, vous devez substituer les méthodes et les propriétés de la classe de base pour implémenter vos fonctionnalités personnalisées.  
  
 Configurez le projet pour signer l'assembly qui sera généré avec un fichier de clé de nom fort.  
  
> [!NOTE]  
>  Nombreux [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] modules fournisseurs d’informations ont une interface utilisateur personnalisée qui implémente <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> et remplace le **Configuration** zone de texte dans le **configurer les journaux SSIS** boîte de dialogue avec une liste déroulante filtrée des gestionnaires de connexions disponibles. Toutefois, les interfaces utilisateur personnalisées des modules fournisseurs d'informations personnalisés ne sont pas implémentées dans [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
### <a name="applying-the-dtslogprovider-attribute"></a>Application de l'attribut DtsLogProvider  
 Appliquez l'attribut <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> à la classe que vous avez créée pour l'identifier en tant que module fournisseur d'informations. Cet attribut fournit des informations de conception, telles que le nom et la description du module fournisseur d'informations. Le **DisplayName** et **Description** propriétés de l’attribut correspondent à la **nom** et **Description** colonnes affichées dans le **configurer les journaux SSIS** éditeur, qui s’affiche lors de la configuration de journalisation d’un package dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].  
  
> [!IMPORTANT]  
>  La propriété <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.LogProviderType%2A> de l'attribut n'est pas utilisée. Toutefois, vous devez entrer une valeur pour cette propriété, sans quoi le module fournisseur d'informations personnalisé n'apparaîtra pas dans la liste des modules fournisseurs d'informations disponibles.  
  
> [!NOTE]  
>  Étant donné que les interfaces utilisateur personnalisées des modules fournisseurs d'informations personnalisés ne sont pas implémentées dans [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], la spécification d'une valeur pour la propriété <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.UITypeName%2A> de l'objet <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> n'a aucun effet.  
  
```vb  
<DtsLogProvider(DisplayName:="MyLogProvider", Description:="A simple log provider.", LogProviderType:="Custom")> _  
Public Class MyLogProvider  
     Inherits LogProviderBase  
    ' TODO: Override the base class methods.  
End Class  
```  
  
```csharp  
[DtsLogProvider(DisplayName="MyLogProvider", Description="A simple log provider.", LogProviderType="Custom")]  
public class MyLogProvider : LogProviderBase  
{  
    // TODO: Override the base class methods.  
}  
```  
  
## <a name="building-deploying-and-debugging-a-custom-log-provider"></a>Génération, déploiement et débogage d'un module fournisseur d'informations personnalisé  
 Les étapes permettant de générer, déployer et déboguer un module fournisseur d'informations personnalisé dans [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sont très similaires à celles requises pour les autres types d'objets personnalisés. Pour plus d’informations, consultez [génération, déploiement et débogage des objets personnalisés](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Codage d’un fournisseur de journal personnalisé](../../../integration-services/extending-packages-custom-objects/log-provider/coding-a-custom-log-provider.md)   
 [Développement d’une Interface utilisateur pour un fournisseur de journal personnalisé](../../../integration-services/extending-packages-custom-objects/log-provider/developing-a-user-interface-for-a-custom-log-provider.md)  
  
  
