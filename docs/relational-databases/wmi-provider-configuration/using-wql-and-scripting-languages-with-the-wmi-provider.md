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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d57413087b08fa4a50ab43531e7c2a32faad2fa9
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85888191"
---
# <a name="using-wql-and-scripting-languages-with-the-wmi-provider"></a>Utilisation des langages WQL et de script avec le fournisseur WMI
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Les applications de gestion accèdent aux services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et aux paramètres de réseau à l'aide des objets Fournisseur WMI (Windows Management Instrumentation) pour la gestion de configuration de deux manières :  
  
-   à l'aide d'un outil d'édition ou de requête WQL, tel que WBEMTest.exe, pour interroger l'objet défini avec le langage WQL ;  
  
-   à l'aide d'un langage de script, tel que VBScript.  
  
 Les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les paramètres de réseau peuvent être gérés par programme également à l'aide des objets managés WMI dans SMO. Pour plus d’informations sur la programmation des objets gérés par WMI, consultez [gestion des services et des paramètres réseau à l’aide du fournisseur WMI](../../relational-databases/server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).  
  
 Le fournisseur WMI pour la gestion de configuration peut être accédé en utilisant le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console. Pour plus d’informations sur l’accès au fournisseur WMI à partir d’une interface utilisateur, consultez [rubriques de procédures relatives à la gestion des Services &#40;Gestionnaire de configuration SQL Server&#41;](https://msdn.microsoft.com/library/78dee169-df0c-4c95-9af7-bf033bc9fdc6).  
  
## <a name="see-also"></a>Voir aussi  
 [Accéder au fournisseur WMI pour la gestion de la configuration à l’aide de WQL](../../relational-databases/wmi-provider-configuration/access-wmi-provider-for-configuration-management-using-wql.md)   
 [Accéder au fournisseur WMI avec VBScript](../../relational-databases/wmi-provider-configuration/access-wmi-provider-for-configuration-management-using-vbscript.md)  
  
  
