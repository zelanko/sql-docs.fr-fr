---
title: Extension de packages avec des objets personnalisés | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 26616eb8-9e80-434d-b22a-ece1b00f449d
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e7460a0ca2d124e55a7b371e5aa6d241d5dacd05
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038373"
---
# <a name="extending-packages-with-custom-objects"></a>Extension de packages avec des objets personnalisés
  Si vous constatez que les composants fournis dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ne satisfont pas vos besoins, vous pouvez étendre la puissance d'[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en codant vos propres extensions. Vous disposez de deux options distinctes pour étendre vos packages : vous pouvez écrire du code dans les puissants wrappers fournis par la tâche de script et le composant Script, ou vous pouvez entièrement créer des extensions [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] personnalisées, dérivées des classes de base fournies par le modèle objet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Cette section explore l'option la plus avancée des deux : l'extension de packages à l'aide d'objets personnalisés.  
  
 Lorsque votre solution [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] personnalisée exige davantage de flexibilité que celle fournie par la tâche de script ou le composant Script, ou lorsque vous avez besoin d'un composant réutilisable dans plusieurs packages, le modèle objet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] vous permet de créer des tâches personnalisées, des composants de flux de données et d'autres objets de package en code managé.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Développement d’objets personnalisés pour Integration Services](developing-custom-objects-for-integration-services.md)  
 Présente les objets personnalisés qui peuvent être créés pour [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et résume les étapes et les paramètres essentiels.  
  
 [Persistance des objets personnalisés](persisting-custom-objects.md)  
 Examine la persistance par défaut des objets personnalisés et le processus d'implémentation de la persistance personnalisée.  
  
 [Génération, déploiement et débogage d’objets personnalisés](building-deploying-and-debugging-custom-objects.md)  
 Présente les méthodes les plus usuelles pour créer, déployer et tester les différents types d'objets personnalisés.  
  
 [Développement d’une tâche personnalisée](task/developing-a-custom-task.md)  
 Décrit le processus de codage d'une tâche personnalisée.  
  
 [Développement d’un gestionnaire de connexions personnalisé](connection-manager/developing-a-custom-connection-manager.md)  
 Décrit le processus de codage d'un gestionnaire de connexions personnalisé.  
  
 [Développement d’un module fournisseur d’informations personnalisé](log-provider/developing-a-custom-log-provider.md)  
 Décrit le processus du codage d'un module fournisseur d'informations personnalisé.  
  
 [Développement d’un énumérateur ForEach personnalisé](foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 Décrit le processus de codage d'un énumérateur personnalisé.  
  
 [Développement d’un composant de flux de données personnalisé](data-flow/developing-a-custom-data-flow-component.md)  
 Explique comment programmer des sources, des transformations et des destinations de flux de données personnalisées.  
  
## <a name="reference"></a>Référence  
 [Guide de référence des erreurs et des messages propres à Integration Services](../integration-services-error-and-message-reference.md)  
 Répertorie les codes d'erreur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] prédéfinis avec leur nom symbolique et leur description.  
  
## <a name="related-sections"></a>Sections connexes  
 [Extension de packages avec des scripts](../extending-packages-scripting/extending-packages-with-scripting.md)  
 Explique comment étendre le flux de contrôle à l'aide de la tâche de script, ou comment étendre le flux de données à l'aide du composant Script.  
  
 [Génération de packages par programmation](../building-packages-programmatically/building-packages-programmatically.md)  
 Décrit comment créer, configurer, exécuter, charger, enregistrer et gérer des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] par programme.  
  
![Icône Integration Services (petite)](../media/dts-16.gif "icône Integration Services (petite)")**restent jusqu'à la Date avec Integration Services** <br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Comparaison des solutions de script et des objets personnalisés](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)   
 [SQL Server Integration Services](../sql-server-integration-services.md)  
  
  