---
title: Redémarrer des packages à l’aide de points de contrôle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- checkpoints [Integration Services]
- restarting packages
- starting packages
ms.assetid: 48f2fbb7-8964-484a-8311-5126cf594bfb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5cfe2595607a1da955942e9f2687322f977f3a22
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85423566"
---
# <a name="restart-packages-by-using-checkpoints"></a>Redémarrer des packages à l'aide de points de contrôle
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] peut redémarrer les packages ayant échoué à partir du point d'échec, au lieu de reprendre l'exécution du package tout entier. Si un package est configuré pour utiliser des points de contrôle, des informations sur l'exécution du package sont écrites dans un fichier de point de contrôle. Lorsque le package ayant échoué est relancé, le fichier de point de contrôle est utilisé pour redémarrer le package à partir du point d'échec. Si le package est exécuté avec succès, le fichier de point de contrôle est supprimé, puis recréé à l’exécution suivante du package.  
  
 L'utilisation des points de contrôle dans un package offre les avantages suivants :  
  
-   Éviter de répéter le téléchargement ascendant et descendant de gros fichiers. Par exemple, un package qui télécharge plusieurs gros fichiers à l'aide d'une tâche FTP pour chaque téléchargement peut être redémarré après l'échec du téléchargement d'un seul fichier, puis ne reprendre le téléchargement que pour ce fichier.  
  
-   Éviter de répéter le téléchargement de grands volumes de données. Par exemple, un package qui effectue des insertions en bloc dans des tables de dimension d'un entrepôt de données à l'aide d'une tâche d'insertion en bloc différente pour chaque dimension, peut être redémarré si l'insertion échoue pour une table de dimension, et ne recharger que cette dimension.  
  
-   Éviter de répéter l'agrégation de valeurs. Par exemple, un package qui calcule de nombreux agrégats, tels que des moyennes et des sommes, à l'aide d'une tâche de flux de données distincte pour la réalisation de chaque agrégation, peut être redémarré en cas d'échec du calcul d'une agrégation pour ne recalculer que cette agrégation.  
  
 Si un package est configuré pour utiliser les points de contrôle, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] capture le point de redémarrage dans le fichier de point de contrôle. Le type de conteneur qui échoue et l'implémentation de fonctionnalités telles que les transactions affectent le point de redémarrage enregistré dans le fichier de point de contrôle. Les valeurs actuelles des variables sont également capturées dans le fichier de point de contrôle. Toutefois, les valeurs des variables de type de données `Object` ne sont pas enregistrées dans les fichiers de point de contrôle.  
  
## <a name="defining-restart-points"></a>Définition des points de redémarrage  
 Le conteneur d'hôte de tâche, qui encapsule une seule tâche, est la plus petite unité atomique à pouvoir être redémarrée. Le conteneur de boucles Foreach et un conteneur transactionnel sont également traités comme des unités atomiques de travail.  
  
 Si un package est arrêté alors qu'un conteneur transactionnel est en cours d'exécution, la transaction est arrêtée et tout travail effectué par le conteneur est annulé. Lorsque le package est redémarré, le conteneur qui a échoué est exécuté à nouveau. La réalisation de conteneurs enfants du conteneur transactionnel n'est pas enregistrée dans le fichier de point de contrôle. Par conséquent, lorsque le package est redémarré, le conteneur transactionnel et ses conteneurs enfants sont exécutés à nouveau.  
  
> [!NOTE]  
>  L'utilisation de points de contrôle et de transactions dans le même package peut entraîner des résultats inattendus. Par exemple, lorsqu'un package échoue et redémarre à partir d'un point de contrôle, il peut répéter une transaction qui a déjà été correctement validée.  
  
 Les données de point de contrôle ne sont pas enregistrées pour les conteneurs de boucles For et Foreach. Lorsqu'un package est redémarré, les conteneurs de boucles For et Foreach et les conteneurs enfants sont exécutés à nouveau. Si un conteneur enfant de la boucle est exécuté correctement, il n'est pas enregistré dans le fichier de point de contrôle et il est exécuté à nouveau. Pour plus d'informations et pour obtenir une solution de contournement, consultez [Les points de contrôle SSIS ne sont pas respectés pour les éléments de conteneur de boucles For ou Foreach](https://go.microsoft.com/fwlink/?LinkId=241633).  
  
 Si le package est redémarré, les configurations du package ne sont pas rechargées, mais le package utilise les informations de configuration écrites dans le fichier de point de contrôle. Cette procédure assure que le package utilise les mêmes configurations lorsqu'il est exécuté à nouveau qu'au moment où il a échoué.  
  
 Un package ne peut être redémarré qu'au niveau du flux de contrôle. Vous ne pouvez pas redémarrer un package au milieu d'un flux de données. Pour éviter de réexécuter tout le flux de données, le package peut être conçu de manière à inclure plusieurs flux de données, utilisant chacun une tâche de flux de données différente. De cette manière, le package peut être redémarré en ne réexécutant qu'une seule tâche de flux de données.  
  
