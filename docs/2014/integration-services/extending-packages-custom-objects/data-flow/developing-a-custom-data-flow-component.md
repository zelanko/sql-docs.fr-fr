---
title: Développement d’un composant de flux de données personnalisé | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow task [Integration Services], extending
- data flow [Integration Services], extending
- extending data flow task [Integration Services]
- components [Integration Services], data flow
ms.assetid: be126913-2a9a-41c9-9bf5-a7b0a0aea2f8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6c174fe5cdf1ebe1dbc9b0350a01fb6e8027effa
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62768965"
---
# <a name="developing-a-custom-data-flow-component"></a>Développement d'un composant de flux de données personnalisé
  La tâche de flux de données comprend des composants qui se connectent à diverses sources de données et qui transforment et acheminent ces données à haut débit. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] fournit un modèle objet extensible qui permet aux développeurs de créer des sources, des transformations et des destinations personnalisées que vous pouvez utiliser dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] et dans des packages déployés. Cette section contient des rubriques qui vous guideront afin de développer des composants de flux de données personnalisés.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Création d’un composant de flux de données personnalisé](creating-a-custom-data-flow-component.md)  
 Décrit les étapes initiales permettant de créer un composant de flux de données personnalisé.  
  
 [Méthodes de conception d’un composant de flux de données](design-time-methods-of-a-data-flow-component.md)  
 Décrit les méthodes de conception à implémenter dans un composant de flux de données personnalisé.  
  
 [Méthodes d’exécution d’un composant de flux de données](run-time-methods-of-a-data-flow-component.md)  
 Décrit les méthodes d'exécution à implémenter dans un composant de flux de données personnalisé.  
  
 [Plan d’exécution et allocation de mémoire tampon](execution-plan-and-buffer-allocation.md)  
 Décrit le plan d'exécution du flux de données et l'allocation des tampons de données.  
  
 [Utilisation de types de données dans le flux de données](working-with-data-types-in-the-data-flow.md)  
 Explique comment le flux mappe les types de données [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] aux types de données managées .NET Framework.  
  
 [Validation d’un composant de flux de données](validating-a-data-flow-component.md)  
 Explique les méthodes utilisées pour valider la configuration du composant et reconfigurer les métadonnées du composant.  
  
 [Implémentation des métadonnées externes](implementing-external-metadata.md)  
 Explique comment utiliser des colonnes de métadonnées externes pour la validation des données.  
  
 [Déclenchement et définition d’événements dans un composant de flux de données](raising-and-defining-events-in-a-data-flow-component.md)  
 Explique comment déclencher des événements prédéfinis et personnalisés.  
  
 [Enregistrement et définition d’entrées de journal dans un composant de flux de données](logging-and-defining-log-entries-in-a-data-flow-component.md)  
 Explique comment créer et écrire des entrées de journal personnalisées.  
  
 [Utilisation de sorties d’erreur dans un composant de flux de données](using-error-outputs-in-a-data-flow-component.md)  
 Explique comment rediriger des lignes d'erreur vers une autre sortie.  
  
 [Mise à niveau de la version d’un composant de flux de données](upgrading-the-version-of-a-data-flow-component.md)  
 Explique comment mettre à jour les métadonnées de composant enregistrées lorsqu'une nouvelle version de votre composant est utilisée pour la première fois.  
  
 [Développement d’une interface utilisateur pour un composant de flux de données](developing-a-user-interface-for-a-data-flow-component.md)  
 Explique comment implémenter un éditeur personnalisé pour un composant.  
  
 [Développement de types spécifiques de composants de flux de données](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)  
 Contient des informations sur le développement des trois types de composants de flux de données : sources, transformations et destinations.  
  
## <a name="reference"></a>Référence  
 <xref:Microsoft.SqlServer.Dts.Pipeline>  
 Contient les classes et les interfaces qui permettent de créer des composants de flux de données personnalisés.  
  
 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>  
 Contient les classes et interfaces qui composent le modèle objet de tâche de flux de données, lequel est utilisé pour créer des composants de flux de données personnalisés ou générer une tâche de flux de données.  
  
 <xref:Microsoft.SqlServer.Dts.Pipeline.Design>  
 Contient les classes et interfaces utilisées pour créer l'interface utilisateur des composants de flux de données.  
  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services-error-and-message-reference.md)  
 Répertorie les codes d'erreur [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] prédéfinis avec leur nom symbolique et leur description.  
  
## <a name="related-sections"></a>Sections connexes  
  
### <a name="information-common-to-all-custom-objects"></a>Informations communes à tous les objets personnalisés  
 Pour obtenir les informations communes à tous les types d'objets personnalisés que vous pouvez créer dans [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], consultez les rubriques suivantes :  
  
 [Développement d’objets personnalisés pour Integration Services](../../extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)  
 Décrit les étapes de base permettant d’implémenter tous les types d’objets personnalisés pour [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
 [Persistance des objets personnalisés](../../extending-packages-custom-objects/persisting-custom-objects.md)  
 Décrit la persistance personnalisée et explique les situations dans lesquelles elle est nécessaire.  
  
 [Génération, déploiement et débogage d’objets personnalisés](../../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)  
 Décrit les techniques permettant de générer, signer, déployer et déboguer des objets personnalisés.  
  
### <a name="information-about-other-custom-objects"></a>Informations sur les autres objets personnalisés  
 Pour plus d’informations sur les autres types d’objets personnalisés que vous pouvez créer dans [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], consultez les rubriques suivantes :  
  
 [Développement d’une tâche personnalisée](../../extending-packages-custom-objects/task/developing-a-custom-task.md)  
 Explique comment programmer des tâches personnalisées.  
  
 [Développement d’un gestionnaire de connexions personnalisé](../../extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md)  
 Explique comment programmer des gestionnaires de connexions personnalisés.  
  
 [Développement d’un module fournisseur d’informations personnalisé](../../extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md)  
 Explique comment programmer des modules fournisseurs d'informations personnalisés.  
  
 [Développement d’un énumérateur ForEach personnalisé](../../extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 Décrit comment programmer des énumérateurs personnalisés.  
  
![Icône Integration Services (petite)](../../media/dts-16.gif "icône Integration Services (petite)")**rester jusqu'à la Date avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension du flux de données avec le composant Script] (.. /.. /Extending-packages-Scripting/Data-Flow-script-Component/Extending-the-Data-Flow-with-the-Script-Component.MD   
 [Comparaison des solutions de script et des objets personnalisés](../../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)  
  
  
