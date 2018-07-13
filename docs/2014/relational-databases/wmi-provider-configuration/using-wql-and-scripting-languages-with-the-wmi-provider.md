---
title: À l’aide de WQL langages et de script avec le fournisseur WMI pour la gestion de Configuration | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- queries [WMI]
- scripts [WMI]
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
- WMI Provider for Configuration Management, scripts
ms.assetid: c1e64905-3c2b-4974-88f4-abf17cf7e289
caps.latest.revision: 17
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 7a55fc42e5186615dbe3e455668eb8cc5f7c199c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37202879"
---
# <a name="using-wql-and-scripting-languages-with-the-wmi-provider-for-configuration-management"></a>Utilisation des langages WQL et de script avec le fournisseur WMI pour la gestion de configuration
  Les applications de gestion accèdent aux services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et aux paramètres de réseau à l'aide des objets Fournisseur WMI (Windows Management Instrumentation) pour la gestion de configuration de deux manières :  
  
-   à l'aide d'un outil d'édition ou de requête WQL, tel que WBEMTest.exe, pour interroger l'objet défini avec le langage WQL ;  
  
-   à l'aide d'un langage de script, tel que VBScript.  
  
 Les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les paramètres de réseau peuvent être gérés par programme également à l'aide des objets managés WMI dans SMO. Pour plus d’informations sur la programmation WMI des objets gérés, consultez [la gestion des Services et des paramètres de réseau en utilisant le fournisseur WMI](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).  
  
 Le fournisseur WMI pour la gestion de configuration peut être accédé en utilisant le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console. Pour plus d’informations sur l’accès au fournisseur WMI à partir d’une interface utilisateur, consultez [la gestion des Services procédures &#40;Gestionnaire de Configuration SQL Server&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Accéder au fournisseur de WMI pour la gestion de Configuration à l’aide de WQL](access-wmi-provider-for-configuration-management-using-wql.md)   
 [Modifier les propriétés avancées du service SQL Server à l’aide de VBScript](access-wmi-provider-for-configuration-management-using-vbscript.md)  
  
  
