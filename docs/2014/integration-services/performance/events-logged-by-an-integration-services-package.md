---
title: Événements journalisés par un package Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- package [Integration Services], events
- events [Integration Services], package
ms.assetid: 55a0951a-46f3-4f0f-9972-74cec9cc26b7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ef709a48f0c5c162e971cebbdf5d49c4417250ed
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62889833"
---
# <a name="events-logged-by-an-integration-services-package"></a>Événements journalisés par un package Integration Services
  Un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] consigne différents messages d'événements dans le journal des événements des applications Windows. Un package enregistre ces messages lorsqu'il démarre, lorsqu'il s'arrête et lorsque certains problèmes se produisent.  
  
 Cette rubrique fournit des informations sur les messages d'événements courants qu'un package enregistre dans le journal des événements des applications. Par défaut, un package enregistre certains de ces messages même si vous n'avez pas activé l'enregistrement sur le package. Toutefois, il existe d'autres messages que le package enregistrera seulement si vous avez activé l'enregistrement sur le package. Que le package enregistre ces messages par défaut ou parce que l'enregistrement a été activé, la source d'événements pour les messages est SQLISPackage.  
  
 Pour obtenir des informations générales sur l’exécution des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [Exécution des projets et des packages](../packages/run-integration-services-ssis-packages.md).  
  
 Pour plus d’informations sur la résolution des packages en cours d’utilisation, consultez [Outils de dépannage pour l’exécution des packages](../troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
## <a name="messages-about-the-status-of-the-package"></a>Messages relatifs à l'état du package  
 Lorsque vous exécutez un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , le package enregistre généralement différents messages sur la progression et l'état du package. Le tableau ci-dessous répertorie ces messages.  
  
> [!NOTE]  
>  Le package enregistrera les messages du tableau ci-dessous même si vous n'avez pas activé l'enregistrement pour le package.  
  
|ID d'événement|Nom symbolique|Text|Remarques|  
|--------------|-------------------|----------|-----------|  
|12288|DTS_MSG_PACKAGESTART|Package «  » démarré.|L'exécution du package a commencé.|  
|12289|DTS_MSG_PACKAGESUCCESS|Fin du package «  » réussie.|Le package s'est exécuté avec succès et ne s'exécute plus.|  
|12290|DTS_MSG_PACKAGECANCEL|Le package « %1!s! » a été annulé.|Le package ne s'exécute plus parce qu'il a été annulé.|  
|12291|DTS_MSG_PACKAGEFAILURE|Échec du package «  ».|Le package n'a pas pu s'exécuter avec succès et son exécution s'est arrêtée.|  
  
 Par défaut, dans une nouvelle installation, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est configuré de façon à ne pas journaliser certains événements en rapport avec l'exécution de packages dans le journal des événements des applications. Ce paramètre limite le nombre d’entrées de journal des événements lorsque vous utilisez la fonctionnalité du collecteur de données de la version actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Les événements qui ne sont pas enregistrés incluent l'ID d'événement 12288, « le Package a démarré », et l'ID d'événement 12289, « le Package a fini avec succès ». Pour enregistrer ces événements dans le journal des événements des applications, ouvrez le Registre pour y apporter des modifications. Dans le Registre, recherchez le nœud HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\SSIS et modifiez la valeur DWORD du paramètre LogPackageExecutionToEventLog en remplaçant 0 par 1. Toutefois, dans une installation de mise à niveau, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est configuré pour enregistrer ces deux événements. Pour désactiver l'enregistrement, modifiez la valeur du paramètre LogPackageExecutionToEventLog en remplaçant 1 par 0.  
  
## <a name="messages-associated-with-package-logging"></a>Messages associés à la journalisation des packages  
 Si vous avez activé l’enregistrement sur le package, le journal des événements des applications représente l’une des destinations prises en charge par les fonctionnalités d’enregistrement facultatives dans les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Pour plus d’informations, consultez [Journalisation Integration Services &#40;SSIS&#41;](integration-services-ssis-logging.md).  
  
 Lorsque vous avez activé l'enregistrement sur le package et que l'emplacement du journal correspond au journal des événements des applications, le package enregistre les entrées en rapport aux informations suivantes :  
  
-   Messages sur la phase dans laquelle le package se trouve au cours de son exécution.  
  
-   Messages sur les événements particuliers qui se produisent alors que le package s'exécute.  
  
### <a name="messages-about-the-stages-of-package-execution"></a>Messages sur les phases d'exécution du package  
  
|ID d'événement|Nom symbolique|Text|Remarques|  
|--------------|-------------------|----------|-----------|  
|12544|DTS_MSG_EVENTLOGENTRY|Nom d'événement : %1%r Message : %9%r Opérateur : %2%r Nom de la source : %3%r ID de la source : %4%r ID d'exécution : %5%r Heure de début : %6%r Heure de fin : %7%r Code de données : %8|Lorsque vous configurez la journalisation du package dans le journal des événements des applications, différents messages utilisent ce format générique.|  
|12556|DTS_MSG_EVENTLOGENTRY_PACKAGESTART|Nom d'événement : %1%r Message : %9%r Opérateur : %2%r Nom de la source : %3%r ID de la source : %4%r ID d'exécution : %5%r Heure de début : %6%r Heure de fin : %7%r Code de données : %8|Le package a démarré.|  
|12547|DTS_MSG_EVENTLOGENTRY_PREVALIDATE|Nom d'événement : %1%r Message : %9%r Opérateur : %2%r Nom de la source : %3%r ID de la source : %4%r ID d'exécution : %5%r Heure de début : %6%r Heure de fin : %7%r Code de données : %8|La validation de l'objet est sur le point de commencer.|  
|12548|DTS_MSG_EVENTLOGENTRY_POSTVALIDATE|Nom d'événement : %1%r Message : %9%r Opérateur : %2%r Nom de la source : %3%r ID de la source : %4%r ID d'exécution : %5%r Heure de début : %6%r Heure de fin : %7%r Code de données : %8|La validation de l'objet est terminée.|  
|12552|DTS_MSG_EVENTLOGENTRY_PROGRESS|Nom d'événement : %1%r Message : %9%r Opérateur : %2%r Nom de la source : %3%r ID de la source : %4%r ID d'exécution : %5%r Heure de début : %6%r Heure de fin : %7%r Code de données : %8|Ce message générique signale la progression du package.|  
|12546|DTS_MSG_EVENTLOGENTRY_POSTEXECUTE|Nom d'événement : %1%r Message : %9%r Opérateur : %2%r Nom de la source : %3%r ID de la source : %4%r ID d'exécution : %5%r Heure de début : %6%r Heure de fin : %7%r Code de données : %8|L'objet a fini son travail.|  
|12557|DTS_MSG_EVENTLOGENTRY_PACKAGEEND|Nom d'événement : %1%r Message : %9%r Opérateur : %2%r Nom de la source : %3%r ID de la source : %4%r ID d'exécution : %5%r Heure de début : %6%r Heure de fin : %7%r Code de données : %8|L'exécution du package est terminée.|  
  
### <a name="messages-about-events-that-occur"></a>Messages relatifs aux événements qui se produisent  
 Le tableau ci-dessous répertorie seulement certains des messages générés par des événements. Pour obtenir une liste plus complète des messages d’erreur, d’avertissement et d’informations utilisés par [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [Guide de référence des erreurs et des messages propres à Integration Services](../integration-services-error-and-message-reference.md).  
  
|ID d'événement|Nom symbolique|Text|Remarques|  
|--------------|-------------------|----------|-----------|  
|12251|DTS_MSG_EVENTLOGENTRY_TASKFAILED|Nom d'événement : %1%r Message : %9%r Opérateur : %2%r Nom de la source : %3%r ID de la source : %4%r ID d'exécution : %5%r Heure de début : %6%r Heure de fin : %7%r Code de données : %8|La tâche a échoué.|  
|12250|DTS_MSG_EVENTLOGENTRY_ERROR|Nom d'événement : %1%r Message : %9%r Opérateur : %2%r Nom de la source : %3%r ID de la source : %4%r ID d'exécution : %5%r Heure de début : %6%r Heure de fin : %7%r Code de données : %8|Ce message signale une erreur qui s'est produite.|  
|12249|DTS_MSG_EVENTLOGENTRY_WARNING|Nom d'événement : %1%r Message : %9%r Opérateur : %2%r Nom de la source : %3%r ID de la source : %4%r ID d'exécution : %5%r Heure de début : %6%r Heure de fin : %7%r Code de données : %8|Ce message signale un avertissement qui s'est produit.|  
|12258|DTS_MSG_EVENTLOGENTRY_INFORMATION|Nom d'événement : %1%r Message : %9%r Opérateur : %2%r Nom de la source : %3%r ID de la source : %4%r ID d'exécution : %5%r Heure de début : %6%r Heure de fin : %7%r Code de données : %8|Ce message signale des informations qui ne sont pas associées à une erreur ou à un avertissement.|  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur l’affichage des entrées de journal en temps réel, consultez [Afficher les entrées de journal dans la fenêtre Journaux d’événements](../view-log-entries-in-the-log-events-window.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Événements consignés par le service Integration Services](../service/events-logged-by-the-integration-services-service.md)  
  
  
