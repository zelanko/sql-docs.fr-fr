---
title: "Erreurs et événements référence (Reporting Services) | Documents Microsoft"
ms.custom: 
ms.date: 03/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages [Reporting Services]
- errors [Reporting Services]
- Reporting Services, errors and events
- troubleshooting [Reporting Services], errors
- events [Reporting Services]
ms.assetid: 818b4cc1-e65d-4f1a-bf7d-fe269e6dd739
caps.latest.revision: 42
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a0738c8ac950a86ef877c26fd8b6a0f6a6b075f2
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="errors-and-events-reference-reporting-services"></a>Guide de référence des erreurs et des événements (Reporting Services)
  Cette rubrique fournit des informations sur les erreurs et les événements pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Les fichiers journaux [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] contiennent également des informations sur les erreurs. Pour plus d’informations sur les types de fichiers journaux disponibles et la manière de les afficher, consultez [Fichiers journaux et sources de Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md).  
  
## <a name="cause-and-resolution-for-reporting-services-error-messages"></a>Cause et solution des messages d'erreur de Reporting Services  
 Les sites Web de [!INCLUDE[msCoName](../../includes/msconame-md.md)] contiennent des informations sur les causes des erreurs rencontrées le plus fréquemment, ainsi que les solutions correspondantes. Pour plus d’informations, consultez [Cause and Resolution of Reporting Services Errors](../../reporting-services/troubleshooting/cause-and-resolution-of-reporting-services-errors.md).  
  
