---
title: Développement d’objets personnalisés pour Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom user interface [Integration Services]
- custom objects [Integration Services]
ms.assetid: ca1929a6-0ae6-47d7-b65f-08173b143720
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: aa5f333b050d817d68c8769d7e53a9455581a3ef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62768655"
---
# <a name="developing-custom-objects-for-integration-services"></a>Développement d'objets personnalisés pour Integration Services
  Lorsque les objets de workflow de contrôle et de données inclus dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ne répondent pas complètement à vos besoins, vous pouvez développer de nombreux types d’objets personnalisés par vous-même, notamment :  
  
-   **Tâches personnalisées**.  
  
-   **Gestionnaires de connexions personnalisés.** Connectez-vous aux sources de données externes qui ne sont pas prises en charge actuellement.  
  
-   **Modules fournisseurs d’informations personnalisés.** Enregistrez des événements de package dans des formats qui ne sont pas pris en charge actuellement.  
  
-   **Énumérateurs personnalisés.** Prenez en charge l'itération sur un jeu d'objets ou de formats de valeurs qui ne sont pas pris en charge actuellement.  
  
-   **Composants de workflow de données personnalisés.** Peuvent être configurés en tant que sources, transformations ou destinations.  
  
 Le modèle objet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] facilite ce développement personnalisé à l'aide de classes de base qui fournissent un cadre cohérent et fiable pour votre implémentation personnalisée.  
  
 Si vous n'avez pas à réutiliser les fonctionnalités personnalisées dans plusieurs packages, la tâche de script et le composant Script vous donnent toute la puissance d'un langage de programmation managé avec beaucoup moins de code d'infrastructure à écrire. Pour plus d’informations, consultez [Comparaison des solutions de script et des objets personnalisés](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md).  
  
## <a name="steps-in-developing-a-custom-object-for-integration-services"></a>Étapes de développement d'un objet personnalisé pour Integration Services  
 Lorsque vous développez un objet personnalisé à utiliser dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous développez une bibliothèque de classes (DLL) qui sera chargée au moment de la conception et au moment de l'exécution par le Concepteur SSIS et par le runtime [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Les méthodes les plus importantes que vous devez implémenter ne sont pas celles que vous appelez à partir de votre propre code, mais celles que le runtime appelle à des moments appropriés pour initialiser et valider votre composant et appeler ses fonctionnalités.  
  
 Voici les étapes à suivre pour développer un objet personnalisé :  
  
1.  Créez un projet de type Bibliothèque de classes dans votre langage de programmation managé préféré.  
  
2.  Héritez de la classe de base appropriée, comme indiqué dans le tableau suivant.  
  
3.  Appliquez l'attribut approprié à votre nouvelle classe, comme indiqué dans le tableau suivant.  
  
4.  Remplacez les méthodes de la classe de base comme requis et écrivez le code des fonctionnalités personnalisées de votre objet.  
  
5.  Générez éventuellement une interface utilisateur personnalisée pour votre composant. Afin de faciliter le déploiement, vous pouvez développer l'interface utilisateur sous la forme d'un projet distinct au sein de la même solution, puis la générer en tant qu'assembly séparé.  
  
6.  (Facultatif) Affichez un lien vers des exemples et contenus d’Aide pour l’objet personnalisé dans la **Boîte à outils SSIS**.  
  
7.  Générez, déployez et déboguez votre nouvel objet personnalisé comme décrit dans [Génération, déploiement et débogage d’objets personnalisés](building-deploying-and-debugging-custom-objects.md).  
  
## <a name="base-classes-attributes-and-important-methods"></a>Classes de base, attributs et méthodes importantes  
 Ce tableau constitue une référence simple aux éléments les plus importants du modèle objet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour chaque type d'objet personnalisé que vous pouvez développer.  
  
|Objet personnalisé|Classe de base|Attribut|Méthodes importantes|  
|-------------------|----------------|---------------|-----------------------|  
|Tâche|<xref:Microsoft.SqlServer.Dts.Runtime.Task>|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>|<xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A>|  
|Gestionnaire de connexions|<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase>|<xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>|<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A>|  
|Module fournisseur d'informations|<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>|<xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute>|<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A>|  
|Énumérateur|<xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>|<xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>|<xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A>|  
|Composant de flux de données|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>|<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>|  
  
