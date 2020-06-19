---
title: Développement d’un énumérateur ForEach personnalisé | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom foreach enumerators [Integration Services]
- custom foreach enumerators [Integration Services], about custom foreach enumerators
- foreach enumerators [Integration Services]
ms.assetid: bffe26e0-1b9a-47ad-bae6-6b708cb4cf4f
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 21c8587ba63ca73674de45684f0beab5e4590606
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968739"
---
# <a name="developing-a-custom-foreach-enumerator"></a>Développement d'un énumérateur ForEach personnalisé
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] utilise des énumérateurs Foreach pour parcourir les éléments d'une collection et effectuer les mêmes tâches pour chaque élément. [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] inclut divers énumérateurs Foreach qui prennent en charge les collections les plus couramment utilisées, telles que tous les fichiers inclus dans un dossier, toutes les tables incluses dans une base de données ou tous les éléments d'une liste stockée dans une variable de package. Si les énumérateurs foreach et les collections fournies ne répondent pas totalement à vos besoins, vous pouvez créer un énumérateur foreach personnalisé.  
  
 Pour créer un énumérateur foreach personnalisé, vous devez créer une classe qui hérite de la classe de base <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>, appliquer l'attribut <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> à votre nouvelle classe et remplacer les méthodes et propriétés importantes de la classe de base, notamment la méthode <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A>.  
  
## <a name="in-this-section"></a>Dans cette section  
 Cette section explique comment créer, configurer et coder un énumérateur foreach personnalisé et son interface utilisateur personnalisée.  
  
 [Création d’un énumérateur Foreach personnalisé](creating-a-custom-foreach-enumerator.md)  
 Explique comment créer les classes d'un projet d'énumérateur foreach personnalisé.  
  
 [Codage d’un énumérateur Foreach personnalisé](coding-a-custom-foreach-enumerator.md)  
 Décrit comment implémenter un énumérateur foreach personnalisé en remplaçant les méthodes et propriétés de la classe de base.  
  
 [Développement d’une interface utilisateur pour un énumérateur ForEach personnalisé](developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
 Explique comment implémenter la classe d'interface utilisateur et le formulaire servant à configurer l'énumérateur foreach personnalisé.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
### <a name="information-common-to-all-custom-objects"></a>Informations communes à tous les objets personnalisés  
 Pour obtenir les informations communes à tous les types d'objets personnalisés que vous pouvez créer dans [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], consultez les rubriques suivantes :  
  
 [Développement d’objets personnalisés pour Integration Services](../developing-custom-objects-for-integration-services.md)  
 Décrit les étapes de base permettant d’implémenter tous les types d’objets personnalisés pour [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
 [Persistance des objets personnalisés](../persisting-custom-objects.md)  
 Décrit la persistance personnalisée et explique les situations dans lesquelles elle est nécessaire.  
  
 [Génération, déploiement et débogage d’objets personnalisés](../building-deploying-and-debugging-custom-objects.md)  
 Décrit les techniques permettant de générer, signer, déployer et déboguer des objets personnalisés.  
  
### <a name="information-about-other-custom-objects"></a>Informations sur les autres objets personnalisés  
 Pour plus d’informations sur les autres types d’objets personnalisés que vous pouvez créer dans [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], consultez les rubriques suivantes :  
  
 [Développement d’une tâche personnalisée](../task/developing-a-custom-task.md)  
 Explique comment programmer des tâches personnalisées.  
  
 [Développement d’un gestionnaire de connexions personnalisé](../connection-manager/developing-a-custom-connection-manager.md)  
 Explique comment programmer des gestionnaires de connexions personnalisés.  
  
 [Développement d’un module fournisseur d’informations personnalisé](../log-provider/developing-a-custom-log-provider.md)  
 Explique comment programmer des modules fournisseurs d'informations personnalisés.  
  
 [Développement d’un composant de flux de données personnalisé](../data-flow/developing-a-custom-data-flow-component.md)  
 Explique comment programmer des sources, des transformations et des destinations de flux de données personnalisées.  
  
![Icône de Integration Services (petite)](../../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
  
