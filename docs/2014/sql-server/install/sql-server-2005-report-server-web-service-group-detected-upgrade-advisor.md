---
title: Groupe de Service Web de SQL Server 2005 Report Server détecté (Conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- deployment [Reporting Services]
ms.assetid: 699d24eb-7756-4b41-9294-ef1a94b2f267
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 4f379675a4d7b37b9eab69598f7c04bc57306d46
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66092108"
---
# <a name="sql-server-2005-report-server-web-service-group-detected-upgrade-advisor"></a>Le groupe de service Web du serveur de rapports SQL Server 2005 a été détecté (Conseiller de mise à niveau)
  Conseiller de mise à niveau a détecté que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance est associée un [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] groupe de service Web Report Server.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] n’utilise pas le [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] groupe de service Web Report Server. Lorsque vous effectuez une mise à niveau de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], ce groupe de service est supprimé et les listes de contrôle d'accès personnalisées pour ce groupe ou les utilisateurs qui appartiennent au groupe ne sont pas conservés pendant la mise à niveau.  
  
## <a name="corrective-action"></a>Action corrective  
 Avant de procéder à la mise à niveau, sauvegardez toutes les listes de contrôle d'accès personnalisées ou tous les utilisateurs qui appartiennent au groupe de service Web Report Server [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Pour ce faire, vous pouvez utiliser la **Icacls.exe** outil de ligne de commande dans [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2 et versions ultérieures ou l’outil de ligne de commande Cacls.exe dans les systèmes d’exploitation Windows antérieurs à [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2. Pour plus d'informations sur la syntaxe utilisée dans ces outils, consultez la documentation produit de Windows. Une fois l'installation terminée, appliquez les listes de contrôle d'accès personnalisées ou les utilisateurs au groupe Windows Report Server [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour votre instance du serveur de rapports. Le [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] groupe de Report Server Windows prend le formulaire de SQLServerReportServerUser$\<*Nom_Ordinateur*>$\<*nom_instance*>.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Reporting Services &#40;Conseiller de mise à niveau&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