## <a name="providing-links-to-samples-and-help-content"></a>Liens vers des exemples et des contenus d'aide  
 Pour afficher un lien dans la **Boîte à outils SSIS** vers des exemples et des contenus d’Aide pour un objet personnalisé écrit en code managé, utilisez les propriétés suivantes.  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.DTSPipelineComponentAttribute.SamplesTag%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.DTSPipelineComponentAttribute.HelpCollection%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.DTSPipelineComponentAttribute.HelpKeyword%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.DTSTaskAttribute.SamplesTag%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.DTSTaskAttribute.HelpCollection%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.DTSTaskAttribute.HelpKeyword%2A>  
  
 Pour afficher un lien vers des exemples et des contenus d'Aide pour un objet personnalisé écrit en code natif, ajoutez des entrées dans le fichier de Registre Script (.rgs) pour SamplesTag, HelpKeyword et HelpCollection. Voici un exemple.  
  
 `val HelpKeyword = s 'sql11.dts.designer.executepackagetask.F1'`  
  
 `val SamplesTag = s 'ExecutePackageTask'`  
  
## <a name="providing-a-custom-user-interface"></a>Interface utilisateur personnalisée  
 Pour permettre aux utilisateurs de votre objet personnalisé de configurer ses propriétés, vous devrez peut-être également développer une interface utilisateur personnalisée. Dans les cas où une interface utilisateur personnalisée n'est pas strictement requise, vous pouvez choisir d'en créer une afin de fournir une interface plus conviviale que l'éditeur par défaut.  
  
 Dans un projet d’interface utilisateur personnalisée ou assembly, vous avez généralement deux classes : une classe qui implémente une interface [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour les interfaces utilisateur du type spécifique de l’objet personnalisé et le formulaire Windows qu’elle affiche pour collecter des informations auprès de l’utilisateur. Les interfaces que vous implémentez comportent uniquement quelques méthodes et une interface utilisateur personnalisée n'est pas difficile à développer.  
  
> [!NOTE]  
>  De nombreux modules fournisseurs d’informations [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ont une interface utilisateur personnalisée qui implémente l’objet <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> et remplace la zone de texte **Configuration** par la liste déroulante filtrée des gestionnaires de connexions disponibles. Toutefois, les interfaces utilisateur personnalisées des modules fournisseurs d'informations personnalisés ne sont pas implémentées dans cette version de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. La spécification d'une valeur pour la propriété <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.UITypeName%2A> de l'objet <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> est sans effet.  
  
 Le tableau suivant constitue une référence simple aux interfaces que vous devez implémenter lorsque vous développez une interface utilisateur personnalisée pour chaque type d'objet personnalisé. Il explique également ce que l'utilisateur voit si vous choisissez de ne pas développer d'interface utilisateur personnalisée pour votre objet, ou si vous ne pouvez pas lier votre objet à son interface utilisateur en utilisant la propriété `UITypeName` dans l'attribut de l'objet. Bien que le puissant éditeur avancé puisse s'avérer satisfaisant pour un composant de flux de données, la fenêtre Propriétés est une solution moins conviviale pour les tâches et les gestionnaires de connexions, et un énumérateur ForEach personnalisé ne peut pas du tout être configuré sans formulaire personnalisé.  
  
|Objet personnalisé|Classe de base pour interface utilisateur|Comportement d'édition par défaut si aucune interface utilisateur personnalisée n'est fournie|  
|-------------------|-----------------------------------|----------------------------------------------------------------------|  
|Tâche|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI>|Fenêtre Propriétés uniquement|  
|Gestionnaire de connexions|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI>|Fenêtre Propriétés uniquement|  
|Module fournisseur d'informations|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI><br /><br /> (Non implémenté dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].)|Zone de texte dans la colonne **Configuration**|  
|Énumérateur|<xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI>|Fenêtre Propriétés uniquement. La zone Configuration de l'énumérateur de l'éditeur est vide.|  
|Composant de flux de données|<xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI>|Éditeur avancé|  
  
## <a name="external-resources"></a>Ressources externes  
  
-   Entrée de blog, [Visual Studio solution build process give a warning about indirect dependency on the .NET Framework assembly due to SSIS references](https://go.microsoft.com/fwlink/?LinkId=215662), sur blogs.msdn.com.  
  
![Icône de Integration Services (petite)](../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Persistance des objets personnalisés](persisting-custom-objects.md)   
 [Génération, déploiement et débogage d’objets personnalisés](building-deploying-and-debugging-custom-objects.md)  
  
  
