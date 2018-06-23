---
title: Présentation du fournisseur WMI pour la gestion de Configuration | Documents Microsoft
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
- WMI Provider for Configuration Management, operations supported
ms.assetid: 92323972-7943-4208-bbf4-050774fb6027
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 459bb3bb7843a0f962d9747ac702da23909ca9fc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152526"
---
# <a name="understanding-the-wmi-provider-for-configuration-management"></a>Présentation du fournisseur WMI pour la gestion de la configuration
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit le fournisseur WMI pour gestion de la Configuration. Cela vous permet d'utiliser WMI (Windows Management Instrumentation) pour gérer les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les paramètres réseau client et serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ainsi que les alias de serveur. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Services, les paramètres réseau et les alias sont représentées par des objets WMI dans le root\Microsoft\SqlServer\ComputerManagement*nn* espace de noms de l’ordinateur. Une fois qu'une connexion est établie avec le fournisseur WMI sur l'ordinateur spécifié, les services, paramètres réseau et alias peuvent être interrogés à l'aide du langage WQL ou d'un langage de script.  
  
 Le fournisseur WMI est un fournisseur d'instances. Il fournit des instances de la [Classes WMI](../wmi-provider-configuration-classes/wmi-provider-for-configuration-management-classes.md) et prend en charge les opérations asynchrones suivantes.  
  
 Récupération d'instance  
 Récupération d'une instance spécifique d'un type de classe.  
  
 Énumération  
 Énumération de toutes les instances d'un type de classe.  
  
 Modification  
 Modification d'une instance spécifique d'un type de classe.  
  
 Les classes ont des méthodes qui autorisent la modification de leurs propriétés.  
  
 Suppression  
 Suppression d'une instance spécifique d'un type de classe.  
  
 Traitement des requêtes  
 Énumération des instances d'un type de classe en fonction d'un filtre.  
  
 Pour obtenir des exemples d’application de gestion à l’aide du fournisseur WMI pour la gestion de la Configuration, consultez [à l’aide de WQL et les langages de script avec le fournisseur WMI pour la gestion de la Configuration](using-wql-and-scripting-languages-with-the-wmi-provider.md).  
  
 Pour plus d’informations sur la programmation d’applications de gestion à l’aide du fournisseur WMI, consultez la documentation WMI dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] du SDK .NET Framework.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du fournisseur WMI pour la gestion de la Configuration](working-with-the-wmi-provider-for-configuration-management.md)   
 [À l’aide de WQL ou langage de script avec le fournisseur WMI pour la gestion de la Configuration](using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  