---
title: Définition des valeurs de délai d’attente pour le traitement d’un rapport et d’un jeu de données partagé (SSRS) | Microsoft Docs
description: Dans Reporting Services, vous pouvez spécifier des valeurs de délai d’attente pour fixer des limites à l’utilisation des ressources système.
ms.date: 01/16/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- time-outs [Reporting Services]
- query time-outs [Reporting Services]
- report processing [Reporting Services], time-outs
- report execution time-outs [Reporting Services]
ms.assetid: 0f9dc61d-d03c-4bbf-8090-7a53844350f8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 1bc1f2f27fa46f8262d3c0ca99549d23f2381ff0
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "76259409"
---
# <a name="setting-time-out-values-for-report-and-shared-dataset-processing-ssrs"></a>Définition des valeurs de délai d'attente pour le traitement d'un rapport et d'un dataset partagé (SSRS)
Dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous pouvez spécifier des valeurs de délai d’attente pour fixer des limites à l’utilisation des ressources système. Les serveurs de rapports acceptent deux valeurs de délai d'attente :  
  
- Une valeur de délai d'attente de requête de dataset incorporé, qui est le nombre de secondes pendant lequel le serveur de rapports attend une réponse de la base de données. Cette valeur est définie dans un rapport.  
  
- Une valeur de délai d'attente de requête de dataset partagé, qui est le nombre de secondes pendant lequel le serveur de rapports attend une réponse de la base de données. Cette valeur fait partie de la définition de dataset partagée et peut être modifiée lorsque vous gérez le dataset partagé sur le serveur de rapports.  
  
- Une valeur de délai d'attente pour l'exécution de rapport représente le nombre maximal de secondes pendant lequel le traitement de rapport peut se poursuivre avant d'être arrêté. Cette valeur est définie au niveau système. Ce paramètre est modifiable pour chaque rapport.  
  
 La plupart des erreurs liées au délai d'attente se produisent pendant le traitement des requêtes. Si vous rencontrez des erreurs de ce type, essayez d'augmenter la valeur du délai d'attente de la requête. Veillez à ce que la valeur du délai d'attente pour l'exécution du rapport soit supérieure au délai d'attente de la requête. Le temps imparti doit être suffisamment long pour permettre aux traitements de la requête et du rapport de s'effectuer.  
  
## <a name="setting-a-query-time-out-for-an-embedded-dataset-in-a-report"></a>Définition d'un délai de requête pour un dataset incorporé dans un rapport  
 Les valeurs de délai d'attente de la requête sont spécifiées pendant la création du rapport, lors de la définition d'un dataset incorporé. La valeur du délai d’attente est conservée avec le rapport, dans l’élément **Timeout** de la définition de rapport. Elle est par défaut de 30 secondes. Pour plus d’informations, consultez [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
 
 > [!NOTE]  
 > Pour les **rapports paginés dans Power BI**, la valeur par défaut est définie sur **600 secondes**.
 
 Les utilisateurs autorisés à modifier les propriétés d'un rapport publié peuvent redéfinir cette valeur en modifiant le fichier de définition de rapport.  
  
 Vous pouvez également spécifier une valeur de délai d'attente de requête pour des abonnements pilotés par les données. Le délai d'attente de requête est spécifié dans les pages Abonnement piloté par les données. La valeur spécifiée détermine le temps pendant lequel le serveur de rapports attend la fin du traitement de la requête lors d'une opération de récupération de données à partir de la source de données des abonnés.  
  
## <a name="setting-a-query-time-out-for-a-shared-dataset"></a>Définition d'un délai de requête pour un dataset partagé  
 Les valeurs de délai de requête sont spécifiées en secondes sur le serveur de rapports lorsque vous créez ou gérez un dataset partagé. Par défaut, cette valeur est définie sur 0 seconde, ce qui équivaut à une valeur sans délai d'attente. Pour plus d’informations, consultez [Gérer des datasets partagés](../../reporting-services/report-data/manage-shared-datasets.md).  
  
## <a name="setting-a-report-execution-time-out"></a>Définition d'un délai d'attente pour l'exécution de rapports  
 Vous pouvez définir un délai d'attente pour l'exécution de rapports de façon à limiter le temps que le serveur de rapports consacre au traitement d'un rapport. Les valeurs de délai d'attente peuvent être spécifiées dans le portail web. Vous pouvez définir une valeur par défaut pour tous les rapports dans la page des paramètres du site, puis remplacer cette valeur dans la page des propriétés d'exécution pour un rapport spécifique. Par défaut, la valeur est fixée à 1 800 secondes. Pour plus d’informations, consultez [Définir les propriétés de traitement d’un rapport](../../reporting-services/report-server/set-report-processing-properties.md).  
  
## <a name="how-report-execution-time-out-values-are-evaluated"></a>Méthode d'évaluation des valeurs d'expiration pour l'exécution de rapports  
 Le serveur de rapports évalue les travaux en cours d'exécution toutes les 60 secondes. Il compare alors la durée de traitement réelle à la valeur d'expiration de l'exécution du rapport. Si la durée du traitement d'un rapport dépasse la valeur d'expiration pour l'exécution du rapport, le traitement du rapport s'arrête.  
  
 Notez que si vous spécifiez une valeur d'expiration inférieure à 60 secondes, le rapport peut s'exécuter intégralement si le traitement démarre et se termine pendant la partie inactive du cycle, alors que le serveur de rapports n'est pas en train d'évaluer les travaux en cours d'exécution. Par exemple, si vous définissez une valeur d'expiration de 10 secondes pour un rapport dont l'exécution en prend 20, le rapport sera entièrement traité si son exécution commence au début du cycle des 60 secondes.  
  
> [!NOTE]  
> Vous pouvez définir le paramètre **RunningRequestsDbCycle** du fichier RSReportServer.config pour changer la fréquence d’évaluation des travaux en cours d’exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Définir les options de traitement &#40;Reporting Services en mode intégré SharePoint&#41;](../../reporting-services/report-server-sharepoint/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)   
 [Serveur de rapports Reporting Services &#40;mode natif&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [Gérer un processus en cours d'exécution](../../reporting-services/subscriptions/manage-a-running-process.md)   
 [Le portail web d’un serveur de rapports (Mode natif SSRS)](../../reporting-services/web-portal-ssrs-native-mode.md)  
  
