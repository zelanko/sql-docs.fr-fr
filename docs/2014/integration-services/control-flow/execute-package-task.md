---
title: Exécuter le package, tâche | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executepackagetask.f1
helpviewer_keywords:
- Execution Package task [Integration Services]
- child packages
- parent packages [Integration Services]
ms.assetid: 042d4ec0-0668-401c-bb3a-a25fe2602eac
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 37d0edcabdb0171c8ca83c79080d59fdd8aafb76
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67284954"
---
# <a name="execute-package-task"></a>Tâche d'exécution de package
  La tâche d'exécution de package étend les fonctionnalités d'entreprise de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en permettant à des packages d'exécuter d'autres packages au sein d'un flux de travail.  
  
 Vous pouvez utiliser la tâche d'exécution de package aux fins suivantes :  
  
-   Division d'un flux de travail de package complexe. Cette tâche vous permet de diviser le flux de travail en plusieurs packages, qui sont plus faciles à lire, à tester et à maintenir. Par exemple, si vous chargez des données dans un schéma en étoile, vous pouvez créer un package distinct pour remplir chaque dimension et la table de faits.  
  
-   Réutilisation de parties de packages. D'autres packages peuvent réutiliser des parties d'un flux de travail de package. Par exemple, vous pouvez créer un module d'extraction des données qui peut être appelé depuis différents packages. Chaque package qui appelle le module d'extraction peut exécuter différentes opérations de purge, de filtrage ou d'agrégation sur les données.  
  
-   Regroupement des unités de travail. Les unités de travail peuvent être encapsulées dans des packages distincts et incluses sous forme de composants transactionnels au flux de travail d'un package parent. Par exemple, le package parent exécute les packages secondaires et, en fonction de la réussite ou de l'échec des packages secondaires, il valide ou annule la transaction.  
  
-   Contrôle de la sécurité des packages. Les auteurs de package ont besoin d'accéder à une seule partie d'une solution multipackage. En séparant un package en plusieurs packages, vous pouvez fournir un niveau de sécurité plus élevé ; en effet, vous pouvez permettre à un auteur d'accéder aux seuls packages appropriés.  
  
 Un package qui exécute d'autres packages est généralement appelé « package parent », tandis que les packages exécutés par un flux de travail parent sont appelés « packages enfants ».  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] comprend des tâches qui effectuent des opérations de flux de travail, telles que l'exécution de fichiers de commandes, d'exécutables et de packages. Pour plus d'informations, consultez [Execute Process Task](execute-process-task.md).  
  
## <a name="running-packages"></a>Exécution des packages  
 La tâche d'exécution de package peut exécuter des packages enfants contenus dans le même projet qui contient le package parent. Vous sélectionnez un package enfant d'un projet en définissant la propriété **ReferenceType** sur **Project Reference**, puis en définissant la propriété **PackageNameFromProjectReference** .  
  
