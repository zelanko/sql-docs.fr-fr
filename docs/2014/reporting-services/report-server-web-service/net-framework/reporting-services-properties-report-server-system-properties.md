---
title: Propriétés système du serveur de rapports | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- report servers [Reporting Services], properties
- system-specific properties [Reporting Services]
ms.assetid: cd874117-00e5-4ae6-8629-eb9ba9f40478
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c0cd5fd82a77d85b59de9fb4ebedebfd560c759f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48211341"
---
# <a name="report-server-system-properties"></a>Propriétés système de Report Server
  Les noms de propriétés système suivants sont réservés. Vous ne pouvez pas créer des propriétés définies par l'utilisateur du même nom. Vous pouvez lire ou modifier nombre de ces propriétés à l'aide des méthodes de service Web.  
  
## <a name="properties"></a>Properties  
  
|Propriété|Description|  
|--------------|-----------------|  
|SiteName|Nom du site du serveur de rapports affiché sur l'interface utilisateur. La valeur par défaut est `Microsoft Report Server`. Cette propriété peut être une chaîne vide. La longueur maximale autorisée s’élève à 8 000 caractères.|  
|SystemSnapshotLimit|Nombre maximal d'instantanés stockées pour un rapport. Les valeurs valides sont `-1` via `2`,`147`,`483`,`647`. Si la valeur est `-1`, il n’existe aucune limite de capture instantanée.|  
|SystemReportTimeout|Valeur (en secondes) du délai d'exécution du traitement du rapport par défaut pour tous les rapports gérés dans l'espace de noms du serveur de rapports. Cette valeur peut être remplacée au niveau du rapport. Si cette propriété est définie, le serveur de rapports essaie d'arrêter le traitement d'un rapport lorsque le délai spécifié est expiré. Les valeurs valides sont `-1` via `2`,`147`,`483`,`647`. Si la valeur est égale à `-1`, les rapports de l'espace de noms ne spécifient pas de délai d'exécution pendant le traitement. La valeur par défaut est `1800`.|  
|UseSessionCookies|Indique si le serveur de rapports doit utiliser les cookies de session lors la communication avec les navigateurs clients. La valeur par défaut est `true`.|  
|SessionTimeout|Durée (en secondes) pendant laquelle une session demeure active. La valeur par défaut est `600`.|  
|EnableMyReports|Indique si la fonctionnalité Mes rapports est activée. La valeur `true` indique que la fonctionnalité est activée.|  
|MyReportsRole|Nom du rôle utilisé lors de la création des stratégies de sécurité sur le dossier Mes rapports de l'utilisateur. La valeur par défaut est `My Reports Role`.|  
|EnableExecutionLogging|Indique si la journalisation de l'exécution des rapports est activée. La valeur par défaut est `true`.|  
|ExecutionLogDaysKept|Nombre de jours pendant lesquels conserver les informations sur l'exécution du rapport dans le journal des exécutions. Valeurs valides pour cette propriété sont `0` via `2`,`147`,`483`,`647`. Si la valeur est égale à `0`, les entrées ne sont pas supprimées de la table du journal des exécutions. La valeur par défaut est `60`.|  
|SnapshotCompression|Définit le mode de compression des instantanés. La valeur par défaut est `SQL`. Les valeurs valides sont les suivantes :<br /><br /> `SQL` = les instantanés sont compressés lorsqu'ils sont stockés dans la base de données du serveur de rapports. Il s'agit du comportement actuel.<br /><br /> **None** = les instantanés ne sont pas compressés.<br /><br /> `All` = les instantanés sont compressés pour toutes les options de stockage, qui incluent la base de données du serveur de rapports ou le système de fichiers.|  
|EnableClientPrinting|Détermine si le contrôle ActiveX RSClientPrint peut être téléchargé à partir du serveur de rapports. Les valeurs valides sont `true` et `false`. La valeur par défaut est `true`. Pour plus d’informations sur les paramètres supplémentaires nécessaires pour ce contrôle, consultez [Activer et désactiver l’impression côté client pour Reporting Services](../../report-server/enable-and-disable-client-side-printing-for-reporting-services.md).|  
|EnableIntegratedSecurity|Détermine si la sécurité intégrée est prise en charge pour les connexions à la source de données de rapports. La valeur par défaut est `True`. Les valeurs valides sont les suivantes :<br /><br /> `True` = la sécurité intégrée est activée.<br /><br /> `False` = la sécurité intégrée n'est pas activée. Les sources de données de rapports qui sont configurées de manière à utiliser la sécurité intégrée ne seront pas exécutées.|  
|EnableRemoteErrors|Inclut les informations externes sur l'erreur (par exemple, les informations d'erreur relatives aux sources de données de rapport) avec les messages d'erreur retournés pour les utilisateurs qui demandent des rapports à partir d'ordinateurs distants. Les valeurs valides sont `true` et `false`. La valeur par défaut est `false`. Pour plus d’informations, consultez [Activer les erreurs distantes &#40;Reporting Services&#41;](../../report-server/enable-remote-errors-reporting-services.md).|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>   
 <xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>   
 [Création d’applications à l’aide du service web et du .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)   
 [Service web Report Server](../report-server-web-service.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../technical-reference-ssrs.md)  
  
  
