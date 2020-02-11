---
title: Outils de dépannage pour le développement des packages | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services packages, troubleshooting
- SSIS packages, troubleshooting
- Integration Services, troubleshooting
- errors [Integration Services], troubleshooting
- packages [Integration Services], troubleshooting
ms.assetid: 41dd248c-dab3-4318-b8ba-789a42d5c00c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 43eed16aa9cd69d70f308c3ce397720020446fdd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62885570"
---
# <a name="troubleshooting-tools-for-package-development"></a>Outils de dépannage pour le développement des packages
  
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] comprend des fonctionnalités et des outils que vous pouvez utiliser pour dépanner les packages quand vous les développez dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
## <a name="troubleshooting-design-time-validation-issues"></a>Dépannage des problèmes de validation au moment de la conception  
 Dans la version actuelle de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], quand un package est ouvert, le système valide toutes les connexions avant de valider tous les composants de flux de données, et définit toutes les connexions qui sont lentes ou non disponibles pour travailler hors connexion. Cela permet de réduire le délai de validation du flux de données du package.  
  
 Quand un package est ouvert, vous pouvez également désactiver une connexion en cliquant avec le bouton droit sur le gestionnaire de connexions dans la zone **Gestionnaires de connexions** et en cliquant sur **Travailler hors connexion**. Cela peut accélérer les opérations exécutées dans le concepteur SSIS.  
  
 Les connexions définies pour travailler hors connexion, restent hors connexion jusqu'à ce que vous effectuiez une des actions suivantes :  
  
-   Vous tester la connexion en cliquant avec le bouton droit sur le gestionnaire de connexions dans la zone **Gestionnaires de connexions** du concepteur SSIS et vous cliquez sur **Tester la connectivité**.  
  
     Par exemple, une connexion est initialement définie pour travailler hors connexion lorsque le package est ouvert. Vous modifiez la chaîne de connexion pour résoudre le problème et cliquez sur **Tester la connectivité** pour tester la connexion.  
  
-   Rouvrir le package ou rouvrir le projet qui contient le package. La validation est réexécutée sur toutes les connexions dans le package.  
  
 
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] inclut les fonctionnalités supplémentaires suivantes pour vous aider à éviter des erreurs de validation :  
  
-   **Définissez tout le package et toutes les connexions pour travailler hors connexion lorsque les sources de données ne sont pas disponibles**. Vous pouvez activer **Travailler hors connexion** à partir du menu **SSIS** . Contrairement à `DelayValidation` la propriété, l’option **travailler hors connexion** est disponible même avant l’ouverture d’un package. Vous pouvez également activer l’option **Travailler hors connexion** pour accélérer les opérations exécutées dans le concepteur, puis la désactiver dès que vous souhaitez valider votre package.  
  
-   **Configurez la propriété DelayValidation sur les éléments de package qui ne sont pas valides jusqu’au moment de l’exécution**. Pour éviter toute erreur de validation, vous pouvez définir la propriété `DelayValidation` avec la valeur `True` dans les éléments de package dont la configuration n'est pas valide au moment de la conception. Par exemple, vous pouvez disposer d'une tâche Flux de données qui utilise une table de destination qui n'existe pas jusqu'à ce qu'une tâche d'exécution SQL crée la table au moment de l'exécution. La propriété `DelayValidation` peut être activée au niveau du package ou au niveau des tâches individuelles et des conteneurs inclus dans le package. En règle générale, pour éviter les mêmes erreurs de validation au moment de l'exécution, vous devez laisser cette propriété avec la valeur `True` dans les mêmes éléments de package lors du déploiement du package.  
  
     La propriété `DelayValidation` peut être définie sur une tâche Flux de données mais pas sur des composants de flux de données individuels. Vous pouvez obtenir un résultat similaire en affectant à la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> des composants de flux de données individuels la valeur `false`. Néanmoins, si cette propriété affiche la valeur `false`, le composant n'a pas connaissance des modifications apportées aux métadonnées des sources de données externes.  
  
 Si les objets de base de données utilisés par le package sont verrouillés lorsque la validation se produit, le processus de validation peut cesser de répondre. Dans ces circonstances, le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] cesse également de répondre. Vous pouvez reprendre la validation à l’aide de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] pour fermer la session associée dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez aussi éviter ce problème en utilisant les paramètres décrits dans cette section.  
  
## <a name="troubleshooting-control-flow"></a>Dépannage du flux de contrôle  
 
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] comprend les fonctionnalités et outils suivants que vous pouvez utiliser pour dépanner le flux de contrôle dans les packages lors de leur développement :  
  
-   **Définir des points d’arrêt sur les tâches, les conteneurs et le package**. Vous pouvez définir des points d’arrêt à l’aide d’outils graphiques fournis par le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Les points d'arrêt peuvent être activés au niveau du package ou au niveau des tâches individuelles et des conteneurs inclus dans le package. Certaines tâches et certains conteneurs présentent des conditions d'arrêt supplémentaires pour la définition des points d'arrêt. Par exemple, vous pouvez activer une condition d'arrêt sur le conteneur de boucles For qui suspend l'exécution au début de chaque itération de la boucle.  
  
-   **Utilisez les fenêtres de débogage**. Lorsque vous exécutez un package doté de points d'arrêt, les fenêtres de débogage dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] fournissent un accès aux valeurs des variables et aux messages d'état.  
  
