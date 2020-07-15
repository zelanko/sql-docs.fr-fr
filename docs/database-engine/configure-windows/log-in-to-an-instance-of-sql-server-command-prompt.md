---
title: Se connecter à une instance de SQL Server (via l’invite de commandes) | Microsoft Docs
description: Découvrez l’utilitaire « sqlcmd ». Découvrez comment l’utiliser dans une invite de commandes pour tester la connectivité à une instance de SQL Server.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], named instance of SQL Server
- log ins [SQL Server]
- logins [SQL Server], default instance of SQL Server
- command prompt [SQL Server], logins
- logging in [SQL Server]
ms.assetid: f67c11e3-c519-40c9-82c1-07efa9d9985e
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0723a5d463757eca93dd7bacb1fc2b8fe232cdd8
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772409"
---
# <a name="log-in-to-an-instance-of-sql-server-command-prompt"></a>Se connecter à une instance de SQL Server (via l'invite de commandes)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette rubrique explique comment tester la connectivité à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]avec l'utilitaire **sqlcmd** .  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-log-in-to-the-default-instance-of-sql-server"></a>Pour se connecter à l’instance par défaut de SQL Server  
  
1.  À partir d'une invite de commandes, saisissez la commande suivante afin de vérifier vos informations d'identification par l'authentification Windows :  
  
    ```  
    sqlcmd [ /E ] [ /S servername ]  
  
    ```  
  
#### <a name="to-log-in-to-a-named-instance-of-sql-server"></a>Pour se connecter à une instance nommée de SQL Server  
  
1.  À partir d'une invite de commandes, saisissez la commande suivante afin de vérifier vos informations d'identification par l'authentification Windows :  
  
    ```  
    sqlcmd [ /E ] /S servername\instancename  
  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire sqlcmd](../../tools/sqlcmd-utility.md)   
 [Utilitaire osql](../../tools/osql-utility.md)  
  
  
