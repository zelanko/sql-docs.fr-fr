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
manager: craigg
ms.openlocfilehash: bfeff5eae569b481edfcc1cacc89c26e44edaece
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952374"
---
# <a name="sql-server-2005-report-server-web-service-group-detected-upgrade-advisor"></a>Le groupe de service Web du serveur de rapports SQL Server 2005 a été détecté (Conseiller de mise à niveau)
  Le conseiller de mise à niveau a détecté que l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est associée à un groupe de service Web du serveur de rapports [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] n’utilise pas le groupe de service Web du serveur de rapports [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Lorsque vous effectuez une mise à niveau de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], ce groupe de service est supprimé et les listes de contrôle d'accès personnalisées pour ce groupe ou les utilisateurs qui appartiennent au groupe ne sont pas conservés pendant la mise à niveau.  
  
## <a name="corrective-action"></a>Action corrective  
 Avant de procéder à la mise à niveau, sauvegardez toutes les listes de contrôle d'accès personnalisées ou tous les utilisateurs qui appartiennent au groupe de service Web Report Server [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Pour ce faire, vous pouvez utiliser l’outil en ligne de commande **icacls. exe** dans [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2 et versions ultérieures ou l’outil de ligne de commande cacls. exe dans les systèmes d’exploitation Windows antérieurs à [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2. Pour plus d'informations sur la syntaxe utilisée dans ces outils, consultez la documentation produit de Windows. Une fois l'installation terminée, appliquez les listes de contrôle d'accès personnalisées ou les utilisateurs au groupe Windows Report Server [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour votre instance du serveur de rapports. Le groupe Windows du serveur de rapports [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] prend la forme SQLServerReportServerUser $ \<*nom_ordinateur*>$ @ no__t-4*nom_instance*>.  
  
## <a name="see-also"></a>Voir aussi  
 [Conseiller de mise &#40;à niveau des problèmes de mise à niveau Reporting Services&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