> [!NOTE]  
>  L’option **ReferenceType** est en lecture seule et est définie sur **Référence externe** si le projet qui contient le package n’a pas été converti en modèle de déploiement de projet. Pour plus d’informations sur la conversion, consultez [Déployer des projets sur le serveur Integration Services](../deploy-projects-to-integration-services-server.md).  
  
 La tâche d’exécution de package peut exécuter des packages stockés dans la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb et des packages stockés dans le système de fichiers. La tâche utilise un gestionnaire de connexions OLE DB pour se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou un gestionnaire de connexions de fichiers pour accéder au système de fichiers. Pour plus d'informations, consultez [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md) et [Flat File Connection Manager](../connection-manager/flat-file-connection-manager.md).  
  
 La tâche d'exécution de package peut également exécuter un plan de maintenance de base de données, ce qui vous permet de gérer les packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] et les plans de maintenance de base de données dans la même solution [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Un plan de maintenance de base de données est similaire à un package [!INCLUDE[ssIS](../../includes/ssis-md.md)] , mais il ne peut inclure que des tâches de maintenance de base de données et est toujours stocké dans la base de données msdb.  
  
 Si vous choisissez un package stocké dans le système de fichiers, vous devez fournir le nom et l'emplacement du package. Le package peut se trouver à n'importe quel endroit dans le système de fichiers ; il n'est pas nécessaire qu'il figure dans le même dossier que le package parent.  
  
 Le package enfant peut être exécuté dans le processus du package parent ou dans son propre processus. L'exécution du package enfant dans son propre processus nécessite davantage de mémoire, mais elle offre plus de souplesse. Par exemple, si le processus enfant échoue, l'exécution du processus parent peut se poursuivre.  
  
 Dans d'autres situations, vous pouvez préférer que les packages parent et enfants échouent ensemble comme une même unité, ou bien éviter la charge de traitement supplémentaire d'un autre processus. Par exemple, si un processus enfant échoue et que les traitements ultérieurs du processus parent du package dépendent de la réussite du processus enfant, alors le package enfant doit s'exécuter dans le processus du package parent.  
  
 Par défaut, la propriété ExecuteOutOfProcess a de la tâche d’exécution de package a `False`la valeur, et le package enfant s’exécute dans le même processus que le package parent. Si vous affectez la valeur `True` à cette propriété, le package enfant s'exécute dans un processus indépendant. Cela peut ralentir le lancement du package enfant. En outre, si vous affectez la valeur `True` à la propriété, vous ne pouvez pas déboguer le package dans une installation d'outils uniquement. Vous devez installer [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Pour plus d’informations, consultez [Installer Integration Services](../install-windows/install-integration-services.md).  
  
## <a name="extending-transactions"></a>Extension des transactions  
 La transaction que le package parent utilise peut être étendue au package enfant ; par conséquent, le travail réalisé par les deux packages peut être validé ou annulé. Par exemple, les insertions dans une base de données effectuées par le package parent peuvent être validées ou annulées, en fonction de celles réalisées par le package enfant, et vice versa. Pour plus d'informations, consultez [Inherited Transactions](../inherited-transactions.md).  
  
## <a name="propagating-logging-details"></a>Propagation des détails de la journalisation  
 Le package enfant exécuté par la tâche d'exécution de package peut ou non être configuré de manière à utiliser la journalisation, mais il transfère toujours les détails du journal au package parent. Si la tâche d'exécution de package est configurée de manière à utiliser la journalisation, elle consigne les informations détaillées du journal à partir du package enfant. Pour plus d’informations, consultez [Journalisation Integration Services &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md).  
  
## <a name="passing-values-to-child-packages"></a>Passage de valeurs à des packages enfants  
 Un package enfant utilise fréquemment des valeurs transmises par un autre package qui l'appelle, généralement son package parent. L'utilisation de valeurs issues d'un package parent est utile dans les scénarios suivants :  
  
-   Les parties d'un flux de travail plus volumineux sont affectées à différents packages. Par exemple, un package télécharge des données chaque nuit, les résume, affecte des valeurs de données de synthèse à des variables, puis les passe à un autre package qui les traite à son tour.  
  
-   Le package parent coordonne dynamiquement les tâches d'un package enfant. Par exemple, le package parent détermine le nombre de jours d'un mois en cours et affecte ce nombre à une variable, puis le package enfant effectue une tâche autant de fois que la valeur du nombre.  
  
-   Un package enfant nécessite l'accès à des données dérivées dynamiquement par le package parent. Par exemple, le package parent extrait des données d'une table et charge l'ensemble de lignes dans une variable, puis le package enfant effectue des opérations supplémentaires sur les données.  
  
 Vous pouvez utiliser les méthodes suivantes pour passer des valeurs à un package enfant :  
  
-   **Configurations de package**  
  
     [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contient un type de configuration, en l'occurrence la configuration Variable de package parent, qui permet de passer les valeurs du package parent au package enfant. La configuration est basée sur le package enfant et utilise une variable dans le package parent. La configuration est mappée à une variable ou à la propriété d'un objet du package enfant. La variable peut également être utilisée dans les scripts utilisés par la tâche de script ou le composant de script.  
  
-   **Paramètres**  
  
     Vous pouvez configurer la tâche d'exécution des packages pour mapper les variables ou paramètres de package parent (ou les paramètres du projet) aux paramètres de package enfant. Le projet doit utiliser le modèle de déploiement de projet et le package enfant doit être contenu dans le même projet qui contient le package parent. Pour plus d'informations, consultez [Execute Package Task Editor](../execute-package-task-editor.md).  
  
    > [!NOTE]  
    >  Si le paramètre de package enfant ne respecte pas la casse et s'il est mappé à un paramètre parent qui respecte la casse, le package enfant ne peut pas s'exécuter.  
    >   
    >  Les conditions de mappage suivantes sont prises en charge :  
    >   
    >  -   Le paramètre de package enfant qui respecte la casse est mappé à un paramètre parent qui respecte la casse.  
    > -   Le paramètre de package enfant qui respecte la casse est mappé à un paramètre parent qui ne respecte pas la casse.  
    > -   Le paramètre de package enfant qui ne respecte pas la casse est mappé à un paramètre parent qui ne respecte pas la casse.  
  
 La variable du package parent peut être définie dans l'étendue de la tâche d'exécution de package ou dans un conteneur parent tel que le package. Si plusieurs variables de même nom sont disponibles, la variable utilisée est celle définie dans l'étendue de la tâche d'exécution de package ou celle qui, du point de vue de l'étendue, est la plus proche de la tâche.  
  
 Pour plus d’informations, consultez [Utiliser les valeurs des variables et des paramètres dans un package enfant](../use-the-values-of-variables-and-parameters-in-a-child-package.md).  
  
### <a name="accessing-parent-package-variables"></a>Accès aux variables de package parent  
 Les packages enfants peuvent accéder à des variables de package parent à l'aide de la tâche de script. Quand vous entrez le nom de la variable de package parent sur la page **Script** dans l’**Éditeur de tâche de script**, n’incluez pas **Utilisateur :** dans le nom de la variable. Sinon, le package enfant ne localise pas la variable quand vous exécutez le package parent. Pour plus d’informations sur l’utilisation de la tâche de script pour accéder aux variables de package parentes, consultez cette entrée de blog, [SSIS : accès aux variables dans un package parent](https://andyleonard.blog/2015/08/ssis-design-pattern-access-parent-variables-from-a-child-package-in-the-ssis-catalog/).  
  
## <a name="configuring-the-execute-package-task"></a>Configuration de la tâche d'exécution de package  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de tâche d’exécution de package](../execute-package-task-editor.md)  
  
-   [Page Expressions](../expressions/expressions-page.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-content"></a>Contenu associé  

Entrée de blog, [SSIS : accès aux variables dans un package parent](https://andyleonard.blog/2015/08/ssis-design-pattern-access-parent-variables-from-a-child-package-in-the-ssis-catalog/), sur andyleonard. blog. 
  
  
