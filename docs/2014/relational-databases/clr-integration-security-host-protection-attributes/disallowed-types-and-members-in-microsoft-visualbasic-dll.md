---
title: Types et membres interdits dans Microsoft.VisualBasic.dll | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: 45f55646-4bf1-4493-9f72-d1363c9a9ac6
author: rothja
ms.author: jroth
ms.openlocfilehash: 9756c67e3cdfe1ff9e30127b3f8b5bf6ddcda436
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84954380"
---
# <a name="disallowed-types-and-members-in-microsoftvisualbasicdll"></a>Types et membres interdits dans Microsoft.VisualBasic.dll
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]la programmation CLR (Common Language Integration) interdit l’utilisation d’un type ou d’un membre ayant un `HostProtectionAttribute` qui spécifie une `System.Security.Permissions.HostProtectionResource` énumération avec la valeur `ExternalProcessMgmt` , `ExternalThreading` ,, `MayLeakOnAbort` `SecurityInfrastructure` , `SelfAffectingProcessMgmnt` , `SelfAffectingThreading` , **SharedState**, `Synchronization` ou `UI` . Le tableau suivant répertorie les membres et les types de l'assembly `Microsoft.VisualBasic.dll` dont les valeurs d'attribut de protection de l'hôte (HPA) sont interdites.  
  
> [!NOTE]  
>  Cette liste a été générée à partir des assemblys pris en charge. Pour plus d’informations, consultez [.NET Framework les bibliothèques prises en charge](../clr-integration/database-objects/supported-net-framework-libraries.md).  
  
|**Type ou membre**|**Valeur(s) HPA**|  
|------------------------|------------------------|  
|Microsoft.VisualBasic.ApplicationServices.ApplicationBase|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeCulture()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.ApplicationBase.get_Info()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.AssemblyInfo|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.BuiltInRoleConverter|SharedState|  
|Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.User|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.WebUser|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase|ExternalProcessMgmt|  
|Microsoft.VisualBasic.CompilerServices.HostServices|SharedState|  
|Microsoft.VisualBasic.CompilerServices.ProjectData.EndApp()|SelfAffectingProcessMgmt|  
|Microsoft.VisualBasic.CompilerServices.Utils.SetCultureInfo()|SelfAffectingThreading|  
|Microsoft.VisualBasic.DateAndTime.set_DateString()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.DateAndTime.set_TimeOfDay()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.DateAndTime.set_TimeString()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.DateAndTime.set_Today()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Audio|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Clock|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Computer|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.ComputerInfo|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Keyboard|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Mouse|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Network|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Ports|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.ServerComputer|ExternalProcessMgmt|  
|Microsoft.VisualBasic.FileIO.FileSystem|ExternalProcessMgmt|  
|Microsoft.VisualBasic.FileIO.SpecialDirectories|ExternalProcessMgmt|  
|Microsoft.VisualBasic.FileIO.TextFieldParser..ctor()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.FileSystem|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Interaction.CreateObject()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Interaction.DeleteSetting()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Interaction.GetObject()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Interaction.InputBox()|UI|  
|Microsoft.VisualBasic.Interaction.MsgBox()|UI|  
|Microsoft.VisualBasic.Logging.AspLog|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener..ctor()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.Close()|Synchronisation|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.Dispose()|Synchronisation|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.Flush()|Synchronisation|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.GetSupportedAttributes()|Synchronisation|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.TraceData()|Synchronisation|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.TraceEvent()|Synchronisation|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.Write()|Synchronisation|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.WriteLine()|Synchronisation|  
|Microsoft.VisualBasic.Logging.Log|ExternalProcessMgmt|  
|Microsoft.VisualBasic.MyServices.ClipboardProxy|ExternalProcessMgmt|  
|Microsoft.VisualBasic.MyServices.FileSystemProxy|ExternalProcessMgmt|  
|Microsoft.VisualBasic.MyServices.RegistryProxy|ExternalProcessMgmt|  
|Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy|ExternalProcessMgmt|  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs de protection de l’hôte et programmation de l’intégration du CLR](host-protection-attributes-and-clr-integration-programming.md)   
 [Types et membres interdits dans mscorlib.dll](disallowed-types-and-members-in-mscorlib-dll.md)   
 [Types et membres interdits dans System.dll](disallowed-types-and-members-in-system-dll.md)   
 [Types et membres interdits dans System.Data.dll](disallowed-types-and-members-in-system-data-dll.md)   
 [Types et membres interdits dans System.Core.dll](disallowed-types-and-members-in-system-core-dll.md)  
  
  
