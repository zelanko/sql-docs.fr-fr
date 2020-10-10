---
title: Accéder au fournisseur WMI avec WQL et l’écriture de scripts
description: Découvrez comment accéder aux services SQL Server et aux paramètres réseau à l’aide du fournisseur WMI à l’aide d’un éditeur WQL ou d’un outil de requête ou d’un langage de script.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 52bc3bc300b1f6412ba2a4cdd3ce55ba5ca93aee
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91891249"
---
# <a name="using-wql-and-scripting-languages-with-the-wmi-provider"></a>Utilisation des langages WQL et de script avec le fournisseur WMI
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Les applications de gestion accèdent aux services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et aux paramètres de réseau à l'aide des objets Fournisseur WMI (Windows Management Instrumentation) pour la gestion de configuration de deux manières :  
  
-   à l'aide d'un outil d'édition ou de requête WQL, tel que WBEMTest.exe, pour interroger l'objet défini avec le langage WQL ;  
  
-   à l'aide d'un langage de script, tel que VBScript.  
  
 Les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les paramètres de réseau peuvent être gérés par programme également à l'aide des objets managés WMI dans SMO. Pour plus d’informations sur la programmation des objets gérés par WMI, consultez [gestion des services et des paramètres réseau à l’aide du fournisseur WMI](../../relational-databases/server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).  
  
 Le fournisseur WMI pour la gestion de configuration peut être accédé en utilisant le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console. Pour plus d’informations sur l’accès au fournisseur WMI à partir d’une interface utilisateur, consultez [rubriques de procédures relatives à la gestion des Services &#40;Gestionnaire de configuration SQL Server&#41;](../../database-engine/configure-windows/scm-services-connect-to-another-computer.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Accéder au fournisseur WMI pour la gestion de la configuration à l’aide de WQL](../../relational-databases/wmi-provider-configuration/access-wmi-provider-for-configuration-management-using-wql.md)   
 [Accéder au fournisseur WMI avec VBScript](../../relational-databases/wmi-provider-configuration/access-wmi-provider-for-configuration-management-using-vbscript.md)  
  
