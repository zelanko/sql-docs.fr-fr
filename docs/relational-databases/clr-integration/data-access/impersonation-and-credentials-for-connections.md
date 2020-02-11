---
title: Emprunt d’identité et informations d’identification pour les connexions | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- impersonation [CLR integration]
- security [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- authentication [CLR integration]
- user impersonation [CLR integration]
- credentials [CLR integration]
- database objects [CLR integration], security
ms.assetid: 293dce7d-1db2-4657-992f-8c583d6e9ebb
author: rothja
ms.author: jroth
ms.openlocfilehash: d83ee1d69e7083931a2f6e6befb89912abec43f0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138679"
---
# <a name="impersonation-and-credentials-for-connections"></a>Emprunt d'identité et informations d'identification pour les connexions
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Dans l'intégration du CLR (Common Language Runtime) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'authentification Windows est complexe à utiliser, mais elle offre une protection supérieure à l'authentification SQL Server. Lorsque vous utilisez l'authentification Windows, gardez à l'esprit les points suivants.  
  
 Par défaut, un processus SQL Server qui se connecte à Windows acquiert le contexte de sécurité du compte de service Windows SQL Server. Mais il est possible de mapper une fonction CLR à une identité de proxy afin que ses connexions sortantes aient un contexte de sécurité différent de celui du compte de service Windows.  
  
 Dans certains cas, vous souhaiterez peut-être emprunter l’identité de l’appelant à l’aide de la propriété **SqlContext. WindowsIdentity** au lieu de s’exécuter en tant que compte de service. L’instance **WindowsIdentity** représente l’identité du client qui a appelé le code appelant et n’est disponible que lorsque le client a utilisé l’authentification Windows. Une fois que vous avez obtenu l’instance **WindowsIdentity** , vous pouvez appeler **Impersonate** pour modifier le jeton de sécurité du thread, puis ouvrir les connexions ADO.net pour le compte du client.  
  
 Une fois que vous avez appelé SQLContext. WindowsIdentity. Impersonate, vous ne pouvez pas accéder aux données locales et vous ne pouvez pas accéder aux données système. Pour accéder à nouveau aux données, vous devez appeler WindowsImpersonationContext. Undo.  
  
 L’exemple suivant montre comment emprunter l’identité de l’appelant à l’aide de la propriété **SqlContext. WindowsIdentity** .  
  
 Visual C#   
  
```  
WindowsIdentity clientId = null;  
WindowsImpersonationContext impersonatedUser = null;  
  
clientId = SqlContext.WindowsIdentity;  
  
// This outer try block is used to protect from   
// exception filter attacks which would prevent  
// the inner finally block from executing and   
// resetting the impersonation.  
try  
{  
   try  
   {  
      impersonatedUser = clientId.Impersonate();  
      if (impersonatedUser != null)  
         return GetFileDetails(directoryPath);  
         else return null;  
   }  
   finally  
   {  
      if (impersonatedUser != null)  
         impersonatedUser.Undo();  
   }  
}  
catch  
{  
   throw;  
}  
```  
  
> [!NOTE]  
>  Pour plus d’informations sur les changements de comportement dans l’emprunt d’identité, consultez [modifications critiques apportées aux fonctionnalités de moteur de base de données dans SQL Server 2016](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md).  
  
 Par ailleurs, si vous avez obtenu l'instance de l'identité [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, vous ne pouvez pas, par défaut, propager cette instance à un autre ordinateur, cette opération étant restreinte par défaut par l'infrastructure de sécurité Windows. Il existe cependant un mécanisme, appelé « délégation », qui permet la propagation d'identités Windows sur plusieurs ordinateurs approuvés. Pour plus d’informations sur la délégation, consultez l’article TechNet «[transition de protocole Kerberos et délégation avec restriction](https://go.microsoft.com/fwlink/?LinkId=50419)».  
  
## <a name="see-also"></a>Voir aussi  
 [Objet SqlContext](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
  
  
