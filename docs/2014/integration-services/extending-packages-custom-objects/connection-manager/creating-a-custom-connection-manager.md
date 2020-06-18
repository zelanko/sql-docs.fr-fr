---
title: Création d’un gestionnaire de connexions personnalisé | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom connection managers [Integration Services], creating
ms.assetid: e83f8e02-ace4-42e0-b979-2f6be1460985
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 7354c9152d075c2ebc3611a342bbf8d7594cde79
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966529"
---
# <a name="creating-a-custom-connection-manager"></a>Création d'un gestionnaire de connexions personnalisé
  Les étapes à suivre pour créer un gestionnaire de connexions personnalisé sont similaires à celles permettant de créer tout autre objet personnalisé pour [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] :  
  
-   Créer une classe qui hérite de la classe de base. Pour un gestionnaire de connexions, la classe de base est <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase>.  
  
-   Appliquer l'attribut qui identifie le type d'objet auprès de la classe. Pour un gestionnaire de connexions, l'attribut est <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>.  
  
-   Remplacer l'implémentation des méthodes et propriétés de la classe de base. Pour un gestionnaire de connexions, celles-ci incluent la propriété <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> et les méthodes <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> et <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A>.  
  
-   Développer éventuellement une interface utilisateur personnalisée. Pour un gestionnaire de connexions, cette opération requiert une classe qui implémente l'interface <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI>.  
  
> [!NOTE]  
>  Une grande partie des tâches, sources et destinations intégrées à [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] utilisent uniquement des types spécifiques de gestionnaires de connexions intégrés. Par conséquent, ces exemples ne peuvent pas être testés avec les tâches et composants intégrés.  
  
## <a name="getting-started-with-a-custom-connection-manager"></a>Mise en route d'un gestionnaire de connexions personnalisé  
  
### <a name="creating-projects-and-classes"></a>Création de projets et de classes  
 Puisque tous les gestionnaires de connexions managés dérivent de la classe de base <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase>, la première étape de création d'un gestionnaire de connexions personnalisé consiste à créer un projet Bibliothèque de classes dans votre langage de programmation managé par défaut et à créer une classe qui hérite de la classe de base. Dans cette classe dérivée, vous allez substituer les méthodes et les propriétés de la classe de base pour implémenter vos fonctionnalités personnalisées.  
  
 Dans la même solution, créez un deuxième projet Bibliothèque de classes pour l'interface utilisateur personnalisée. Il est recommandé d’utiliser un assembly distinct pour l’interface utilisateur afin de faciliter le déploiement car vous pouvez ainsi mettre à jour et redéployer le gestionnaire de connexions ou son interface utilisateur de manière indépendante.  
  
 Configurez les deux projets pour qu'ils signent les assemblys qui seront créés au moment de la génération à l'aide d'un fichier de clé de nom fort.  
  
### <a name="applying-the-dtsconnection-attribute"></a>Application de l'attribut DtsConnection  
 Appliquez l'attribut <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> à la classe que vous avez créée pour l'identifier en tant que gestionnaire de connexions. Cet attribut fournit des informations au moment de la conception, telles que le nom, la description et le type de connexion du gestionnaire de connexions. Les <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.ConnectionType%2A> `Description` Propriétés et correspondent au **type** et aux `Description` colonnes affichées dans la boîte de dialogue **Ajouter un gestionnaire de connexions SSIS** , qui s’affiche lors de la configuration des connexions pour un package dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] .  
  
 Utilisez la propriété <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.UITypeName%2A> pour lier le gestionnaire de connexions à son interface utilisateur personnalisée. Pour obtenir le jeton de clé publique requis pour cette propriété, vous pouvez utiliser **sn.exe -t** de manière à afficher le jeton de clé publique du fichier de paire de clés (.snk) que vous voulez utiliser pour signer l’assembly de l’interface utilisateur.  
  
```vb  
<DtsConnection(ConnectionType:="SQLVB", _  
  DisplayName:="SqlConnectionManager (VB)", _  
  Description:="Connection manager for Sql Server", _  
  UITypeName:="SqlConnMgrUIVB.SqlConnMgrUIVB,SqlConnMgrUIVB,Version=1.0.0.0,Culture=neutral,PublicKeyToken=<insert public key token here>")> _  
Public Class SqlConnMgrVB  
  Inherits ConnectionManagerBase  
  . . .  
End Class  
```  
  
```csharp  
[DtsConnection(ConnectionType = "SQLCS",  
  DisplayName = "SqlConnectionManager (CS)",  
  Description = "Connection manager for Sql Server",  
  UITypeName = "SqlConnMgrUICS.SqlConnMgrUICS,SqlConnMgrUICS,Version=1.0.0.0,Culture=neutral,PublicKeyToken=<insert public key token here>")]  
public class SqlConnMgrCS :  
ConnectionManagerBase  
{  
  . . .  
}  
```  
  
## <a name="building-deploying-and-debugging-a-custom-connection-manager"></a>Génération, déploiement et débogage d'un gestionnaire de connexions personnalisé  
 Les étapes permettant de générer, déployer et déboguer un gestionnaire de connexions personnalisé dans [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sont très similaires aux étapes requises pour les autres types d'objets personnalisés. Pour plus d’informations, consultez [Génération, déploiement et débogage d’objets personnalisés](../building-deploying-and-debugging-custom-objects.md).  
  
![Icône de Integration Services (petite)](../../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Codage d’un gestionnaire de connexions personnalisé](coding-a-custom-connection-manager.md)   
 [Développement d'une interface utilisateur pour un gestionnaire de connexions personnalisé](developing-a-user-interface-for-a-custom-connection-manager.md)  
  
  
