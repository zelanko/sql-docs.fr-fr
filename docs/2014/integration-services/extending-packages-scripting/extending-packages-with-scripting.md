---
title: Extension de packages avec des scripts | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- SQL Server Integration Services, scripting
- SSIS, scripting
- scripts [Integration Services], about scripting
ms.assetid: 67fe18ef-f3aa-41d4-9b9d-5defd4618c4b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: bb567bffe0c184907ca61bd583eb5666948a0f03
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "78176180"
---
# <a name="extending-packages-with-scripting"></a>Extension de packages avec des scripts
  Si vous constatez que les composants intégrés [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ne satisfont pas vos besoins, vous pouvez étendre la puissance d'[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en codant vos propres extensions. Vous disposez de deux options distinctes pour étendre vos packages : vous pouvez écrire du code dans les puissants wrappers fournis par la tâche de script et le composant Script, ou vous pouvez entièrement créer des extensions [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] personnalisées, dérivées des classes de base fournies par le modèle objet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].

 Cette section explore le plus simple des deux options : étendre des packages à l’aide de scripts.

 La tâche de script et le composant Script vous permettent d'étendre le flux de contrôle et le flux de données d'un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] avec un minimum de code. Les deux objets utilisent l’environnement de développement [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) et les langages de programmation [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#. Par ailleurs, ils bénéficient de toutes les fonctionnalités offertes par la bibliothèque de classes [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], ainsi que des assemblys personnalisés. La tâche de script et le composant Script permettent aux développeurs de créer des fonctionnalités personnalisées sans devoir écrire tout le code d'infrastructure généralement requis lors du développement d'une tâche personnalisée ou d'un composant de flux de données personnalisé.

## <a name="in-this-section"></a>Dans cette section
 [Comparaison de la tâche de script et du composant script](../extending-packages-scripting/comparing-the-script-task-and-the-script-component.md) Décrit les similitudes et les différences entre la tâche de script et le composant script.

 [Comparaison des solutions de script et des objets personnalisés](comparing-scripting-solutions-and-custom-objects.md) Décrit les critères à utiliser pour choisir entre une solution de script et le développement d’un objet personnalisé.

 [Référencement d’autres assemblys dans des solutions de script](referencing-other-assemblies-in-scripting-solutions.md) Décrit les étapes requises pour référencer et utiliser des assemblys et des espaces de noms externes dans un projet de script.

 [Extension du package à l’aide de la tâche de script](../extending-packages-scripting/task/extending-the-package-with-the-script-task.md) Explique comment créer des tâches personnalisées à l’aide de la tâche de script. Une tâche est généralement appelée une fois par package exécuté, ou une fois pour chaque source de données ouverte par un package.

 [Extension du workflow de données à l’aide du composant script](data-flow-script-component/extending-the-data-flow-with-the-script-component.md) Explique comment créer des sources de données, des transformations et des destinations de workflow personnalisées à l’aide du composant script. Un composant de flux de données est généralement appelé une fois pour chaque ligne de données traitée.

## <a name="reference"></a>Informations de référence
 [Integration Services de référence des erreurs et des messages](../integration-services-error-and-message-reference.md) Répertorie les codes d' [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] erreur prédéfinis avec leur nom symbolique et leur description.

## <a name="related-sections"></a>Sections connexes
 [Extension de packages avec des objets personnalisés](../extending-packages-custom-objects/extending-packages-with-custom-objects.md) Explique comment créer des tâches personnalisées de programme, des composants de workflow de données et d’autres objets de package à utiliser dans plusieurs packages.

 [Génération de packages par programmation](../building-packages-programmatically/building-packages-programmatically.md) Décrit comment créer, configurer, exécuter, charger, enregistrer et gérer [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] des packages par programme.

![Icône de Integration Services (petite)](../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les téléchargements, articles, exemples et vidéos les plus récents de [!INCLUDE[msCoName](../../includes/msconame-md.md)], ainsi que les solutions retenues par la communauté informatique, consultez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.

## <a name="see-also"></a>Voir aussi
 [SQL Server Integration Services](../sql-server-integration-services.md)


