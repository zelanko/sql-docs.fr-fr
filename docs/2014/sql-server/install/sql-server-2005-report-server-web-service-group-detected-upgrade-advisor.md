---
title: SQL Server groupe de services Web du serveur de rapports 2005 détecté (conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- deployment [Reporting Services]
ms.assetid: 699d24eb-7756-4b41-9294-ef1a94b2f267
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 70be2b9c4e7abd55daaa752830a73cbe6e222659
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054664"
---
# <a name="sql-server-2005-report-server-web-service-group-detected-upgrade-advisor"></a>Le groupe de service Web du serveur de rapports SQL Server 2005 a été détecté (Conseiller de mise à niveau)
  Le conseiller de mise à niveau a détecté que l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance est associée à un [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] groupe de service Web Report Server.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Mode natif.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]n’utilise pas la [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Groupe de service Web Report Server. Lorsque vous effectuez une mise à niveau de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], ce groupe de service est supprimé et les listes de contrôle d'accès personnalisées pour ce groupe ou les utilisateurs qui appartiennent au groupe ne sont pas conservés pendant la mise à niveau.  
  
## <a name="corrective-action"></a>Action corrective  
 Avant de procéder à la mise à niveau, sauvegardez toutes les listes de contrôle d'accès personnalisées ou tous les utilisateurs qui appartiennent au groupe de service Web Report Server [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Pour ce faire, vous pouvez utiliser l’outil en ligne de commande **Icacls.exe** dans [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2 (ou version ultérieure) ou l’outil de ligne de commande Cacls.exe dans les systèmes d’exploitation Windows antérieurs à [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2. Pour plus d'informations sur la syntaxe utilisée dans ces outils, consultez la documentation produit de Windows. Une fois l'installation terminée, appliquez les listes de contrôle d'accès personnalisées ou les utilisateurs au groupe Windows Report Server [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour votre instance du serveur de rapports. Le [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] groupe Windows du serveur de rapports prend la forme SQLServerReportServerUser $ \<*computer_name*> $ \<*instance_name*> .  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau de Reporting Services &#40;conseiller de mise à niveau&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
