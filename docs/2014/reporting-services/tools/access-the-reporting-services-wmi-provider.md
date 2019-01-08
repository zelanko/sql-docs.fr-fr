---
title: Accéder au fournisseur WMI de Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- Reporting Services WMI Provider
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WMI provider [Reporting Services]
- programming [Reporting Services]
ms.assetid: 22cfbeb8-4ea3-4182-8f54-3341c771e87b
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e021f38487c744124cc06a62ce2627d7097aedb8
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53367681"
---
# <a name="access-the-reporting-services-wmi-provider"></a>Accéder au fournisseur WMI de Reporting Services
  Le fournisseur WMI de Reporting Services présente deux classes WMI pour l'administration des instances de serveur de rapports en mode natif par script :  
  
> [!IMPORTANT]  
>  À compter de la version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , le fournisseur WMI est pris en charge uniquement pour les serveurs de rapports en mode natif. Les serveurs de rapports en mode SharePoint peuvent être gérés avec les scripts PowerShell et les pages de l'Administration centrale de SharePoint.  
  
|Classe|Espace de noms|Description|  
|-----------|---------------|-----------------|  
|MSReportServer_Instance|root\Microsoft\SqlServer\ReportServer\RS_*\<EncodedInstanceName >* \v11|Fournit les informations de base nécessaires à un client pour établir la connexion à un serveur de rapports installé.|  
|MSReportServer_ConfigurationSetting|root\Microsoft\SqlServer\ReportServer\RS_*\<EncodedInstanceName >* \v11\Admin|Représente les paramètres d'installation et d'exécution d'une instance de serveur de rapports. Ces paramètres sont stockés dans le fichier de configuration du serveur de rapports.<br /><br /> **\*\* Important \*\*** Cette classe est accessible uniquement avec des privilèges d’administrateur.|  
  
 Une instance de chaque classe ci-dessus est créée pour chaque instance du serveur de rapports. Vous pouvez utiliser tous les outils Microsoft ou tiers pour accéder aux objets WMI exposés par le serveur de rapports, notamment les interfaces de programmation WMI exposées par .NET framework lui-même. Cette rubrique décrit comment accéder aux instances de classes WMI, et les utiliser, avec la commande PowerShell [Get-WmiObject](https://technet.microsoft.com/library/dd315295.aspx).  
  
## <a name="determine-the-instance-name-in-the-namespace-string"></a>Déterminez le nom de l'instance dans la chaîne de l'espace de noms  
 Le nom de l'instance dans le chemin d'accès de l'espace de noms pour les classes WMI de Reporting Services est un encodage des noms d'instance que vous spécifiez lors de l'installation des instances nommées Reporting Services. À savoir, les caractères spéciaux dans les noms d'instance sont encodés. Par exemple, un trait de soulignement (_) étant encodé en « _5f », le nom d’instance « Mon_instance » est encodé en « Mon_5finstance » dans le chemin de l’espace de noms WMI.  
  
 Pour répertorier les noms d'instance encodés de vos instances de serveur de rapports dans le chemin d'accès de l'espace de noms WMI, utilisez la commande suivante PowerShell :  
  
```  
PS C:\windows\system32> Get-WmiObject -namespace root\Microsoft\SqlServer\ReportServer  -class __Namespace -ComputerName hostname | select Name  
```  
  
## <a name="access-the-wmi-classes-using-powershell"></a>Accédez aux classes WMI à l'aide de PowerShell  
 Pour accéder aux classes WMI, exécutez la commande suivante :  
  
```  
PS C:\windows\system32> Get-WmiObject -namespace <namespacename> -class <classname> -ComputerName <hostname>  
```  
  
 Par exemple, pour accéder à la classe MSReportServer_ConfigurationSetting sur l'instance de serveur de rapports par défaut de l'hôte myrshost, exécutez la commande suivante. L'instance du serveur de rapports par défaut doit être installée sur myrshost pour que cette commande réussisse.  
  
```  
PS C:\windows\system32> Get-WmiObject -namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLSERER\v11\Admin" -class MSReportServer_ConfigurationSetting -ComputerName myrshost  
```  
  
 Cette syntaxe de commande génère tous les noms et valeurs de propriété de classe. Notez que toutes les instances de la classe MSReportServer_ConfigurationSetting sont retournées, même si vous accédez à la classe dans l'espace de noms de l'instance de serveur de rapports par défaut (RS_MSSQLSERVER). Par exemple, si myrshost est installé avec l'instance de serveur de rapports par défaut et une instance du serveur de rapports nommée appelées SHAREPOINT, cette commande retourne deux objets WMI et génère les noms et valeurs des propriétés pour les deux instances du serveur de rapports.  
  
 Pour retourner une instance de classe spécifique quand plusieurs instances sont retournées, utilisez le paramètre –Filter pour filtrer les résultats en fonction de propriétés à valeurs uniques comme InstanceName. Par exemple, pour retourner uniquement l'objet WMI pour l'instance de serveur de rapports par défaut, utilisez la commande suivante :  
  
```  
PS C:\windows\system32> Get-WmiObject -namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -class MSReportServer_ConfigurationSetting -ComputerName myrshost -filter "InstanceName='MSSQLSERVER'"  
```  
  
## <a name="query-the-available-methods-and-properties"></a>Interrogez les méthodes et les propriétés disponibles  
 Pour connaître les méthodes et propriétés disponibles dans l'une des classes WMI de Reporting Services, acheminez les résultats de Get-WmiObject vers la commande Get-Member. Exemple :  
  
```  
PS C:\windows\system32> Get-WmiObject -namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -class MSReportServer_ConfigurationSetting -ComputerName myrshost | Get-Member  
```  
  
 Pour obtenir une documentation sur les propriétés et méthodes des classes WMI de Reporting Services, consultez...  
  
## <a name="use-a-wmi-method-or-property"></a>Utilisez une propriété ou une méthode WMI  
 une fois que vous avez les objets WMI dans les classes de Reporting Services et que vous connaissez les propriétés et les méthodes disponibles, vous pouvez utiliser ces méthodes et propriétés. Par exemple, si vous avez une instance de serveur de rapports nommée dans le mode intégré SharePoint appelée SHAREPOINT, utilisez la séquence de commande suivante pour récupérer l'URL pour le site Administration centrale de SharePoint :  
  
```  
PS C:\windows\system32> $rsconfig = Get-WmiObject -namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -class MSReportServer_ConfigurationSetting -ComputerName myrshost -filter "InstanceName='SHAREPOINT'"  
PS C:\windows\system32> $rsconfig.GetAdminSiteUrl()  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de bibliothèque du fournisseur WMI de Reporting Services &#40;SSRS&#41;](../wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs.md)   
 [Fichier de configuration RSReportServer](../report-server/rsreportserver-config-configuration-file.md)  
  
  
