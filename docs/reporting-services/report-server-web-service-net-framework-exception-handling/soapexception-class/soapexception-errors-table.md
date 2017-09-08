---
title: "Table d’erreurs SoapException | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- SoapException class
ms.assetid: 3dbf1b5a-bd2a-4385-925d-5d095d72014c
caps.latest.revision: 32
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: bce2a94413b1aa40c3c935da4ed8c8d70814028c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/12/2017

---
# <a name="soapexception-errors-table"></a>Table d'erreurs SoapException
  Le serveur de rapports génère des erreurs et des messages d'erreur dans l'exception SOAP en fonction des erreurs qui se produisent dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Le tableau suivant indique les erreurs qui sont accessibles à partir des méthodes via un **SoapException** dans le service Web Report Server. Il est organisé en fonction de la méthode ou des méthodes qui lèvent l'exception.  
  
|Méthode(s)|Code d'erreur|  
|-----------------|----------------|  
|**ALL**|**rsEvaluationCopyExpired**|  
|**ALL**|**rsFailedToDecryptConfigInformation**|  
|**ALL**|**rsInvalidRSEditionConfiguration**|  
|**ALL**|**rsReportServerNotActivated**|  
|**ALL**|**rsServerBusy**|  
|**ALL**|**rsReportServerServiceUnavailable**|  
|**ALL**|**rsReportServerDisabled**|  
|**Tous les** sauf **GetPermissions**, **GetRenderResource**, **GetSystemPermissions**, **ListEvents**, et **ListSecureMethods**|**rsAccessDenied**|  
|**Tous les** sauf **CreateBatch**, **ExecuteBatch**, **GetSystemPolicies**, **GetSystemPermissions**, **GetSystemProperties**, **ListEvents**, **ListJobs**, **ListRoles**, **ListSchedules**, **ListSecureMethods**, **ListSubscriptions**, **ListSystemRoles**, **ListSystemTasks**, **ListTasks**|**rsMissingParameter**|  
|**CreateDataDrivenSubscription**, **CreateDataSource**, **CreateFolder**, **CreateLinkedReport**, **CreateReport**, **CreateReportHistorySnapshot**, **CreateResource a**, **CreateSubscription**, **DeleteItem**, **DeleteReportHistorySnapshot**, **DisableDataSource**, **EnableDataSource**, **FindItems**, **FlushCache**, **GetCacheOptions**, **GetDataSourceContents** , **GetExecutionOptions**, **GetPermissions**, **GetPolicies**, **GetProperties**, **GetReportDataSourcePrompts**, **GetReportDataSources**, **GetReportDefinition**, **GetReportHistoryLimit**, **GetReportHistoryOptions**, **GetReportLink**, **GetReportParameters**, **GetResourceContents**, **GetRoleProperties**, **GetServerDateTime**,  **IheritParentSecurity**, **ListChildren**, **ListLinkedReports**, **ListReportHistory**, **ListReportsUsingDataSource**, **ListSchedules**, **ListSubscriptions**, **ListSubscriptionsUsingDataSource**, **MoveItem**, **restituer**, **RenderStream**, **SetCacheOptions**, **SetDataSourceContents**, **SetExecutionOptions**,  **SetPolicies**, **SetProperties**, **SetReportDataSources**, **SetReportDefinition**, **SetReportHistoryLimit**, **SetReportHistoryOptions**, **SetReportLink**, **SetReportParameters**, **SetResourceContents**, **UpdateReportExecutionSnapshot**, **ValidateExtensionSettings**|**rsItemNotFound**|  
|**CancelBatch**, **CreateDataDrivenSubscription**, **CreateDataSource**, **CreateFolder**, **CreateLinkedReport**, **CreateReport**, **CreateReportHistorySnapshot**, **CreateResource a**, **CreateRole**, **CreateSchedule**, **CreateSubscription**, **DeleteItem**, **DeleteReportHistorySnapshot**, **DeleteRole**, **DeleteSchedule**, **DeleteSubscription**,  **DisableDataSource**, **EnableDataSource**, **ExecuteBatch**, **FindItems**, **FlushCache**, **GetResourceContents**, **GetServerDateTime**, **MoveItem**, **PauseSchedule**, **ResumeSchedule**, **SetCacheOptions**, **SetDataDrivenSubscriptionProperties**, **SetDataSourceContents**, **SetExecutionOptions**, **SetPolicies**,  **SetProperties**, **SetReportDataSources**, **SetReportDefinition**, **SetReportHistoryLimit**, **SetReportHistoryOptions**, **SetReportLink**, **SetReportParameters**, **SetResourceContents**, **SetRoleProperties**, **SetScheduleProperties**, **SetSubscriptionProperties**, **SetSystemPolicies**, **SetSystemProperties**,  **UpdateReportExecutionSnapshot**, **ValidateExtensionSettings**|**rsBatchNotFound**|  
|**CreateDataDrivenSubscription**, **CreateDataSource**, **CreateFolder**, **CreateLinkedReport**, **CreateReport**, **CreateReportHistorySnapshot**, **CreateResource a**, **CreateSubscription**, **DeleteItem**, **DeleteReportHistorySnapshot**, **DisableDataSource**, **EnableDataSource**, **FindItems**, **FlushCache**, **GetCacheOptions**, **GetDataSourceContents** , **GetExecutionOptions**, **GetItemType**, **GetPermissions**, **GetPolicies**, **GetProperties**, **GetReportDataSourcePrompts**, **GetReportDataSources**, **GetReportDefinition**, **GetReportHistoryLimit**, **GetReportHistoryOptions**, **GetReportLink**, **GetResourceContents**, **GetServerDateTime**, **IheritParentSecurity**, **ListChildren** , **ListLinkedReports**, **ListReportHistory**, **ListSchedules**, **ListSubscriptionsUsingDataSource**, **MoveItem**, **restituer**, **RenderStream**, **SetCacheOptions**, **SetDataSourceContents**, **SetExecutionOptions**, **SetPolicies**, **SetProperties**, **SetReportDataSources**, **SetReportDefinition** , **SetReportHistoryLimit**, **SetReportHistoryOptions**, **SetReportLink**, **SetReportParameters**, **SetResourceContents**, **SetSubscriptionProperties**, **UpdateReportExecutionSnapshot**, **ValidateExtensionSettings**|**rsInvalidItemPath**|  
|**CreateDataDrivenSubscription**, **CreateDataSource**, **CreateFolder**, **CreateLinkedReport**, **CreateReport**, **CreateReportHistorySnapshot**, **CreateResource a**, **CreateSubscription**, **DeleteReportHistorySnapshot**, **DisableDataSource**, **EnableDataSource**, **FindItems**, **FlushCache**, **GetCacheOptions**, **GetDataSourceContents**, **GetExecutionOptions**, **GetReportDataSourcePrompts**, **GetReportDataSources**, **GetReportDefinition**, **GetReportHistoryLimit**, **GetReportHistoryOptions**, **GetReportLink**, **GetReportParameters**, **GetResourceContents**, **GetServerDateTime**, **GetSystemProperties**, **ListChildren**, **ListLinkedReports**, **ListReportHistory**, **ListReportsUsingDataSource** , **ListSchedules**, **ListSubscriptions**, **ListSubscriptionsUsingDataSource**, **MoveItem**, **restituer**, **RenderStream**, **SetCacheOptions**, **SetDataSourceContents**, **SetExecutionOptions**, **SetReportDataSources**, **SetReportDefinition**, **SetReportHistoryLimit**, **SetReportHistoryOptions**, **SetReportLink**, **SetReportParameters**, **SetResourceContents**, **UpdateReportExecutionSnapshot**, **ValidateExtensionSettings**|**rsWrongItemType**|  
|**CreateReport**, **CreateResource a**, **DeleteReportHistorySnapshot**, **DeleteSchedule**, **DeleteSubscription**, **GetDataDrivenSubscriptionProperties**, **GetSubscriptionProperties**, **ListChildren**, **ListScheduledReports**, **PauseSchedule**, **restituer**, **RenderStream**, **ResumeSchedule**, **SetCacheOptions**, **SetDataDrivenSubscriptionProperties**,  **SetReportHistoryLimit**, **SetReportHistoryOptions**, **SetScheduleProperties**, **SetSubscriptionProperties**|**rsParameterTypeMismatch**|  
|**CreateDataDrivenSubscription**, **CreateDataSource**, **CreateSchedule**, **CreateSubscription**, **FindItems**, **GetReportParameters**, **PrepareQuery**, **restituer**, **SetCacheOptions**, **SetDataDrivenSubscriptionProperties**, **SetDataSourceContents**, **SetPolicies**, **SetReportDataSources**, **SetReportParameters**, **SetScheduleProperties**,  **SetSubscriptionProperties**, **SetSystemPolicies**|**rsMissingElement**|  
|**CreateDataDrivenSubscription**, **CreateDataSource**, **CreateSchedule**, **CreateSubscription**, **PrepareQuery**, **restituer**, **SetCacheOptions**, **SetDataDrivenSubscriptionProperties**, **SetDataSourceContents**, **SetProperties**, **SetReportDataSources**, **SetReportParameters**, **SetScheduleProperties**, **SetSubscriptionProperties**, **SetSystemProperties**|**rsInvalidElement**|  
|**CreateDataDrivenSubscription**, **CreateSchedule**, **CreateSubscription**, **FindItems**, **GetRenderResource**, **PrepareQuery**, **restituer**, **RenderStream**, **SetCacheOptions**, **SetDataDrivenSubscriptionProperties**, **SetExecutionOptions**, **SetProperties**, **SetReportHistoryOptions**, **SetReportParameters**, **SetScheduleProperties**, **SetSubscriptionProperties** , **SetSystemProperties**|**rsElementTypeMismatch**|  
|**CreateDataSource**, **CreateRole**, **GetDataDrivenSubscriptionProperties**, **GetRenderResource**, **ListExtensions**, **restituer**, **SetDataDrivenSubscriptionProperties**, **SetDataSourceContents**, **SetExecutionOptions**, **SetReportHistoryLimit**, **SetReportHistoryOptions**, **SetScheduleProperties**|**rsInvalidParameter**|  
|**CreateDataDrivenSubscription**, **CreateReportHistorySnapshot**, **CreateSubscription**, **PrepareQuery**, **SetDataDrivenSubscriptionProperties**, **SetExecutionOptions**, **SetReportHistoryOptions**, **SetSubscriptionProperties**|**rsInvalidDataSourceCredentialSetting**|  
|**CreateDataDrivenSubscriptionProperties**, **CreateReportHistorySnapshot**, **CreateSchedule**, **CreateSubscription**, **SetDataDrivenSubscriptionProperties**, **SetSubscriptionProperties**, **UpdateReportExecutionSnapshot**|**rsReportParameterValueNotSet**|  
|**CreateDataDrivenSubscription**, **CreateSubscription**, **GetExtensionSettings**, **GetRenderResource**, **restituer**, **RenderStream**, **SetDataDrivenSubscriptionProperties**, **SetSubscriptionProperties**|**rsMultipleExtensionsFoundInAssembly**|  
|**CreateDataDrivenSubscriptionProperties**, **CreateSubscription**, **restituer**, **SetCacheOptions**, **SetExecutionOptions**, **SetReportParameters**, **SetDataDrivenSubscriptionProperties**, **SetSubscriptionProperties**|**rsReportParameterTypeMismatch**|  
|**CreateSchedule**, **CreateSubscription**, **DeleteSchedule**, **PauseSchedule**, **ResumeSchedule**, **SetCacheOptions**, **SetExecutionOptions**, **SetScheduleProperties**, **SetSubscriptionProperties**|**rsSchedulerNotResponding**|  
|**DeleteSchedule**, **GetScheduleProperties**, **ListScheduledReports**, **PauseSchedule**, **ResumeSchedule**, **SetCacheOptions**, **SetExecutionOptions**, **SetScheduleProperties**|**rsScheduleNotFound**|  
|**CreateDataDrivenSubscriptionProperties**, **CreateSubscription**, **restituer**, **SetReportParameters**, **SetDataDrivenSubscriptionProperties**, **SetSubscriptionProperties**|**rsReadOnlyReportParameter**|  
|**CreateDataDrivenSubscriptionProperties**, **CreateSubscription**, **GetReportParameters**, **restituer**, **SetReportParameters**, **SetDataDrivenSubscriptionProperties**, **SetSubscriptionProperties**|**rsUnknownReportParameter**|  
|**DeleteSubscription**, **GetDataDrivenSubscriptionProperties**, **GetSubscriptionProperties**, **SetDataDrivenSubscriptionProperties**, **SetExecutionOptions**, **SetSubscriptionProperties**|**rsSubscriptionNotFound**|  
|**CreateDataDrivenSubscription**, **CreateSubscription**, **GetExtensionSettings**, **SetDataDrivenSubscriptionProperties**, **SetSubscriptionProperties**|**rsDeliveryExtensionNotFound**|  
|**CreateDataDrivenSubscription**, **CreateSubscription**, **GetExtensionSettings**, **SetDataDrivenSubscriptionProperties**, **SetSubscriptionProperties**|**rsDeliveryError**|  
|**CreateDataDrivenSubscription**, **GetDataDrivenSubscriptionProperties**, **PrepareQuery**, **SetDataDrivenSubscriptionProperties**|**rsSecureConnectionRequired**|  
|**CreateDataDrivenSubscription**, **CreateSubscription**, **SetDataDrivenSubscriptionProperties**, **SetSubscriptionProperties**|**rsCannotSubscribeToEvent**|  
|**CreateDataDrivenSubscription**, **CreateSubscription**, **FireEvent**, **SetDataDrivenSubscriptionProperties**, **SetSubscriptionProperties**|**rsUnknownEventType**|  
|**CreateDataSource**, **CreateFolder**, **CreateLinkedReport**, **CreateReport**, **CreateResource a**, **MoveItem**|**rsItemPathLengthExceeded**|  
|**CopyItem**, **CreateFolder**, **CreateReport**, **CreateResource a**, **DeleteItem**|**rsreserveditem est**|  
|**CreateDataSource**, **SetDataSourceContents**, **SetReportDataSources**|**rsInvalidElementCombination**|  
|**SetCacheOptions**, **SetExecutionOptions**, **SetReportHistoryOptions**|**rsInvalidParameterCombination**|  
|**CreateDataSource**, **CreateFolder**, **CreateLinkedReport**, **CreateReport**, **CreateResource a**, **MoveItem**|**rsInvalidItemName**|  
|**CreateDataSource**, **CreateFolder**, **CreateLinkedReport**, **CreateReport**, **CreateResource a**, **MoveItem**|**rsItemAlreadyExists**|  
|**CreateFolder**, **CreateLinkedReport**, **CreateReport**, **CreateResource a**, **SetProperties**|**rsReadOnlyProperty**|  
|**GetPolicies**, **GetSystemPolicies**, **SetPolicies**, **SetSystemPolicies**|**rsInvalidPolicyDefinition**|  
|**SetCacheOptions**, **SetDataSourceContents**, **SetReportDataSources**, **SetReportParameters**|**rsOperationPreventsUnattendedExecution**|  
|**CreateReportHistorySnapshot**, **restituer**, **PrepareQuery**, **UpdateReportExecutionSnapshot**|**rsInvalidDataSourceReference**|  
|**CreateReportHistorySnapshot**, **PrepareQuery**, **restituer**, **UpdateReportExecutionSnapshot**|**rsDataSourceDisabled**|  
|**CreateReport**, **PrepareQuery**, **SetReportDefinition**|**rsProcessingError**|  
|**GetRenderResource**, **restituer**, **RenderStream**|**rsInvalidReportLink**|  
|**DeleteReportHistorySnapshot**, **restituer**, **RenderStream**|**rsReportHistoryNotFound**|  
|**SetCacheOptions**, **SetExecutionOptions**, **SetReportHistoryOptions**|**rsReportMayNotBeScheduled**|  
|**CreateDataDrivenSubscription**, **GetDataDrivenSubscriptionProperties**, **SetDataDrivenSubscriptionProperties**|**rsOperationNotSupported**|  
|**CreateDataSource**, **SetDataSourceContents**, **SetReportDataSources**|**rsDataExtensionNotFound**|  
|**DeleteRole**, **SetPolicies**, **SetRoleProperties**|**rsRoleNotFound**|  
|**DeleteReportHistorySnapshot**, **restituer**, **RenderStream**|**rsParametersNotSpecified**|  
|**GetReportParameters**, **SetReportParameters**|**rsNotSupported**|  
|**SetReportParameters**, **UpdateReportExecutionSnapshot**|**rsReportSnapshotNotEnabled**|  
|**CreateSchedule**, **SetScheduleProperties**|**rsScheduleAlreadyExists**|  
|**CreateRole**, **SetRoleProperties**|**rsTaskNotFound**|  
|**CreateRole**, **SetRoleProperties**|**rsMixedTasks**|  
|**ListSubscriptions**, **SetPolicies**|**rsUnknownUserName**|  
|**MoveItem**|**rsInvalidMove**|  
|**RenderStream**|**rsStreamNotFound**|  
|**RenderStream**|**rsMissingSessionId**|  
|**Render**|**rsReportNotReady**|  
|**Render**|**rsAssemblyNotPermissioned**|  
|**SetExecutionOptions**|**rsReportSnapshotEnabled**|  
|**FindItems**|**rsInvalidSearchOperator**|  
|**SetReportDataSources**|**rsDataSourceNotFound**|  
|**PrepareQuery**, **de rendu**|**rsDataSourceNoPrompt**|  
|**PrepareQuery**|**rsCannotPrepareQuery**|  
|**DeleteRole**|**rsReservedRole**|  
|**CreateRole**|**rsEmptyRole**|  
|**InheritParentSecurity**|**rsInheritedPolicy**|  
|**CreateRole**|**rsRoleAlreadyExists**|  
|**InheritParentSecurity**|**rsCannotDeleteRootPolicy**|  
|**CancelJob**|**rsJobWasCanceled**|  
|**ListSecureMethods**|**rsServerConfigurationError**|  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de gestion des exceptions dans Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Erreurs et événements référence &#40; Reporting Services &#41;](../../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)   
 [Classe SoapException Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)   
 [À l’aide de la propriété Detail pour gérer les erreurs spécifiques](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
