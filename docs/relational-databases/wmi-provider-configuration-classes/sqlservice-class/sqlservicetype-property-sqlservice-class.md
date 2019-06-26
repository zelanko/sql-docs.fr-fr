---
title: Sqlservicetype, propriété (classe SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SqlServiceType Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SqlServiceType property
ms.assetid: dbff2968-3011-41d6-a141-52d814af0213
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 778316994f607201d45f93c60f9c57a9dce4160c
ms.sourcegitcommit: 20d24654e056561fc33cadc25eca8b4e7f214b1b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67351590"
---
# <a name="sqlservicetype-property-sqlservice-class"></a>Propriété SqlServiceType (classe SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Obtient le type du service managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.SqlServiceType [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) qui représente le service.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur uint32 qui spécifie le type du service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="remarks"></a>Notes  
 Les valeurs retournées peuvent être les suivantes :  
  
|type|Définition|  
|----------|----------------|  
|*1*|MSSQLSERVER est le service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|*2*|SQLSERVERAGENT est le service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent.|  
|*3*|MSFTESQL est le service du moteur de recherche en texte intégral [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|*4*|MsDtsServer est le service [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] .|  
|*5*|MSSQLServerOLAPService est le service [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .|  
|*6*|ReportServer est le service [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] .|  
|*7*|SQLBrowser est le service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Browser.|  
|*8*|NsService est le [!INCLUDE[ssNoVersion](../../../includes/ssns-md.md)] service de Notification.|  
|*9*|MSSQLFDLauncher est le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service Lanceur de démon de filtre de recherche en texte intégral.|  
|*10*|SQLPBENGINE est le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service de moteur Polybase.|  
|*11*|SQLPBDMS est le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service de déplacement de données Polybase.|  
|*12*|MSSQLLaunchpad est le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service Launchpad.|  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
