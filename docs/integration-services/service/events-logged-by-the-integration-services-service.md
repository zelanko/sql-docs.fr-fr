---
title: "&#201;v&#233;nements consign&#233;s par le service Integration Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "service [Integration Services], événements"
  - "événements [Integration Services], service"
  - "service Integration Services, événements"
ms.assetid: d4122dcf-f16f-47a0-93a2-ffa3d0d4f9cf
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 19
---
# &#201;v&#233;nements consign&#233;s par le service Integration Services
  Le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] consigne différents messages dans le journal des événements des applications Windows. Le service enregistre ces messages lorsque le service démarre, lorsqu'il s'arrête et lorsque certains problèmes se produisent.  
  
 Cette rubrique fournit des informations sur les messages d'événements courants que le service enregistre dans le journal des événements des applications. Le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] consigne tous les messages décrits dans cette rubrique avec SQLISService comme source d’événement.  
  
 Pour des informations générales sur le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [Service Integration Services &#40;Service SSIS&#41;](../../integration-services/service/integration-services-service-ssis-service.md).  
  
## Messages relatifs à l'état du service  
 Quand vous sélectionnez [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour l’installation, le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est installé et démarré, et son type de démarrage est défini sur Automatique.  
  
|ID d'événement|Nom symbolique|Texte|Remarques|  
|--------------|-------------------|----------|-----------|  
|256|DTS_MSG_SERVER_STARTING|Démarrage du service [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)].|Le service est sur le point de démarrer.|  
|257|DTS_MSG_SERVER_STARTED|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] Service   démarré.|Le service a démarré.|  
|260|DTS_MSG_SERVER_START_FAILED|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] Échec du démarrage du service.%nErreur : %1|Le service n'a pas pu démarrer. Cette inaptitude à démarrer peut résulter d'une installation endommagée ou d'un compte de service inapproprié.|  
|258|DTS_MSG_SERVER_STOPPING|Arrêt du service [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)].% n%nArrêtez tous les packages en cours d'exécution à la fin de l'opération : %1|Le service est en cours d'arrêt et si vous configurez le service pour cela, tous les packages en cours d'exécution seront arrêtés. Vous pouvez définir une valeur vraie ou fausse dans le fichier de configuration qui détermine si le service doit cesser d'exécuter des packages lorsque le service lui-même s'arrête. Le message pour cet événement inclut la valeur de ce paramètre.|  
|259|DTS_MSG_SERVER_STOPPED|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] Service arrêté.%nVersion du serveur %1|Le service s'est arrêté.|  
  
## Messages relatifs au fichier de configuration  
 Les paramètres pour le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sont stockés dans un fichier XML que vous pouvez modifier. Pour plus d’informations, consultez [Configuration du service Integration Services &#40;Service SSIS&#41;](../../integration-services/service/configuring-the-integration-services-service-ssis-service.md).  
  
|ID d'événement|Nom symbolique|Texte|Remarques|  
|--------------|-------------------|----------|-----------|  
|274|DTS_MSG_SERVER_MISSING_CONFIG_REG|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] Service : %nparamètre de Registre spécifiant que le fichier de configuration n’existe pas. %nTentative de chargement du fichier de configuration par défaut en cours.|L'entrée du Registre qui contient le chemin d'accès du fichier de configuration n'existe pas ou est vide.|  
|272|DTS_MSG_SERVER_MISSING_CONFIG|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] Le fichier de configuration du service n’existe pas.%nChargement avec les paramètres par défaut.|Le fichier de configuration lui-même n'existe pas à l'emplacement spécifié.|  
|273|DTS_MSG_SERVER_BAD_CONFIG|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] Le fichier de configuration du service est incorrect.%nErreur lors de la lecture du fichier de configuration : %1%n%nChargement du serveur avec les paramètres par défaut.|Le fichier de configuration n'a pas pu être lu ou n'est pas valide. Cette erreur peut résulter d'une erreur de syntaxe XML dans le fichier.|  
  
## Autres messages  
  
|ID d'événement|Nom symbolique|Texte|Remarques|  
|--------------|-------------------|----------|-----------|  
|336|DTS_MSG_SERVER_STOPPING_PACKAGE|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] Service : arrêt de l’exécution du package.%nID d’instance du package : %1%nID du package : %2%nNom : %3%nDescription : %4%nPackage|Le service essaie d'arrêter un package en cours d'exécution. Vous pouvez analyser et arrêter des packages en cours d'exécution dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Pour plus d’informations sur la gestion des packages dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], consultez [Gestion de packages &#40;Service SSIS&#41;](../../integration-services/service/package-management-ssis-service.md).|  
  
## Tâches associées  
 Pour plus d’informations sur l’affichage des entrées de journal, consultez [Afficher les entrées de journal dans la fenêtre Journaux d’événements](../../integration-services/performance/view-log-entries-in-the-log-events-window.md)  
  
## Voir aussi  
 [Événements journalisés par un package Integration Services](../../integration-services/performance/events-logged-by-an-integration-services-package.md)  
  
  