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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ee2b30cf0796953d12f976745fb195169de86c68
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437076"
---
# <a name="developing-a-custom-data-flow-component"></a>Développement d'un composant de flux de données personnalisé
  La tâche de flux de données comprend des composants qui se connectent à diverses sources de données et qui transforment et acheminent ces données à haut débit. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] fournit un modèle objet extensible qui permet aux développeurs de créer des sources, des transformations et des destinations personnalisées que vous pouvez utiliser dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] et dans des packages déployés. Cette section contient des rubriques qui vous guideront afin de développer des composants de flux de données personnalisés.

## <a name="in-this-section"></a>Dans cette section
 [Création d’un composant de workflow de données personnalisé](creating-a-custom-data-flow-component.md) Décrit les étapes initiales à suivre pour créer un composant de workflow de données personnalisé.

 [Méthodes au moment du design d’un composant de Data Flow](design-time-methods-of-a-data-flow-component.md) Décrit les méthodes de conception à implémenter dans un composant de workflow de données personnalisé.

 [Méthodes d’exécution d’un composant de transmission de données](run-time-methods-of-a-data-flow-component.md) Décrit les méthodes d’exécution à implémenter dans un composant de workflow de données personnalisé.

 [Plan d’exécution et allocation de mémoire tampon](execution-plan-and-buffer-allocation.md) Décrit le plan d’exécution du workflow et l’allocation des tampons de données.

 [Utilisation des types de données dans le workflow](working-with-data-types-in-the-data-flow.md) Explique comment le workflow mappe les [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] types de données aux types de données managées .NET Framework.

 [Validation d’un composant de transmission de données](validating-a-data-flow-component.md) Explique les méthodes utilisées pour valider la configuration des composants et pour reconfigurer les métadonnées des composants.

 [Implémentation de métadonnées externes](implementing-external-metadata.md) Explique comment utiliser des colonnes de métadonnées externes pour la validation des données.

 [Déclenchement et définition d’événements dans un composant de transmission de données](raising-and-defining-events-in-a-data-flow-component.md) Explique comment déclencher des événements prédéfinis et personnalisés.

 [Journalisation et définition des entrées de journal dans un composant de Data Flow](logging-and-defining-log-entries-in-a-data-flow-component.md) Explique comment créer et écrire dans des entrées de journal personnalisées.

 [Utilisation des sorties d’erreur dans un composant de transmission de données](using-error-outputs-in-a-data-flow-component.md) Explique comment rediriger les lignes d’erreur vers une autre sortie.

 [Mise à niveau de la version d’un composant de Data Flow](upgrading-the-version-of-a-data-flow-component.md) Explique comment mettre à jour les métadonnées de composant enregistrées lorsqu’une nouvelle version de votre composant est utilisée pour la première fois.

 [Développement d’une interface utilisateur pour un composant de Data Flow](developing-a-user-interface-for-a-data-flow-component.md) Explique comment implémenter un éditeur personnalisé pour un composant.

 [Développement de types spécifiques de composants de workflow](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md) Contient des informations sur le développement des trois types de composants de Data Flow : les sources, les transformations et les destinations.

## <a name="reference"></a>Informations de référence
 <xref:Microsoft.SqlServer.Dts.Pipeline>Contient les classes et les interfaces utilisées pour créer des composants de workflow de données personnalisés.

 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>Contient les classes et les interfaces qui composent le modèle objet de tâche de workflow et est utilisé pour créer des composants de workflow de données personnalisés ou pour générer une tâche de Workflow.

 <xref:Microsoft.SqlServer.Dts.Pipeline.Design>Contient les classes et les interfaces utilisées pour créer l’interface utilisateur pour les composants de Data Flow.

 [Integration Services de référence des erreurs et des messages](../../integration-services-error-and-message-reference.md) Répertorie les [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] codes d’erreur prédéfinis avec leur nom symbolique et leur description.

## <a name="related-sections"></a>Sections connexes

### <a name="information-common-to-all-custom-objects"></a>Informations communes à tous les objets personnalisés
 Pour obtenir les informations communes à tous les types d'objets personnalisés que vous pouvez créer dans [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], consultez les rubriques suivantes :

 [Développement d’objets personnalisés pour Integration Services](../../extending-packages-custom-objects/developing-custom-objects-for-integration-services.md) Décrit les étapes de base de l’implémentation de tous les types d’objets personnalisés pour [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] .

 [Persistance des objets personnalisés](../../extending-packages-custom-objects/persisting-custom-objects.md) Décrit la persistance personnalisée et explique quand elle est nécessaire.

 [Génération, déploiement et débogage d’objets personnalisés](../../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md) Décrit les techniques permettant de générer, signer, déployer et déboguer des objets personnalisés.

### <a name="information-about-other-custom-objects"></a>Informations sur les autres objets personnalisés
 Pour plus d’informations sur les autres types d’objets personnalisés que vous pouvez créer dans [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], consultez les rubriques suivantes :

 [Développement d’une tâche personnalisée](../../extending-packages-custom-objects/task/developing-a-custom-task.md) Explique comment programmer des tâches personnalisées.

 [Développement d’un gestionnaire de connexions personnalisé](../../extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md) Explique comment programmer des gestionnaires de connexions personnalisés.

 [Développement d’un module fournisseur d’informations personnalisé](../../extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md) Explique comment programmer des modules fournisseurs d’informations personnalisés.

 [Développement d’un énumérateur foreach personnalisé](../../extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md) Explique comment programmer des énumérateurs personnalisés.

![Icône de Integration Services (petite)](../../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.

## <a name="see-also"></a>Voir aussi
 [Extension du workflow de données à l’aide du composant Script] (.. /.. /Extending-packages-Scripting/Data-Flow-script-Component/Extending-the-Data-Flow-with-the-script-Component.MD [comparaison des solutions de script et des objets personnalisés](../../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)


