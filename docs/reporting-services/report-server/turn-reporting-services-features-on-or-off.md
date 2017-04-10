---
title: "Activer ou d&#233;sactiver les fonctionnalit&#233;s Reporting Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Reporting Services, configuration"
  - "sécurité [Reporting Services], stratégies"
ms.assetid: b69db02a-43a7-4fdc-ad9b-438d817a7f83
caps.latest.revision: 10
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 9
---
# Activer ou d&#233;sactiver les fonctionnalit&#233;s Reporting Services
  Vous pouvez désactiver les fonctionnalités de serveur de rapports que vous n'utilisez pas dans le cadre d'une stratégie de verrouillage pour réduire l'exposition aux attaques d'un serveur de rapports de production. Dans la plupart des cas, vous préférerez exécuter les fonctionnalités de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] conjointement afin de bénéficier de toutes les fonctionnalités offertes dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Toutefois, vous pouvez désactiver les fonctionnalités dont vous n'avez pas besoin, selon votre modèle de déploiement. Par exemple, vous pouvez activer le traitement en arrière-plan uniquement si le traitement de tous les rapports a été planifié. De même, vous pouvez exécuter simplement le service Web Report Server si vous souhaitez disposer uniquement de rapports interactifs à la demande.  
  
 Les procédures passées en revue dans cette rubrique vous indiquent comment désactiver les fonctionnalités [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif. Les fonctionnalités peuvent être configurées de différentes façons, par exemple en modifiant directement le fichier `RsReportServer.config` ou en utilisant la facette **Configuration de la surface d’exposition pour Reporting Services** de la gestion basée sur des stratégies dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Utilisez les liens pour localiser les procédures qui expliquent comment activer ou désactiver une fonctionnalité :  
  
-   [service Web Report Server](#RSWebSvc)  
  
-   [Traitement et événements planifiés](#Sched)  
  
-   [Gestionnaire de rapports](#ReportManager)  
  
-   [Générateur de rapports](#ReportBuilder)  
  
-   [Sécurité intégrée de Windows pour les sources de données de rapports](#WinIntSec)  
  
##  <a name="RSWebSvc"></a> service Web Report Server  
  
#### Pour activer le service Web Report Server en modifiant la configuration  
  
1.  Ouvrez le fichier `RsReportServer.config` dans un éditeur de texte. Pour plus d’informations, consultez [Modifier un fichier de configuration Reporting Services &#40;RSreportserver.config&#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Pour activer le service Web Report Server, affectez à **IsWebServiceEnabled** la valeur **true**:  
  
    ```  
    <IsWebServiceEnabled>true</IsWebServiceEnabled>  
    ```  
  
3.  Pour désactiver le service Web Report Server, affectez à **IsWebServiceEnabled** la valeur **false**:  
  
    ```  
    <IsWebServiceEnabled>false</IsWebServiceEnabled>  
    ```  
  
4.  Enregistrez vos modifications et fermez le fichier.  
  
#### Pour activer ou désactiver le service Web Report Server en utilisant SQL Server Management Studio  
  
1.  Ouvrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , puis connectez-vous à l'instance [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à configurer.  
  
2.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur le nœud [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], pointez sur **Stratégies**, puis cliquez sur **Facettes**.  
  
3.  Dans la liste **Facette** , sélectionnez **Configuration de la surface d'exposition pour Reporting Services**.  
  
4.  Sous **Propriétés de la facette**:  
  
    -   Pour activer le service Web Report Server, affectez à **WebServiceAndHTTPAccessEnabled** la valeur **True**.  
  
    -   Pour désactiver le service Web Report Server, affectez à **WebServiceAndHTTPAccessEnabled** la valeur **False**.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="Sched"></a> Événements planifiés et remise  
  
#### Pour activer ou désactiver les événements planifiés et la remise en modifiant la configuration  
  
1.  Ouvrez le fichier RsReportServer.config dans un éditeur de texte. Pour plus d’informations, consultez [Modifier un fichier de configuration Reporting Services &#40;RSreportserver.config&#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Pour activer le traitement et la remise des rapports planifiés, affectez à **IsSchedulingService**, **IsNotificationService**et **IsEventService** la valeur **true**:  
  
    ```  
    <IsSchedulingService>true</IsSchedulingService>  
    <IsNotificationService>true</IsNotificationService>  
    <IsEventService>true</IsEventService>  
    ```  
  
3.  Pour désactiver le traitement et la remise des rapports planifiés, affectez la à **IsSchedulingService**, **IsNotificationService**et **IsEventService** la valeur **false**:  
  
    ```  
    <IsSchedulingService>false</IsSchedulingService>  
    <IsNotificationService>false</IsNotificationService>  
    <IsEventService>false</IsEventService>  
    ```  
  
4.  Enregistrez vos modifications et fermez le fichier.  
  
> [!NOTE]  
>  Vous ne pouvez pas désactiver complètement le traitement en arrière-plan car il fournit des fonctionnalités de maintenance de base de données requises pour les opérations de serveur.  
  
#### Pour activer ou désactiver les événements planifiés et leur remise en utilisant SQL Server Management Studio  
  
1.  Ouvrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , puis connectez-vous à l'instance [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à configurer.  
  
2.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur le nœud [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], pointez sur **Stratégies**, puis cliquez sur **Facettes**.  
  
3.  Dans la liste **Facette** , sélectionnez **Configuration de la surface d'exposition pour Reporting Services**.  
  
4.  Sous **Propriétés de la facette**:  
  
    -   Pour activer les événements planifiés et leur remise, affectez à **ScheduleEventsAndReportDeliveryEnabled** la valeur **True**.  
  
    -   Pour désactiver les événements planifiés et leur remise, affectez à **ScheduleEventsAndReportDeliveryEnabled** la valeur **False**.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  Vous ne pouvez pas désactiver complètement le traitement en arrière-plan car il fournit des fonctionnalités de maintenance de base de données requises pour les opérations de serveur.  
  
##  <a name="ReportManager"></a> Gestionnaire de rapports  
  
#### Pour activer ou désactiver le Gestionnaire de rapports en modifiant la configuration  
  
1.  Ouvrez le fichier RsReportServer.config dans un éditeur de texte. Pour obtenir des instructions, consultez [Modifier un fichier de configuration Reporting Services &#40;RSreportserver.config&#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Pour activer le Gestionnaire de rapports, affectez à **IsReportManagerEnabled** la valeur **true**:  
  
    ```  
    <IsReportManagerEnabled>true</IsReportManagerEnabled>  
    ```  
  
3.  Pour désactiver le Gestionnaire de rapports, affectez à **IsReportManagerEnabled** la valeur **false**:  
  
    ```  
    <IsReportManagerEnabled>false</IsReportManagerEnabled>  
    ```  
  
4.  Enregistrez vos modifications et fermez le fichier.  
  
#### Pour activer ou désactiver le Gestionnaire de rapports en utilisant SQL Server Management Studio  
  
1.  Ouvrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , puis connectez-vous à l'instance [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à configurer.  
  
2.  Dans **l’Explorateur d’objets**, cliquez avec le bouton droit sur le nœud [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], pointez sur **Stratégies**, puis cliquez sur **Facettes**.  
  
3.  Dans la liste **Facette** , sélectionnez **Configuration de la surface d'exposition pour Reporting Services**.  
  
4.  Sous **Propriétés de la facette**:  
  
    -   Pour activer le Gestionnaire de rapports, affectez à **ReportManagerEnabled** la valeur **True**.  
  
    -   Pour désactiver le Gestionnaire de rapports, affectez à **ReportManagerEnabled** la valeur **False**.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="ReportBuilder"></a> Générateur de rapports  
  
#### Pour activer ou désactiver le Générateur de rapports en utilisant SQL Server Management Studio  
  
1.  Ouvrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , puis connectez-vous à l'instance [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à configurer.  
  
2.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur le nœud [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], puis cliquez sur **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés du serveur** , sous **Sélectionner une page**, cliquez sur **Sécurité**.  
  
    -   Pour activer le Générateur de rapports, sélectionnez l'option **Activer les exécutions de rapports ad hoc** .  
  
    -   Pour désactiver le Générateur de rapports, désélectionnez l'option **Activer les exécutions de rapports ad hoc** .  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="WinIntSec"></a> Sécurité intégrée de Windows  
  
#### Pour activer ou désactiver la sécurité intégrée de Windows en utilisant SQL Server Management Studio  
  
1.  Ouvrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , puis connectez-vous à l'instance [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à configurer.  
  
2.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur le nœud [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], puis cliquez sur **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés du serveur** , sous **Sélectionner une page**, cliquez sur **Sécurité**.  
  
    -   Pour activer la sécurité intégrée de Windows, sélectionnez l'option **Activer la sécurité intégrée Windows pour les sources de données de rapport** .  
  
    -   Pour désactiver la sécurité intégrée de Windows, désélectionnez l'option **Activer la sécurité intégrée Windows pour les sources de données de rapport** .  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## Voir aussi  
 [Gestionnaire de configurations de Reporting Services (SSRS en mode natif)](http://msdn.microsoft.com/fr-fr/63519ef4-e68a-42fb-9cf7-31228ea4e434)  
  
  