-   **Passez en revue les informations de l’onglet progression**. [!INCLUDE[ssIS](../../includes/ssis-md.md)] Le concepteur fournit des informations supplémentaires sur le contrôle de workflow lorsque vous [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]exécutez un package dans. L'onglet Progression énumère les tâches et les conteneurs par ordre d'exécution et indique les heures de début et de fin, les avertissements et les messages d'erreur pour chaque tâche et chaque conteneur, y compris le package lui-même.  
  
 Pour plus d’informations sur ces fonctionnalités, consultez [Débogage du flux de contrôle](debugging-control-flow.md).  
  
## <a name="troubleshooting-data-flow"></a>Dépannage du flux de données  
 
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] comprend les fonctionnalités et outils suivants que vous pouvez utiliser pour dépanner les flux de données dans les packages lors du développement de ces derniers :  
  
-   **Testez avec seulement un sous-ensemble de vos données**. Si vous voulez dépanner le flux de données dans un package en utilisant seulement un échantillon du dataset, vous pouvez inclure une transformation d'échantillonnage du pourcentage ou de ligne pour créer un exemple de données en ligne à l'exécution. Pour plus d’informations, consultez [Transformation de l’échantillonnage du pourcentage](../data-flow/transformations/percentage-sampling-transformation.md) et [Transformation d’échantillonnage de lignes](../data-flow/transformations/row-sampling-transformation.md).  
  
-   **Utilisez les visionneuses de données pour surveiller les données lors de leur déplacement dans le workflow**. Les visionneuses de données affichent des valeurs des données lors de leur déplacement entre des sources, des transformations et des destinations. Une visionneuse de données peut afficher des données dans une grille. Vous pouvez copier les données d'une visionneuse de données vers le Presse-papiers, puis coller les données dans un fichier ou une feuille de calcul Excel. Pour plus d’informations, consultez [Ajouter une visionneuse de données à un flux de données](../add-a-data-viewer-to-a-data-flow.md).  
  
-   **Configurez les sorties d’erreur sur les composants de Data Flow qui les prennent en charge**. De nombreuses sources, transformations et destinations de flux de données prennent également en charge les sorties d'erreur. En configurant la sortie d'erreur d'un composant de flux de données, vous pouvez diriger les données contenant des erreurs vers une autre destination. Par exemple, vous pouvez capturer les données qui ont échoué ou qui ont été tronquées dans un fichier texte séparé. Vous pouvez aussi associer des visionneuses de données aux sorties d'erreur et examiner uniquement les données erronées. Au moment de la conception, les sorties d'erreur capturent des valeurs de données problématiques pour vous aider à développer des packages qui prennent effectivement en charge les données réelles. Néanmoins, tandis que les autres outils et fonctionnalités de dépannage ne sont utiles qu'au moment de la conception, les sorties d'erreur le restent également dans l'environnement de production. Pour plus d’informations, consultez [Gestion des erreurs dans les données](../data-flow/error-handling-in-data.md).  
  
-   **Capturer le nombre de lignes traitées**. Quand vous exécutez un package dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , le nombre de lignes transmises par le biais d’un chemin est affiché dans le concepteur de flux de données. Ce nombre est mis à jour régulièrement lorsque des données empruntent le chemin d'accès. Vous pouvez également ajouter une transformation de nombre de lignes au flux de données pour capturer le nombre de lignes final dans une variable. Pour plus d’informations, voir [Row Count Transformation](../data-flow/transformations/row-count-transformation.md).  
  
-   **Passez en revue les informations de l’onglet progression**. [!INCLUDE[ssIS](../../includes/ssis-md.md)] Le concepteur fournit des informations supplémentaires sur les flux de données lorsque vous [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]exécutez un package dans. L'onglet Progression répertorie les composants de flux de données par ordre d'exécution et comprend des informations sur la progression de chaque phase du package (sous forme de pourcentage) et le nombre de lignes écrites sur la destination.  
  
 Pour plus d’informations sur ces fonctionnalités, consultez [Débogage d’un flux de données](debugging-data-flow.md).  
  
## <a name="troubleshooting-scripts"></a>Dépannage des scripts  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) est l’environnement de développement dans lequel vous écrivez les scripts utilisés par la tâche de script et le composant script. VSTA fournit les fonctionnalités et outils suivants que vous pouvez utiliser pour résoudre les problèmes liés aux scripts lors du développement des packages :  
  
-   **Définir des points d’arrêt dans le script des tâches de script.** VSTA prend en charge le débogage de scripts pour les tâches de script uniquement. Les points d'arrêt que vous définissez dans les tâches de script sont intégrés à ceux que vous définissez pour les packages, et les tâches et conteneurs du package, ce qui permet un débogage transparent de tous les éléments de package.  
  
    > [!NOTE]  
    >  Lorsque vous déboguez un package qui contient plusieurs tâches de script, le débogueur accède aux points d'arrêt d'une seule tâche de script et ignore les points d'arrêt des autres tâches de script. Si une tâche de script fait partie d'un conteneur de boucle Foreach ou For, le débogueur ignore les points d'arrêt de la tâche de script après la première itération de la boucle.  
  
 Pour plus d’informations, consultez [Script de débogage](debugging-script.md). Pour obtenir des suggestions sur le débogage du composant script, consultez [codage et débogage du composant Script] (.. /extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md.  
  
## <a name="troubleshooting-errors-without-a-description"></a>Dépannage des erreurs sans description  
 Si vous rencontrez un numéro d’erreur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] accompagné d’aucune description lors du développement du package, vous pouvez rechercher la description dans le [Guide de référence des erreurs et des messages propres à Integration Services](../integration-services-error-and-message-reference.md). La liste ne comporte actuellement aucune information de dépannage.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de dépannage pour l’exécution des packages](troubleshooting-tools-for-package-execution.md)   
 [Fonctionnalités de performances de flux de données](../data-flow/data-flow-performance-features.md)  
  
  
