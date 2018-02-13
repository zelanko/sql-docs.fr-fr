---
title: "Propriété SqlServiceType (classe SqlServiceAdvancedProperty) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- SqlServiceType Property (SqlServiceAdvancedProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SqlServiceType property
ms.assetid: 20f1663a-9a14-4f14-8c1b-8aa133e272c3
caps.latest.revision: 
author: JennieHubbard
ms.author: jhubbard
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2d71f68250cb0ab7d3838df72ea41241bbcb003f
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2018
---
# <a name="sqlservicetype-property-sqlserviceadvancedproperty-class"></a>Propriété SqlServiceType (classe SqlServiceAdvancedProperty)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
Obtient le type du service managé associé à la propriété avancée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.SetBoolValue(NumValue)  
```  
  
## <a name="parts"></a>Éléments  
 *objet*  
 Objet de [classe SqlServiceAdvancedProperty](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) qui représente une propriété avancée.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur uint32 qui spécifie le type du service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="remarks"></a>Notes  
 Les valeurs retournées peuvent être les suivantes :  
  
|Type|Définition|  
|----------|----------------|  
|*1*|MSSQLSERVER est le service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|*2*|SQLSERVERAGENT est le service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent.|  
|*3*|MSFTESQL est le service du moteur de recherche en texte intégral [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|*4*|MsDtsServer est le service [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] .|  
|*5*|MSSQLServerOLAPService est le service [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .|  
|*6*|ReportServer est le service [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] .|  
|*7*|SQLBrowser est le service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Browser.|  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des Services](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