## <a name="configuring-a-package-to-restart"></a>Configuration d'un package pour le redémarrage  
 Le fichier de point de contrôle comprend les résultats d'exécution de tous les conteneurs achevés, les valeurs actuelles des variables système et définies par l'utilisateur, ainsi que les informations de configuration du package. Le fichier peut également inclure un identificateur unique du package. Pour redémarrer correctement le package, l'identificateur du package dans le fichier de point de contrôle doit correspondre au package. Dans le cas contraire, le redémarrage échoue. Cela empêche un package d'utiliser un fichier de point de contrôle écrit par une version de package différente. Si un package redémarre après avoir été exécuté correctement, le fichier de point de contrôle est supprimé.  
  
 Le tableau suivant présente les propriétés de package que vous définissez pour implémenter les points de contrôle.  
  
|Propriété|Description|  
|--------------|-----------------|  
|CheckpointFileName|Indique le nom du fichier de point de contrôle.|  
|CheckpointUsage|Indique si les points de contrôle sont utilisés.|  
|SaveCheckpoints|Indique si le package enregistre les points de contrôle. Cette propriété doit avoir pour valeur True pour redémarrer le package à partir d'un point d'échec.|  
  
 En outre, vous devez définir la propriété FailPackageOnFailure sur `true` pour tous les conteneurs du package que vous souhaitez identifier comme points de redémarrage.  
  
 Vous pouvez utiliser la propriété ForceExecutionResult pour tester l’utilisation des points de contrôle dans un package. En affectant la valeur la valeur Failure à la propriété ForceExecutionResult d’une tâche ou d’un conteneur, vous pouvez imiter un échec en temps réel. Lorsque vous redémarrez le package, la tâche et les conteneurs ayant échoué sont réexécutés.  
  
### <a name="checkpoint-usage"></a>Utilisation des points de contrôle  
 La propriété CheckpointUsage peut avoir les valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|`Never`|Spécifie que le fichier de point de contrôle n'est pas utilisé et que le package est exécuté à partir du début du flux de travail du package.|  
|`Always`|Spécifie que le fichier de point de contrôle est toujours utilisé et que le package redémarre à partir du point de l'échec de la précédente exécution. Si le fichier de point de contrôle est introuvable, le package échoue.|  
|`IfExists`|Spécifie que le fichier de point de contrôle est utilisé s'il existe. Si le fichier de point de contrôle existe, le package redémarre à partir du point de l'échec de la précédente exécution. Sinon il est exécuté à partir du début du flux de travail du package.|  
  
> [!NOTE]  
>  L’option **/checkpointing on on** de dtexec équivaut à affecter à la `SaveCheckpoints` propriété du package la valeur `True` et à la `CheckpointUsage` propriété la valeur Always. Pour plus d'informations, consultez [Utilitaire dtexec](dtexec-utility.md).  
  
## <a name="securing-checkpoint-files"></a>Sécurisation des fichiers de point de contrôle  
 La protection au niveau du package n'inclut pas la protection des fichiers de point de contrôle ; vous devez donc sécuriser ces fichiers séparément. Les données de point de contrôle peuvent être stockées uniquement dans le système de fichiers et vous devez utiliser une liste de contrôle d'accès au système d'exploitation pour sécuriser l'emplacement ou le dossier de stockage du fichier. Il est important de sécuriser les fichiers de point de contrôle car ceux-ci contiennent des informations sur l'état du package, notamment les valeurs actuelles des variables. Une variable peut ainsi contenir un ensemble d'enregistrements doté de plusieurs lignes de données privées, telles que des numéros de téléphone. Pour plus d’informations, consultez [accès aux fichiers utilisés par les packages](../access-to-files-used-by-packages.md).  
  
### <a name="to-configure-the-checkpoint-properties"></a>Pour configurer les propriétés des points de contrôle  
  
-   [Configurer des points de contrôle pour redémarrer un package ayant échoué](../configure-checkpoints-for-restarting-a-failed-package.md)  
  
## <a name="external-resources"></a>Ressources externes  
  
-   Article technique, [Redémarrage automatique des packages SSIS après un basculement ou un échec](https://go.microsoft.com/fwlink/?LinkId=200407), sur social.technet.microsoft.com  
  
-   Article du Support technique Microsoft, [Les points de contrôle SSIS ne sont pas respectés pour les éléments de conteneur de boucles For ou Foreach](https://go.microsoft.com/fwlink/?LinkId=241633), sur le site support.microsoft.com.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Integration Services](../sql-server-integration-services.md)  
  
  