## <a name="report-server-events"></a>Événements du serveur de rapports  
 Les événements suivants du serveur de rapports sont consignés dans le journal des applications [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
|ID d'événement|Type|Catégorie|Source|Description|  
|--------------|----------|--------------|------------|-----------------|  
|106|Erreur|Planification|Serveur de rapports|L'Agent SQL Server doit être en cours d'exécution lorsque vous définissez une opération de planification (par exemple, un abonnement à un rapport et une remise).|  
|[107](../../reporting-services/troubleshooting/report-server-windows-service-mssqlserver-107.md)|Erreur|Démarrage/Fermeture|Serveur de rapports<br /><br /> Processeur de planification et de remise|*\<Source >* ne peut pas se connecter à la base de données du serveur de rapports. Pour plus d’informations, consultez [Service Report Server Windows &#40;MSSQLServer&#41; 107](../../reporting-services/troubleshooting/report-server-windows-service-mssqlserver-107.md).|  
|108|Erreur|Extension|Serveur de rapports<br /><br /> Gestionnaire de rapports|*\<Source >* ne peut pas charger de remise, le traitement des données ou extension de rendu.<br /><br /> Ce problème est vraisemblablement dû à un déploiement incomplet ou à la suppression d'une extension. Pour plus d'informations, consultez [Deploying a Data Processing Extension](../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md) et [Deploying a Delivery Extension](../../reporting-services/extensions/delivery-extension/deploying-a-delivery-extension.md).|  
|109|Informations|Gestion|Serveur de rapports<br /><br /> Gestionnaire de rapports|Un fichier de configuration a été modifié. Pour plus d’informations, consultez [Reporting Services Configuration Files](../../reporting-services/report-server/reporting-services-configuration-files.md).|  
|110|Avertissement|Gestion|Serveur de rapports<br /><br /> Gestionnaire de rapports|Un paramètre a été modifié dans l'un des fichiers de configuration et n'est donc plus valide. La valeur par défaut sera utilisée à la place. Pour plus d’informations, consultez [Reporting Services Configuration Files](../../reporting-services/report-server/reporting-services-configuration-files.md).|  
|111|Erreur|Journalisation|Serveur de rapports<br /><br /> Gestionnaire de rapports|*\<Source >* ne peut pas créer le journal des traces. Pour plus d’informations, consultez [Report Server Service Trace Log](../../reporting-services/report-server/report-server-service-trace-log.md).|  
|112|Avertissement|Sécurité|Serveur de rapports|Le serveur de rapports a détecté une possible attaque par déni de service. Pour plus d’informations, consultez [Sécurité et protection de Reporting Services](../../reporting-services/security/reporting-services-security-and-protection.md).|  
|113|Erreur|Journalisation|Serveur de rapports|Le serveur de rapports ne peut pas créer le compteur de performance.|  
|114|Erreur|Démarrage/Fermeture|Gestionnaire de rapports|Le Gestionnaire de rapports ne peut pas se connecter au service Report Server.|  
|115|Avertissement|Planification|Processeur de planification et de remise|Une tâche planifiée dans la file d'attente de l'Agent SQL Server a été modifiée ou supprimée.|  
|116|Erreur|Interne|Serveur de rapports<br /><br /> Gestionnaire de rapports<br /><br /> Processeur de planification et de remise|Une erreur interne s'est produite.|  
|117|Erreur|Démarrage/Fermeture|Serveur de rapports|La version de la base de données du serveur de rapports n'est pas valide.|  
|118|Avertissement|Journalisation|Serveur de rapports<br /><br /> Gestionnaire de rapports|Le journal des traces ne se trouve pas à l'emplacement attendu. Un nouveau journal des traces sera créé dans le répertoire par défaut. Pour plus d’informations, consultez [Report Server Service Trace Log](../../reporting-services/report-server/report-server-service-trace-log.md).|  
|119|Erreur|Activation|Serveur de rapports<br /><br /> Processeur de planification et de remise|*\<Source >* n’a pas reçu d’accéder au contenu de la base de données du serveur de rapports.|  
|120|Erreur|Activation|Serveur de rapports|Impossible de déchiffrer la clé symétrique. Le compte sous lequel le service est exécuté a vraisemblablement été modifié. Pour plus d’informations, consultez [configurer et gérer les clés de chiffrement &#40; Gestionnaire de Configuration de SSRS &#41; ](../../reporting-services/install-windows/ssrs-encryption-keys-manage-encryption-keys.md).|  
|121|Erreur|Démarrage/Fermeture|Serveur de rapports|Échec de démarrage du service d'appel de procédure distante (RPC).|  
|122|Avertissement|Remise|Processeur de planification et de remise|Le processeur de planification et de remise ne peut pas se connecter au serveur SMTP qui est utilisé pour la remise du courrier électronique. Pour plus d’informations sur les connexions au serveur SMTP, consultez [Configurer un serveur de rapports pour la remise par messagerie (Gestionnaire de configuration de SSRS)](http://msdn.microsoft.com/en-us/b838f970-d11a-4239-b164-8d11f4581d83).|  
|123|Avertissement|Journalisation|Serveur de rapports<br /><br /> Gestionnaire de rapports|Le serveur de rapports n'a pas réussi à écrire dans le journal des traces. Pour plus d’informations sur les journaux des traces, consultez [Journal des traces du service Report Server](../../reporting-services/report-server/report-server-service-trace-log.md).|  
|124|Informations|Activation|Serveur de rapports|Le service Report Server est initialisé. Pour plus d’informations, consultez [initialiser un serveur de rapports &#40; Gestionnaire de Configuration de SSRS &#41; ](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md).|  
|125|Informations|Activation|Serveur de rapports|Extraction réussie de la clé utilisée pour chiffrer les données. Pour plus d’informations sur les clés, consultez [configurer et gérer les clés de chiffrement &#40; Gestionnaire de Configuration de SSRS &#41; ](../../reporting-services/install-windows/ssrs-encryption-keys-manage-encryption-keys.md).|  
|126|Informations|Activation|Serveur de rapports|Application réussie de la clé utilisée pour chiffrer les données. Pour plus d’informations sur les clés, consultez [configurer et gérer les clés de chiffrement &#40; Gestionnaire de Configuration de SSRS &#41; ](../../reporting-services/install-windows/ssrs-encryption-keys-manage-encryption-keys.md).|  
|127|Informations|Activation|Serveur de rapports|Suppression réussie du contenu chiffré dans la base de données du serveur de rapports. Pour plus d’informations sur la suppression des données chiffrées non récupérable, consultez [configurer et gérer les clés de chiffrement &#40; Gestionnaire de Configuration de SSRS &#41; ](../../reporting-services/install-windows/ssrs-encryption-keys-manage-encryption-keys.md).|  
|128|Erreur|Activation|Serveur de rapports|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de différentes éditions ne fonctionnent pas ensemble.|  
|129|Erreur|Gestion|Serveur de rapports<br /><br /> Processeur de planification et de remise|Impossible de déchiffrer un paramètre chiffré d'un fichier de configuration.|  
|130|Erreur|Gestion|Serveur de rapports<br /><br /> Processeur de planification et de remise|*\<Source >* ne peut pas trouver le fichier de configuration. Des fichiers de configuration sont nécessaires pour le serveur de rapports.|  
|131|Erreur|Sécurité|Serveur de rapports<br /><br /> Processeur de planification et de remise|Une valeur de données utilisateur chiffrée n'a pas pu être déchiffrée.|  
|132|Erreur|Sécurité|Serveur de rapports|Une erreur s'est produite au cours du chiffrement des données utilisateur. La valeur ne peut pas être enregistrée.|  
|133|Erreur|Gestion|Serveur de rapports<br /><br /> Gestionnaire de rapports<br /><br /> Processeur de planification et de remise|Échec de chargement du fichier de configuration. Cette erreur peut se produire si le fichier XML n'est pas valide.|  
|134|Erreur|Gestion|Serveur de rapports|Le serveur de rapports n'a pas réussi à chiffrer les valeurs d'un paramètre dans le fichier de configuration.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser les abonnements Reportions Services](../../reporting-services/subscriptions/monitor-reporting-services-subscriptions.md)   
 [Fichiers journaux et sources de Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)  
  
  
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]

